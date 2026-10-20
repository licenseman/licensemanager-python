# PolicySettingsDurationAnyOf1


## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**value** | **int** |  | 
**unit** | **str** | Calendar months: a license created on January 31 with a 1 month duration expires on the last day of February. | 

## Example

```python
from licensemanager.models.policy_settings_duration_any_of1 import PolicySettingsDurationAnyOf1

# TODO update the JSON string below
json = "{}"
# create an instance of PolicySettingsDurationAnyOf1 from a JSON string
policy_settings_duration_any_of1_instance = PolicySettingsDurationAnyOf1.from_json(json)
# print the JSON string representation of the object
print(PolicySettingsDurationAnyOf1.to_json())

# convert the object into a dict
policy_settings_duration_any_of1_dict = policy_settings_duration_any_of1_instance.to_dict()
# create an instance of PolicySettingsDurationAnyOf1 from a dict
policy_settings_duration_any_of1_from_dict = PolicySettingsDurationAnyOf1.from_dict(policy_settings_duration_any_of1_dict)
```
[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)


