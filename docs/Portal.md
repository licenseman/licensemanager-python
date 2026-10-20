# Portal


## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**product_id** | **str** |  | 
**product_name** | **str** |  | 
**organization_name** | **str** |  | 
**logo_url** | **str** | Public URL of the product&#39;s logo. &#x60;null&#x60; without a logo. | 
**brand_color** | **str** | Background of the side panel, as &#x60;#rrggbb&#x60;. &#x60;null&#x60; for the default color. | 
**accent_color** | **str** | Color of the inputs and buttons, as &#x60;#rrggbb&#x60;. &#x60;null&#x60; for the default color. | 
**return_url** | **str** | Link back to the product&#39;s website: the requested &#x60;returnUrl&#x60; when its domain is allowed, the product&#39;s default return link otherwise. &#x60;null&#x60; for no link. | 

## Example

```python
from licensemanager.models.portal import Portal

# TODO update the JSON string below
json = "{}"
# create an instance of Portal from a JSON string
portal_instance = Portal.from_json(json)
# print the JSON string representation of the object
print(Portal.to_json())

# convert the object into a dict
portal_dict = portal_instance.to_dict()
# create an instance of Portal from a dict
portal_from_dict = Portal.from_dict(portal_dict)
```
[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)


