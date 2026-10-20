# CreateRelease


## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**version** | **str** | Semantic version, like &#x60;\&quot;2.3.1\&quot;&#x60; or &#x60;\&quot;2.4.0-beta.1\&quot;&#x60;, without a &#x60;v&#x60; prefix. Unique within the product. Each number has at most 9 digits. | 
**released_at** | **datetime** | When the version is released, which can be in the future. Defaults to now. | [optional] 

## Example

```python
from licensemanager.models.create_release import CreateRelease

# TODO update the JSON string below
json = "{}"
# create an instance of CreateRelease from a JSON string
create_release_instance = CreateRelease.from_json(json)
# print the JSON string representation of the object
print(CreateRelease.to_json())

# convert the object into a dict
create_release_dict = create_release_instance.to_dict()
# create an instance of CreateRelease from a dict
create_release_from_dict = CreateRelease.from_dict(create_release_dict)
```
[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)


