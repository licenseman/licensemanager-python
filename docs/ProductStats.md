# ProductStats


## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**license_count** | **int** | Number of licenses of the product. | 
**active_license_count** | **int** | Number of licenses that haven&#39;t expired nor were canceled, and that a machine validated in the last 90 days. | 
**new_license_count** | **int** | Number of licenses created in the last 30 days, today included, in UTC. | 
**expiring_license_count** | **int** | Number of licenses expiring in the next 30 days, canceled ones left out. | 
**expired_license_count** | **int** | Number of licenses that expired in the last 30 days, canceled ones left out. | 
**active_machine_count** | **int** | Number of active machines of the licenses of the product. | 
**in_use_license_count** | **int** | Number of licenses with at least one active machine. | 
**seat_count** | **int** | Sum of the maximum numbers of machines of the licenses that haven&#39;t expired nor were canceled. Licenses without a maximum are left out. | 
**used_seat_count** | **int** | Number of active machines of the licenses counted in &#x60;seatCount&#x60;, at most their maximum number of machines each. | 
**full_license_count** | **int** | Number of licenses counted in &#x60;seatCount&#x60; active on their maximum number of machines. | 
**days** | **List[date]** | The 30 days covered by the daily stats, from the oldest one, in UTC. | 
**months** | **List[str]** | The 12 months covered by the monthly stats, from the oldest one, in UTC. | 
**new_licenses_by_day** | **List[int]** | Number of licenses created each day, aligned on &#x60;days&#x60;. | 
**new_licenses_by_month** | **List[int]** | Number of licenses created each month, aligned on &#x60;months&#x60;. | 
**new_licenses_by_policy** | [**List[ProductStatsNewLicensesByPolicyInner]**](ProductStatsNewLicensesByPolicyInner.md) | Number of licenses of each policy created each day and each month, for the policies with licenses created over the covered months. | 
**cancellation** | [**CancellationStats**](CancellationStats.md) | Cancellations of the licenses with a money back guarantee. &#x60;null&#x60; when no license of the product has one. | 
**subscriptions** | [**SubscriptionStats**](SubscriptionStats.md) | Subscriptions of the product. &#x60;null&#x60; when it has never had one. | 
**revenue** | [**List[Revenue]**](Revenue.md) | Revenue in each currency licenses were sold in, from the one with the most licenses sold. Amounts aren&#39;t converted between currencies. | 
**activations_by_version** | [**List[ProductStatsActivationsByVersionInner]**](ProductStatsActivationsByVersionInner.md) | Successful activations of the licenses of the product each day, per version of the application, from the most recent one. | 
**active_machines_by_version** | [**List[ProductStatsActiveMachinesByVersionInner]**](ProductStatsActiveMachinesByVersionInner.md) | Number of active machines running each version of the application, from the most recent one. | 
**active_machines_by_platform** | [**List[ProductStatsActiveMachinesByPlatformInner]**](ProductStatsActiveMachinesByPlatformInner.md) | Number of active machines on each platform, from the one with the most machines. | 

## Example

```python
from licensemanager.models.product_stats import ProductStats

# TODO update the JSON string below
json = "{}"
# create an instance of ProductStats from a JSON string
product_stats_instance = ProductStats.from_json(json)
# print the JSON string representation of the object
print(ProductStats.to_json())

# convert the object into a dict
product_stats_dict = product_stats_instance.to_dict()
# create an instance of ProductStats from a dict
product_stats_from_dict = ProductStats.from_dict(product_stats_dict)
```
[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)


