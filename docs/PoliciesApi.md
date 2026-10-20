# licensemanager.PoliciesApi

All URIs are relative to *https://api.licensemanager.dev*

Method | HTTP request | Description
------------- | ------------- | -------------
[**create_policy**](PoliciesApi.md#create_policy) | **POST** /v1/products/{productId}/policies | Create a policy
[**delete_policy**](PoliciesApi.md#delete_policy) | **DELETE** /v1/policies/{id} | Delete a policy
[**get_policy**](PoliciesApi.md#get_policy) | **GET** /v1/policies/{id} | Get a policy
[**list_policies**](PoliciesApi.md#list_policies) | **GET** /v1/products/{productId}/policies | List the policies of a product
[**update_policy**](PoliciesApi.md#update_policy) | **PATCH** /v1/policies/{id} | Update a policy


# **create_policy**
> Policy create_policy(product_id, create_policy)

Create a policy

Without a `slug`, the policy gets one derived from its name, made unique within the product by appending a dash and 3 random lowercase letters or digits when needed. An explicit `slug` is used as is: the request fails with a `409` when it's taken.

With `isDefault: true`, the new policy replaces the product's current default policy.

A product always has a default policy, so when it has no policies the new one becomes the default: the request fails with a `409` when `isDefault` is `false`.

**Required role permission**: `policy:create` when called with a session, granted by the member's role. API keys aren't limited by roles.

### Example

* Api Key Authentication (apiKey):

```python
import licensemanager
from licensemanager.models.create_policy import CreatePolicy
from licensemanager.models.policy import Policy
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
    api_instance = licensemanager.PoliciesApi(api_client)
    product_id = 'x7Kp2QaZ' # str | 
    create_policy = licensemanager.CreatePolicy() # CreatePolicy | 

    try:
        # Create a policy
        api_response = api_instance.create_policy(product_id, create_policy)
        print("The response of PoliciesApi->create_policy:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling PoliciesApi->create_policy: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **product_id** | **str**|  | 
 **create_policy** | [**CreatePolicy**](CreatePolicy.md)|  | 

### Return type

[**Policy**](Policy.md)

### Authorization

[apiKey](../README.md#apiKey)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details

| Status code | Description | Response headers |
|-------------|-------------|------------------|
**201** | Created policy |  -  |
**401** | &#x60;unauthorized&#x60;: no credentials. &#x60;invalid_api_key&#x60;: the API key doesn&#39;t exist, was revoked or has expired. &#x60;invalid_token&#x60;: the token&#39;s signature is invalid, it has expired, or the resource it&#39;s scoped to was deleted |  -  |
**402** | &#x60;plan_limit_exceeded&#x60;: the organization stayed over its plan&#39;s limits after the grace period, its API is blocked until it upgrades. &#x60;plan_limit_reached&#x60;: creating the resource would go over the plan&#39;s limit |  -  |
**403** | &#x60;token_not_allowed&#x60;: the endpoint doesn&#39;t accept tokens, or not of this type. &#x60;insufficient_scope&#x60;: the token lacks the permission. &#x60;no_active_organization&#x60; or &#x60;forbidden&#x60;: the session has no organization, or isn&#39;t a member of the one requested |  -  |
**404** | Product not found |  -  |
**409** | &#x60;slug_taken&#x60;: the explicit slug is already used by another policy of the product, or a concurrent request took the same slug first. &#x60;default_required&#x60;: &#x60;isDefault: false&#x60; for the first policy of the product |  -  |
**422** | &#x60;validation_error&#x60;: invalid path, query or body, with the &#x60;issues&#x60; |  -  |
**429** | &#x60;rate_limited&#x60;: the API key made more than 10 requests in the last second. Wait for the &#x60;Retry-After&#x60; seconds |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

# **delete_policy**
> delete_policy(id)

Delete a policy

Deleting the default policy makes the oldest remaining policy of the product the default. The last policy of a product can't be deleted, nor a policy that licenses follow. Its events can no longer be listed.

**Required role permission**: `policy:delete` when called with a session, granted by the member's role. API keys aren't limited by roles.

### Example

* Api Key Authentication (apiKey):

```python
import licensemanager
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
    api_instance = licensemanager.PoliciesApi(api_client)
    id = 'p4Rt8LmQ' # str | 

    try:
        # Delete a policy
        api_instance.delete_policy(id)
    except Exception as e:
        print("Exception when calling PoliciesApi->delete_policy: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **id** | **str**|  | 

### Return type

void (empty response body)

### Authorization

[apiKey](../README.md#apiKey)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details

| Status code | Description | Response headers |
|-------------|-------------|------------------|
**204** | Deleted |  -  |
**401** | &#x60;unauthorized&#x60;: no credentials. &#x60;invalid_api_key&#x60;: the API key doesn&#39;t exist, was revoked or has expired. &#x60;invalid_token&#x60;: the token&#39;s signature is invalid, it has expired, or the resource it&#39;s scoped to was deleted |  -  |
**402** | &#x60;plan_limit_exceeded&#x60;: the organization stayed over its plan&#39;s limits after the grace period, its API is blocked until it upgrades. &#x60;plan_limit_reached&#x60;: creating the resource would go over the plan&#39;s limit |  -  |
**403** | &#x60;token_not_allowed&#x60;: the endpoint doesn&#39;t accept tokens, or not of this type. &#x60;insufficient_scope&#x60;: the token lacks the permission. &#x60;no_active_organization&#x60; or &#x60;forbidden&#x60;: the session has no organization, or isn&#39;t a member of the one requested |  -  |
**404** | Policy not found |  -  |
**409** | &#x60;last_policy&#x60;: the policy is the last one of its product. &#x60;policy_in_use&#x60;: licenses follow it |  -  |
**422** | &#x60;validation_error&#x60;: invalid path, query or body, with the &#x60;issues&#x60; |  -  |
**429** | &#x60;rate_limited&#x60;: the API key made more than 10 requests in the last second. Wait for the &#x60;Retry-After&#x60; seconds |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

# **get_policy**
> Policy get_policy(id)

Get a policy

### Example

* Api Key Authentication (apiKey):

```python
import licensemanager
from licensemanager.models.policy import Policy
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
    api_instance = licensemanager.PoliciesApi(api_client)
    id = 'p4Rt8LmQ' # str | 

    try:
        # Get a policy
        api_response = api_instance.get_policy(id)
        print("The response of PoliciesApi->get_policy:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling PoliciesApi->get_policy: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **id** | **str**|  | 

### Return type

[**Policy**](Policy.md)

### Authorization

[apiKey](../README.md#apiKey)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details

| Status code | Description | Response headers |
|-------------|-------------|------------------|
**200** | Policy |  -  |
**401** | &#x60;unauthorized&#x60;: no credentials. &#x60;invalid_api_key&#x60;: the API key doesn&#39;t exist, was revoked or has expired. &#x60;invalid_token&#x60;: the token&#39;s signature is invalid, it has expired, or the resource it&#39;s scoped to was deleted |  -  |
**402** | &#x60;plan_limit_exceeded&#x60;: the organization stayed over its plan&#39;s limits after the grace period, its API is blocked until it upgrades. &#x60;plan_limit_reached&#x60;: creating the resource would go over the plan&#39;s limit |  -  |
**403** | &#x60;token_not_allowed&#x60;: the endpoint doesn&#39;t accept tokens, or not of this type. &#x60;insufficient_scope&#x60;: the token lacks the permission. &#x60;no_active_organization&#x60; or &#x60;forbidden&#x60;: the session has no organization, or isn&#39;t a member of the one requested |  -  |
**404** | Policy not found |  -  |
**422** | &#x60;validation_error&#x60;: invalid path, query or body, with the &#x60;issues&#x60; |  -  |
**429** | &#x60;rate_limited&#x60;: the API key made more than 10 requests in the last second. Wait for the &#x60;Retry-After&#x60; seconds |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

# **list_policies**
> PolicyList list_policies(product_id, page=page, page_size=page_size, sort=sort, search=search, slug=slug, is_default=is_default, license_count=license_count, license_count_min=license_count_min, license_count_max=license_count_max)

List the policies of a product

`?isDefault=true` returns the product's default policy alone: a product always has exactly one. Sorting by `duration` counts months for their average length, about 30.4 days.

### Example

* Api Key Authentication (apiKey):

```python
import licensemanager
from licensemanager.models.policy_list import PolicyList
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
    api_instance = licensemanager.PoliciesApi(api_client)
    product_id = 'x7Kp2QaZ' # str | 
    page = 1 # int | Page to return. Pages are numbered from 1: `1` is the first page. A page past the last one returns an empty `data`, not an error. Defaults to `1`. (optional) (default to 1)
    page_size = 20 # int | Maximum number of items per page, from 1 to 100. Every page holds this many items except the last one, which can hold fewer. Defaults to `20`. (optional) (default to 20)
    sort = 'name' # str | Field to sort by, prefixed with `-` for descending order. Defaults to `name`. (optional) (default to 'name')
    search = 'pro' # str | Case-insensitive text the name or slug contains. (optional)
    slug = 'yearly' # str | Only returns the policy with this exact slug. (optional)
    is_default = 'true' # str | `true` only returns the product's default policy, `false` only the other ones. (optional)
    license_count = 1 # int | Only returns the policies followed by exactly this number of licenses. (optional)
    license_count_min = 1 # int | Only returns the policies followed by at least this number of licenses. (optional)
    license_count_max = 1 # int | Only returns the policies followed by at most this number of licenses. (optional)

    try:
        # List the policies of a product
        api_response = api_instance.list_policies(product_id, page=page, page_size=page_size, sort=sort, search=search, slug=slug, is_default=is_default, license_count=license_count, license_count_min=license_count_min, license_count_max=license_count_max)
        print("The response of PoliciesApi->list_policies:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling PoliciesApi->list_policies: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **product_id** | **str**|  | 
 **page** | **int**| Page to return. Pages are numbered from 1: &#x60;1&#x60; is the first page. A page past the last one returns an empty &#x60;data&#x60;, not an error. Defaults to &#x60;1&#x60;. | [optional] [default to 1]
 **page_size** | **int**| Maximum number of items per page, from 1 to 100. Every page holds this many items except the last one, which can hold fewer. Defaults to &#x60;20&#x60;. | [optional] [default to 20]
 **sort** | **str**| Field to sort by, prefixed with &#x60;-&#x60; for descending order. Defaults to &#x60;name&#x60;. | [optional] [default to &#39;name&#39;]
 **search** | **str**| Case-insensitive text the name or slug contains. | [optional] 
 **slug** | **str**| Only returns the policy with this exact slug. | [optional] 
 **is_default** | **str**| &#x60;true&#x60; only returns the product&#39;s default policy, &#x60;false&#x60; only the other ones. | [optional] 
 **license_count** | **int**| Only returns the policies followed by exactly this number of licenses. | [optional] 
 **license_count_min** | **int**| Only returns the policies followed by at least this number of licenses. | [optional] 
 **license_count_max** | **int**| Only returns the policies followed by at most this number of licenses. | [optional] 

### Return type

[**PolicyList**](PolicyList.md)

### Authorization

[apiKey](../README.md#apiKey)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details

| Status code | Description | Response headers |
|-------------|-------------|------------------|
**200** | One page of the policies of the product |  -  |
**401** | &#x60;unauthorized&#x60;: no credentials. &#x60;invalid_api_key&#x60;: the API key doesn&#39;t exist, was revoked or has expired. &#x60;invalid_token&#x60;: the token&#39;s signature is invalid, it has expired, or the resource it&#39;s scoped to was deleted |  -  |
**402** | &#x60;plan_limit_exceeded&#x60;: the organization stayed over its plan&#39;s limits after the grace period, its API is blocked until it upgrades. &#x60;plan_limit_reached&#x60;: creating the resource would go over the plan&#39;s limit |  -  |
**403** | &#x60;token_not_allowed&#x60;: the endpoint doesn&#39;t accept tokens, or not of this type. &#x60;insufficient_scope&#x60;: the token lacks the permission. &#x60;no_active_organization&#x60; or &#x60;forbidden&#x60;: the session has no organization, or isn&#39;t a member of the one requested |  -  |
**404** | Product not found |  -  |
**422** | &#x60;validation_error&#x60;: invalid path, query or body, with the &#x60;issues&#x60; |  -  |
**429** | &#x60;rate_limited&#x60;: the API key made more than 10 requests in the last second. Wait for the &#x60;Retry-After&#x60; seconds |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

# **update_policy**
> Policy update_policy(id, update_policy)

Update a policy

`isDefault: true` makes the policy the product's default, in place of the current one. A product always has a default policy, so the default can't be unset with `isDefault: false`: make another policy the default instead.

Licenses copy the settings of their policy when they're created, so changing them only affects the licenses created afterwards: update the existing licenses to change theirs.

**Required role permission**: `policy:update` when called with a session, granted by the member's role. API keys aren't limited by roles.

### Example

* Api Key Authentication (apiKey):

```python
import licensemanager
from licensemanager.models.policy import Policy
from licensemanager.models.update_policy import UpdatePolicy
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
    api_instance = licensemanager.PoliciesApi(api_client)
    id = 'p4Rt8LmQ' # str | 
    update_policy = licensemanager.UpdatePolicy() # UpdatePolicy | 

    try:
        # Update a policy
        api_response = api_instance.update_policy(id, update_policy)
        print("The response of PoliciesApi->update_policy:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling PoliciesApi->update_policy: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **id** | **str**|  | 
 **update_policy** | [**UpdatePolicy**](UpdatePolicy.md)|  | 

### Return type

[**Policy**](Policy.md)

### Authorization

[apiKey](../README.md#apiKey)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details

| Status code | Description | Response headers |
|-------------|-------------|------------------|
**200** | Updated policy |  -  |
**401** | &#x60;unauthorized&#x60;: no credentials. &#x60;invalid_api_key&#x60;: the API key doesn&#39;t exist, was revoked or has expired. &#x60;invalid_token&#x60;: the token&#39;s signature is invalid, it has expired, or the resource it&#39;s scoped to was deleted |  -  |
**402** | &#x60;plan_limit_exceeded&#x60;: the organization stayed over its plan&#39;s limits after the grace period, its API is blocked until it upgrades. &#x60;plan_limit_reached&#x60;: creating the resource would go over the plan&#39;s limit |  -  |
**403** | &#x60;token_not_allowed&#x60;: the endpoint doesn&#39;t accept tokens, or not of this type. &#x60;insufficient_scope&#x60;: the token lacks the permission. &#x60;no_active_organization&#x60; or &#x60;forbidden&#x60;: the session has no organization, or isn&#39;t a member of the one requested |  -  |
**404** | Policy not found |  -  |
**409** | &#x60;slug_taken&#x60;: slug already used by another policy of the product. &#x60;default_required&#x60;: &#x60;isDefault: false&#x60; on the default policy |  -  |
**422** | &#x60;validation_error&#x60;: invalid path, query or body, with the &#x60;issues&#x60; |  -  |
**429** | &#x60;rate_limited&#x60;: the API key made more than 10 requests in the last second. Wait for the &#x60;Retry-After&#x60; seconds |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

