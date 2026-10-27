# StripePrice


## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**id** | **str** |  | 
**product_id** | **str** |  | 
**product_name** | **str** |  | 
**nickname** | **str** |  | 
**price** | [**Price**](Price.md) |  | 
**recurring** | [**StripePriceRecurring**](StripePriceRecurring.md) |  | 
**mapped** | **bool** | Whether the price already creates licenses of a product. | 

## Example

```python
from licensemanager.models.stripe_price import StripePrice

# TODO update the JSON string below
json = "{}"
# create an instance of StripePrice from a JSON string
stripe_price_instance = StripePrice.from_json(json)
# print the JSON string representation of the object
print(StripePrice.to_json())

# convert the object into a dict
stripe_price_dict = stripe_price_instance.to_dict()
# create an instance of StripePrice from a dict
stripe_price_from_dict = StripePrice.from_dict(stripe_price_dict)
```
[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)


