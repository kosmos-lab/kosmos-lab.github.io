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



## kubernetes example
This is an example for a kubernetes deployment, the kubernetes deployment does not setup home assistant automatically.
Kubernetes is a rather complex issue and this is only to have a starting point if needed.
We recommend using the docker-compose deployment.
```yaml
---
apiVersion: apps/v1
kind: Deployment
metadata:
  labels:
    io.kompose.service: kosmos-platform
  name: kosmos-platform
  namespace: kosmos

spec:
  replicas: 1
  selector:
    matchLabels:
      io.kompose.service: kosmos-platform
  strategy:
    type: Recreate
  template:
    metadata:
      labels:
        io.kompose.service: kosmos-platform
    spec:
      containers:
        - env:
            - name: PGID
              value: "1000"
            - name: PUID
              value: "1000"
            - name: SETUPHA
              value: "0"
            - name: USE_ROS2
              value: "0"
            - name: USERS
              value: '[{"username":"ha","password":"<update>","level":1},{"username":"admin","level":100,"password":"<update>"}]'
            - name: OWM_KEY
              value: "<update>"
          image: ghcr.io/kosmos-lab/kosmos-platform:0.8.7a
          imagePullPolicy: Always
          name: kosmos-platform
          ports:
            - containerPort: 18080
            - containerPort: 1883
          resources: {}
          volumeMounts:
            - mountPath: /app/config
              name: kosmos-platform-config
            - mountPath: /app/db
              name: kosmos-platform-db
            - mountPath: /app/plugins
              name: kosmos-platform-plugins
            - mountPath: /app/rules/rules
              name: kosmos-platform-rules
            - mountPath: /app/web/oz/assets/ui.json
              name: kosmos-platform-uijson
      restartPolicy: Always
      volumes:
        - hostPath:
            path: /gv0/kosmos/config
          name: kosmos-platform-config
        - hostPath:
            path: /gv0/kosmos/db
          name: kosmos-platform-db
        - hostPath:
            path: /gv0/kosmos/plugins
          name: kosmos-platform-plugins
        - hostPath:
            path: /gv0/kosmos/rules
          name: kosmos-platform-rules
        - hostPath:
            path: /gv0/kosmos/oz/ui.json
          name: kosmos-platform-uijson
status: {}
---
apiVersion: v1
kind: Service
metadata:
  creationTimestamp: null
  labels:
    io.kompose.service: kosmos-platform
  name: kosmos-platform
  namespace: kosmos
spec:
  type: LoadBalancer
  ports:
    - name: "18080"
      port: 18080
      targetPort: 18080
    - name: "1883"
      port: 1883
      targetPort: 1883
  selector:
    io.kompose.service: kosmos-platform
status:
  loadBalancer: {}
---  
apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
  name: kosmos
  namespace: kosmos
spec:
  rules:
    - host: "kosmos.<update>"
      http:
        paths:
          - path: /
            pathType: Prefix
            backend:
              service:
                name: kosmos-platform
                port:
                  number: 18080
```