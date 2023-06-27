## Plugins

The platform supports a plugin system based upon [pf4j](https://github.com/pf4j/pf4j).

The repository containing the plugin Interfaces can be found on [github.com/kosmos-lab/kosmos-plugins](https://github.com/kosmos-lab/kosmos-plugins).
It currently is rather rudimentary and might change significant in a short amount of time.

???+ check "stable"
    This core feature is stable and heavily tested in production use.
    
### Example Plugins

There are multiple example plugins available

[github.com/kosmos-lab/kosmos-plugin-web-chat](https://github.com/kosmos-lab/kosmos-plugin-web-chat)

[github.com/kosmos-lab/kosmos-plugin-web-example](https://github.com/kosmos-lab/kosmos-plugin-web-example)

### Kiosk Plugin
This plugin is used in the BAALL to control multiple browserconnected screens.
It might also be useful for an example plugin using websockets and regular synchronous requests.

[github.com/kosmos-lab/kosmos-plugin-web-kiosk](https://github.com/kosmos-lab/kosmos-plugin-web-kiosk)
### Weather Plugin
This is a weather plugin using openweathermap.

[github.com/kosmos-lab/kosmos-plugin-weather](https://github.com/kosmos-lab/kosmos-plugin-weather)

### OSC Plugin
This is a plugin used for OpenSoundControl inside the BAALL.

[github.com/kosmos-lab/kosmos-plugin-web-osc](https://github.com/kosmos-lab/kosmos-plugin-web-osc)
### Reolink camera plugin

To have an example for the camera plugin api the previously integrated camera system for ReoLink was moved to a plugin, you can find it on [github.com/kosmos-lab/kosmos-plugin-camera-reolink](https://github.com/kosmos-lab/kosmos-plugin-camera-reolink).

???+ bug "needs testing"
    This feature is currently only tested with the Reolink RLC-410-5MP and RLC-520-5MP, but should work for all reolink cameras
