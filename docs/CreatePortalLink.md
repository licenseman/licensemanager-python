# CreatePortalLink


## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**expires_in_seconds** | **int** | How long the link works, in seconds, from 300 (5 minutes) to 31536000 (365 days). | 

## Example

```python
from licensemanager.models.create_portal_link import CreatePortalLink

# TODO update the JSON string below
json = "{}"
# create an instance of CreatePortalLink from a JSON string
create_portal_link_instance = CreatePortalLink.from_json(json)
# print the JSON string representation of the object
print(CreatePortalLink.to_json())

# convert the object into a dict
create_portal_link_dict = create_portal_link_instance.to_dict()
# create an instance of CreatePortalLink from a dict
create_portal_link_from_dict = CreatePortalLink.from_dict(create_portal_link_dict)
```
[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)


