# MrrByPolicyInner


## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**policy_id** | **str** |  | 
**subscription_count** | **int** |  | 
**mrr** | **float** |  | 

## Example

```python
from licensemanager.models.mrr_by_policy_inner import MrrByPolicyInner

# TODO update the JSON string below
json = "{}"
# create an instance of MrrByPolicyInner from a JSON string
mrr_by_policy_inner_instance = MrrByPolicyInner.from_json(json)
# print the JSON string representation of the object
print(MrrByPolicyInner.to_json())

# convert the object into a dict
mrr_by_policy_inner_dict = mrr_by_policy_inner_instance.to_dict()
# create an instance of MrrByPolicyInner from a dict
mrr_by_policy_inner_from_dict = MrrByPolicyInner.from_dict(mrr_by_policy_inner_dict)
```
[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)


