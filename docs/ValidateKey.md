# ValidateKey


## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**key** | **str** | License key, compared exactly: keys are case sensitive. | 
**fingerprint** | **str** | Identifies the machine. Unique within the license. Compared exactly, case included: a different fingerprint is another machine. | 
**version** | **str** | Version of the application running on the machine, like &#x60;\&quot;1.4.2\&quot;&#x60;. Its major and minor numbers are checked against the license&#39;s &#x60;maxVersion.version&#x60;: a &#x60;v&#x60; prefix and a pre-release are accepted, &#x60;\&quot;v2.3.0-beta.1\&quot;&#x60; counting as 2.3, and a version that doesn&#39;t start with a number is refused when the license has a &#x60;maxVersion.version&#x60;. It doesn&#39;t have to be one of the product&#39;s releases. | 
**name** | **str** | Name of the machine. Replaces the current one when given. | [optional] 
**platform** | **str** | Platform of the machine. Replaces the current one when given. | [optional] 

## Example

```python
from licensemanager.models.validate_key import ValidateKey

# TODO update the JSON string below
json = "{}"
# create an instance of ValidateKey from a JSON string
validate_key_instance = ValidateKey.from_json(json)
# print the JSON string representation of the object
print(ValidateKey.to_json())

# convert the object into a dict
validate_key_dict = validate_key_instance.to_dict()
# create an instance of ValidateKey from a dict
validate_key_from_dict = ValidateKey.from_dict(validate_key_dict)
```
[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)


