# PortalNotFound


## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**error** | [**ErrorError**](ErrorError.md) |  | 
**organization_slug** | **str** | Slug of the product&#39;s organization. Present on &#x60;portal_disabled&#x60; errors. | [optional] 
**product_slug** | **str** | Slug of the product. Present on &#x60;portal_disabled&#x60; errors. | [optional] 

## Example

```python
from licensemanager.models.portal_not_found import PortalNotFound

# TODO update the JSON string below
json = "{}"
# create an instance of PortalNotFound from a JSON string
portal_not_found_instance = PortalNotFound.from_json(json)
# print the JSON string representation of the object
print(PortalNotFound.to_json())

# convert the object into a dict
portal_not_found_dict = portal_not_found_instance.to_dict()
# create an instance of PortalNotFound from a dict
portal_not_found_from_dict = PortalNotFound.from_dict(portal_not_found_dict)
```
[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)


