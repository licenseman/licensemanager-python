# LicenseStatsActivationsByMachineInner


## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**machine_id** | **str** |  | 
**name** | **str** |  | 
**fingerprint** | **str** |  | 
**counts** | **List[int]** | Number of successful activations each day, aligned on &#x60;days&#x60;. | 

## Example

```python
from licensemanager.models.license_stats_activations_by_machine_inner import LicenseStatsActivationsByMachineInner

# TODO update the JSON string below
json = "{}"
# create an instance of LicenseStatsActivationsByMachineInner from a JSON string
license_stats_activations_by_machine_inner_instance = LicenseStatsActivationsByMachineInner.from_json(json)
# print the JSON string representation of the object
print(LicenseStatsActivationsByMachineInner.to_json())

# convert the object into a dict
license_stats_activations_by_machine_inner_dict = license_stats_activations_by_machine_inner_instance.to_dict()
# create an instance of LicenseStatsActivationsByMachineInner from a dict
license_stats_activations_by_machine_inner_from_dict = LicenseStatsActivationsByMachineInner.from_dict(license_stats_activations_by_machine_inner_dict)
```
[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)


