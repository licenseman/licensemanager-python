# LicenseList


## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**data** | [**List[License]**](License.md) | Items of the page, in the requested order. Empty past the last page. | 
**pagination** | [**Pagination**](Pagination.md) |  | 

## Example

```python
from licensemanager.models.license_list import LicenseList

# TODO update the JSON string below
json = "{}"
# create an instance of LicenseList from a JSON string
license_list_instance = LicenseList.from_json(json)
# print the JSON string representation of the object
print(LicenseList.to_json())

# convert the object into a dict
license_list_dict = license_list_instance.to_dict()
# create an instance of LicenseList from a dict
license_list_from_dict = LicenseList.from_dict(license_list_dict)
```
[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)


