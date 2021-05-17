# Model Metadata Specification

This document describes the structure and content of a top-level Model Metadata object.

## Model Metadata Fields

| Field Name              | Type                    | Description                                                                                                                                           |
| ----------------------- | ----------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------- |
| `model_id`              | string                  | **REQUIRED.** A unique string identifier for the model. This ID must be unique across the provider.                                                   |
| `model_type`            | [Model Type]            | **REQUIRED.** Describes the learning approach, type of prediction, and model architecture.                                                            |
| `license`               | string                  | **REQUIRED.** The model's license(s). Either a SPDX [License identifier], `various` if multiple licenses apply, or `proprietary` for all other cases. |
| `contacts`              | \[[Contacts]\]          | **REQUIRED.** List of names and contact information for question and issues related to the model.                                                     |
| `citation`              | [Citation]              | Citation information related to the model.                                                                                                            |
| `training`              | [Model Training]        | **REQUIRED.** A description of the data and environment used to train the model.                                                                      |
| `inputs`                | \[[Model Input]\]       | **REQUIRED.** A list of [Model Input] objects describing the names and types of model inputs.                                                         |
| `outputs`               | \[[Model Output]\]      | **REQUIRED.** A list of [Model Output] objects describing the names and types of model outputs.                                                       |
| `runtimes`              | \[[Runtime]\]           | A list of [Runtime] objects describing serialized or containerized versions of the model that can be used to generate inferences.                     |
| `usage_recommendations` | [Usage Recommendations] | A description of the recommended conditions under which the model can be used.                                                                        |

### Model Type

This object defines the type of model based on the learning approach and type of prediction. It also allows the
publisher to provide a free-text description of the model type to cover any nuances that are not
adequately described by the other fields.

| Field Name          | Type   | Description                                                                                                                                                                                                 |
| ------------------- | ------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `learning_approach` | string | **REQUIRED.** The learning approach used to train the model. It is STRONGLY RECOMMENDED that you use one of the values in the [Learning Approach] section below, but other values are allowed.              |
| `prediction_type`   | string | **REQUIRED.** The type of prediction that the model makes. It is STRONGLY RECOMMENDED that you use one of the values in the [Prediction Type] section below, but other values are allowed.                  |
| `architecture`      | string | **REQUIRED.** Identifies the architecture employed by the model (e.g. RCNN, U-Net, etc.). This may be any string identifier, but publishers are encouraged to use well-known identifiers whenever possible. |
| `description`       | string | A free text description of the model type.                                                                                                                                                                  |

#### Learning Approach

Describes the learning approach used to train the model. It is STRONGLY RECOMMENDED that you use one of the 
following values, but other values are allowed.

* `"Supervised"`
* `"Unsupervised"`
* `"Semi-Supervised"`
* `"Reinforcement Learning"`

#### Prediction Type
Describes the type of predictions made by the model. It is STRONGLY RECOMMENDED that you use one of the 
following values, but other values are allowed. Note that not all Prediction Type values are valid
for a given [Learning Approach].

* `"Object Detection"`
* `"Classification"`
* `"Segmentation"`
* `"Regression"`

### Contacts

This object describes contact information for individuals associated with the model. These contacts
may be different than the model authors listed in [Citation] section.

| Field Name     | Type   | Description                                                       |
| -------------- | ------ | ----------------------------------------------------------------- |
| `name`         | string | **REQUIRED.** The full name of the contact.                       |
| `organization` | string | The name of the organization to which this contact is affiliated. |
| `email`        | string | **REQUIRED.** The email for this contact.                         |

### Citation

This object indicates from which publication the model originates and how the model itself should be cited or 
referenced. The object follows the [STAC Scientific Citation Extension], with 2 notable changes: (
    * There is no `sci:` prefix on the field names
    * If `doi` is present, then `citation` is also required

All field descriptions are adapted from the corresponding [STAC Scientific Citation Extension]
definitions. *As per the Scientific Citation Extension spec, at least one field is required.*

| Field Name     | Type                     | Description                                                                                                                                                                                                                                                                 |
| -------------- | ------------------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `doi`          | string                   | The DOI of the data, e.g. `10.1000/xyz123`. This MUST NOT be a DOIs link.                                                                                                                                                                                                   |
| `citation`     | string                   | The recommended human-readable reference (citation) to be used by publications citing the model. No specific citation style is suggested, but the citation should contain all information required to find the publication distinctively. **Required if `doi` is present.** |
| `publications` | \[[Publication Object]\] | List of relevant publications referencing and describing the data.                                                                                                                                                                                                          |

#### Publication Object

| Field Name | Type   | Description                                                                  |
| ---------- | ------ | ---------------------------------------------------------------------------- |
| `doi`      | string | See the description of `doi` field in the [Citation] description above.      |
| `citation` | string | See the description of `citation` field in the [Citation] description above. |

### Model Input

This object describes a single model input parameter.

| Field Name    | Type   | Description                                                                                    |
| ------------- | ------ | ---------------------------------------------------------------------------------------------- |
| `name`        | string | **REQUIRED.** The name of the parameter.                                                       |
| `type`        | string | **REQUIRED.** The data type of the parameter (e.g. `float32`).                                 |
| `shape`       | [int]  | **REQUIRED.** The shape of the parameter as an array of integers.                              |
| `description` | string | A human-readable description of the parameter that indicates what type of content is required. |

### Model Output

This object describes a single model output.

| Field Name    | Type   | Description                                                                                    |
| ------------- | ------ | ---------------------------------------------------------------------------------------------- |
| `name`        | string | **REQUIRED.** The name of the parameter.                                                       |
| `type`        | string | **REQUIRED.** The data type of the parameter (e.g. `float32`).                                 |
| `shape`       | [int]  | **REQUIRED.** The shape of the parameter as an array of integers.                              |
| `description` | string | A human-readable description of the parameter that indicates what type of content it contains. |

### Usage Recommendations

**COMING SOON**

[License identifier]: https://spdx.org/licenses/
[STAC Scientific Citation Extension]: https://github.com/radiantearth/stac-spec/tree/v1.0.0-rc.1/extensions/scientific
[Runtime]: ../fragments/runtime
[Model Training]: ../fragments/training
[Learning Approach]: #learning-approach
[Prediction Type]: #prediction-type
[Model Type]: #model-type
[Contacts]: #contacts
[Citation]: #citation
[Model Input]: #model-input
[Model Output]: #model-output
[Usage Recommendations]: #usage-recommendations
[Publication Object]: #publication-object
