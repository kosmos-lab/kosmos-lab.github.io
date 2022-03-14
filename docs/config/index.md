# Configuration


## config/config.json
This is the default configuration file for the KosmoS Platform.
It can be overriden by starting kosmoslab with the paramaters -c [file] or --config [file]
```json
{
   "pepper":"4nedfo7ff34opcgjbsragi1u5n",
   "jwt":"qleif5j2gr0onu3ukpdsnrrn22",
   "sql":{
      "url":"jdbc:sqlite:./db/database.sqlite",
      "maxConnections":10
   },
    "webserver":{
      "port":18080
   },
   "mqtt":{
      "port":1883,
      "host":"0.0.0.0"
   },
   "statelog":{
      "blacklist":[
         
      ],
      "whitelist":[
         
      ]
   }
}
```
### pepper
This defines the system pepper that is used, in combination with a per user salt, to hash the password.
If it does not exist it will be randomly generated. Please dont change this value manually, this will render your user database useless.

### jwt
This defines the secret used to generate JWT keys. This should never be shared with anyone. Can be changed after, but this renders all currently active tokens as invalid.
It will be automatically generated if not present.

### sql
Used to set the jdbc url for the database connection, currently optimized for sqlite.
Will be automatically set to a sqlite database at ./db/database.sqlite if not present

### webserver
This defines the configuration for the webserver
#### port
The port to listen to - if you use docker please make sure that you update this as well if you want to change the external port. The platform needs knowledge of the actual port for some features.

### mqtt
Defines the setup for the internal mqtt server.
#### port
On which port to listen for new mqtt connections.
#### host
The host to use for the socket.

### statelog
Used to define which states should actually be logged.
Checks if a device is in blacklist first, supports wildcards.
#### blacklist
If a device name or a wildcard matching the name is found here the changes will NOT be logged to the database.

#### whitelist
If a device is NOT on the blacklist but matches this list it will be logged - an empty whitelist is the same as a whitelist containing '*'.






