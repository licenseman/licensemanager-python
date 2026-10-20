# EventActorOneOf1


## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**type** | **str** |  | 
**id** | **str** | &#x60;null&#x60; when the API key has been deleted. | 
**name** | **str** |  | 
**start** | **str** | First characters of the key, to recognize it. | 

## Example

```python
from licensemanager.models.event_actor_one_of1 import EventActorOneOf1

# TODO update the JSON string below
json = "{}"
# create an instance of EventActorOneOf1 from a JSON string
event_actor_one_of1_instance = EventActorOneOf1.from_json(json)
# print the JSON string representation of the object
print(EventActorOneOf1.to_json())

# convert the object into a dict
event_actor_one_of1_dict = event_actor_one_of1_instance.to_dict()
# create an instance of EventActorOneOf1 from a dict
event_actor_one_of1_from_dict = EventActorOneOf1.from_dict(event_actor_one_of1_dict)
```
[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)


