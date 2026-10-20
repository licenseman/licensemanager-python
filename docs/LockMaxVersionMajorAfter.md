# LockMaxVersionMajorAfter

Time after the creation of a license its major version is locked, in seconds or calendar months: it then only gets the minor versions and bug fixes of the major version released by then. `0` locks it when the license is created.

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**value** | **int** |  | 
**unit** | **str** | Calendar months: a license created on January 31 with a 1 month duration expires on the last day of February. | 

## Example

```python
from licensemanager.models.lock_max_version_major_after import LockMaxVersionMajorAfter

# TODO update the JSON string below
json = "{}"
# create an instance of LockMaxVersionMajorAfter from a JSON string
lock_max_version_major_after_instance = LockMaxVersionMajorAfter.from_json(json)
# print the JSON string representation of the object
print(LockMaxVersionMajorAfter.to_json())

# convert the object into a dict
lock_max_version_major_after_dict = lock_max_version_major_after_instance.to_dict()
# create an instance of LockMaxVersionMajorAfter from a dict
lock_max_version_major_after_from_dict = LockMaxVersionMajorAfter.from_dict(lock_max_version_major_after_dict)
```
[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)


