# Revenue

Revenue of the licenses sold in one currency, each license counting on the day it was created. Licenses without a price are left out.

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**currency** | **str** | ISO 4217 code of the currency of the revenue. | 
**license_count** | **int** | Number of licenses sold in the currency, free ones included. | 
**total** | **float** | Sum of the prices of the licenses sold in the currency, in major units. | 
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


