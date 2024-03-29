# openapi-extractor

[![Test](https://github.com/onmetal/openapi-extractor/actions/workflows/test.yml/badge.svg)](https://github.com/onmetal/openapi-extractor/actions/workflows/test.yml)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg?style=flat-square)](https://makeapullrequest.com)
[![GitHub License](https://img.shields.io/static/v1?label=License&message=Apache-2.0&color=blue&style=flat-square)](LICENSE)

The `openapi-extractor` extracts the OpenAPI v2 and v3 specifications of a given Kubernetes API server.

## Installation

### From source

To install the `openapi-extractor` binary into your Go bin path run

```bash
go install github.com/onmetal/openapi-extractor/cmd/openapi-extractor@main
```

## Usage

### Command based extraction

In case you have the api server binary present, you can extract the OpenAPI specifications by running

```shell
openapi-extractor --apiserver-command=<PATH-TO-APISERVER-BIN> \
  --apiservices=<PATH-TO-APISERVICES-DIR>
```

### Go module based extraction

The [`sample`](/sample) folder contains an example on how to extract the Open API spec from an api server package. In 
our example we are using the [`onmetal-api`](https://github.com/onmetal/onmetal-api) aggregated api server.

```shell
openapi-extractor --apiserver-package=github.com/onmetal/onmetal-api/cmd/onmetal-apiserver \
  --apiserver-build-opts=mod \
  --apiservices=<PATH-TO-APISERVICES-DIR>
```

In case you want to use your own package, first `go get` it so you have to correct dependencies in your `go.mod` file and
adjust the `--apiserver-package` flag accordingly.

### Output

The extracted OpenAPI v2 and v3 files can be found in current folder where the v2 version will be stored in the `swagger.json`
file and the v3 versions will be stored in individual files per group in the `./v3` folder.

To override the location of the output pass on the `--output` flag e.g. via `--output=dev` store extract the files into
the `./dev` folder.

## Contributing

We'd love to get feedback from you. Please report bugs, suggestions or post questions by opening a GitHub issue.

## License

Copyright 2022.

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

    http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
