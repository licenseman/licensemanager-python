# SendLicenseKeys


## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**ids** | **List[str]** | Ids of the licenses whose keys to email, up to 100. | 

## Example

```python
from licensemanager.models.send_license_keys import SendLicenseKeys

# TODO update the JSON string below
json = "{}"
# create an instance of SendLicenseKeys from a JSON string
send_license_keys_instance = SendLicenseKeys.from_json(json)
# print the JSON string representation of the object
print(SendLicenseKeys.to_json())

# convert the object into a dict
send_license_keys_dict = send_license_keys_instance.to_dict()
# create an instance of SendLicenseKeys from a dict
send_license_keys_from_dict = SendLicenseKeys.from_dict(send_license_keys_dict)
```
[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)


