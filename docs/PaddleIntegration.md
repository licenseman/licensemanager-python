# PaddleIntegration


## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**livemode** | **bool** | Environment of the Paddle connection the product uses: live for live products, sandbox for test products. | 
**webhook_url_reachable** | **bool** | Whether Paddle can reach the API&#39;s webhook URL. A local URL can&#39;t be: set &#x60;WEBHOOK_URL&#x60; on the server, like to a tunnel in development. | 
**required_permissions** | [**List[PaddlePermission]**](PaddlePermission.md) | Permissions the API key needs, and why, the &#x60;optional&#x60; ones included. Every other permission can stay off. | 
**integration** | [**Integration**](Integration.md) | The organization&#39;s Paddle connection in this environment, &#x60;null&#x60; when there&#39;s none. | 
**mappings** | [**List[IntegrationMapping]**](IntegrationMapping.md) | Paddle prices creating licenses of the product. | 

## Example

```python
from licensemanager.models.paddle_integration import PaddleIntegration

# TODO update the JSON string below
json = "{}"
# create an instance of PaddleIntegration from a JSON string
paddle_integration_instance = PaddleIntegration.from_json(json)
# print the JSON string representation of the object
print(PaddleIntegration.to_json())

# convert the object into a dict
paddle_integration_dict = paddle_integration_instance.to_dict()
# create an instance of PaddleIntegration from a dict
paddle_integration_from_dict = PaddleIntegration.from_dict(paddle_integration_dict)
```
[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)


