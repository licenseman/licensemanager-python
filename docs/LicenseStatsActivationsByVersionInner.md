# LicenseStatsActivationsByVersionInner


## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**version** | **str** |  | 
**counts** | **List[int]** | Number of successful activations each day, aligned on &#x60;days&#x60;. | 

## Example

```python
from licensemanager.models.license_stats_activations_by_version_inner import LicenseStatsActivationsByVersionInner

# TODO update the JSON string below
json = "{}"
# create an instance of LicenseStatsActivationsByVersionInner from a JSON string
license_stats_activations_by_version_inner_instance = LicenseStatsActivationsByVersionInner.from_json(json)
# print the JSON string representation of the object
print(LicenseStatsActivationsByVersionInner.to_json())

# convert the object into a dict
license_stats_activations_by_version_inner_dict = license_stats_activations_by_version_inner_instance.to_dict()
# create an instance of LicenseStatsActivationsByVersionInner from a dict
license_stats_activations_by_version_inner_from_dict = LicenseStatsActivationsByVersionInner.from_dict(license_stats_activations_by_version_inner_dict)
```
[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)


