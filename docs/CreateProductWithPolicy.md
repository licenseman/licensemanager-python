# CreateProductWithPolicy


## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**name** | **str** |  | 
**slug** | **str** | Unique within the organization. Defaults to the name, lower cased, without accents and special characters. Starts with &#x60;test_&#x60; in test products, which is added when missing, and removed in live products. | [optional] 
**default_policy** | [**PolicySettings**](PolicySettings.md) |  | [optional] 
**is_test_from_product_id** | **str** | Creates a test product: a sandbox of this live product of the organization, starting with copies of its policies, releases and portal settings. | [optional] 

## Example

```python
from licensemanager.models.create_product_with_policy import CreateProductWithPolicy

# TODO update the JSON string below
json = "{}"
# create an instance of CreateProductWithPolicy from a JSON string
create_product_with_policy_instance = CreateProductWithPolicy.from_json(json)
# print the JSON string representation of the object
print(CreateProductWithPolicy.to_json())

# convert the object into a dict
create_product_with_policy_dict = create_product_with_policy_instance.to_dict()
# create an instance of CreateProductWithPolicy from a dict
create_product_with_policy_from_dict = CreateProductWithPolicy.from_dict(create_product_with_policy_dict)
```
[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)


