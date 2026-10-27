# PolicySettings


## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**duration** | [**PolicySettingsDuration**](PolicySettingsDuration.md) |  | [optional] 
**max_machines** | **int** | Maximum number of active machines of the licenses created with this policy, copied to each of them. &#x60;null&#x60; for no limit. Defaults to &#x60;null&#x60;. | [optional] 
**max_offline_duration_seconds** | **int** | Longest the applications can run offline with the licenses created with this policy, in seconds, copied to each of them. At least one hour (&#x60;3600&#x60;). Defaults to one week. | [optional] 
**max_version** | [**PolicySettingsMaxVersion**](PolicySettingsMaxVersion.md) |  | [optional] 
**money_back_guarantee_days** | **int** | Number of days after their creation during which customers can cancel the licenses created with this policy, from the customer portal or with &#x60;cancelLicense&#x60;, which refunds their Stripe payment. Each license keeps the end of its own period as &#x60;cancellableUntil&#x60;. &#x60;null&#x60; for no money back guarantee. Defaults to &#x60;null&#x60;. | [optional] 

## Example

```python
from licensemanager.models.policy_settings import PolicySettings

# TODO update the JSON string below
json = "{}"
# create an instance of PolicySettings from a JSON string
policy_settings_instance = PolicySettings.from_json(json)
# print the JSON string representation of the object
print(PolicySettings.to_json())

# convert the object into a dict
policy_settings_dict = policy_settings_instance.to_dict()
# create an instance of PolicySettings from a dict
policy_settings_from_dict = PolicySettings.from_dict(policy_settings_dict)
```
[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)


