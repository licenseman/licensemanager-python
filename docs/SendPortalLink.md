# SendPortalLink


## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**token** | **str** | Token of a link created for the customer. | 

## Example

```python
from licensemanager.models.send_portal_link import SendPortalLink

# TODO update the JSON string below
json = "{}"
# create an instance of SendPortalLink from a JSON string
send_portal_link_instance = SendPortalLink.from_json(json)
# print the JSON string representation of the object
print(SendPortalLink.to_json())

# convert the object into a dict
send_portal_link_dict = send_portal_link_instance.to_dict()
# create an instance of SendPortalLink from a dict
send_portal_link_from_dict = SendPortalLink.from_dict(send_portal_link_dict)
```
[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)


