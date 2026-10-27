# ConnectStripe


## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**api_key** | **str** | Restricted API key of the Stripe account (&#x60;rk_live_…&#x60; for live products, &#x60;rk_test_…&#x60; for test products), with the &#x60;requiredPermissions&#x60; of &#x60;getStripeIntegration&#x60;. Without the optional ones, it connects with what they&#39;re for turned off. A secret key works too, but gives the app more access than it needs. | 

## Example

```python
from licensemanager.models.connect_stripe import ConnectStripe

# TODO update the JSON string below
json = "{}"
# create an instance of ConnectStripe from a JSON string
connect_stripe_instance = ConnectStripe.from_json(json)
# print the JSON string representation of the object
print(ConnectStripe.to_json())

# convert the object into a dict
connect_stripe_dict = connect_stripe_instance.to_dict()
# create an instance of ConnectStripe from a dict
connect_stripe_from_dict = ConnectStripe.from_dict(connect_stripe_dict)
```
[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)


