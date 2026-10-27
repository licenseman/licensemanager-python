# Mrr


## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**currency** | **str** |  | 
**mrr** | **float** | Monthly recurring revenue: the price of every ongoing subscription in the currency, times its quantity, brought to one month (a year counts for a twelfth), before taxes and discounts. | 
**by_interval** | [**List[MrrByIntervalInner]**](MrrByIntervalInner.md) | Ongoing subscriptions and MRR of each billing period, like monthly and yearly, from the highest MRR. | 
**by_policy** | [**List[MrrByPolicyInner]**](MrrByPolicyInner.md) | MRR of each policy, from the highest. | 
**by_month** | **List[float]** | MRR at the end of each month, aligned on &#x60;months&#x60;, today for this month, at the current prices of the subscriptions. | 

## Example

```python
from licensemanager.models.mrr import Mrr

# TODO update the JSON string below
json = "{}"
# create an instance of Mrr from a JSON string
mrr_instance = Mrr.from_json(json)
# print the JSON string representation of the object
print(Mrr.to_json())

# convert the object into a dict
mrr_dict = mrr_instance.to_dict()
# create an instance of Mrr from a dict
mrr_from_dict = Mrr.from_dict(mrr_dict)
```
[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)


