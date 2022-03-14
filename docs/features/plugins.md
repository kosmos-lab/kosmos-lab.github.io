## Plugins

The platform supports a plugin system based upon [pf4j](https://github.com/pf4j/pf4j).
Currently the only supported plugin is for cameras, but support for HTTP and Async (WebSocket|MQTT) Endpoints will be coming soon.

The repository containing the plugin Interfaces can be found on [github.com/kosmos-lab/kosmos-plugins](https://github.com/kosmos-lab/kosmos-plugins).
It currently is rather rudimentary and might change significant in a short amount of time.

???+ danger "early access/in development"
    This core feature is still in an early state and may introduce breaking changes soon

### Reolink camera plugin

To have an example for the camera plugin api the previously integrated camera system for ReoLink was moved to a plugin, you can find it on [github.com/kosmos-lab/kosmos-plugin-camera-reolink](https://github.com/kosmos-lab/kosmos-plugin-camera-reolink).

???+ bug "needs testing"
    This feature is currently only tested with the Reolink RLC-410-5MP and RLC-520-5MP, but should work for all reolink cameras
