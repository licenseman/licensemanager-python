# ProductStatsActiveMachinesByCountryInner


## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**country** | **str** | ISO 3166-1 alpha-2 code of the country the machine was last successfully validated from. &#x60;null&#x60; for the machines it couldn&#39;t be located for. | 
**count** | **int** |  | 

## Example

```python
from licensemanager.models.product_stats_active_machines_by_country_inner import ProductStatsActiveMachinesByCountryInner

# TODO update the JSON string below
json = "{}"
# create an instance of ProductStatsActiveMachinesByCountryInner from a JSON string
product_stats_active_machines_by_country_inner_instance = ProductStatsActiveMachinesByCountryInner.from_json(json)
# print the JSON string representation of the object
print(ProductStatsActiveMachinesByCountryInner.to_json())

# convert the object into a dict
product_stats_active_machines_by_country_inner_dict = product_stats_active_machines_by_country_inner_instance.to_dict()
# create an instance of ProductStatsActiveMachinesByCountryInner from a dict
product_stats_active_machines_by_country_inner_from_dict = ProductStatsActiveMachinesByCountryInner.from_dict(product_stats_active_machines_by_country_inner_dict)
```
[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)


