# CancellationStatsByReasonInner


## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**reason** | [**CancellationReason**](CancellationReason.md) |  | 
**count** | **int** |  | 

## Example

```python
from licensemanager.models.cancellation_stats_by_reason_inner import CancellationStatsByReasonInner

# TODO update the JSON string below
json = "{}"
# create an instance of CancellationStatsByReasonInner from a JSON string
cancellation_stats_by_reason_inner_instance = CancellationStatsByReasonInner.from_json(json)
# print the JSON string representation of the object
print(CancellationStatsByReasonInner.to_json())

# convert the object into a dict
cancellation_stats_by_reason_inner_dict = cancellation_stats_by_reason_inner_instance.to_dict()
# create an instance of CancellationStatsByReasonInner from a dict
cancellation_stats_by_reason_inner_from_dict = CancellationStatsByReasonInner.from_dict(cancellation_stats_by_reason_inner_dict)
```
[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)


