# PolicyDuration

Duration of the licenses created with this policy. `null` when they never expire.

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**value** | **int** |  | 
**unit** | **str** | Calendar months: a license created on January 31 with a 1 month duration expires on the last day of February. | 

## Example

```python
from licensemanager.models.policy_duration import PolicyDuration

# TODO update the JSON string below
json = "{}"
# create an instance of PolicyDuration from a JSON string
policy_duration_instance = PolicyDuration.from_json(json)
# print the JSON string representation of the object
print(PolicyDuration.to_json())

# convert the object into a dict
policy_duration_dict = policy_duration_instance.to_dict()
# create an instance of PolicyDuration from a dict
policy_duration_from_dict = PolicyDuration.from_dict(policy_duration_dict)
```
[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)


