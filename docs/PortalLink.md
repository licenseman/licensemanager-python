# PortalLink


## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**url** | **str** | Link to the customer portal, holding the token. | 
**token** | **str** | Customer token in the link, with the &#x60;customer:read&#x60;, &#x60;license:read&#x60;, &#x60;license:cancel&#x60; and &#x60;machine:write&#x60; permissions. | 
**expires_at** | **datetime** | When the link stops working. | 

## Example

```python
from licensemanager.models.portal_link import PortalLink

# TODO update the JSON string below
json = "{}"
# create an instance of PortalLink from a JSON string
portal_link_instance = PortalLink.from_json(json)
# print the JSON string representation of the object
print(PortalLink.to_json())

# convert the object into a dict
portal_link_dict = portal_link_instance.to_dict()
# create an instance of PortalLink from a dict
portal_link_from_dict = PortalLink.from_dict(portal_link_dict)
```
[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)


