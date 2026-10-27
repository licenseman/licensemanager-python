# UpdateProduct


## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**name** | **str** |  | [optional] 
**slug** | **str** | Unique within the organization. Defaults to the name, lower cased, without accents and special characters. Starts with &#x60;test_&#x60; in test products, which is added when missing, and removed in live products. | [optional] 
**portal** | [**UpdateProductPortal**](UpdateProductPortal.md) |  | [optional] 
**auto_machine_change** | **bool** | Whether a new machine validating a license already on its max machines takes the place of the license&#39;s machine validated the longest ago, rather than being refused with &#x60;machine_limit_reached&#x60;. When the replaced machine is validated again, it takes its place back and the machine that replaced it is locked. See &#x60;validateKey&#x60;. | [optional] 

## Example

```python
from licensemanager.models.update_product import UpdateProduct

# TODO update the JSON string below
json = "{}"
# create an instance of UpdateProduct from a JSON string
update_product_instance = UpdateProduct.from_json(json)
# print the JSON string representation of the object
print(UpdateProduct.to_json())

# convert the object into a dict
update_product_dict = update_product_instance.to_dict()
# create an instance of UpdateProduct from a dict
update_product_from_dict = UpdateProduct.from_dict(update_product_dict)
```
[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)


