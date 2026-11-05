# SlackConnection


## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**id** | **str** |  | 
**team_id** | **str** |  | 
**team_name** | **str** |  | 
**channel_id** | **str** |  | 
**channel_name** | **str** | Name of the channel when it was connected, with its &#x60;#&#x60;. | 
**configuration_url** | **str** | Page of the installation in Slack. | 
**events** | **List[str]** | Notifications the channel gets: &#x60;purchased&#x60; (a license bought through Stripe), &#x60;renewed&#x60; (a subscription renewal paid), &#x60;payment_failed&#x60; (a subscription payment failed) and &#x60;canceled&#x60; (a license canceled, or its subscription ended). | 
**status** | **str** | &#x60;revoked&#x60; once Slack refuses the messages, like when the app was removed from the workspace or the channel deleted: remove it and add it again. | 
**status_reason** | **str** |  | 
**last_sent_at** | **datetime** |  | 
**created_at** | **datetime** |  | 

## Example

```python
from licensemanager.models.slack_connection import SlackConnection

# TODO update the JSON string below
json = "{}"
# create an instance of SlackConnection from a JSON string
slack_connection_instance = SlackConnection.from_json(json)
# print the JSON string representation of the object
print(SlackConnection.to_json())

# convert the object into a dict
slack_connection_dict = slack_connection_instance.to_dict()
# create an instance of SlackConnection from a dict
slack_connection_from_dict = SlackConnection.from_dict(slack_connection_dict)
```
[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)


