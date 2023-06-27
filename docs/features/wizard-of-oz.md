## KosmoS Wizard-of-Oz

The KosmoS platform has a full featured Wizard-of-Oz interface that will be automatically populated but can be (and most likely should be) manually configured to support the features and parameters needed for a given Wizard-of-Oz experiment.


```json
[
  {
    "uuid": "ubiact1",
    "name": "UbiAct",
    "body": [
      {
        "type": "select_prob",
        "property2": "gesture",
        "property": "detected_gestures",
        "show": true
      },
      {
        "type": "_displayjson",
        "property": "detected_gestures",
        "show": true
      },
      {
        "type": "display",
        "property": "gesture",
        "show": true
      },
      {
        "type": "radio_json",
        "property": "detected_gestures",
        "prefix": "set detected_gestures to",
        "options": [
          {
            "name": "hand_closed",
            "prob":  0.81
          },
          {
            "name": "hand_opened",
            "prob": 0.94
          },
          {
            "name": "none",
            "prob": 0.94
          }
        ]
      }
    ]
  }
]
```

???+ check "stable"
    The Interface is tested and used in a production environment but lacks some user experience tweaks and fixes.
