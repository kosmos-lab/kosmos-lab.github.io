# Installation

## docker-compose

You can easily install the KosmoS Platform via docker-compose.

### download from github

The simplest way to get the full KosmoS Platform via docker-compose is to check out the latest version from [github :material-github:](https://github.com/kosmos-lab/kosmos-platform).

#### download files
--8<-- "docs/install/download.md"

#### setup

Please change the paramaters of the docker-compose.yml to your likings.
You should at least change the user accounts.

#### start the containers

```shell
docker-compose up -d
```

### Start only KosmoS Platform without download

If you dont want to checkout the project and do not want to use HomeAssistant you can create your own docker-compose.yml.

#### Create and setup docker-compose.yml

=== "full KosmoS Stack"

    ```yaml
    --8<-- "kosmos-platform/docker-compose.yaml"
    ```

=== "only KosmoS platform, no HomeAssistant"

    ```yaml
    --8<-- "kosmos-platform/docker-compose.mini.yaml"

    ```

Please change the file to your liking (especially the user configuration).
Important: if you want to change the HTTP port to another port please change both instances of 18080 here and also change the port in the configuration file (see [config](/config))

#### prepare needed files and folders

--8<-- "docs/install/prepare_env.md"


#### start the container

Afterwards you can start it with:

```shell
docker-compose up -d
```


## native without docker
### download from github
--8<-- "docs/install/download.md"
### install java >= 11 (jdk14 recommended)
To start the kosmos platform java 11 or newer is needed.
Refer to [java.com](https://www.java.com/), [oracle.com](https://www.oracle.com/java/technologies/downloads/) or your distribution on how to install jre or jdk on your system.
### prepare needed files and folders
--8<-- "docs/install/prepare_env.md"

### (optional) enable execution of KREE scripts
To be able to have a working KREE instance it is needed to have python3/python3-pip installed, and download the requirements for KREE.

=== "command python3 (many linux systems)"
    ```shell
    python3 -m pip install -r rules/requirements.txt
    ```
=== "command python (windows some linux distros)"
    ```shell
    python -m pip install -r rules/requirements.txt
    ```
    

### start the application

=== "default startup (config/config.json)"
    ```shell
    java -jar target/kosmos.jar
    ``` 
    is equal to
    ```shell
    java -jar target/kosmos.jar -c config/config.json
    ``` 
=== "custom configuration file"
    ```shell
    java -jar target/kosmos.jar -c myconfig.json
    ``` 
