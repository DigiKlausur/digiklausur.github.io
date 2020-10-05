.. _dynamic-config:

*********************
Dynamic Configuration
*********************

Zero-to-JupyterHub allows extra JupyterHub config to be added to the default config. We can change or 
override the default config through the extra configuration. 

We use this to override some single user configuration. In the helm config, we add the following extra config 
under `hub`:

.. code-block:: python

  hub:
    extraConfig:     
        00-0-override-singleuser-config.py: |
          # This config will take effects once the hub is shutdown/restart through admin panel
          # change this to /srv/jupyterhub/      
          import pandas as pd
          import yaml
          config_mount = '/srv/jupyterhub/config'
          config_file = os.path.join(config_mount, 'config.yaml')
          if os.path.isfile(config_file):
              configs = {}
              with open(config_file, 'r') as infile:
                  configs = yaml.safe_load(infile)

              hub_config = configs['server']['e2x_hub_exam_staging_01']
              c.KubeSpawner.image = "{}:{}".format(hub_config['image']['name'],hub_config['image']['tag'])
              c.KubeSpawner.image_pull_policy = hub_config['image']['pullPolicy']             
              
              if hub_config['resources']['cpu_guarantee']:
                  c.KubeSpawner.cpu_guarantee = hub_config['resources']['cpu_guarantee']
              if hub_config['resources']['cpu_limit']:
                  c.KubeSpawner.cpu_limit = hub_config['resources']['cpu_limit']
              if hub_config['resources']['mem_guarantee']:
                  c.KubeSpawner.mem_guarantee = hub_config['resources']['mem_guarantee']
              if hub_config['resources']['mem_limit']:
                  c.KubeSpawner.mem_limit = hub_config['resources']['mem_limit']
        
        00-1-prespawn-hook.py: |      
          # Find in the database how many courses this user is registered to
          # Prespawn hook and mount his/her course volumes.
          import pandas as pd
          import yaml
          #list of command to execute during spawning
          cmds = []
          async def pre_spawn_hook(spawner):
              await spawner.load_user_options()
              username = spawner.user.name
              
              #reset commands
              cmds = []
              # clear spawner attributes as Python spawner objects are peristent
              # if you dont clear them, they will be persistent across restarts
              # there may be duplicate mounts
              spawner.volume_mounts = []

              # db directory in the container
              config_root = '/srv/jupyterhub/config'
              
              # mount user home directory
              config_file = os.path.join(config_root, 'config.yaml')
              
              #list of command to be appended to file, e.g. nbgrader_config.py
              cmds.append(r"echo 'c = get_config()'  >> /etc/jupyter/nbgrader_config.py")
              #cmds.append(r"echo 'c.Exchange.timezone = '"Europe/Berlin"'' >> /etc/jupyter/nbgrader_config.py")
              #cmds.append(r"echo 'c.NbGraderAPI.timezone = '"Europe/Berlin"'' >> /etc/jupyter/nbgrader_config.py")
              if os.path.isfile(config_file):
                  configs = {}
                  with open(config_file, 'r') as infile:
                      configs = yaml.safe_load(infile)

                  hub_config = configs['server']['e2x_hub_exam_staging_01']
                  hub_mode = hub_config['mode'].lower()
                  semester_id = hub_config['semester_id'].lower()

          c.KubeSpawner.pre_spawn_hook = pre_spawn_hook        
        00-3-other-config.py: |      
          c.KubeSpawner.disable_user_config = True
        
A complete version of this extra config can be found on `our github <https://github.com/DigiKlausur/e2x-jupyterhub/tree/master/kubernetes/jupyterhub>`_

The `config.yaml` which is loaded in this extra config is yaml file which is shared by the NFS server, 
and mounted to the hub container under `/srv/jupyterhub/config`. 

.. code-block:: yaml

  server:
    e2x_hub_exam_staging_01:
      mode: exam
      semester_id: ss20
      course_list: 
        - MRC-Exam
      image:
        name: digiklausur/restricted-notebook
        tag: latest
        pullPolicy: Always
      resources:
        cpu_guarantee: 0.01
        cpu_limit: 2.0
        mem_guarantee: 0.15G
        mem_limit: 0.75G
      nbgrader:
        personalized_inbound: True
        personalized_outbound: False
        assignment_id: Klausur
      extra_mounts:
        enabled: True
        volumes: 
        volume_mounts:
          1:
            name: nfs-disk2-volume
            mountPath: /srv/shared_files/e2x_instruction
            subPath: 'shared_files/e2x_instruction'
      #Commands to be executed after spawning
      commands:
        - rm -rf $HOME/.jupyter/nbconfig*
        - FORCE_COPY=false
        - INSTRUCTION_EN=/srv/shared_files/e2x_instruction/e2x_instruction_en
        - if [ -d $INSTRUCTION_EN ] && $FORCE_COPY;then cp -r $INSTRUCTION_EN $HOME;else if [ -d $INSTRUCTION_EN ] && [ ! -d $HOME/e2x_instruction_en ];then cp -r $INSTRUCTION_EN $HOME;fi;fi  

The above config is used by `e2x_hub_exam_staging_01` hub which is deployed on Kubernetes for examination.
The complete configurations of both exam and teaching can be found on `our github repository <https://github.com/DigiKlausur/e2x-jupyterhub/tree/master/kubernetes>`_.

Currently, the changes on the single user resources (CPU and RAM) require restart on the hub in 
order to apply them. The other configuration however will reflect the single user image directly 
when they log in. The running single user requires restart on their server in order to have the 
new config. 

Extra mounts can be added too via `extra_mount` by specifying the name of the nfs volume, the mount 
path and the sub path in the nfs shared directory. Furthermore, commands after the user spawn can be 
added. This extra command is useful when you want the server to remove or add files to the user 
container.

This config is very much integrated to our system, so if you want to use it on your system, you 
should probably make some changes.