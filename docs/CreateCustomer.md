# CreateCustomer


## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**email** | **str** | Unique within the product, regardless of case. Stored lower cased. | 
**name** | **str** | Display name of the customer. &#x60;null&#x60; when unknown. Defaults to &#x60;null&#x60;. | [optional] 

## Example

```python
from licensemanager.models.create_customer import CreateCustomer

# TODO update the JSON string below
json = "{}"
# create an instance of CreateCustomer from a JSON string
create_customer_instance = CreateCustomer.from_json(json)
# print the JSON string representation of the object
print(CreateCustomer.to_json())

# convert the object into a dict
create_customer_dict = create_customer_instance.to_dict()
# create an instance of CreateCustomer from a dict
create_customer_from_dict = CreateCustomer.from_dict(create_customer_dict)
```
[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)


