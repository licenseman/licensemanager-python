# StripeIntegration


## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**livemode** | **bool** | Mode of the Stripe connection the product uses: live for live products, test for test products. | 
**webhook_url_reachable** | **bool** | Whether Stripe can reach the API&#39;s webhook URL. A local URL can&#39;t be: set &#x60;WEBHOOK_URL&#x60; on the server, like to a tunnel in development. | 
**required_permissions** | [**List[StripePermission]**](StripePermission.md) | Permissions the restricted API key needs, and why, the &#x60;optional&#x60; ones included. Every other permission can stay &#x60;None&#x60;. | 
**integration** | [**Integration**](Integration.md) | The organization&#39;s Stripe connection in this mode, &#x60;null&#x60; when there&#39;s none. | 
**mappings** | [**List[IntegrationMapping]**](IntegrationMapping.md) | Stripe prices creating licenses of the product. | 

## Example

```python
from licensemanager.models.stripe_integration import StripeIntegration

# TODO update the JSON string below
json = "{}"
# create an instance of StripeIntegration from a JSON string
stripe_integration_instance = StripeIntegration.from_json(json)
# print the JSON string representation of the object
print(StripeIntegration.to_json())

# convert the object into a dict
stripe_integration_dict = stripe_integration_instance.to_dict()
# create an instance of StripeIntegration from a dict
stripe_integration_from_dict = StripeIntegration.from_dict(stripe_integration_dict)
```
[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)


