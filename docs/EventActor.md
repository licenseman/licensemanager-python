# EventActor

Who caused the event: a user of the app, an API key, a token, `automation` for the changes the app makes on its own, like applying the version locks, or `integration` for the changes of an integration, like the licenses a Stripe payment creates. `null` for requests that don't authenticate, like validating a license key.

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**type** | **str** |  | 
**id** | **str** | &#x60;null&#x60; when the integration has been disconnected. | 
**name** | **str** |  | 
**email** | **str** |  | 
**image** | **str** | URL of the user&#39;s profile picture. | 
**start** | **str** | First characters of the key, to recognize it. | 
**token_type** | **str** | Type of resource the token is scoped to. | 
**subject_id** | **str** | Id of the resource the token is scoped to. | 
**provider** | **str** | Service the integration connects to. | 

## Example

```python
from licensemanager.models.event_actor import EventActor

# TODO update the JSON string below
json = "{}"
# create an instance of EventActor from a JSON string
event_actor_instance = EventActor.from_json(json)
# print the JSON string representation of the object
print(EventActor.to_json())

# convert the object into a dict
event_actor_dict = event_actor_instance.to_dict()
# create an instance of EventActor from a dict
event_actor_from_dict = EventActor.from_dict(event_actor_dict)
```
[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)


