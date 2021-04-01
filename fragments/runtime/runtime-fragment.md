# Model Runtime Fragment Specification

A model runtime provides a thorough description of the tools and frameworks needed to generate inferences using the 
model. This could be a file (or collection of files) representing the serialized model, or a containerized version of 
the model that can be run on a well-known platform. 

In order to make client-side parsing easier, all Model Runtime objects contain the same 2 top-level fields (see [Model 
Runtime Fields]). The structure of the `properties` field will depend on the specific type of runtime being described.


## Model Runtime Fields

| Field Name          | Type                | Description                                                           |
|---------------------|---------------------|-----------------------------------------------------------------------|
| `type`              | string              | The type of model runtime. Either `"docker"` or `"onnx"`.
| `properties`        | \[ONNX Fields\]\|\[Docker Fields\] | Describes the properties of the runtime environment (depends on the `"type"`). |

## Serialized Models

The spec currently only supports models serialized in the [ONNX] format.

### ONNX Fields

| Field Name       | Type           | Description                                                           |
|------------------|----------------|-----------------------------------------------------------------------|
| `format`         | string         | Always `"ONNX"` for the ONNX serialization format.                    |
| `link`           | string         | URL to the ONNX file.                                                 |
| `environment`    | [Environment]  | Description of the environment required to run the model.             |
| `code_examples`  | \[string\]     | A list of URLs to code examples demonstrating model usage.            |

## Containerized Models

The spec currently supports model containerized using [Docker].

### Docker Fields

| Field Name            | Type                  | Description                                                           |
|-----------------------|-----------------------|-----------------------------------------------------------------------|
| `format`              | string                | Always `"Docker"` for the Docker container format.                    |
| `link`                | string                | Full identifier for the model image. See the [Docker Tag Reference] for details. |
| `code_examples`       | \[string\]            | A list of URLs to code examples demonstrating model usage.            |
| `host_requirements`   | [Host Requirements]   | Description of the host requirements for running the container.       |

### Host Requirements

> **TODO:** Flesh out these fields (memory, CPU, networking, etc.). Maybe look to AWS and Azure requirements for Docker services.

[ONNX]: https://onnx.ai/index.html
[Docker]: https://www.docker.com/
[Docker Tag Reference]: https://docs.docker.com/engine/reference/commandline/tag/#extended-description
[Environment]: ../environment/environment-fragment.md
[Model Runtime Fields]: #model-runtime-fields
[Host Requirements]: #host-requirements
