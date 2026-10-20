# MachineList


## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**data** | [**List[Machine]**](Machine.md) | Items of the page, in the requested order. Empty past the last page. | 
**pagination** | [**Pagination**](Pagination.md) |  | 

## Example

```python
from licensemanager.models.machine_list import MachineList

# TODO update the JSON string below
json = "{}"
# create an instance of MachineList from a JSON string
machine_list_instance = MachineList.from_json(json)
# print the JSON string representation of the object
print(MachineList.to_json())

# convert the object into a dict
machine_list_dict = machine_list_instance.to_dict()
# create an instance of MachineList from a dict
machine_list_from_dict = MachineList.from_dict(machine_list_dict)
```
[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)


