# CreateToken


## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**scope** | **List[str]** | Permissions of the token. A write permission implies the matching read one. A token creating a token can only give the permissions it has. | 
**expires_in_seconds** | **int** | How long the token works, in seconds, from 60 (1 minute) to 31536000 (365 days). Defaults to 900 (15 minutes). A token creating a token can&#39;t give it a later expiration than its own: it&#39;s shortened to it. | [optional] [default to 900]

## Example

```python
from licensemanager.models.create_token import CreateToken

# TODO update the JSON string below
json = "{}"
# create an instance of CreateToken from a JSON string
create_token_instance = CreateToken.from_json(json)
# print the JSON string representation of the object
print(CreateToken.to_json())

# convert the object into a dict
create_token_dict = create_token_instance.to_dict()
# create an instance of CreateToken from a dict
create_token_from_dict = CreateToken.from_dict(create_token_dict)
```
[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)


