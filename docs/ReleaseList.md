# ReleaseList


## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**data** | [**List[Release]**](Release.md) | Items of the page, in the requested order. Empty past the last page. | 
**pagination** | [**Pagination**](Pagination.md) |  | 

## Example

```python
from licensemanager.models.release_list import ReleaseList

# TODO update the JSON string below
json = "{}"
# create an instance of ReleaseList from a JSON string
release_list_instance = ReleaseList.from_json(json)
# print the JSON string representation of the object
print(ReleaseList.to_json())

# convert the object into a dict
release_list_dict = release_list_instance.to_dict()
# create an instance of ReleaseList from a dict
release_list_from_dict = ReleaseList.from_dict(release_list_dict)
```
[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)


