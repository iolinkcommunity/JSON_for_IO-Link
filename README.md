# IOT integration for IO-Link

In general, the functionality of gateways, masters, and devices is accessed using data in JSON format. The specification is split into an OpenAPI and AysncAPI document to describe the feature set for HTTP/REST and MQTT interfaces.

## Contribution

In order to raise a bugfix, improvement or change/feature request file an issue in the [Github Repository](https://github.com/iolinkcommunity/JSON_for_IO-Link/issues). This issue will then be discussed by the community and the change can be done via pull request. Minor changes like typing errors can be fixed directly by a pull request and does not require opening an issue.

## Linting

The Linting tool [Spectral](https://stoplight.io/open-source/spectral) is used for automatic validation of the specifications.
You can run it locally with the command:

`docker run --rm -v ${PWD}:/usr/src/spectral stoplight/spectral lint -r spectral.yaml  JSON_for_IO-Link_unmerged.yaml `

## Merge files

The schemas and examples are separated into different files in order to use the them in the OpenAPI and AsyncAPI document. This requires merging all files into on final document via `swagger-merger`.

Installation of merging tool:

`npm install -g swagger-merger `

Run swagger-merger:

`swagger-merger -i MQTT_for_IO-Link_unmerged.yaml schemas.yaml examples.yaml -o MQTT_for_IO-Link.yaml`

`swagger-merger -i JSON_for_IO-Link_unmerged.yaml schemas.yaml examples.yaml -o JSON_for_IO-Link.yaml`
