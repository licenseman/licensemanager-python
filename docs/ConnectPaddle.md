# ConnectPaddle


## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**api_key** | **str** | API key of the Paddle Billing account (&#x60;pdl_live_apikey_…&#x60; for live products, &#x60;pdl_sdbx_apikey_…&#x60; from a sandbox account for test products), with the &#x60;requiredPermissions&#x60; of &#x60;getPaddleIntegration&#x60;. Without the optional ones, it connects with what they&#39;re for turned off. | 

## Example

```python
from licensemanager.models.connect_paddle import ConnectPaddle

# TODO update the JSON string below
json = "{}"
# create an instance of ConnectPaddle from a JSON string
connect_paddle_instance = ConnectPaddle.from_json(json)
# print the JSON string representation of the object
print(ConnectPaddle.to_json())

# convert the object into a dict
connect_paddle_dict = connect_paddle_instance.to_dict()
# create an instance of ConnectPaddle from a dict
connect_paddle_from_dict = ConnectPaddle.from_dict(connect_paddle_dict)
```
[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)


