# Environment Fragment Specification

This document describes the structure and content of an Environment object.

## Environment Fields
| Field Name              | Type               | Description                                                           |
|-------------------------|--------------------|-----------------------------------------------------------------------|
| `processor`             | [Processor]        | A description of the processor used in the environment.               |
| `operating_system`      | string             | The name of the environment's operating system. For training environments this indicates the operating system used to train the model. For runtime environments this indicates an operating system on which the model may be run. |
| `programming_language`  | string             | A string identifying the programming language used in the environment.  This should be a lower-cased string with spaces replaced by underscores (`_`). For instance, JavaScript would be `"javascript"` and Objective-C would be `"objective-c"`. |
| `dependencies`          | string             | A link to a file defining the dependencies for creating the environment. This file must be interpretable using common tools in the given `programming_language`. |

### Processor

Describes the processor used in the environment.

| Field Name        | Type      | Description                                                            |
|-------------------|-----------|------------------------------------------------------------------------|
| `number_of_cores` | number    | The number of cores required by the environment.                       |
| `processor_type`  | string    | The type of processor used. Must be either `"CPU"` or `"GPU"`          |

[Processor]: #processor