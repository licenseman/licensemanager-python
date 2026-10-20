# SigningKey


## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**id** | **str** | Id of the key, in the &#x60;kid&#x60; header of the tokens it signs. | 
**algorithm** | **str** | JWT algorithm of the tokens it signs, with an Ed25519 key. | 
**public_key** | **str** | PEM encoded SPKI public key. | 
**created_at** | **datetime** |  | 

## Example

```python
from licensemanager.models.signing_key import SigningKey

# TODO update the JSON string below
json = "{}"
# create an instance of SigningKey from a JSON string
signing_key_instance = SigningKey.from_json(json)
# print the JSON string representation of the object
print(SigningKey.to_json())

# convert the object into a dict
signing_key_dict = signing_key_instance.to_dict()
# create an instance of SigningKey from a dict
signing_key_from_dict = SigningKey.from_dict(signing_key_dict)
```
[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)


