# Machine


## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**id** | **str** |  | 
**license_id** | **str** |  | 
**fingerprint** | **str** | Identifies the machine. Unique within the license. | 
**platform** | **str** |  | 
**name** | **str** |  | 
**status** | **str** | Whether the machine counts as using the license. | 
**version** | **str** | Version of the application last validated on the machine. | 
**last_validated_at** | **datetime** | When the license was last validated on the machine. | 
**created_at** | **datetime** |  | 
**updated_at** | **datetime** |  | 

## Example

```python
from licensemanager.models.machine import Machine

# TODO update the JSON string below
json = "{}"
# create an instance of Machine from a JSON string
machine_instance = Machine.from_json(json)
# print the JSON string representation of the object
print(Machine.to_json())

# convert the object into a dict
machine_dict = machine_instance.to_dict()
# create an instance of Machine from a dict
machine_from_dict = Machine.from_dict(machine_dict)
```
[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)


