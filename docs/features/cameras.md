## Camera Integration

We currently support plugin based integration with Reolink cameras (see [plugins](/features/plugins)). It is possible to get the recording of a specific timeframe via the Reolink API, those videos will be stitched together, and subtitles will be automatically created for the devices the user selected. In those subtitles all changes will be displayed. It is also possible to provide a custom delay between the "recording time" and the "database time".

???+ missing "in development"
    This core feature is still in an early state and may introduce breaking changes soon, currently there is no UI to check/configure the cameras.

### Plans

[ONVIF integration](https://www.onvif.org/profiles/specifications/) with discovery and recording of current live videos and subtitle integration.
Integration of the ONVIF [recording service](https://www.onvif.org/specs/srv/rsrch/ONVIF-RecordingSearch-Service-Spec.pdf) to gather previously recorded videos.
