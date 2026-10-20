# CreateProduct


## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**name** | **str** |  | 
**slug** | **str** | Unique within the organization. Defaults to the name, lower cased, without accents and special characters. Starts with &#x60;test_&#x60; in test products, which is added when missing, and removed in live products. | [optional] 

## Example

```python
from licensemanager.models.create_product import CreateProduct

# TODO update the JSON string below
json = "{}"
# create an instance of CreateProduct from a JSON string
create_product_instance = CreateProduct.from_json(json)
# print the JSON string representation of the object
print(CreateProduct.to_json())

# convert the object into a dict
create_product_dict = create_product_instance.to_dict()
# create an instance of CreateProduct from a dict
create_product_from_dict = CreateProduct.from_dict(create_product_dict)
```
[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)


