# EventMachine

The machine the event is about, with its current name. `null` when the event has no machine or it has been deleted.

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**id** | **str** |  | 
**name** | **str** |  | 
**fingerprint** | **str** |  | 

## Example

```python
from licensemanager.models.event_machine import EventMachine

# TODO update the JSON string below
json = "{}"
# create an instance of EventMachine from a JSON string
event_machine_instance = EventMachine.from_json(json)
# print the JSON string representation of the object
print(EventMachine.to_json())

# convert the object into a dict
event_machine_dict = event_machine_instance.to_dict()
# create an instance of EventMachine from a dict
event_machine_from_dict = EventMachine.from_dict(event_machine_dict)
```
[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)


