# ListPolicyEventsTypeParameter

Only returns the events of this type. Repeat it to return the events of any of these types.

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------

## Example

```python
from licensemanager.models.list_policy_events_type_parameter import ListPolicyEventsTypeParameter

# TODO update the JSON string below
json = "{}"
# create an instance of ListPolicyEventsTypeParameter from a JSON string
list_policy_events_type_parameter_instance = ListPolicyEventsTypeParameter.from_json(json)
# print the JSON string representation of the object
print(ListPolicyEventsTypeParameter.to_json())

# convert the object into a dict
list_policy_events_type_parameter_dict = list_policy_events_type_parameter_instance.to_dict()
# create an instance of ListPolicyEventsTypeParameter from a dict
list_policy_events_type_parameter_from_dict = ListPolicyEventsTypeParameter.from_dict(list_policy_events_type_parameter_dict)
```
[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)


