# BillingPortalSession


## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**url** | **str** | Link to the Stripe customer portal, to open right away: it expires shortly. | 

## Example

```python
from licensemanager.models.billing_portal_session import BillingPortalSession

# TODO update the JSON string below
json = "{}"
# create an instance of BillingPortalSession from a JSON string
billing_portal_session_instance = BillingPortalSession.from_json(json)
# print the JSON string representation of the object
print(BillingPortalSession.to_json())

# convert the object into a dict
billing_portal_session_dict = billing_portal_session_instance.to_dict()
# create an instance of BillingPortalSession from a dict
billing_portal_session_from_dict = BillingPortalSession.from_dict(billing_portal_session_dict)
```
[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)


