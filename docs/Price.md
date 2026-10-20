# Price

Price paid for a license. Licenses have `null` instead when it's unknown, which leaves them out of the revenue stats.

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**amount** | **float** | Amount in major units of the currency: &#x60;49.99&#x60; for $49.99, &#x60;5000&#x60; for ¥5,000. &#x60;0&#x60; for a free license. | 
**currency** | **str** | ISO 4217 code of the currency, in upper case. | 

## Example

```python
from licensemanager.models.price import Price

# TODO update the JSON string below
json = "{}"
# create an instance of Price from a JSON string
price_instance = Price.from_json(json)
# print the JSON string representation of the object
print(Price.to_json())

# convert the object into a dict
price_dict = price_instance.to_dict()
# create an instance of Price from a dict
price_from_dict = Price.from_dict(price_dict)
```
[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)


