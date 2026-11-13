# PaddlePermission


## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**resource** | **str** |  | 
**access** | **str** |  | 
**scope** | **str** | Permission of the Paddle API. | 
**reason** | **str** |  | 
**optional** | **bool** | Whether the key can connect without it, losing what it&#39;s for, explained by &#x60;reason&#x60;. | 
**subscriptions** | **bool** | Whether it&#39;s only needed to sell subscriptions: checked once a recurring price is mapped. | 

## Example

```python
from licensemanager.models.paddle_permission import PaddlePermission

# TODO update the JSON string below
json = "{}"
# create an instance of PaddlePermission from a JSON string
paddle_permission_instance = PaddlePermission.from_json(json)
# print the JSON string representation of the object
print(PaddlePermission.to_json())

# convert the object into a dict
paddle_permission_dict = paddle_permission_instance.to_dict()
# create an instance of PaddlePermission from a dict
paddle_permission_from_dict = PaddlePermission.from_dict(paddle_permission_dict)
```
[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)


