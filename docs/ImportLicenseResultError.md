# ImportLicenseResultError

Why it wasn't imported. `key_taken` when skipped. `policy_not_found`, `validation_error`, `integration_not_connected`, `integration_error`, `subscription_not_found`, `subscription_not_mapped` or `subscription_taken` when failed.

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**code** | **str** |  | 
**message** | **str** |  | 

## Example

```python
from licensemanager.models.import_license_result_error import ImportLicenseResultError

# TODO update the JSON string below
json = "{}"
# create an instance of ImportLicenseResultError from a JSON string
import_license_result_error_instance = ImportLicenseResultError.from_json(json)
# print the JSON string representation of the object
print(ImportLicenseResultError.to_json())

# convert the object into a dict
import_license_result_error_dict = import_license_result_error_instance.to_dict()
# create an instance of ImportLicenseResultError from a dict
import_license_result_error_from_dict = ImportLicenseResultError.from_dict(import_license_result_error_dict)
```
[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)


