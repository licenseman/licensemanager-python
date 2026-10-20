# ProductList


## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**data** | [**List[Product]**](Product.md) | Items of the page, in the requested order. Empty past the last page. | 
**pagination** | [**Pagination**](Pagination.md) |  | 

## Example

```python
from licensemanager.models.product_list import ProductList

# TODO update the JSON string below
json = "{}"
# create an instance of ProductList from a JSON string
product_list_instance = ProductList.from_json(json)
# print the JSON string representation of the object
print(ProductList.to_json())

# convert the object into a dict
product_list_dict = product_list_instance.to_dict()
# create an instance of ProductList from a dict
product_list_from_dict = ProductList.from_dict(product_list_dict)
```
[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)


