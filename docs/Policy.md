# Policy


## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**id** | **str** |  | 
**product_id** | **str** |  | 
**slug** | **str** |  | 
**name** | **str** |  | 
**is_default** | **bool** | Whether this is the product&#39;s default policy. Each product has exactly one. | 
**duration** | [**PolicyDuration**](PolicyDuration.md) |  | 
**max_machines** | **int** | Maximum number of active machines of the licenses created with this policy. &#x60;null&#x60; when there&#39;s no limit. | 
**max_offline_duration_seconds** | **int** | Longest the applications can run offline with the licenses created with this policy, in seconds. | 
**max_version** | [**PolicyMaxVersion**](PolicyMaxVersion.md) |  | 
**money_back_guarantee_days** | **int** | Number of days after their creation during which customers can cancel the licenses created with this policy, from the customer portal or with &#x60;cancelLicense&#x60;. &#x60;null&#x60; when they can&#39;t. | 
**license_count** | **int** | Number of licenses following this policy. | 
**created_at** | **datetime** |  | 
**updated_at** | **datetime** |  | 

## Example

```python
from licensemanager.models.policy import Policy

# TODO update the JSON string below
json = "{}"
# create an instance of Policy from a JSON string
policy_instance = Policy.from_json(json)
# print the JSON string representation of the object
print(Policy.to_json())

# convert the object into a dict
policy_dict = policy_instance.to_dict()
# create an instance of Policy from a dict
policy_from_dict = Policy.from_dict(policy_dict)
```
[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)


