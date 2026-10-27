# CancellationStats

Cancellations of the licenses with a money back guarantee. Licenses canceled without one are left out.

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**license_count** | **int** | Number of licenses with a money back guarantee: a &#x60;cancellableUntil&#x60;. | 
**canceled_license_count** | **int** | Number of them that were canceled. | 
**cancellable_license_count** | **int** | Number of them whose money back guarantee hasn&#39;t ended, and that weren&#39;t canceled: they can still be. | 
**rate** | **float** | Share of them that were canceled, from 0 to 1: &#x60;canceledLicenseCount&#x60; over &#x60;licenseCount&#x60;. | 
**canceled_by_day** | **List[int]** | Number of them canceled each day, aligned on &#x60;days&#x60;, on the day of their cancellation. | 
**canceled_by_month** | **List[int]** | Number of them canceled each month, aligned on &#x60;months&#x60;, on the month of their cancellation. | 
**by_reason** | [**List[CancellationStatsByReasonInner]**](CancellationStatsByReasonInner.md) | Number of them canceled for each reason, from the most given one. Reasons never given are left out. | 

## Example

```python
from licensemanager.models.cancellation_stats import CancellationStats

# TODO update the JSON string below
json = "{}"
# create an instance of CancellationStats from a JSON string
cancellation_stats_instance = CancellationStats.from_json(json)
# print the JSON string representation of the object
print(CancellationStats.to_json())

# convert the object into a dict
cancellation_stats_dict = cancellation_stats_instance.to_dict()
# create an instance of CancellationStats from a dict
cancellation_stats_from_dict = CancellationStats.from_dict(cancellation_stats_dict)
```
[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)


