# ProductStatsActiveMachinesByVersionInner


## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**version** | **str** | &#x60;null&#x60; for the machines that didn&#39;t send a version. | 
**count** | **int** |  | 

## Example

```python
from licensemanager.models.product_stats_active_machines_by_version_inner import ProductStatsActiveMachinesByVersionInner

# TODO update the JSON string below
json = "{}"
# create an instance of ProductStatsActiveMachinesByVersionInner from a JSON string
product_stats_active_machines_by_version_inner_instance = ProductStatsActiveMachinesByVersionInner.from_json(json)
# print the JSON string representation of the object
print(ProductStatsActiveMachinesByVersionInner.to_json())

# convert the object into a dict
product_stats_active_machines_by_version_inner_dict = product_stats_active_machines_by_version_inner_instance.to_dict()
# create an instance of ProductStatsActiveMachinesByVersionInner from a dict
product_stats_active_machines_by_version_inner_from_dict = ProductStatsActiveMachinesByVersionInner.from_dict(product_stats_active_machines_by_version_inner_dict)
```
[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)


