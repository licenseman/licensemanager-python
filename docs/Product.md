# Product


## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**id** | **str** |  | 
**slug** | **str** |  | 
**name** | **str** |  | 
**is_test_from_product_id** | **str** | For test products, id of the live product they&#39;re a sandbox of. &#x60;null&#x60; for live products. | 
**logo_url** | **str** | Public URL of the product&#39;s logo, shown in the web app and the customer portal. &#x60;null&#x60; without a logo. | 
**portal** | [**PortalSettings**](PortalSettings.md) |  | 
**auto_machine_change** | **bool** | Whether a new machine validating a license already on its max machines takes the place of the license&#39;s machine validated the longest ago, rather than being refused with &#x60;machine_limit_reached&#x60;. When the replaced machine is validated again, it takes its place back and the machine that replaced it is locked. See &#x60;validateKey&#x60;. | 
**created_at** | **datetime** |  | 
**updated_at** | **datetime** |  | 

## Example

```python
from licensemanager.models.product import Product

# TODO update the JSON string below
json = "{}"
# create an instance of Product from a JSON string
product_instance = Product.from_json(json)
# print the JSON string representation of the object
print(Product.to_json())

# convert the object into a dict
product_dict = product_instance.to_dict()
# create an instance of Product from a dict
product_from_dict = Product.from_dict(product_dict)
```
[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)


