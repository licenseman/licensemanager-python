# LockMaxVersion

The licenses can use every version released after their creation, until their major version locks `majorAfter` it, then the updates of their major version until their minor version locks `minorAfter` it, if ever. Bug fixes are never locked.

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**type** | **str** |  | 
**major_after** | [**LockMaxVersionMajorAfter**](LockMaxVersionMajorAfter.md) |  | 
**minor_after** | [**LockMaxVersionMinorAfter**](LockMaxVersionMinorAfter.md) |  | 

## Example

```python
from licensemanager.models.lock_max_version import LockMaxVersion

# TODO update the JSON string below
json = "{}"
# create an instance of LockMaxVersion from a JSON string
lock_max_version_instance = LockMaxVersion.from_json(json)
# print the JSON string representation of the object
print(LockMaxVersion.to_json())

# convert the object into a dict
lock_max_version_dict = lock_max_version_instance.to_dict()
# create an instance of LockMaxVersion from a dict
lock_max_version_from_dict = LockMaxVersion.from_dict(lock_max_version_dict)
```
[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)


