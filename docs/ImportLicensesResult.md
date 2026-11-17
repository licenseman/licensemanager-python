# ImportLicensesResult


## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**created** | **int** |  | 
**skipped** | **int** |  | 
**failed** | **int** |  | 
**results** | [**List[ImportLicenseResult]**](ImportLicenseResult.md) | Result of each license, in the order sent. | 

## Example

```python
from licensemanager.models.import_licenses_result import ImportLicensesResult

# TODO update the JSON string below
json = "{}"
# create an instance of ImportLicensesResult from a JSON string
import_licenses_result_instance = ImportLicensesResult.from_json(json)
# print the JSON string representation of the object
print(ImportLicensesResult.to_json())

# convert the object into a dict
import_licenses_result_dict = import_licenses_result_instance.to_dict()
# create an instance of ImportLicensesResult from a dict
import_licenses_result_from_dict = ImportLicensesResult.from_dict(import_licenses_result_dict)
```
[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)


