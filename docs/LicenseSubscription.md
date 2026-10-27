# LicenseSubscription

The Stripe subscription keeping the license valid, `null` when it isn't a subscription license. The license expires when it stops being paid, includes every update, and can't be canceled during a money back guarantee.

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**stripe_subscription_id** | **str** |  | 
**status** | **str** | Status of the subscription in Stripe: &#x60;active&#x60;, &#x60;trialing&#x60;, &#x60;past_due&#x60; while a failed payment is retried, &#x60;canceled&#x60;, &#x60;unpaid&#x60;, &#x60;paused&#x60;, &#x60;incomplete&#x60; or &#x60;incomplete_expired&#x60;. | 
**interval** | **str** |  | 
**interval_count** | **int** | Number of intervals between payments. | 
**quantity** | **int** | Units subscribed, multiplying the policy&#39;s machines. | 
**price** | [**Price**](Price.md) | Price of one unit for one period, before taxes. | 
**current_period_end** | **datetime** | End of the paid period, when the subscription renews or ends. | 
**cancel_at_period_end** | **bool** | Whether the subscription ends at the end of the period. | 
**ended_at** | **datetime** |  | 

## Example

```python
from licensemanager.models.license_subscription import LicenseSubscription

# TODO update the JSON string below
json = "{}"
# create an instance of LicenseSubscription from a JSON string
license_subscription_instance = LicenseSubscription.from_json(json)
# print the JSON string representation of the object
print(LicenseSubscription.to_json())

# convert the object into a dict
license_subscription_dict = license_subscription_instance.to_dict()
# create an instance of LicenseSubscription from a dict
license_subscription_from_dict = LicenseSubscription.from_dict(license_subscription_dict)
```
[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)


