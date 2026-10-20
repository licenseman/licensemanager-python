# UpdateCustomer


## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**email** | **str** | Unique within the product, regardless of case. Stored lower cased. | [optional] 
**name** | **str** | Display name of the customer. &#x60;null&#x60; when unknown. Defaults to &#x60;null&#x60;. | [optional] 

## Example

```python
from licensemanager.models.update_customer import UpdateCustomer

# TODO update the JSON string below
json = "{}"
# create an instance of UpdateCustomer from a JSON string
update_customer_instance = UpdateCustomer.from_json(json)
# print the JSON string representation of the object
print(UpdateCustomer.to_json())

# convert the object into a dict
update_customer_dict = update_customer_instance.to_dict()
# create an instance of UpdateCustomer from a dict
update_customer_from_dict = UpdateCustomer.from_dict(update_customer_dict)
```
[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)


