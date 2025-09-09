# JSON_for_IO-Link

JSON serialization for IO-Link data.

## Contribution

In order to raise a bugfix, improvement or change/feature request file an issue. This issue will then be discussed by the community and the change can be done via pull request. Minor changes like typing errors can be fixed directly by a pull request and does not require opening an issue.

## Branches:

- master: released version (1.0)
- version-1-x: Draft for the next version

## Open in Swagger Editor:

https://editor.swagger.io/?url=https://raw.githubusercontent.com/iolinkcommunity/JSON_for_IO-Link/version-1-x/JSON_for_IO-Link.yaml


## Open in AsyncAPI Editor:

https://studio.asyncapi.com/?url=https://raw.githubusercontent.com/iolinkcommunity/JSON_for_IO-Link/version-1-x/MQTT_for_IO-Link.yaml

## Linting

The Linting tool ["Spectral"](https://stoplight.io/open-source/spectral) is used for automatic validation of the specifications.
You can run it locally with the command:

`docker run --rm -v ${PWD}:/usr/src/spectral stoplight/spectral lint -r spectral.yaml  JSON_for_IO-Link.yaml `

## Merge files

The OpenAPI and MQTT specification share the same schemas/examples contained by a separate files. An addtional step is included in the build process to merge all files together, in order to create only one file.

Installation of merging tool:

`npm install -g swagger-merger `

Run swagger-merger:

`swagger-merger -i MQTT_for_IO-Link.yaml schemas.yaml examples.yaml -o MQTT_for_IO-Link_merged.yaml`

`swagger-merger -i JSON_for_IO-Link.yaml schemas.yaml examples.yaml -o JSON_for_IO-Link_merged.yaml`
