# FixedMaxVersion

The licenses can use up to `version`, whenever they're created.

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**type** | **str** |  | 
**version** | **str** | &#x60;\&quot;2\&quot;&#x60; allows every 2.y.z version: the minor versions and bug fixes of version 2. &#x60;\&quot;2.3\&quot;&#x60; allows every 2.3.z version: the bug fixes of version 2.3. Bug fixes can&#39;t be locked, so patch numbers like &#x60;\&quot;2.3.1\&quot;&#x60; are rejected. | 

## Example

```python
from licensemanager.models.fixed_max_version import FixedMaxVersion

# TODO update the JSON string below
json = "{}"
# create an instance of FixedMaxVersion from a JSON string
fixed_max_version_instance = FixedMaxVersion.from_json(json)
# print the JSON string representation of the object
print(FixedMaxVersion.to_json())

# convert the object into a dict
fixed_max_version_dict = fixed_max_version_instance.to_dict()
# create an instance of FixedMaxVersion from a dict
fixed_max_version_from_dict = FixedMaxVersion.from_dict(fixed_max_version_dict)
```
[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)


