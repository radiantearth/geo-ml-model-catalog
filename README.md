# Geospatial ML Model Catalog \(GMLMC\) Specification

## Purpose

The number and variety of machine learning (ML) models that utilize satellite imagery and other remotely sensed data 
is growing rapidly. Many of these models have the potential to contribute to useful insights for the 
global development community if they can be made more discoverable and usable by users who are not ML experts. This 
specification aims to address these issues through a common metadata definition for ML models that operate on remotely 
sensed data. 

At a high level, this specification should provide sufficient information to answer the following questions:

* Is this model applicable to my domain (e.g. land cover, agricultural monitoring, etc.)?
* What kind of input data are required to use the model?
* Will this model contribute to the kinds of insights I am hoping to gain?
* How well does this model perform under the kinds of conditions under which I will be using it?

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

**COMING SOON**