# UpdateRelease


## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**version** | **str** | Semantic version, like &#x60;\&quot;2.3.1\&quot;&#x60; or &#x60;\&quot;2.4.0-beta.1\&quot;&#x60;, without a &#x60;v&#x60; prefix. Unique within the product. Each number has at most 9 digits. | [optional] 
**released_at** | **datetime** | When the version is released, which can be in the future. Defaults to now. | [optional] 

## Example

```python
from licensemanager.models.update_release import UpdateRelease

# TODO update the JSON string below
json = "{}"
# create an instance of UpdateRelease from a JSON string
update_release_instance = UpdateRelease.from_json(json)
# print the JSON string representation of the object
print(UpdateRelease.to_json())

# convert the object into a dict
update_release_dict = update_release_instance.to_dict()
# create an instance of UpdateRelease from a dict
update_release_from_dict = UpdateRelease.from_dict(update_release_dict)
```
[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)


