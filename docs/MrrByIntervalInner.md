# MrrByIntervalInner


## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**interval** | **str** |  | 
**interval_count** | **int** |  | 
**subscription_count** | **int** |  | 
**mrr** | **float** |  | 

## Example

```python
from licensemanager.models.mrr_by_interval_inner import MrrByIntervalInner

# TODO update the JSON string below
json = "{}"
# create an instance of MrrByIntervalInner from a JSON string
mrr_by_interval_inner_instance = MrrByIntervalInner.from_json(json)
# print the JSON string representation of the object
print(MrrByIntervalInner.to_json())

# convert the object into a dict
mrr_by_interval_inner_dict = mrr_by_interval_inner_instance.to_dict()
# create an instance of MrrByIntervalInner from a dict
mrr_by_interval_inner_from_dict = MrrByIntervalInner.from_dict(mrr_by_interval_inner_dict)
```
[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)


