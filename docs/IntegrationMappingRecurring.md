# IntegrationMappingRecurring

Billing period of a recurring price, `null` for a one-time price. Subscribing to a recurring price creates one subscription license, valid while it's paid.

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**interval** | **str** |  | 
**interval_count** | **int** |  | 

## Example

```python
from licensemanager.models.integration_mapping_recurring import IntegrationMappingRecurring

# TODO update the JSON string below
json = "{}"
# create an instance of IntegrationMappingRecurring from a JSON string
integration_mapping_recurring_instance = IntegrationMappingRecurring.from_json(json)
# print the JSON string representation of the object
print(IntegrationMappingRecurring.to_json())

# convert the object into a dict
integration_mapping_recurring_dict = integration_mapping_recurring_instance.to_dict()
# create an instance of IntegrationMappingRecurring from a dict
integration_mapping_recurring_from_dict = IntegrationMappingRecurring.from_dict(integration_mapping_recurring_dict)
```
[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)


