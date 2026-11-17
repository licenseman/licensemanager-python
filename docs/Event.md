# Event


## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**id** | **str** |  | 
**type** | [**EventType**](EventType.md) |  | 
**created_at** | **datetime** |  | 
**payload** | **Dict[str, Optional[object]]** | Details of the event, depending on its &#x60;type&#x60;. | 
**policy_id** | **str** |  | 
**license_id** | **str** |  | 
**machine_id** | **str** |  | 
**machine** | [**EventMachine**](EventMachine.md) |  | 
**actor** | [**EventActor**](EventActor.md) |  | 
**country** | **str** | ISO 3166-1 alpha-2 code of the country of the IP address the request came from, for &#x60;license.validated&#x60; and &#x60;license.validation_failed&#x60; events. &#x60;null&#x60; until it&#39;s looked up, shortly after, or when it can&#39;t be. | 
**latitude** | **float** | Approximate latitude of the IP address the request came from, for &#x60;license.validated&#x60; and &#x60;license.validation_failed&#x60; events. &#x60;null&#x60; until it&#39;s looked up, shortly after, or when it can&#39;t be. | 
**longitude** | **float** | Approximate longitude of the IP address the request came from, for &#x60;license.validated&#x60; and &#x60;license.validation_failed&#x60; events. &#x60;null&#x60; until it&#39;s looked up, shortly after, or when it can&#39;t be. | 

## Example

```python
from licensemanager.models.event import Event

# TODO update the JSON string below
json = "{}"
# create an instance of Event from a JSON string
event_instance = Event.from_json(json)
# print the JSON string representation of the object
print(Event.to_json())

# convert the object into a dict
event_dict = event_instance.to_dict()
# create an instance of Event from a dict
event_from_dict = Event.from_dict(event_dict)
```
[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)


