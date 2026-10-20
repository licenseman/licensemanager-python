# ValidateKeyError


## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**error** | [**ValidateKeyErrorError**](ValidateKeyErrorError.md) |  | 

## Example

```python
from licensemanager.models.validate_key_error import ValidateKeyError

# TODO update the JSON string below
json = "{}"
# create an instance of ValidateKeyError from a JSON string
validate_key_error_instance = ValidateKeyError.from_json(json)
# print the JSON string representation of the object
print(ValidateKeyError.to_json())

# convert the object into a dict
validate_key_error_dict = validate_key_error_instance.to_dict()
# create an instance of ValidateKeyError from a dict
validate_key_error_from_dict = ValidateKeyError.from_dict(validate_key_error_dict)
```
[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)


