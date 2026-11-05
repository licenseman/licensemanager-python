# UpdateSlackConnection


## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**events** | **List[str]** | Notifications the channel gets. | 

## Example

```python
from licensemanager.models.update_slack_connection import UpdateSlackConnection

# TODO update the JSON string below
json = "{}"
# create an instance of UpdateSlackConnection from a JSON string
update_slack_connection_instance = UpdateSlackConnection.from_json(json)
# print the JSON string representation of the object
print(UpdateSlackConnection.to_json())

# convert the object into a dict
update_slack_connection_dict = update_slack_connection_instance.to_dict()
# create an instance of UpdateSlackConnection from a dict
update_slack_connection_from_dict = UpdateSlackConnection.from_dict(update_slack_connection_dict)
```
[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)


