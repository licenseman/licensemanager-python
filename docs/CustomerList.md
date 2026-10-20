# CustomerList


## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**data** | [**List[Customer]**](Customer.md) | Items of the page, in the requested order. Empty past the last page. | 
**pagination** | [**Pagination**](Pagination.md) |  | 

## Example

```python
from licensemanager.models.customer_list import CustomerList

# TODO update the JSON string below
json = "{}"
# create an instance of CustomerList from a JSON string
customer_list_instance = CustomerList.from_json(json)
# print the JSON string representation of the object
print(CustomerList.to_json())

# convert the object into a dict
customer_list_dict = customer_list_instance.to_dict()
# create an instance of CustomerList from a dict
customer_list_from_dict = CustomerList.from_dict(customer_list_dict)
```
[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)


