# ValidateKeyErrorError


## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**code** | **str** |  | 
**message** | **str** |  | 
**issues** | [**List[ErrorErrorIssuesInner]**](ErrorErrorIssuesInner.md) | Present on &#x60;validation_error&#x60; errors. | [optional] 
**latest_allowed_version** | **str** | On &#x60;version_not_allowed&#x60; errors: version of the latest stable release of the product the license allows, among the ones already released. &#x60;null&#x60; when it allows none of them. | [optional] 

## Example

```python
from licensemanager.models.validate_key_error_error import ValidateKeyErrorError

# TODO update the JSON string below
json = "{}"
# create an instance of ValidateKeyErrorError from a JSON string
validate_key_error_error_instance = ValidateKeyErrorError.from_json(json)
# print the JSON string representation of the object
print(ValidateKeyErrorError.to_json())

# convert the object into a dict
validate_key_error_error_dict = validate_key_error_error_instance.to_dict()
# create an instance of ValidateKeyErrorError from a dict
validate_key_error_error_from_dict = ValidateKeyErrorError.from_dict(validate_key_error_error_dict)
```
[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)


