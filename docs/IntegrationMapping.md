# IntegrationMapping


## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**id** | **str** |  | 
**integration_id** | **str** |  | 
**provider** | **str** |  | 
**product_id** | **str** |  | 
**policy_id** | **str** |  | 
**external_product_id** | **str** | Id of the product in the provider: &#x60;prod_…&#x60; in Stripe, &#x60;pro_…&#x60; in Paddle. | 
**external_price_id** | **str** | Id of the price in the provider: &#x60;price_…&#x60; in Stripe, &#x60;pri_…&#x60; in Paddle. | 
**stripe_product_id** | **str** | Deprecated: use &#x60;externalProductId&#x60;, which it equals. | 
**stripe_price_id** | **str** | Deprecated: use &#x60;externalPriceId&#x60;, which it equals. | 
**product_name** | **str** | Name of the provider&#39;s product when it was mapped. | 
**price** | [**Price**](Price.md) |  | 
**recurring** | [**IntegrationMappingRecurring**](IntegrationMappingRecurring.md) |  | 
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


