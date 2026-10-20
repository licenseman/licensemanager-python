# licensemanager.TokensApi

All URIs are relative to *https://api.licensemanager.dev*

Method | HTTP request | Description
------------- | ------------- | -------------
[**create_customer_token**](TokensApi.md#create_customer_token) | **POST** /v1/customers/{id}/tokens | Create a customer token
[**create_license_token**](TokensApi.md#create_license_token) | **POST** /v1/licenses/{id}/tokens | Create a license token
[**create_machine_token**](TokensApi.md#create_machine_token) | **POST** /v1/machines/{id}/tokens | Create a machine token


# **create_customer_token**
> Token create_customer_token(id, create_token)

Create a customer token

Creates a token scoped to the customer, with the permissions of `scope`, to hand to your customers: a page of your website can then call the endpoints accepting tokens directly, without your API key. See the `token` security scheme for what a token reaches.

A token can't be revoked: it works until it expires, unless the resource it's scoped to is deleted.

**Required role permission**: `token:create` when called with a session, granted by the member's role. API keys aren't limited by roles.

### Example

* Api Key Authentication (apiKey):

```python
import licensemanager
from licensemanager.models.create_token import CreateToken
from licensemanager.models.token import Token
from licensemanager.rest import ApiException
from pprint import pprint

# Defining the host is optional and defaults to https://api.licensemanager.dev
# See configuration.py for a list of all supported configuration parameters.
configuration = licensemanager.Configuration(
    host = "https://api.licensemanager.dev"
)

# The client must configure the authentication and authorization parameters
# in accordance with the API server security policy.
# Examples for each auth method are provided below, use the example that
# satisfies your auth use case.

# Configure API key authorization: apiKey
configuration.api_key['apiKey'] = os.environ["API_KEY"]

# Uncomment below to setup prefix (e.g. Bearer) for API key, if needed
# configuration.api_key_prefix['apiKey'] = 'Bearer'

# Enter a context with an instance of the API client
with licensemanager.ApiClient(configuration) as api_client:
    # Create an instance of the API class
    api_instance = licensemanager.TokensApi(api_client)
    id = 'c9Wd3RtE' # str | 
    create_token = licensemanager.CreateToken() # CreateToken | 

    try:
        # Create a customer token
        api_response = api_instance.create_customer_token(id, create_token)
        print("The response of TokensApi->create_customer_token:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling TokensApi->create_customer_token: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **id** | **str**|  | 
 **create_token** | [**CreateToken**](CreateToken.md)|  | 

### Return type

[**Token**](Token.md)

### Authorization

[apiKey](../README.md#apiKey)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details

| Status code | Description | Response headers |
|-------------|-------------|------------------|
**201** | Created token |  -  |
**401** | &#x60;unauthorized&#x60;: no credentials. &#x60;invalid_api_key&#x60;: the API key doesn&#39;t exist, was revoked or has expired. &#x60;invalid_token&#x60;: the token&#39;s signature is invalid, it has expired, or the resource it&#39;s scoped to was deleted |  -  |
**402** | &#x60;plan_limit_exceeded&#x60;: the organization stayed over its plan&#39;s limits after the grace period, its API is blocked until it upgrades. &#x60;plan_limit_reached&#x60;: creating the resource would go over the plan&#39;s limit |  -  |
**403** | &#x60;token_not_allowed&#x60;: the endpoint doesn&#39;t accept tokens, or not of this type. &#x60;insufficient_scope&#x60;: the token lacks the permission. &#x60;no_active_organization&#x60; or &#x60;forbidden&#x60;: the session has no organization, or isn&#39;t a member of the one requested |  -  |
**404** | Customer not found |  -  |
**422** | &#x60;validation_error&#x60;: invalid path, query or body, with the &#x60;issues&#x60; |  -  |
**429** | &#x60;rate_limited&#x60;: the API key made more than 10 requests in the last second. Wait for the &#x60;Retry-After&#x60; seconds |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

# **create_license_token**
> Token create_license_token(id, create_token)

Create a license token

Creates a token scoped to the license, with the permissions of `scope`, to hand to your customers: a page of your website can then call the endpoints accepting tokens directly, without your API key. See the `token` security scheme for what a token reaches.

A token can't be revoked: it works until it expires, unless the resource it's scoped to is deleted.

**Token access**: customer tokens. A customer token creates tokens for its customer's licenses, with the permissions and at most the expiration it has.

**Required role permission**: `token:create` when called with a session, granted by the member's role. API keys aren't limited by roles.

### Example

* Api Key Authentication (apiKey):
* Bearer (JWT) Authentication (token):

```python
import licensemanager
from licensemanager.models.create_token import CreateToken
from licensemanager.models.token import Token
from licensemanager.rest import ApiException
from pprint import pprint

# Defining the host is optional and defaults to https://api.licensemanager.dev
# See configuration.py for a list of all supported configuration parameters.
configuration = licensemanager.Configuration(
    host = "https://api.licensemanager.dev"
)

# The client must configure the authentication and authorization parameters
# in accordance with the API server security policy.
# Examples for each auth method are provided below, use the example that
# satisfies your auth use case.

# Configure API key authorization: apiKey
configuration.api_key['apiKey'] = os.environ["API_KEY"]

# Uncomment below to setup prefix (e.g. Bearer) for API key, if needed
# configuration.api_key_prefix['apiKey'] = 'Bearer'

# Configure Bearer authorization (JWT): token
configuration = licensemanager.Configuration(
    access_token = os.environ["BEARER_TOKEN"]
)

# Enter a context with an instance of the API client
with licensemanager.ApiClient(configuration) as api_client:
    # Create an instance of the API class
    api_instance = licensemanager.TokensApi(api_client)
    id = 'c9Wd3RtE' # str | 
    create_token = licensemanager.CreateToken() # CreateToken | 

    try:
        # Create a license token
        api_response = api_instance.create_license_token(id, create_token)
        print("The response of TokensApi->create_license_token:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling TokensApi->create_license_token: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **id** | **str**|  | 
 **create_token** | [**CreateToken**](CreateToken.md)|  | 

### Return type

[**Token**](Token.md)

### Authorization

[apiKey](../README.md#apiKey), [token](../README.md#token)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details

| Status code | Description | Response headers |
|-------------|-------------|------------------|
**201** | Created token |  -  |
**401** | &#x60;unauthorized&#x60;: no credentials. &#x60;invalid_api_key&#x60;: the API key doesn&#39;t exist, was revoked or has expired. &#x60;invalid_token&#x60;: the token&#39;s signature is invalid, it has expired, or the resource it&#39;s scoped to was deleted |  -  |
**402** | &#x60;plan_limit_exceeded&#x60;: the organization stayed over its plan&#39;s limits after the grace period, its API is blocked until it upgrades. &#x60;plan_limit_reached&#x60;: creating the resource would go over the plan&#39;s limit |  -  |
**403** | &#x60;token_not_allowed&#x60;: the endpoint doesn&#39;t accept tokens, or not of this type. &#x60;insufficient_scope&#x60;: the token lacks the permission. &#x60;no_active_organization&#x60; or &#x60;forbidden&#x60;: the session has no organization, or isn&#39;t a member of the one requested |  -  |
**404** | License not found |  -  |
**422** | &#x60;validation_error&#x60;: invalid path, query or body, with the &#x60;issues&#x60; |  -  |
**429** | &#x60;rate_limited&#x60;: the API key made more than 10 requests in the last second. Wait for the &#x60;Retry-After&#x60; seconds |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

# **create_machine_token**
> Token create_machine_token(id, create_token)

Create a machine token

Creates a token scoped to the machine, with the permissions of `scope`, to hand to your customers: a page of your website can then call the endpoints accepting tokens directly, without your API key. See the `token` security scheme for what a token reaches.

A token can't be revoked: it works until it expires, unless the resource it's scoped to is deleted.

**Token access**: customer, license tokens. A customer or license token creates tokens for the machines it reaches, with the permissions and at most the expiration it has.

**Required role permission**: `token:create` when called with a session, granted by the member's role. API keys aren't limited by roles.

### Example

* Api Key Authentication (apiKey):
* Bearer (JWT) Authentication (token):

```python
import licensemanager
from licensemanager.models.create_token import CreateToken
from licensemanager.models.token import Token
from licensemanager.rest import ApiException
from pprint import pprint

# Defining the host is optional and defaults to https://api.licensemanager.dev
# See configuration.py for a list of all supported configuration parameters.
configuration = licensemanager.Configuration(
    host = "https://api.licensemanager.dev"
)

# The client must configure the authentication and authorization parameters
# in accordance with the API server security policy.
# Examples for each auth method are provided below, use the example that
# satisfies your auth use case.

# Configure API key authorization: apiKey
configuration.api_key['apiKey'] = os.environ["API_KEY"]

# Uncomment below to setup prefix (e.g. Bearer) for API key, if needed
# configuration.api_key_prefix['apiKey'] = 'Bearer'

# Configure Bearer authorization (JWT): token
configuration = licensemanager.Configuration(
    access_token = os.environ["BEARER_TOKEN"]
)

# Enter a context with an instance of the API client
with licensemanager.ApiClient(configuration) as api_client:
    # Create an instance of the API class
    api_instance = licensemanager.TokensApi(api_client)
    id = 'c9Wd3RtE' # str | 
    create_token = licensemanager.CreateToken() # CreateToken | 

    try:
        # Create a machine token
        api_response = api_instance.create_machine_token(id, create_token)
        print("The response of TokensApi->create_machine_token:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling TokensApi->create_machine_token: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **id** | **str**|  | 
 **create_token** | [**CreateToken**](CreateToken.md)|  | 

### Return type

[**Token**](Token.md)

### Authorization

[apiKey](../README.md#apiKey), [token](../README.md#token)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details

| Status code | Description | Response headers |
|-------------|-------------|------------------|
**201** | Created token |  -  |
**401** | &#x60;unauthorized&#x60;: no credentials. &#x60;invalid_api_key&#x60;: the API key doesn&#39;t exist, was revoked or has expired. &#x60;invalid_token&#x60;: the token&#39;s signature is invalid, it has expired, or the resource it&#39;s scoped to was deleted |  -  |
**402** | &#x60;plan_limit_exceeded&#x60;: the organization stayed over its plan&#39;s limits after the grace period, its API is blocked until it upgrades. &#x60;plan_limit_reached&#x60;: creating the resource would go over the plan&#39;s limit |  -  |
**403** | &#x60;token_not_allowed&#x60;: the endpoint doesn&#39;t accept tokens, or not of this type. &#x60;insufficient_scope&#x60;: the token lacks the permission. &#x60;no_active_organization&#x60; or &#x60;forbidden&#x60;: the session has no organization, or isn&#39;t a member of the one requested |  -  |
**404** | Machine not found |  -  |
**422** | &#x60;validation_error&#x60;: invalid path, query or body, with the &#x60;issues&#x60; |  -  |
**429** | &#x60;rate_limited&#x60;: the API key made more than 10 requests in the last second. Wait for the &#x60;Retry-After&#x60; seconds |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

