# Model Training Fragment

This document describes the structure and content of a Model Training object.

| Field Name          | Type                | Description                                                           |
|---------------------|---------------------|-----------------------------------------------------------------------|
| `created_at`        | string              | **Required.** Approximate date and time at which the model was trained. It is formatted according to [RFC 3339, section 5.6].  |
| `environment`       | [Environment]       | **Required.** Description of the environment used to train the model. |
| `data`              | [string]            | **Required.** A list of URLs, each of which points to a [STAC Collection] representing source imagery used to train the model. |

#### created_at

This field is intended to capture the approximate date and time at which the model was trained in order to give 
other developers a sense of the currency of the model. The model publisher is free to choose the exact event that 
this timestamp represents (e.g. start of model training, completion of model training, etc.). Publishers may also 
choose to use `00` for all time values if they wish to only represent a date (e.g.
`2020-02-01T00:00:00Z`). This format keeps the spec in line the datetime format requirements from
the STAC spec.

#### data

A list of URLs, each of which points to a [STAC Collection] representing input data used to train
the model. The Collection must implement the [ML AOI Extension], which describes how individual
Items are split into `train`, `test`, and `validation` sets. As per the ML AOI Extension, Items 
in the Collection will then link to Items describing either source imagery or labels (for 
supervised learning models). 

##### Source Imagery Data

The Collection referred to in the `data` field will in turn reference Items in a source imagery
Collection. This Collection should implement any [STAC Extensions] required to thoroughly describe 
the source data. For instance, a collection of optical satellite imagery should probably implement 
the [Projection], [View Geometry], and [Electro-Optical] extensions.

##### Label Data

For supervised learning models, the Collection referred to in the `data` field will in turn
reference Items in a label Collection. Items in this label Collection must implement the [Label 
Extension] and should also implement any other [STAC Extensions] that the model publisher 
believes are necessary to thoroughly describe the dataset.

The STAC [Label Extension] is intended to support the use of labeled AOIs with machine learning models and supports 
the use of both raster labels and vector labels. The extension supports labels for the following machine learning model 
types:

* Tile classification
* Tile regression
* Object detection
* Segmentation

Model publishers are encouraged to review the [Label Extension] in detail to better understand its capabilities and how
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
[Label Extension]: https://github.com/stac-extensions/label
[Input Datasets]: #input-datasets
[STAC Spec site]: https://stacspec.org/
[ML AOI Extension]: https://github.com/azavea/stac-ml-aoi-extension/tree/master/ml-aoi
