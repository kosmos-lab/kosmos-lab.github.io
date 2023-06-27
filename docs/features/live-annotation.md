## Live Annotation/Status website optimized for OBS

A website is available to annotate OBS live with changes in user selected entities/devices.
See [Doc](https://kosmos-lab.de/doc/#get-/obs/live).

Examples:
Just monitor "Light.Stehlampe"
```
http://localhost:18080/obs/live?username=xxx&password=xxx&uuid=light.stehlampe
```
Monitor only the sensor.temp_living
```
http://localhost:18080/obs/live?username=xxx&password=xxx&uuid=sensor.temp_living
```
Monitor all Lights and Sensors available in HomeAssistant

```
http://localhost:18080/obs/live?username=xxx&password=xxx&uuid=light.*,sensor.*
```
Everything
```
http://localhost:18080/obs/live?username=xxx&password=xxx&uuid=*
```

???+ check "stable"
    This core feature is stable and heavily tested in production use.
