# ProductStatsNewLicensesByPolicyInner


## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**policy_id** | **str** |  | 
**by_day** | **List[float]** | Value each day, aligned on &#x60;days&#x60;. | 
**by_month** | **List[float]** | Value each month, aligned on &#x60;months&#x60;. | 

## Example

```python
from licensemanager.models.product_stats_new_licenses_by_policy_inner import ProductStatsNewLicensesByPolicyInner

# TODO update the JSON string below
json = "{}"
# create an instance of ProductStatsNewLicensesByPolicyInner from a JSON string
product_stats_new_licenses_by_policy_inner_instance = ProductStatsNewLicensesByPolicyInner.from_json(json)
# print the JSON string representation of the object
print(ProductStatsNewLicensesByPolicyInner.to_json())

# convert the object into a dict
product_stats_new_licenses_by_policy_inner_dict = product_stats_new_licenses_by_policy_inner_instance.to_dict()
# create an instance of ProductStatsNewLicensesByPolicyInner from a dict
product_stats_new_licenses_by_policy_inner_from_dict = ProductStatsNewLicensesByPolicyInner.from_dict(product_stats_new_licenses_by_policy_inner_dict)
```
[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)


