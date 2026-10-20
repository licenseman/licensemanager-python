# ListStripePrices200Response


## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**data** | [**List[StripePrice]**](StripePrice.md) |  | 

## Example

```python
from licensemanager.models.list_stripe_prices200_response import ListStripePrices200Response

# TODO update the JSON string below
json = "{}"
# create an instance of ListStripePrices200Response from a JSON string
list_stripe_prices200_response_instance = ListStripePrices200Response.from_json(json)
# print the JSON string representation of the object
print(ListStripePrices200Response.to_json())

# convert the object into a dict
list_stripe_prices200_response_dict = list_stripe_prices200_response_instance.to_dict()
# create an instance of ListStripePrices200Response from a dict
list_stripe_prices200_response_from_dict = ListStripePrices200Response.from_dict(list_stripe_prices200_response_dict)
```
[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)


