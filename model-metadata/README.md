# Model Metadata

The Model Metadata document is the top-level structure containing all metadata pertaining to a geospatial ML model. 
Consumers of the metadata document will start here and navigate the structure of this object to extract the information 
they need regarding the model.

The attributes in the top-level Model Metadata document may be simple types (e.g. a string `model_id`) or more complex 
structures (e.g. a `training_data` section). In most cases, these attributes are documented directly in this section. 
However, in the case of more complicated sections (like `training_data`), the definitions have been moved to their own 
directory in the [`fragments`](../fragments) directory. In either case, you can start with the 
[`model-metadata.md`](./model-metadata.md) specification and follow links to the appropriate definitions.

## Directory Contents

* [`model-metadata.md`](./model-metadata.md) - The detailed Model Metadata specification, including attribute 
  definitions.