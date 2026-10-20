# PortalSettings


## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**enabled** | **bool** | Whether customers can use the customer portal. When disabled, it answers &#x60;404&#x60;. | 
**brand_color** | **str** | Background of the portal&#39;s side panel, as &#x60;#rrggbb&#x60;, stored lower cased. &#x60;null&#x60; for the default color. | 
**accent_color** | **str** | Color of the portal&#39;s inputs and buttons, as &#x60;#rrggbb&#x60;, stored lower cased. &#x60;null&#x60; for the default color. | 
**return_url** | **str** | Link back to your website shown in the portal, when the portal&#39;s URL has no allowed &#x60;return_url&#x60;. &#x60;null&#x60; for no link. | 
**return_domains** | **List[str]** | Domains the portal&#39;s &#x60;return_url&#x60; query parameter may point to, their subdomains included. Other return URLs are ignored, in favor of &#x60;returnUrl&#x60;. | 

## Example

```python
from licensemanager.models.portal_settings import PortalSettings

# TODO update the JSON string below
json = "{}"
# create an instance of PortalSettings from a JSON string
portal_settings_instance = PortalSettings.from_json(json)
# print the JSON string representation of the object
print(PortalSettings.to_json())

# convert the object into a dict
portal_settings_dict = portal_settings_instance.to_dict()
# create an instance of PortalSettings from a dict
portal_settings_from_dict = PortalSettings.from_dict(portal_settings_dict)
```
[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)


