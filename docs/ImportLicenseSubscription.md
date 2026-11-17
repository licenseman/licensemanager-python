# ImportLicenseSubscription

Subscription of the provider keeping the license valid, like one moved to Stripe by Lemon Squeezy's migration: its renewals then extend this license rather than creating one with a new key. Its price must be mapped to a policy of the product, which the license follows instead of `policyId`, and the license's expiration, version and money back guarantee follow the subscription like the ones it creates. Read from the provider of the product's mode, through the integration.

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**provider** | **str** | Provider of the subscription. | 
**external_id** | **str** | Id of the subscription in the provider: &#x60;sub_…&#x60; in Stripe and in Paddle. | 

## Example

```python
from licensemanager.models.import_license_subscription import ImportLicenseSubscription

# TODO update the JSON string below
json = "{}"
# create an instance of ImportLicenseSubscription from a JSON string
import_license_subscription_instance = ImportLicenseSubscription.from_json(json)
# print the JSON string representation of the object
print(ImportLicenseSubscription.to_json())

# convert the object into a dict
import_license_subscription_dict = import_license_subscription_instance.to_dict()
# create an instance of ImportLicenseSubscription from a dict
import_license_subscription_from_dict = ImportLicenseSubscription.from_dict(import_license_subscription_dict)
```
[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)


