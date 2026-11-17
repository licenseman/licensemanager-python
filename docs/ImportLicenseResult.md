# ImportLicenseResult


## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**index** | **int** | Position of the license in &#x60;licenses&#x60;, from 0. | 
**key** | **str** |  | 
**status** | **str** | &#x60;created&#x60;: imported. &#x60;skipped&#x60;: a license of the product already uses the key, like one imported before: it&#39;s left as is. &#x60;failed&#x60;: not imported, see &#x60;error&#x60;. | 
**license_id** | **str** | Id of the license created, or of the one using the key. | 
**error** | [**ImportLicenseResultError**](ImportLicenseResultError.md) |  | 

## Example

```python
from licensemanager.models.import_license_result import ImportLicenseResult

# TODO update the JSON string below
json = "{}"
# create an instance of ImportLicenseResult from a JSON string
import_license_result_instance = ImportLicenseResult.from_json(json)
# print the JSON string representation of the object
print(ImportLicenseResult.to_json())

# convert the object into a dict
import_license_result_dict = import_license_result_instance.to_dict()
# create an instance of ImportLicenseResult from a dict
import_license_result_from_dict = ImportLicenseResult.from_dict(import_license_result_dict)
```
[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)


