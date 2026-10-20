# licensemanager.EventsApi

All URIs are relative to *https://api.licensemanager.dev*

Method | HTTP request | Description
------------- | ------------- | -------------
[**list_license_events**](EventsApi.md#list_license_events) | **GET** /v1/licenses/{id}/events | List the events of a license
[**list_policy_events**](EventsApi.md#list_policy_events) | **GET** /v1/policies/{id}/events | List the events of a policy


# **list_license_events**
> EventList list_license_events(id, page=page, page_size=page_size, sort=sort, type=type, machine_id=machine_id)

List the events of a license

Includes the validations of the license on each of its machines. Doesn't accept tokens: only API keys and sessions.

### Example

* Api Key Authentication (apiKey):

```python
import licensemanager
from licensemanager.models.event_list import EventList
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
    api_instance = licensemanager.EventsApi(api_client)
    id = 'l3Nv8KwB' # str | 
    page = 1 # int | Page to return. Pages are numbered from 1: `1` is the first page. A page past the last one returns an empty `data`, not an error. Defaults to `1`. (optional) (default to 1)
    page_size = 20 # int | Maximum number of items per page, from 1 to 100. Every page holds this many items except the last one, which can hold fewer. Defaults to `20`. (optional) (default to 20)
    sort = '-createdAt' # str | Field to sort by, prefixed with `-` for descending order. Defaults to `-createdAt`. (optional) (default to '-createdAt')
    type = licensemanager.ListPolicyEventsTypeParameter() # ListPolicyEventsTypeParameter | Only returns the events of this type. Repeat it to return the events of any of these types. (optional)
    machine_id = 'm9Tq3VhD' # str | Only returns the events of this machine of the license. (optional)

    try:
        # List the events of a license
        api_response = api_instance.list_license_events(id, page=page, page_size=page_size, sort=sort, type=type, machine_id=machine_id)
        print("The response of EventsApi->list_license_events:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling EventsApi->list_license_events: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **id** | **str**|  | 
 **page** | **int**| Page to return. Pages are numbered from 1: &#x60;1&#x60; is the first page. A page past the last one returns an empty &#x60;data&#x60;, not an error. Defaults to &#x60;1&#x60;. | [optional] [default to 1]
 **page_size** | **int**| Maximum number of items per page, from 1 to 100. Every page holds this many items except the last one, which can hold fewer. Defaults to &#x60;20&#x60;. | [optional] [default to 20]
 **sort** | **str**| Field to sort by, prefixed with &#x60;-&#x60; for descending order. Defaults to &#x60;-createdAt&#x60;. | [optional] [default to &#39;-createdAt&#39;]
 **type** | [**ListPolicyEventsTypeParameter**](.md)| Only returns the events of this type. Repeat it to return the events of any of these types. | [optional] 
 **machine_id** | **str**| Only returns the events of this machine of the license. | [optional] 

### Return type

[**EventList**](EventList.md)

### Authorization

[apiKey](../README.md#apiKey)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details

| Status code | Description | Response headers |
|-------------|-------------|------------------|
**200** | One page of the events of the license |  -  |
**401** | &#x60;unauthorized&#x60;: no credentials. &#x60;invalid_api_key&#x60;: the API key doesn&#39;t exist, was revoked or has expired. &#x60;invalid_token&#x60;: the token&#39;s signature is invalid, it has expired, or the resource it&#39;s scoped to was deleted |  -  |
**402** | &#x60;plan_limit_exceeded&#x60;: the organization stayed over its plan&#39;s limits after the grace period, its API is blocked until it upgrades. &#x60;plan_limit_reached&#x60;: creating the resource would go over the plan&#39;s limit |  -  |
**403** | &#x60;token_not_allowed&#x60;: the endpoint doesn&#39;t accept tokens, or not of this type. &#x60;insufficient_scope&#x60;: the token lacks the permission. &#x60;no_active_organization&#x60; or &#x60;forbidden&#x60;: the session has no organization, or isn&#39;t a member of the one requested |  -  |
**404** | License not found |  -  |
**422** | &#x60;validation_error&#x60;: invalid path, query or body, with the &#x60;issues&#x60; |  -  |
**429** | &#x60;rate_limited&#x60;: the API key made more than 10 requests in the last second. Wait for the &#x60;Retry-After&#x60; seconds |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

# **list_policy_events**
> EventList list_policy_events(id, page=page, page_size=page_size, sort=sort, type=type)

List the events of a policy

Doesn't accept tokens: only API keys and sessions.

### Example

* Api Key Authentication (apiKey):

```python
import licensemanager
from licensemanager.models.event_list import EventList
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
    api_instance = licensemanager.EventsApi(api_client)
    id = 'l3Nv8KwB' # str | 
    page = 1 # int | Page to return. Pages are numbered from 1: `1` is the first page. A page past the last one returns an empty `data`, not an error. Defaults to `1`. (optional) (default to 1)
    page_size = 20 # int | Maximum number of items per page, from 1 to 100. Every page holds this many items except the last one, which can hold fewer. Defaults to `20`. (optional) (default to 20)
    sort = '-createdAt' # str | Field to sort by, prefixed with `-` for descending order. Defaults to `-createdAt`. (optional) (default to '-createdAt')
    type = licensemanager.ListPolicyEventsTypeParameter() # ListPolicyEventsTypeParameter | Only returns the events of this type. Repeat it to return the events of any of these types. (optional)

    try:
        # List the events of a policy
        api_response = api_instance.list_policy_events(id, page=page, page_size=page_size, sort=sort, type=type)
        print("The response of EventsApi->list_policy_events:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling EventsApi->list_policy_events: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **id** | **str**|  | 
 **page** | **int**| Page to return. Pages are numbered from 1: &#x60;1&#x60; is the first page. A page past the last one returns an empty &#x60;data&#x60;, not an error. Defaults to &#x60;1&#x60;. | [optional] [default to 1]
 **page_size** | **int**| Maximum number of items per page, from 1 to 100. Every page holds this many items except the last one, which can hold fewer. Defaults to &#x60;20&#x60;. | [optional] [default to 20]
 **sort** | **str**| Field to sort by, prefixed with &#x60;-&#x60; for descending order. Defaults to &#x60;-createdAt&#x60;. | [optional] [default to &#39;-createdAt&#39;]
 **type** | [**ListPolicyEventsTypeParameter**](.md)| Only returns the events of this type. Repeat it to return the events of any of these types. | [optional] 

### Return type

[**EventList**](EventList.md)

### Authorization

[apiKey](../README.md#apiKey)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details

| Status code | Description | Response headers |
|-------------|-------------|------------------|
**200** | One page of the events of the policy |  -  |
**401** | &#x60;unauthorized&#x60;: no credentials. &#x60;invalid_api_key&#x60;: the API key doesn&#39;t exist, was revoked or has expired. &#x60;invalid_token&#x60;: the token&#39;s signature is invalid, it has expired, or the resource it&#39;s scoped to was deleted |  -  |
**402** | &#x60;plan_limit_exceeded&#x60;: the organization stayed over its plan&#39;s limits after the grace period, its API is blocked until it upgrades. &#x60;plan_limit_reached&#x60;: creating the resource would go over the plan&#39;s limit |  -  |
**403** | &#x60;token_not_allowed&#x60;: the endpoint doesn&#39;t accept tokens, or not of this type. &#x60;insufficient_scope&#x60;: the token lacks the permission. &#x60;no_active_organization&#x60; or &#x60;forbidden&#x60;: the session has no organization, or isn&#39;t a member of the one requested |  -  |
**404** | Policy not found |  -  |
**422** | &#x60;validation_error&#x60;: invalid path, query or body, with the &#x60;issues&#x60; |  -  |
**429** | &#x60;rate_limited&#x60;: the API key made more than 10 requests in the last second. Wait for the &#x60;Retry-After&#x60; seconds |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

