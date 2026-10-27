# CreateIntegrationMapping


## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**stripe_price_id** | **str** | Active one-time or licensed recurring price of the Stripe account. | 
**policy_id** | **str** |  | 

## Example

```python
from licensemanager.models.create_integration_mapping import CreateIntegrationMapping

# TODO update the JSON string below
json = "{}"
# create an instance of CreateIntegrationMapping from a JSON string
create_integration_mapping_instance = CreateIntegrationMapping.from_json(json)
# print the JSON string representation of the object
print(CreateIntegrationMapping.to_json())

# convert the object into a dict
create_integration_mapping_dict = create_integration_mapping_instance.to_dict()
# create an instance of CreateIntegrationMapping from a dict
create_integration_mapping_from_dict = CreateIntegrationMapping.from_dict(create_integration_mapping_dict)
```
[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)


