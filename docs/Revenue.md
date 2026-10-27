# Revenue

Revenue in one currency: the licenses sold once, each counting on the day it was created, and the payments of the subscription licenses, each counting on the day it was paid, with the license's policy. Licenses without a price are left out, and so are canceled ones, but in `canceledLicenseCount` and `canceledTotal`.

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**currency** | **str** | ISO 4217 code of the currency of the revenue. | 
**license_count** | **int** | Number of licenses sold once in the currency, free ones included, canceled ones and subscription licenses left out. | 
**total** | **float** | Revenue in the currency, in major units: the prices of the licenses sold once, canceled ones left out, plus the payments of the subscriptions, &#x60;subscriptionTotal&#x60;. | 
**subscription_total** | **float** | Sum of the payments of the subscription licenses in the currency, before taxes, in major units. | 
**payment_count** | **int** | Number of payments of the subscription licenses in the currency. | 
**canceled_license_count** | **int** | Number of canceled licenses sold once in the currency. | 
**canceled_total** | **float** | Sum of the prices of the canceled licenses sold once in the currency, in major units: revenue lost to cancellations. | 
**this_month** | **float** | Revenue of the current month, in UTC. | 
**last_month** | **float** | Revenue of the previous month, in UTC. | 
**last30_days** | **float** | Revenue of the last 30 days, today included, in UTC. | 
**by_day** | **List[float]** | Revenue each day, aligned on &#x60;days&#x60;. | 
**by_month** | **List[float]** | Revenue each month, aligned on &#x60;months&#x60;. | 
**by_policy** | [**List[ProductStatsNewLicensesByPolicyInner]**](ProductStatsNewLicensesByPolicyInner.md) | Revenue of the licenses of each policy, for the policies with licenses sold in the currency over the covered months. | 

## Example

```python
from licensemanager.models.revenue import Revenue

# TODO update the JSON string below
json = "{}"
# create an instance of Revenue from a JSON string
revenue_instance = Revenue.from_json(json)
# print the JSON string representation of the object
print(Revenue.to_json())

# convert the object into a dict
revenue_dict = revenue_instance.to_dict()
# create an instance of Revenue from a dict
revenue_from_dict = Revenue.from_dict(revenue_dict)
```
[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)


