## Access Control

The KosmoS Platform has advanced access control which include access control based specific users, groups and scopes.
A user that creates a Device will be the automatically added with admin access for the device.

```mermaid
graph TD
   start("User2 tries<br/>to read status<br/>of Lamp17") --> checkLampExists{"Lamp17 is a<br>known device"}
   checkLampExists -->|No| notFound("return NotFound<br>(HTTP404)"):::fail
   checkLampExists -->|Yes| checkReadScope{"Device has<br>a read scope"} -->|No| returnStatus:::success
   checkReadScope -->|Yes| checkSystemAdmin{"User is<br>system admin?"} -->|Yes| returnStatus
   checkSystemAdmin -->|No| checkUserScopeAdmin{"User has<br>admin access<br>to scope"}
   checkUserScopeAdmin -->|Yes| returnStatus("return status<br>of device")
   checkUserScopeAdmin -->|No| checkUserScopeUser{"User has<br>user access<br>to scope"}
   checkUserScopeUser -->|Yes| returnStatus
   checkUserScopeUser -->|No| forbidden("return Forbidden<br>(HTTP403)"):::fail
    classDef default font-size:12px;
    classDef success fill:#087f23,font-size:12px;
    classDef fail fill:#f44336,font-size:12px;


```

???+ check "stable"
    This core feature is stable and heavily tested in production use.
