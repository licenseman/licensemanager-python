# LicenseStats


## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**var_from** | **date** | First day covered, in UTC. | 
**to** | **date** | Last day covered, in UTC: today. | 
**days** | **List[date]** | The 90 days covered, from the oldest one, in UTC. | 
**activations_by_machine** | [**List[LicenseStatsActivationsByMachineInner]**](LicenseStatsActivationsByMachineInner.md) | Machines that activated the license in the period, from the one with the most activations. | 
**activations_by_version** | [**List[LicenseStatsActivationsByVersionInner]**](LicenseStatsActivationsByVersionInner.md) | Versions of the application that activated the license in the period, from the most recent one. | 

## Example

```python
from licensemanager.models.license_stats import LicenseStats

# TODO update the JSON string below
json = "{}"
# create an instance of LicenseStats from a JSON string
license_stats_instance = LicenseStats.from_json(json)
# print the JSON string representation of the object
print(LicenseStats.to_json())

# convert the object into a dict
license_stats_dict = license_stats_instance.to_dict()
# create an instance of LicenseStats from a dict
license_stats_from_dict = LicenseStats.from_dict(license_stats_dict)
```
[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)


