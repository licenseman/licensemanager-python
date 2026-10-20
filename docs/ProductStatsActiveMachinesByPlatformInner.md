# ProductStatsActiveMachinesByPlatformInner


## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**platform** | **str** | &#x60;null&#x60; for the machines that didn&#39;t send a platform. | 
**count** | **int** |  | 

## Example

```python
from licensemanager.models.product_stats_active_machines_by_platform_inner import ProductStatsActiveMachinesByPlatformInner

# TODO update the JSON string below
json = "{}"
# create an instance of ProductStatsActiveMachinesByPlatformInner from a JSON string
product_stats_active_machines_by_platform_inner_instance = ProductStatsActiveMachinesByPlatformInner.from_json(json)
# print the JSON string representation of the object
print(ProductStatsActiveMachinesByPlatformInner.to_json())

# convert the object into a dict
product_stats_active_machines_by_platform_inner_dict = product_stats_active_machines_by_platform_inner_instance.to_dict()
# create an instance of ProductStatsActiveMachinesByPlatformInner from a dict
product_stats_active_machines_by_platform_inner_from_dict = ProductStatsActiveMachinesByPlatformInner.from_dict(product_stats_active_machines_by_platform_inner_dict)
```
[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)


