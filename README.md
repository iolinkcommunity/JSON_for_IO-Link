# JSON_for_IO-Link

JSON serialization for IO-Link data.

## Branches:
  - master: released version (1.0)
  - version-1-x: Draft for the next version
  
  https://editor.swagger.io/?url=https://raw.githubusercontent.com/iolinkcommunity/JSON_for_IO-Link/version-1-x/JSON_for_IO-Link.yaml
  https://studio.asyncapi.com/?url=https://raw.githubusercontent.com/iolinkcommunity/JSON_for_IO-Link/version-1-x/MQTT_for_IO-Link.yaml
=======

## Linting

The Linting tool ["Spectral"](https://stoplight.io/open-source/spectral) is used for automatic validation of the specifications.
You can run it locally with the command:

```docker run --rm -v ${PWD}:/usr/src/spectral stoplight/spectral lint -r spectral.yaml  JSON_for_IO-Link.yaml ```

