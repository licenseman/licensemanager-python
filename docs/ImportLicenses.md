# ImportLicenses


## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**licenses** | [**List[ImportLicense]**](ImportLicense.md) | Licenses to import, up to 500. | 

## Example

```python
from licensemanager.models.import_licenses import ImportLicenses

# TODO update the JSON string below
json = "{}"
# create an instance of ImportLicenses from a JSON string
import_licenses_instance = ImportLicenses.from_json(json)
# print the JSON string representation of the object
print(ImportLicenses.to_json())

# convert the object into a dict
import_licenses_dict = import_licenses_instance.to_dict()
# create an instance of ImportLicenses from a dict
import_licenses_from_dict = ImportLicenses.from_dict(import_licenses_dict)
```
[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)


