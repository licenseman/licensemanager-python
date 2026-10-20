# EventActorOneOf2


## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**type** | **str** |  | 
**token_type** | **str** | Type of resource the token is scoped to. | 
**subject_id** | **str** | Id of the resource the token is scoped to. | 

## Example

```python
from licensemanager.models.event_actor_one_of2 import EventActorOneOf2

# TODO update the JSON string below
json = "{}"
# create an instance of EventActorOneOf2 from a JSON string
event_actor_one_of2_instance = EventActorOneOf2.from_json(json)
# print the JSON string representation of the object
print(EventActorOneOf2.to_json())

# convert the object into a dict
event_actor_one_of2_dict = event_actor_one_of2_instance.to_dict()
# create an instance of EventActorOneOf2 from a dict
event_actor_one_of2_from_dict = EventActorOneOf2.from_dict(event_actor_one_of2_dict)
```
[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)


