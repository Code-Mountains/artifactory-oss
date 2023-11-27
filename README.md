### System Requirements
Before you install, please validate the system requirements provided here: https://service.jfrog.org/installer/System+Requirements  
​
### How to run
* `./config.sh` # should provide you an interactive install or upgrade
​
### Default credentials for PostgreSQL
username: artifactory
password: password

### Install or upgrade using docker volumes
* To use docker-volumes, the script `./config.sh` will not need to be run. Instead, For more deatils on install or upgrade using docker volumes refer below links and use the template `docker-compose-volumes.yaml`.

### MORE DETAILS 
For more details on installation scripts, refer: https://service.jfrog.org/installer/Installing+Artifactory

For more details on  Upgrade scripts, refer: https://service.jfrog.org/installer/Upgrading+Artifactory

For troubleshooting, refer: https://service.jfrog.org/installer/Troubleshooting


# Ubuntu Linux Setup:
```
sudo ./config.sh

## OUTPUT: 

$ sudo ./config.sh 


Beginning JFrog Artifactory setup


Validating System requirements

Installation Directory (Default: /root/.jfrog/artifactory): 

Running system diagnostics checks, logs can be found at [/mnt/samsung/code/artifactory/artifactory-oss/systemDiagnostics.log]
[ERROR] Router external port (8082) is being used by another process
[ERROR] Artifactory port (8081) is being used by another process

[WARN] One or more system diagnostic checks have failed, check [/mnt/samsung/code/artifactory/artifactory-oss/systemDiagnostics.log] for additional details

Triggering migration script. This will migrate if needed and may take some time.

Migration logs will be available at [/mnt/samsung/code/artifactory/artifactory-oss/bin/migration.log]. The file will be archived at [/root/.jfrog/artifactory/var/log] after installation

For IPv6 address, enclose value within square brackets as follows : [<ipv6_address>]
Please specify the IP address of this machine (Default: 127.0.0.1): 

Are you adding an additional node to an existing product cluster? [y/N]: n

The installer can install a PostgreSQL database, or you can connect to an existing compatible PostgreSQL database
(https://service.jfrog.org/installer/System+Requirements#SystemRequirements-RequirementsMatrix)
If you are upgrading from an existing installation, select N if you have externalized PostgreSQL, select Y if not.
Do you want to install PostgreSQL? [Y/n]: y

To setup PostgreSQL, please enter a password
database password: 

confirm database password: 

Creating third party directories (if necessary)

Attempting to seed PostgreSQL. This may take some time.

Successfully seeded PostgreSQL

Docker setup complete

Installation directory: [/root/.jfrog/artifactory] contains data and configurations.

Use docker-compose commands to start the application. Once the application has started, it can be accessed at [http://127.0.0.1:8082]

Examples:
cd /mnt/samsung/code/artifactory/artifactory-oss


start postgresql:    docker-compose -p rt-postgres -f docker-compose-postgres.yaml up -d
stop  postgresql:    docker-compose -p rt-postgres -f docker-compose-postgres.yaml down
start:               docker-compose -p rt up -d
stop:                docker-compose -p rt down

NOTE: The compose file uses several environment variables from the .env file. Remember to run from within the [/mnt/samsung/code/artifactory/artifactory-oss] folder

Done

```

# Start Artifactory Container:
```
docker-compose -p rt up -d

# OUTPUT :
$ docker-compose -p rt up -d
Recreating artifactory ... done

$ docker ps -a
CONTAINER ID   IMAGE                                                   COMMAND                  CREATED              STATUS              PORTS                                                                                                      NAMES
50f222835083   releases-docker.jfrog.io/jfrog/artifactory-oss:7.71.5   "/entrypoint-artifac…"   About a minute ago   Up About a minute   0.0.0.0:8081-8082->8081-8082/tcp, :::8081-8082->8081-8082/tcp, 0.0.0.0:8085->8085/tcp, :::8085->8085/tcp   artifactory
1bb594706368   releases-docker.jfrog.io/postgres:13.10-alpine          "docker-entrypoint.s…"   42 minutes ago       Up 42 minutes       0.0.0.0:5432->5432/tcp, :::5432->5432/tcp
                                           postgresql


```