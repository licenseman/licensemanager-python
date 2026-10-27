# UpdateIntegration


## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**auto_refund** | **bool** | Whether canceling a license bought through Stripe refunds its payment. Can only be turned on when the integration&#39;s &#x60;canRefund&#x60; is true: the API key has the Refunds: Write permission. | [optional] 
**subscription_grace_days** | **int** | Days a subscription license stays valid after its period ends while its renewal is unpaid, as Stripe retries the payment. | [optional] 

## Example

```python
from licensemanager.models.update_integration import UpdateIntegration

# TODO update the JSON string below
json = "{}"
# create an instance of UpdateIntegration from a JSON string
update_integration_instance = UpdateIntegration.from_json(json)
# print the JSON string representation of the object
print(UpdateIntegration.to_json())

# convert the object into a dict
update_integration_dict = update_integration_instance.to_dict()
# create an instance of UpdateIntegration from a dict
update_integration_from_dict = UpdateIntegration.from_dict(update_integration_dict)
```
[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)


