# CreateLicense


## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**email** | **str** | Email of the customer the license belongs to. The product&#39;s customer with this email, compared regardless of case, or a new one when there&#39;s none. | 
**key** | **str** | Unique within the product. Case sensitive: &#x60;validateKey&#x60; compares keys exactly. Defaults to a random key of 5 groups of 5 characters separated by dashes, each character an upper case letter or a digit other than &#x60;O&#x60;, &#x60;0&#x60;, &#x60;I&#x60; and &#x60;1&#x60;, for 125 random bits. Starts with &#x60;TEST-&#x60; in test products, which is added when missing, and removed in live products. | [optional] 
**policy_id** | **str** | Policy of the product the license follows. Defaults to the product&#39;s default policy. | [optional] 
**expires_at** | **datetime** | &#x60;null&#x60; makes the license never expire. Defaults to the creation date plus the duration of the policy, or &#x60;null&#x60; when the policy has none. | [optional] 
**meta** | **Dict[str, Optional[object]]** | Free-form JSON object. | [optional] 
**max_machines** | **int** | Maximum number of active machines the license can be used on. &#x60;null&#x60; for no limit. Defaults to the one of the policy. | [optional] 
**max_offline_duration_seconds** | **int** | Longest the applications can run offline with the license, in seconds. At least one hour (&#x60;3600&#x60;). Defaults to the one of the policy. | [optional] 
**price** | [**PriceInput**](PriceInput.md) |  | [optional] 
**max_version** | [**LicenseMaxVersionInput**](LicenseMaxVersionInput.md) |  | [optional] 
**send_key** | **bool** | &#x60;true&#x60; emails the key to the customer once the license is created, like &#x60;sendLicenseKeys&#x60;. Sent in the background: a failed email doesn&#39;t fail the creation. In test products, it&#39;s only sent when the customer&#39;s email is a member&#39;s of the organization. Defaults to &#x60;false&#x60;. | [optional] 

## Example

```python
from licensemanager.models.create_license import CreateLicense

# TODO update the JSON string below
json = "{}"
# create an instance of CreateLicense from a JSON string
create_license_instance = CreateLicense.from_json(json)
# print the JSON string representation of the object
print(CreateLicense.to_json())

# convert the object into a dict
create_license_dict = create_license_instance.to_dict()
# create an instance of CreateLicense from a dict
create_license_from_dict = CreateLicense.from_dict(create_license_dict)
```
[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)


