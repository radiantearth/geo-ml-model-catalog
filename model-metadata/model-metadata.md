# Model Metadata Specification

This document describes the structure and content of a top-level Model Metadata object.

## Model Metadata Fields

| Field                | Type               | Description                                                                         |
|----------------------|--------------------|-------------------------------------------------------------------------------------|
| `model_id`           | string             | **REQUIRED.** A unique string identifier for the model. This ID must be unique across the provider. |
| `model_type`         | [Model Type]\|string | **REQUIRED.** Identifier for the type of model. STRONGLY RECOMMENDED to use on of the standard [Model Types](#model-types), but other values are allowed. |
| `model_architecture` | string             | Identifies the model architecture used (e.g. RCNN, U-Net, etc.)                     |
| `license`            | string             | **REQUIRED.** The model's license(s). Either a SPDX [License identifier], `various` if multiple licenses apply, or `proprietary` for all other cases. |
| `authors`            | \[[Author]\]       | **REQUIRED.** List of names and contact information for the model author(s).                 |
| `citation`           | [Citation]         | Citation information related to the model.                                          |
| `training`           | [Training Info]    | **REQUIRED.** A description of the data and environment used to train the model.    |
| `inputs`             | \[[Model Input]\]  | A list of [Model Input] objects describing the names and types of model inputs.  |
| `outputs`            | \[[Model Output]\] | A list of [Model Output] objects describing the names and types of model outputs |
| `runtimes`           | \[[Runtime]\]      | A list of [Runtime] objects describing serialized or containerized versions of the model that can be used to generate inferences |
| `usage_recommendations` | [Usage Recommendations] | A description of the recommended conditions under which the model can be used. |

### Model Types

**COMING SOON**

### Author

**COMING SOON**

### Citation

**COMING SOON**

### Model Input

**COMING SOON**

### Model Output

**COMING SOON**

### Usage Recommendations

**COMING SOON**

[License identifier]: https://spdx.org/licenses/
[Runtime]: ../fragments/runtime
[Training Info]: ../fragments/training
[Author]: #author
[Citation]: #citation
[Model Input]: #model-input
[Model Output]: #model-output
[Usage Recommendations]: #usage-recommendations
