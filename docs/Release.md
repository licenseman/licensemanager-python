# Release


## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**id** | **str** |  | 
**product_id** | **str** |  | 
**version** | **str** |  | 
**released_at** | **datetime** |  | 
**created_at** | **datetime** |  | 
**active_machine_count** | **int** | Number of active machines of the product&#39;s licenses running this version: the ones whose &#x60;version&#x60; is exactly the release&#39;s, so &#x60;v2.3.1&#x60; doesn&#39;t count for &#x60;2.3.1&#x60;. | 

## Example

```python
from licensemanager.models.release import Release

# TODO update the JSON string below
json = "{}"
# create an instance of Release from a JSON string
release_instance = Release.from_json(json)
# print the JSON string representation of the object
print(Release.to_json())

# convert the object into a dict
release_dict = release_instance.to_dict()
# create an instance of Release from a dict
release_from_dict = Release.from_dict(release_dict)
```
[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)


