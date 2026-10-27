# CreateBillingPortalSession


## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**return_url** | **str** | Where the Stripe customer portal links back to: a page of the customer portal, or of one of the product&#39;s &#x60;returnDomains&#x60;. The customer portal of the product by default. | [optional] 

## Example

```python
from licensemanager.models.create_billing_portal_session import CreateBillingPortalSession

# TODO update the JSON string below
json = "{}"
# create an instance of CreateBillingPortalSession from a JSON string
create_billing_portal_session_instance = CreateBillingPortalSession.from_json(json)
# print the JSON string representation of the object
print(CreateBillingPortalSession.to_json())

# convert the object into a dict
create_billing_portal_session_dict = create_billing_portal_session_instance.to_dict()
# create an instance of CreateBillingPortalSession from a dict
create_billing_portal_session_from_dict = CreateBillingPortalSession.from_dict(create_billing_portal_session_dict)
```
[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)


