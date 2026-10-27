# licensemanager.MachinesApi

All URIs are relative to *https://api.licensemanager.dev*

Method | HTTP request | Description
------------- | ------------- | -------------
[**deactivate_machine**](MachinesApi.md#deactivate_machine) | **POST** /v1/machines/{id}/deactivate | Deactivate a machine
[**get_machine**](MachinesApi.md#get_machine) | **GET** /v1/machines/{id} | Get a machine
[**list_machines**](MachinesApi.md#list_machines) | **GET** /v1/licenses/{licenseId}/machines | List the machines of a license


# **deactivate_machine**
> Machine deactivate_machine(id)

Deactivate a machine

The machine no longer counts as using the license, freeing its place when the license has a maximum number of machines. Validating the license key on the machine activates it again, unless the license is on its maximum number of machines by then. Deactivating a deactivated or locked machine does nothing.

The license token `validateKey` returned to the machine isn't revoked: the application can keep running offline until it expires. Machines can't be deleted: they're deleted with their license.

**Token access**: customer, license, machine tokens with the `machine:write` permission (or the matching write one). A token reaches the machine it's scoped to, or the machines of its license or customer.

**Required role permission**: `machine:deactivate` when called with a session, granted by the member's role. API keys aren't limited by roles.

### Example

* Api Key Authentication (apiKey):
* Bearer (JWT) Authentication (token):

```python
import licensemanager
from licensemanager.models.machine import Machine
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
    api_instance = licensemanager.MachinesApi(api_client)
    id = 'm9Tq3VhD' # str | 

    try:
        # Deactivate a machine
        api_response = api_instance.deactivate_machine(id)
        print("The response of MachinesApi->deactivate_machine:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling MachinesApi->deactivate_machine: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **id** | **str**|  | 

### Return type

[**Machine**](Machine.md)

### Authorization

[apiKey](../README.md#apiKey), [token](../README.md#token)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details

| Status code | Description | Response headers |
|-------------|-------------|------------------|
**200** | Deactivated machine |  -  |
**401** | &#x60;unauthorized&#x60;: no credentials. &#x60;invalid_api_key&#x60;: the API key doesn&#39;t exist, was revoked or has expired. &#x60;invalid_token&#x60;: the token&#39;s signature is invalid, it has expired, or the resource it&#39;s scoped to was deleted |  -  |
**402** | &#x60;plan_limit_exceeded&#x60;: the organization stayed over its plan&#39;s limits after the grace period, its API is blocked until it upgrades. &#x60;plan_limit_reached&#x60;: creating the resource would go over the plan&#39;s limit |  -  |
**403** | &#x60;token_not_allowed&#x60;: the endpoint doesn&#39;t accept tokens, or not of this type. &#x60;insufficient_scope&#x60;: the token lacks the permission. &#x60;no_active_organization&#x60; or &#x60;forbidden&#x60;: the session has no organization, or isn&#39;t a member of the one requested |  -  |
**404** | Machine not found |  -  |
**422** | &#x60;validation_error&#x60;: invalid path, query or body, with the &#x60;issues&#x60; |  -  |
**429** | &#x60;rate_limited&#x60;: the API key made more than 10 requests in the last second. Wait for the &#x60;Retry-After&#x60; seconds |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

# **get_machine**
> Machine get_machine(id)

Get a machine

**Token access**: customer, license, machine tokens with the `machine:read` permission (or the matching write one). A token reaches the machine it's scoped to, or the machines of its license or customer.

### Example

* Api Key Authentication (apiKey):
* Bearer (JWT) Authentication (token):

```python
import licensemanager
from licensemanager.models.machine import Machine
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
    api_instance = licensemanager.MachinesApi(api_client)
    id = 'm9Tq3VhD' # str | 

    try:
        # Get a machine
        api_response = api_instance.get_machine(id)
        print("The response of MachinesApi->get_machine:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling MachinesApi->get_machine: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **id** | **str**|  | 

### Return type

[**Machine**](Machine.md)

### Authorization

[apiKey](../README.md#apiKey), [token](../README.md#token)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details

| Status code | Description | Response headers |
|-------------|-------------|------------------|
**200** | Machine |  -  |
**401** | &#x60;unauthorized&#x60;: no credentials. &#x60;invalid_api_key&#x60;: the API key doesn&#39;t exist, was revoked or has expired. &#x60;invalid_token&#x60;: the token&#39;s signature is invalid, it has expired, or the resource it&#39;s scoped to was deleted |  -  |
**402** | &#x60;plan_limit_exceeded&#x60;: the organization stayed over its plan&#39;s limits after the grace period, its API is blocked until it upgrades. &#x60;plan_limit_reached&#x60;: creating the resource would go over the plan&#39;s limit |  -  |
**403** | &#x60;token_not_allowed&#x60;: the endpoint doesn&#39;t accept tokens, or not of this type. &#x60;insufficient_scope&#x60;: the token lacks the permission. &#x60;no_active_organization&#x60; or &#x60;forbidden&#x60;: the session has no organization, or isn&#39;t a member of the one requested |  -  |
**404** | Machine not found |  -  |
**422** | &#x60;validation_error&#x60;: invalid path, query or body, with the &#x60;issues&#x60; |  -  |
**429** | &#x60;rate_limited&#x60;: the API key made more than 10 requests in the last second. Wait for the &#x60;Retry-After&#x60; seconds |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

# **list_machines**
> MachineList list_machines(license_id, page=page, page_size=page_size, sort=sort, search=search, fingerprint=fingerprint, status=status)

List the machines of a license

**Token access**: customer, license tokens with the `machine:read` permission (or the matching write one). A token reaches the license it's scoped to, or the licenses of its customer.

### Example

* Api Key Authentication (apiKey):
* Bearer (JWT) Authentication (token):

```python
import licensemanager
from licensemanager.models.machine_list import MachineList
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
    api_instance = licensemanager.MachinesApi(api_client)
    license_id = 'l3Nv8KwB' # str | 
    page = 1 # int | Page to return. Pages are numbered from 1: `1` is the first page. A page past the last one returns an empty `data`, not an error. Defaults to `1`. (optional) (default to 1)
    page_size = 20 # int | Maximum number of items per page, from 1 to 100. Every page holds this many items except the last one, which can hold fewer. Defaults to `20`. (optional) (default to 20)
    sort = '-createdAt' # str | Field to sort by, prefixed with `-` for descending order. Defaults to `-createdAt`. (optional) (default to '-createdAt')
    search = 'macbook' # str | Case-insensitive text the fingerprint or name contains. (optional)
    fingerprint = '4c:32:75:8f:9a:1e' # str | Only returns the machine with this exact fingerprint. (optional)
    status = 'active' # str | Only returns the machines with this status. (optional)

    try:
        # List the machines of a license
        api_response = api_instance.list_machines(license_id, page=page, page_size=page_size, sort=sort, search=search, fingerprint=fingerprint, status=status)
        print("The response of MachinesApi->list_machines:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling MachinesApi->list_machines: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **license_id** | **str**|  | 
 **page** | **int**| Page to return. Pages are numbered from 1: &#x60;1&#x60; is the first page. A page past the last one returns an empty &#x60;data&#x60;, not an error. Defaults to &#x60;1&#x60;. | [optional] [default to 1]
 **page_size** | **int**| Maximum number of items per page, from 1 to 100. Every page holds this many items except the last one, which can hold fewer. Defaults to &#x60;20&#x60;. | [optional] [default to 20]
 **sort** | **str**| Field to sort by, prefixed with &#x60;-&#x60; for descending order. Defaults to &#x60;-createdAt&#x60;. | [optional] [default to &#39;-createdAt&#39;]
 **search** | **str**| Case-insensitive text the fingerprint or name contains. | [optional] 
 **fingerprint** | **str**| Only returns the machine with this exact fingerprint. | [optional] 
 **status** | **str**| Only returns the machines with this status. | [optional] 

### Return type

[**MachineList**](MachineList.md)

### Authorization

[apiKey](../README.md#apiKey), [token](../README.md#token)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details

| Status code | Description | Response headers |
|-------------|-------------|------------------|
**200** | One page of the machines of the license |  -  |
**401** | &#x60;unauthorized&#x60;: no credentials. &#x60;invalid_api_key&#x60;: the API key doesn&#39;t exist, was revoked or has expired. &#x60;invalid_token&#x60;: the token&#39;s signature is invalid, it has expired, or the resource it&#39;s scoped to was deleted |  -  |
**402** | &#x60;plan_limit_exceeded&#x60;: the organization stayed over its plan&#39;s limits after the grace period, its API is blocked until it upgrades. &#x60;plan_limit_reached&#x60;: creating the resource would go over the plan&#39;s limit |  -  |
**403** | &#x60;token_not_allowed&#x60;: the endpoint doesn&#39;t accept tokens, or not of this type. &#x60;insufficient_scope&#x60;: the token lacks the permission. &#x60;no_active_organization&#x60; or &#x60;forbidden&#x60;: the session has no organization, or isn&#39;t a member of the one requested |  -  |
**404** | License not found |  -  |
**422** | &#x60;validation_error&#x60;: invalid path, query or body, with the &#x60;issues&#x60; |  -  |
**429** | &#x60;rate_limited&#x60;: the API key made more than 10 requests in the last second. Wait for the &#x60;Retry-After&#x60; seconds |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

