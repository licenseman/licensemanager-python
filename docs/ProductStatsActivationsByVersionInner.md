# ProductStatsActivationsByVersionInner


## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**version** | **str** | &#x60;null&#x60; for the activations that didn&#39;t send a version. | 
**counts** | **List[int]** | Number of successful activations each day, aligned on &#x60;days&#x60;. | 

## Example

```python
from licensemanager.models.product_stats_activations_by_version_inner import ProductStatsActivationsByVersionInner

# TODO update the JSON string below
json = "{}"
# create an instance of ProductStatsActivationsByVersionInner from a JSON string
product_stats_activations_by_version_inner_instance = ProductStatsActivationsByVersionInner.from_json(json)
# print the JSON string representation of the object
print(ProductStatsActivationsByVersionInner.to_json())

# convert the object into a dict
product_stats_activations_by_version_inner_dict = product_stats_activations_by_version_inner_instance.to_dict()
# create an instance of ProductStatsActivationsByVersionInner from a dict
product_stats_activations_by_version_inner_from_dict = ProductStatsActivationsByVersionInner.from_dict(product_stats_activations_by_version_inner_dict)
```
[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)


