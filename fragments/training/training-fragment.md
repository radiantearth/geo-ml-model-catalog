# Model Training Fragment

This document describes the structure and content of a Model Training object.

| Field Name          | Type                | Description                                                           |
|---------------------|---------------------|-----------------------------------------------------------------------|
| `created_at`        | string              | **Required.** Approximate date and time at which the model was trained. It is formatted according to [RFC 3339, section 5.6].  |
| `environment`       | [Environment]       | **Required.** Description of the environment used to train the model. |
| `source_imagery`    | [string]            | **Required.** A list of URLs, each of which points to a [STAC Collection] representing source imagery used to train the model. |
| `labels`            | [string]            | A list of URLs, each of which points to a [STAC Collection] representing labels used to train the model. This is only applicable to supervised models and should be omitted for all unsupervised models. |

#### created_at

This field is intended to capture the approximate date and time at which the model was trained in order to give 
other developers a sense of the currency of the model. The model publisher is free to choose the exact event that 
this timestamp represents (e.g. start of model training, completion of model training, etc.). Publishers may also 
choose to use `00` for all time values if they wish to only represent a date (e.g. `2020-02-01T00:00:00Z`).

#### source_imagery

This field will be a list of URLs, each of which points to a [STAC Collection] representing input data used to train 
the model. This will most typically be a Collection of source images, and should implement any [STAC Extensions] 
required to thoroughly describe the source data. For instance, a collection of optical satellite imagery should probably 
implement the [Projection], [View Geometry], and [Electro-Optical] extensions.

#### labels

This field will be a list of URLs, each of which points to a [STAC Collection] representing labels used to train the 
model. The Collection must implement the [Label] extension and should also implement any other [STAC Extensions] 
that the model publisher believes are necessary to thoroughly describe the dataset.

The STAC [Label] extension is intended to support the use of labeled AOIs with machine learning models and supports 
the use of both raster labels and vector labels. The extension supports labels for the following machine learning model 
types:

* Tile classification
* Tile regression
* Object detection
* Segmentation

Model publishers are encouraged to review the [Label] extension in detail to better understand its capabilities and how
to use it to properly catalog training data. *The extension is still in the "Proposal" stage and is undergoing active 
development.* Model publishers are encouraged to contribute to the development of that specification to ensure that it 
meets the needs of the community. See the "Get Involved" section of the [STAC Spec site] for details on how to join the 
discussion.


[RFC 3339, section 5.6]: https://tools.ietf.org/html/rfc3339#section-5.6
[STAC Collection]: https://github.com/radiantearth/stac-spec/tree/master/collection-spec
[Environment]: ../environment/environment-fragment.md
[STAC Extensions]: https://stac-extensions.github.io/
[Projection]: https://github.com/stac-extensions/projection
[View Geometry]: https://github.com/stac-extensions/view
[Electro-Optical]: https://github.com/stac-extensions/eo
[Label]: https://github.com/stac-extensions/label
[Input Datasets]: #input-datasets
[STAC Spec site]: https://stacspec.org/
