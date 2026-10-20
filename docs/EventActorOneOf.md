# EventActorOneOf


## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**type** | **str** |  | 
**id** | **str** | &#x60;null&#x60; when the user has been deleted. | 
**name** | **str** |  | 
**email** | **str** |  | 
**image** | **str** | URL of the user&#39;s profile picture. | 

## Example

```python
from licensemanager.models.event_actor_one_of import EventActorOneOf

# TODO update the JSON string below
json = "{}"
# create an instance of EventActorOneOf from a JSON string
event_actor_one_of_instance = EventActorOneOf.from_json(json)
# print the JSON string representation of the object
print(EventActorOneOf.to_json())

# convert the object into a dict
event_actor_one_of_dict = event_actor_one_of_instance.to_dict()
# create an instance of EventActorOneOf from a dict
event_actor_one_of_from_dict = EventActorOneOf.from_dict(event_actor_one_of_dict)
```
[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)


