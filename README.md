# Geospatial ML Model Catalog \(GMLMC\) Specification

## Purpose

The number and variety of machine learning (ML) models that utilize geospatial data (e.g. satellite imagery, airborne 
observations, and physical model estimates) is growing rapidly. Many of these ML models have the potential to be 
deployed to derive useful insights for many global problems, or become benchmark baselines that empower development of 
more accurate and complex models. For this to happen, these models should be made more discoverable and usable by ML 
practitioners and data scientists. The GMLMC specification aims to address this goal through a common metadata 
definition for ML models that operate on geospatial data.

At a high level, this specification should provide sufficient information to enable search and discovery of geospatial 
ML models and answer the following questions:

* Is this model applicable to my domain (e.g. land cover, agricultural monitoring, etc.)?
* What kind of input data are required to use the model?
* Is this model applicable to the geographic region I am interested in?
* How well does this model perform under the kinds of conditions under which I will be using it?

## Getting Started

The best place to start is with the [Model Metadata](./model-metadata) spec. This describes the top-level metadata 
document for a geospatial ML model. The Model Metadata spec describes the fields that may be present in the top-level 
metadata document with links more detailed descriptions and definitions of more complex fields.

## Relation to STAC

The [SpatioTemporal Asset Catalog (STAC) spec](https://github.com/radiantearth/stac-spec) is a mature and well-defined 
standard for cataloging geospatial assets. STAC has mature specifications for describing remotely sensed data, as well 
as labeled data related to machine learning applications. The 
[Electro-Optical](https://github.com/radiantearth/stac-spec/tree/master/extensions/eo), 
[Projection](https://github.com/radiantearth/stac-spec/tree/master/extensions/projection), 
[View](https://github.com/radiantearth/stac-spec/tree/master/extensions/view), and
[SAR](https://github.com/stac-extensions/sar) extensions, among others, provide a thorough description of remotely 
sensed data from a variety of sources. Combined with the [Label](https://github.com/stac-extensions/label) extension, 
these provide a thorough description of the data required for training an ML model using remotely sensed imagery. 

The Geospatial ML Model Catalog (GMLMC) specification takes advantage of the STAC specification to describe training data 
associated with a model, and we hope that discussions relating to the GMLMC spec will help guide development of those 
standards as well.

## Stability & Versioning

This specification is a work in progress and should be considered unstable until further notice. The specification 
is not currently versioned, but we plan to begin versioning once we have a basic working draft.

## Contributing

See the [Contributing guidelines](./CONTRIBUTING.md) for more information on how you can contribute to the spec.