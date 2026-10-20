# RequestPortalLink


## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**email** | **str** | Email of the customer. | 
**return_url** | **str** | Link back to your website, kept in the emailed link when its domain is one of the product&#39;s &#x60;returnDomains&#x60;. | [optional] 

## Example

```python
from licensemanager.models.request_portal_link import RequestPortalLink

# TODO update the JSON string below
json = "{}"
# create an instance of RequestPortalLink from a JSON string
request_portal_link_instance = RequestPortalLink.from_json(json)
# print the JSON string representation of the object
print(RequestPortalLink.to_json())

# convert the object into a dict
request_portal_link_dict = request_portal_link_instance.to_dict()
# create an instance of RequestPortalLink from a dict
request_portal_link_from_dict = RequestPortalLink.from_dict(request_portal_link_dict)
```
[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)


