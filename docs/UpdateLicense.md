# UpdateLicense


## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**expires_at** | **datetime** | &#x60;null&#x60; makes the license never expire. | [optional] 
**meta** | **Dict[str, Optional[object]]** | Free-form JSON object. | [optional] 
**max_machines** | **int** | Maximum number of active machines the license can be used on. &#x60;null&#x60; for no limit. | [optional] 
**max_offline_duration_seconds** | **int** | Longest the applications can run offline with the license, in seconds. At least one hour (&#x60;3600&#x60;). | [optional] 
**max_version** | [**LicenseMaxVersionInput**](LicenseMaxVersionInput.md) | Latest version of the product the license can use. The values left out are kept. | [optional] 
**price** | [**PriceInput**](PriceInput.md) |  | [optional] 

## Example

```python
from licensemanager.models.update_license import UpdateLicense

# TODO update the JSON string below
json = "{}"
# create an instance of UpdateLicense from a JSON string
update_license_instance = UpdateLicense.from_json(json)
# print the JSON string representation of the object
print(UpdateLicense.to_json())

# convert the object into a dict
update_license_dict = update_license_instance.to_dict()
# create an instance of UpdateLicense from a dict
update_license_from_dict = UpdateLicense.from_dict(update_license_dict)
```
[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)


