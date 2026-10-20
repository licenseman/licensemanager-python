# License


## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**id** | **str** |  | 
**product_id** | **str** |  | 
**policy_id** | **str** |  | 
**customer_id** | **str** |  | 
**key** | **str** | Unique within the product. Case sensitive: &#x60;validateKey&#x60; compares keys exactly. | 
**created_at** | **datetime** |  | 
**expires_at** | **datetime** | &#x60;null&#x60; when the license never expires. | 
**meta** | **Dict[str, Optional[object]]** | Free-form JSON object. | 
**stripe_payment_intent_id** | **str** | Id of the Stripe payment intent that paid the license, when it was bought through the Stripe integration. &#x60;null&#x60; otherwise, or when nothing was paid. | 
**max_machines** | **int** | Maximum number of active machines the license can be used on. &#x60;null&#x60; when there&#39;s no limit. Can be lower than &#x60;activeMachineCount&#x60; after it was lowered: machines aren&#39;t deactivated to match it. | 
**max_offline_duration_seconds** | **int** | Longest the applications can run offline with the license: the license tokens returned by &#x60;validateKey&#x60; expire this long after they&#39;re issued, unless the license expires sooner. | 
**active_machine_count** | **int** | Number of active machines the license is used on. | 
**last_activated_at** | **datetime** | Last time a machine validated the license key. &#x60;null&#x60; when it was never validated. | 
**max_version** | [**LicenseMaxVersion**](LicenseMaxVersion.md) |  | 
**price** | [**Price**](Price.md) |  | 
**status** | [**LicenseStatus**](LicenseStatus.md) |  | 
**updated_at** | **datetime** | Last time the license&#39;s settings were edited, not when its key was validated. | 

## Example

```python
from licensemanager.models.license import License

# TODO update the JSON string below
json = "{}"
# create an instance of License from a JSON string
license_instance = License.from_json(json)
# print the JSON string representation of the object
print(License.to_json())

# convert the object into a dict
license_dict = license_instance.to_dict()
# create an instance of License from a dict
license_from_dict = License.from_dict(license_dict)
```
[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)


