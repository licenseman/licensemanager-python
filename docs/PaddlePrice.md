# PaddlePrice


## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**id** | **str** |  | 
**product_id** | **str** |  | 
**product_name** | **str** |  | 
**description** | **str** | Name or internal description of the price in Paddle. | 
**price** | [**Price**](Price.md) |  | 
**recurring** | [**StripePriceRecurring**](StripePriceRecurring.md) |  | 
**mapped** | **bool** | Whether the price already creates licenses of a product. | 

## Example

```python
from licensemanager.models.paddle_price import PaddlePrice

# TODO update the JSON string below
json = "{}"
# create an instance of PaddlePrice from a JSON string
paddle_price_instance = PaddlePrice.from_json(json)
# print the JSON string representation of the object
print(PaddlePrice.to_json())

# convert the object into a dict
paddle_price_dict = paddle_price_instance.to_dict()
# create an instance of PaddlePrice from a dict
paddle_price_from_dict = PaddlePrice.from_dict(paddle_price_dict)
```
[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)


