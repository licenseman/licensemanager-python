# CreatePaddleMapping


## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**paddle_price_id** | **str** | Active one-time or recurring catalog price of the Paddle account. | 
**policy_id** | **str** |  | 

## Example

```python
from licensemanager.models.create_paddle_mapping import CreatePaddleMapping

# TODO update the JSON string below
json = "{}"
# create an instance of CreatePaddleMapping from a JSON string
create_paddle_mapping_instance = CreatePaddleMapping.from_json(json)
# print the JSON string representation of the object
print(CreatePaddleMapping.to_json())

# convert the object into a dict
create_paddle_mapping_dict = create_paddle_mapping_instance.to_dict()
# create an instance of CreatePaddleMapping from a dict
create_paddle_mapping_from_dict = CreatePaddleMapping.from_dict(create_paddle_mapping_dict)
```
[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)


