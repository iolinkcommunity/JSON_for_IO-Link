# JSON_for_IO-Link

JSON serialization for IO-Link data.

## Contribution

In order to raise a bugfix, improvement or change/feature request file an issue. This issue will then be discussed by the community and the change can be done via pull request. Minor changes like typing errors can be fixed directly by a pull request and does not require opening an issue.

## Branches:
  - master: released version (1.0)
  - version-1-x: Draft for the next version

## Open in Swagger Editor:  
  https://editor.swagger.io/?url=https://raw.githubusercontent.com/iolinkcommunity/JSON_for_IO-Link/version-1-x/JSON_for_IO-Link.yaml
  https://studio.asyncapi.com/?url=https://raw.githubusercontent.com/iolinkcommunity/JSON_for_IO-Link/version-1-x/MQTT_for_IO-Link.yaml

## Linting

The Linting tool ["Spectral"](https://stoplight.io/open-source/spectral) is used for automatic validation of the specifications.
You can run it locally with the command:

```docker run --rm -v ${PWD}:/usr/src/spectral stoplight/spectral lint -r spectral.yaml  JSON_for_IO-Link.yaml ```

