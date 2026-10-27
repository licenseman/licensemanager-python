# StripePriceRecurring

Billing period of a recurring price, `null` for a one-time price.

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**interval** | **str** |  | 
**interval_count** | **int** |  | 

## Example

```python
from licensemanager.models.stripe_price_recurring import StripePriceRecurring

# TODO update the JSON string below
json = "{}"
# create an instance of StripePriceRecurring from a JSON string
stripe_price_recurring_instance = StripePriceRecurring.from_json(json)
# print the JSON string representation of the object
print(StripePriceRecurring.to_json())

# convert the object into a dict
stripe_price_recurring_dict = stripe_price_recurring_instance.to_dict()
# create an instance of StripePriceRecurring from a dict
stripe_price_recurring_from_dict = StripePriceRecurring.from_dict(stripe_price_recurring_dict)
```
[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)


