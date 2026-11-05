# SlackAuthorize


## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**url** | **str** | Slack&#39;s consent screen: open it in the browser to pick the channel. Valid 10 minutes. | 

## Example

```python
from licensemanager.models.slack_authorize import SlackAuthorize

# TODO update the JSON string below
json = "{}"
# create an instance of SlackAuthorize from a JSON string
slack_authorize_instance = SlackAuthorize.from_json(json)
# print the JSON string representation of the object
print(SlackAuthorize.to_json())

# convert the object into a dict
slack_authorize_dict = slack_authorize_instance.to_dict()
# create an instance of SlackAuthorize from a dict
slack_authorize_from_dict = SlackAuthorize.from_dict(slack_authorize_dict)
```
[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)


