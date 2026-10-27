# CancelLicense


## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**reason** | [**CancellationReason**](CancellationReason.md) |  | 
**comment** | **str** | What the customer said about the cancellation. | [optional] 
**refund** | **bool** | Whether to refund the license&#39;s Stripe payment, when it was bought through the Stripe integration. Defaults to the integration&#39;s &#x60;autoRefund&#x60;. Ignored for tokens, which always follow &#x60;autoRefund&#x60;, and when the integration&#39;s &#x60;canRefund&#x60; is false: its API key can&#39;t create refunds. | [optional] 

## Example

```python
from licensemanager.models.cancel_license import CancelLicense

# TODO update the JSON string below
json = "{}"
# create an instance of CancelLicense from a JSON string
cancel_license_instance = CancelLicense.from_json(json)
# print the JSON string representation of the object
print(CancelLicense.to_json())

# convert the object into a dict
cancel_license_dict = cancel_license_instance.to_dict()
# create an instance of CancelLicense from a dict
cancel_license_from_dict = CancelLicense.from_dict(cancel_license_dict)
```
[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)


