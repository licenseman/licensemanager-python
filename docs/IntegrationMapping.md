# IntegrationMapping


## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**id** | **str** |  | 
**integration_id** | **str** |  | 
**product_id** | **str** |  | 
**policy_id** | **str** |  | 
**stripe_product_id** | **str** |  | 
**stripe_price_id** | **str** |  | 
**product_name** | **str** | Name of the Stripe product when it was mapped. | 
**price** | [**Price**](Price.md) |  | 
**status** | **str** | &#x60;error&#x60; when the price can no longer be paid, explained by &#x60;statusReason&#x60;. | 
**status_reason** | **str** |  | 
**created_at** | **datetime** |  | 

## Example

```python
from licensemanager.models.integration_mapping import IntegrationMapping

# TODO update the JSON string below
json = "{}"
# create an instance of IntegrationMapping from a JSON string
integration_mapping_instance = IntegrationMapping.from_json(json)
# print the JSON string representation of the object
print(IntegrationMapping.to_json())

# convert the object into a dict
integration_mapping_dict = integration_mapping_instance.to_dict()
# create an instance of IntegrationMapping from a dict
integration_mapping_from_dict = IntegrationMapping.from_dict(integration_mapping_dict)
```
[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)


