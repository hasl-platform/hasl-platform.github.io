[<<Back to index](/)

## Debugging and logging

HASL is using the standard logging facilities in Home Assistant. There is some logging of normal operations but it have been built to be as quiet as possible. Keys and APIs will mostly just log a failure to debug and retry next time. Such things do occur from time to time due to API or just Internet. However setup and other more defining actions are logged as errors to make sure you see them. However you can tweak logging:

````
logger:
  logs:
    custom_components.hasl3.core: debug       # Plattform setup and startup
    custom_components.hasl3.config: debug     # Booring.. this is setup stuff when creating sensors
    custom_components.hasl3.sensor: debug     # Mostly booring startup and keying stuff, can be needed
    custom_components.hasl3.services: debug   # Can be needed if you use services/events
    custom_components.hasl3.worker: debug     # This is the communications coordinator, can be needed
    custom_components.hasl3.slapi: debug      # This is SLAPI, the underlying library, should be needed
````