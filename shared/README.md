# AirFlow vm with docker docker-compose, and airflow config
This is a vagrant environment using VirtualBox that builds a Ubuntu 22.04 VM. It configures Ansible on the base image and uses that to add the vagrant user to the docker group so docker and docker-compose commands do not require sudo privileges to run. It creates the following structure of files for the environment:
```
/-- Vagrantfile
|-- shared
   |-- dags
   |-- scripts
      |-- airflow
         -- check_init.sql
         -- set_init.sql
         -- init.sh
      |-- postgres
         -- 00_init.sql
    -- Dockerfile
    -- docker-compose.yaml
    -- airflow.env
    -- airflow_db.env
    -- postgres.env
```
Once the vagrant box has been brought online with `vagrant up` you can `vagrant ssh` into the machine and start up the AirFlow deployment based on the ``docker-compose.yml`` file contents.
1. ``cd /opt/airflow``
2. ``docker-compose up -d``
3. When the process finishes you can run docker ps -a to see if all the containers are running properly. If all is well, we can login to the UI.
4. Open browser and navigate to ``http://192.168.1.200:8080``
5. Login with username airflow and password airflow. 
6. For the Astro CLI addition, we nbeed to run the following command at the CLI ``curl -sSL install.astronomer.io | sudo bash -s``
7. For astro bash auto-completion we need to run the following: ``astro completion bash > ~/.bash_profile`` then source that into the working environment (shell) ``source ~/.bash_profile``

Tada! An easy way to get an AirFlow test environment on any machine that can run VirtualBox and Vagrant with enough resources to do so. Much could be added to this but for now, it is just an environment to use that is easily deployed.