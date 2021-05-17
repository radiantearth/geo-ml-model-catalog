# Usage Recommendations Specification

The Usage Recommendations section defines conditions under which the model publishers believe the
model will perform as expected. It also provides a mechanism for publishers to explicitly call out
conditions under which they believe the model is likely to not performa as expected. It is important
to note that these are *recommendations* and that they **in no way provide any guarantee of model 
performance under the given conditions**.

If no Usage Recommendation section is provided, then users should assume that the model will only
perform as expected under conditions that match those described in the [Model Training] section.
This also applies to any fields that are not present in the Usage Recommendations section. For
instance, if no `temporal` field is provided, users should assume the model will only perform as
expected for data in the time range given in the [Model Training] section.


## Usage Recommendations Fields

The `recommendations` and `cautions` fields in this section are arrays of objects that describe
conditions under which the model either should perform as expected or should *not* behave as
expected, respectively.

If the Usage Recommendations section is present, then at least one of these fields is required and
must be a non-empty array.

| Field Name        | Type                  | Description                                                                                    |
| ----------------- | --------------------- | ---------------------------------------------------------------------------------------------- |
| `recommendations` | \[[Usage Conditions]] | An array of objects describing conditions under which the model *should* perform as expected.  |
| `cautions`        | \[[Usage Conditions]] | An array of objects describing conditions under which the model *may not* perform as expected. |

## Usage Conditions

This object is used to described conditions under which model usage is either recommended (if found
in the `recommendations` list) or discouraged (if found in the `cautions` list).

| Field Name  | Type                     | Description                                                                                |
| ----------- | ------------------------ | ------------------------------------------------------------------------------------------ |
| spatial     | [Spatial Extent Object]  | The spatial extents to which the recommendation or caution applies.                        |
| temporal    | [Temporal Extent Object] | The temporal extents to which the recommendation or caution applies.                       |
| description | string                   | A human-readable description of conditions to which the recommendation or caution applies. |

### Spatial Extent Object

| Element | Type         | Description                                                                                  |
| ------- | ------------ | -------------------------------------------------------------------------------------------- |
| bbox    | \[\[number]] | **REQUIRED.** Potential *spatial extents* within which the model should perform as expected. |

The `bbox` element is an *array* whose elements are themselves arrays. Each inner array is a bounding 
box that describes a spatial extent within which the model should perform as expected.

The format of the inner bounding box arrays follows the specification outlined in the **bbox**
section of the [STAC Spatial Extent Object] documentation. However, the `bbox` element defined in
this spec differs from the `bbox` element in the STAC Spatial Extent Object in that there is no
first element that always represents the overall spatial extent. Such an overall extent might give
users the incorrect impression that the model should perform as expected anywhere within that
spatial extent, when in fact there may be only specific areas in which this is true.

### Temporal Extent Object

| Element  | Type               | Description                                                                                   |
| -------- | ------------------ | --------------------------------------------------------------------------------------------- |
| interval | \[\[string\|null]] | **REQUIRED.** Potential *temporal extents* within which the model should perform as expected. |

The `interval` element is an *array* whose elements are themselves arrays. Each inner array is an
interval array containing 2 elements, each of which may be either `null` or a timestamp. Timestamps
must follow the specifications outlined in the [STAC Temporal Extent Object] documentation.

The format of the inner interval arrays follows the specification outlined in the [STAC Temporal
Extent Object] documentation. However, the `interval` element defined in this spec differs from 
the `interval` element in the STAC Temporal Extent Object in that there is no first element that 
always represents the overall temporal extent. Such an overall extent might give users the 
incorrect impression that the model should perform as expected anywhere within that temporal range, 
when in fact there may be only specific ranges in which this is true.


[Model Training]: ../training
[Spatial Extent Object]: #spatial-extent-object
[Temporal Extent Object]: #temporal-extent-object
[Usage Conditions]: #usage-conditions
[STAC Spatial Extent Object]: https://github.com/radiantearth/stac-spec/blob/v1.0.0-rc.4/collection-spec/collection-spec.md#spatial-extent-object
[STAC Temporal Extent Object]: https://github.com/radiantearth/stac-spec/blob/v1.0.0-rc.4/collection-spec/collection-spec.md#temporal-extent-object
