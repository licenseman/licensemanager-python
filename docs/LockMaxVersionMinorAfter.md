# LockMaxVersionMinorAfter

Time after the creation of a license its minor version is locked, in seconds or calendar months: it then only gets the bug fixes of the minor version released by then. Never shorter than `majorAfter`, whatever the length of the months: 1 month is longer than 28 days but may be shorter than 31. `0` locks it when the license is created. `null` to never lock it.

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**value** | **int** |  | 
**unit** | **str** | Calendar months: a license created on January 31 with a 1 month duration expires on the last day of February. | 

## Example

```python
from licensemanager.models.lock_max_version_minor_after import LockMaxVersionMinorAfter

# TODO update the JSON string below
json = "{}"
# create an instance of LockMaxVersionMinorAfter from a JSON string
lock_max_version_minor_after_instance = LockMaxVersionMinorAfter.from_json(json)
# print the JSON string representation of the object
print(LockMaxVersionMinorAfter.to_json())

# convert the object into a dict
lock_max_version_minor_after_dict = lock_max_version_minor_after_instance.to_dict()
# create an instance of LockMaxVersionMinorAfter from a dict
lock_max_version_minor_after_from_dict = LockMaxVersionMinorAfter.from_dict(lock_max_version_minor_after_dict)
```
[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)


