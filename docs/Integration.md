# Integration


## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**id** | **str** |  | 
**provider** | **str** |  | 
**livemode** | **bool** | Whether it&#39;s connected in live mode, for the live products, or in test mode, for the test products. | 
**account_name** | **str** | Name of the Stripe account, &#x60;null&#x60; when the API key can&#39;t read it, and for Paddle, whose API doesn&#39;t give it. | 
**api_key_hint** | **str** | Start and end of the API key, to recognize it. | 
**webhook_url** | **str** | URL of the webhook endpoint created on the Stripe account, or of the notification destination created on the Paddle account. | 
**status** | [**IntegrationStatus**](IntegrationStatus.md) |  | 
**status_reason** | **str** | Why the integration isn&#39;t &#x60;active&#x60;, &#x60;null&#x60; when it is. | 
**last_checked_at** | **datetime** | Last time its health was checked, done every day. | 
**last_event_at** | **datetime** | Last time it received an event from the provider. | 
**auto_refund** | **bool** | Whether canceling a license bought through the integration refunds its payment. On by default, always off when &#x60;canRefund&#x60; is false. | 
**can_refund** | **bool** | Whether the API key has the optional refund permission (Stripe: Refunds: Write, Paddle: Adjustments: Write), checked when connecting and every day. Without it, canceled licenses aren&#39;t refunded: refund their payments from the provider. | 
**can_manage_subscriptions** | **bool** | Whether the API key has the optional Subscriptions: Write permission, checked when connecting and every day. Without it, subscription licenses can&#39;t be canceled from the app: cancel their subscriptions from the provider. | 
**can_billing_portal** | **bool** | Whether the API key has the optional customer portal permission (Stripe: Customer portal: Write, Paddle: Customer portal sessions: Write), checked when connecting and every day. Without it, the license portal doesn&#39;t link to the provider&#39;s customer portal. | 
**subscription_grace_days** | **int** | Days a subscription license stays valid after its period ends while its renewal is unpaid, as the provider retries the payment. 7 by default. | 
**created_at** | **datetime** |  | 

## Example

```python
from licensemanager.models.integration import Integration

# TODO update the JSON string below
json = "{}"
# create an instance of Integration from a JSON string
integration_instance = Integration.from_json(json)
# print the JSON string representation of the object
print(Integration.to_json())

# convert the object into a dict
integration_dict = integration_instance.to_dict()
# create an instance of Integration from a dict
integration_from_dict = Integration.from_dict(integration_dict)
```
[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)


