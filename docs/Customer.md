# Customer


## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**id** | **str** |  | 
**product_id** | **str** |  | 
**email** | **str** |  | 
**name** | **str** | Display name of the customer. &#x60;null&#x60; when unknown. | 
**license_count** | **int** | Number of licenses of this customer. | 
**stripe_customer_id** | **str** | Id of the Stripe customer, when the customer bought licenses through the Stripe integration as a Stripe customer. &#x60;null&#x60; otherwise, e.g. for a guest checkout. | 
**created_at** | **datetime** |  | 

## Example

```python
from licensemanager.models.customer import Customer

# TODO update the JSON string below
json = "{}"
# create an instance of Customer from a JSON string
customer_instance = Customer.from_json(json)
# print the JSON string representation of the object
print(Customer.to_json())

# convert the object into a dict
customer_dict = customer_instance.to_dict()
# create an instance of Customer from a dict
customer_from_dict = Customer.from_dict(customer_dict)
```
[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)


