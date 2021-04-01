# Model Runtime Fragment

This fragment defines representations of a model as a file or container that can be used to generate inferences on new 
data. There are 2 types of model runtimes supported by the spec:

* Containerized: An image that can be used to run the model 
* Serialized: A model saved in a well-known file format

## Containerized Model Runtimes

Containerized model runtimes take the form of images that can be used to run a model using a container platform. 
[Docker] is currently the only supported containerized runtime. 

## Serialized Model Runtimes

Serialized model runtimes represent a file (or group of files) that serialize the model in such a way that it can be 
the model can be reproduced in an ML framework and used to generate inferences. [ONNX] is currently the only supported 
containerized runtime.

## Directory Contents

* [`runtime-fragment.md`](./runtime-fragment.md) - The detailed Model Runtime Fragment specification.

[Docker]: https://www.docker.com/
[ONNX]: https://onnx.ai/index.html