# StripePermission


## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**resource** | **str** |  | 
**access** | **str** |  | 
**reason** | **str** |  | 

## Example

```python
from licensemanager.models.stripe_permission import StripePermission

# TODO update the JSON string below
json = "{}"
# create an instance of StripePermission from a JSON string
stripe_permission_instance = StripePermission.from_json(json)
# print the JSON string representation of the object
print(StripePermission.to_json())

# convert the object into a dict
stripe_permission_dict = stripe_permission_instance.to_dict()
# create an instance of StripePermission from a dict
stripe_permission_from_dict = StripePermission.from_dict(stripe_permission_dict)
```
[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)


