# EventActorOneOf4


## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**type** | **str** |  | 
**id** | **str** | &#x60;null&#x60; when the integration has been disconnected. | 
**provider** | **str** | Service the integration connects to. | 

## Example

```python
from licensemanager.models.event_actor_one_of4 import EventActorOneOf4

# TODO update the JSON string below
json = "{}"
# create an instance of EventActorOneOf4 from a JSON string
event_actor_one_of4_instance = EventActorOneOf4.from_json(json)
# print the JSON string representation of the object
print(EventActorOneOf4.to_json())

# convert the object into a dict
event_actor_one_of4_dict = event_actor_one_of4_instance.to_dict()
# create an instance of EventActorOneOf4 from a dict
event_actor_one_of4_from_dict = EventActorOneOf4.from_dict(event_actor_one_of4_dict)
```
[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)


