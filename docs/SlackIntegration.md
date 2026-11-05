# SlackIntegration


## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**configured** | **bool** | Whether the server has a Slack app to connect channels with: &#x60;SLACK_CLIENT_ID&#x60; and &#x60;SLACK_CLIENT_SECRET&#x60; are set. | 
**connections** | [**List[SlackConnection]**](SlackConnection.md) | Slack channels getting the product&#39;s notifications. | 

## Example

```python
from licensemanager.models.slack_integration import SlackIntegration

# TODO update the JSON string below
json = "{}"
# create an instance of SlackIntegration from a JSON string
slack_integration_instance = SlackIntegration.from_json(json)
# print the JSON string representation of the object
print(SlackIntegration.to_json())

# convert the object into a dict
slack_integration_dict = slack_integration_instance.to_dict()
# create an instance of SlackIntegration from a dict
slack_integration_from_dict = SlackIntegration.from_dict(slack_integration_dict)
```
[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)


