# licensemanager.ProductsApi

All URIs are relative to *https://api.licensemanager.dev*

Method | HTTP request | Description
------------- | ------------- | -------------
[**create_product**](ProductsApi.md#create_product) | **POST** /v1/products | Create a product
[**delete_product**](ProductsApi.md#delete_product) | **DELETE** /v1/products/{id} | Delete a product
[**delete_product_logo**](ProductsApi.md#delete_product_logo) | **DELETE** /v1/products/{id}/logo | Delete a product logo
[**get_product**](ProductsApi.md#get_product) | **GET** /v1/products/{id} | Get a product
[**get_product_stats**](ProductsApi.md#get_product_stats) | **GET** /v1/products/{id}/stats | Get the stats of a product
[**list_products**](ProductsApi.md#list_products) | **GET** /v1/products | List products
[**reset_product**](ProductsApi.md#reset_product) | **POST** /v1/products/{id}/reset | Reset a test product
[**update_product**](ProductsApi.md#update_product) | **PATCH** /v1/products/{id} | Update a product
[**upload_product_logo**](ProductsApi.md#upload_product_logo) | **PUT** /v1/products/{id}/logo | Upload a product logo


# **create_product**
> Product create_product(create_product_with_policy)

Create a product

Without a `slug`, the product gets one derived from its name: lower cased, without accents and special characters (`Élan Pro 2!` becomes `elan-pro-2`).
When another product of the organization already uses it, a dash and 3 random lowercase letters or digits are appended (`elan-pro-2-k3f`), until the slug is free.

An explicit `slug` is used as is: the request fails with a `409` when it's taken, it's never changed.

Slug uniqueness is enforced by the database, so when concurrent requests end up with the same slug, only one succeeds and the others get a `409`, even without an explicit `slug`. Retrying such a request without a `slug` derives a new one.

The product is created with its default policy, named `Default policy` with the `default` slug, whose settings are given by `defaultPolicy`. Omitted settings default to licenses that never expire, on a single machine, offline for one week, for every version of the product. Unlike `createPolicy`, where `maxMachines` defaults to no limit.

With `isTestFromProductId`, the product is a test product: its id, its slug, and the ids, slugs and license keys of its resources start with `test_` (`TEST-` for license keys), and only test API keys reach it. It starts with copies of the policies, releases, portal settings and `autoMachineChange` of the live product, `defaultPolicy` is ignored. Later changes to the live product aren't copied: reset the test product to copy them again. Test API keys can only create test products, live API keys only live ones.

**Required role permission**: `product:create` when called with a session, granted by the member's role. API keys aren't limited by roles.

### Example

* Api Key Authentication (apiKey):

```python
import licensemanager
from licensemanager.models.create_product_with_policy import CreateProductWithPolicy
from licensemanager.models.product import Product
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
    api_instance = licensemanager.ProductsApi(api_client)
    create_product_with_policy = licensemanager.CreateProductWithPolicy() # CreateProductWithPolicy | 

    try:
        # Create a product
        api_response = api_instance.create_product(create_product_with_policy)
        print("The response of ProductsApi->create_product:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling ProductsApi->create_product: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **create_product_with_policy** | [**CreateProductWithPolicy**](CreateProductWithPolicy.md)|  | 

### Return type

[**Product**](Product.md)

### Authorization

[apiKey](../README.md#apiKey)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details

| Status code | Description | Response headers |
|-------------|-------------|------------------|
**201** | Created product |  -  |
**401** | &#x60;unauthorized&#x60;: no credentials. &#x60;invalid_api_key&#x60;: the API key doesn&#39;t exist, was revoked or has expired. &#x60;invalid_token&#x60;: the token&#39;s signature is invalid, it has expired, or the resource it&#39;s scoped to was deleted |  -  |
**402** | &#x60;plan_limit_exceeded&#x60;: the organization stayed over its plan&#39;s limits after the grace period, its API is blocked until it upgrades. &#x60;plan_limit_reached&#x60;: creating the resource would go over the plan&#39;s limit |  -  |
**403** | &#x60;api_key_mode&#x60;: the API key&#39;s mode doesn&#39;t match the product&#39;s: test keys only create test products, live keys only live ones |  -  |
**404** | &#x60;not_found&#x60;: &#x60;isTestFromProductId&#x60; isn&#39;t a live product of the organization |  -  |
**409** | &#x60;slug_taken&#x60;: the explicit slug is already used by another product of the organization, or a concurrent request took the same slug first |  -  |
**422** | &#x60;validation_error&#x60;: invalid path, query or body, with the &#x60;issues&#x60; |  -  |
**429** | &#x60;rate_limited&#x60;: the API key made more than 10 requests in the last second. Wait for the &#x60;Retry-After&#x60; seconds |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

# **delete_product**
> delete_product(id)

Delete a product

Deletes the product along with its policies, customers and releases, and its test products with everything they hold. A live product that licenses belong to can't be deleted: delete them first. A test product can always be deleted, along with its licenses and machines. The events of the deleted policies and licenses can no longer be listed.

**Required role permission**: `product:delete` when called with a session, granted by the member's role. API keys aren't limited by roles.

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
    api_instance = licensemanager.ProductsApi(api_client)
    id = 'x7Kp2QaZ' # str | 

    try:
        # Delete a product
        api_instance.delete_product(id)
    except Exception as e:
        print("Exception when calling ProductsApi->delete_product: %s\n" % e)
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
**404** | Product not found |  -  |
**409** | &#x60;product_in_use&#x60;: licenses belong to the live product |  -  |
**422** | &#x60;validation_error&#x60;: invalid path, query or body, with the &#x60;issues&#x60; |  -  |
**429** | &#x60;rate_limited&#x60;: the API key made more than 10 requests in the last second. Wait for the &#x60;Retry-After&#x60; seconds |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

# **delete_product_logo**
> Product delete_product_logo(id)

Delete a product logo

Removes the logo of the product, and deletes its image. Succeeds when the product has no logo.

**Required role permission**: `product:update` when called with a session, granted by the member's role. API keys aren't limited by roles.

### Example

* Api Key Authentication (apiKey):

```python
import licensemanager
from licensemanager.models.product import Product
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
    api_instance = licensemanager.ProductsApi(api_client)
    id = 'x7Kp2QaZ' # str | 

    try:
        # Delete a product logo
        api_response = api_instance.delete_product_logo(id)
        print("The response of ProductsApi->delete_product_logo:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling ProductsApi->delete_product_logo: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **id** | **str**|  | 

### Return type

[**Product**](Product.md)

### Authorization

[apiKey](../README.md#apiKey)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details

| Status code | Description | Response headers |
|-------------|-------------|------------------|
**200** | Product without a logo |  -  |
**401** | &#x60;unauthorized&#x60;: no credentials. &#x60;invalid_api_key&#x60;: the API key doesn&#39;t exist, was revoked or has expired. &#x60;invalid_token&#x60;: the token&#39;s signature is invalid, it has expired, or the resource it&#39;s scoped to was deleted |  -  |
**402** | &#x60;plan_limit_exceeded&#x60;: the organization stayed over its plan&#39;s limits after the grace period, its API is blocked until it upgrades. &#x60;plan_limit_reached&#x60;: creating the resource would go over the plan&#39;s limit |  -  |
**403** | &#x60;token_not_allowed&#x60;: the endpoint doesn&#39;t accept tokens, or not of this type. &#x60;insufficient_scope&#x60;: the token lacks the permission. &#x60;no_active_organization&#x60; or &#x60;forbidden&#x60;: the session has no organization, or isn&#39;t a member of the one requested |  -  |
**404** | Product not found |  -  |
**422** | &#x60;validation_error&#x60;: invalid path, query or body, with the &#x60;issues&#x60; |  -  |
**429** | &#x60;rate_limited&#x60;: the API key made more than 10 requests in the last second. Wait for the &#x60;Retry-After&#x60; seconds |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

# **get_product**
> Product get_product(id)

Get a product

### Example

* Api Key Authentication (apiKey):

```python
import licensemanager
from licensemanager.models.product import Product
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
    api_instance = licensemanager.ProductsApi(api_client)
    id = 'x7Kp2QaZ' # str | 

    try:
        # Get a product
        api_response = api_instance.get_product(id)
        print("The response of ProductsApi->get_product:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling ProductsApi->get_product: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **id** | **str**|  | 

### Return type

[**Product**](Product.md)

### Authorization

[apiKey](../README.md#apiKey)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details

| Status code | Description | Response headers |
|-------------|-------------|------------------|
**200** | Product |  -  |
**401** | &#x60;unauthorized&#x60;: no credentials. &#x60;invalid_api_key&#x60;: the API key doesn&#39;t exist, was revoked or has expired. &#x60;invalid_token&#x60;: the token&#39;s signature is invalid, it has expired, or the resource it&#39;s scoped to was deleted |  -  |
**402** | &#x60;plan_limit_exceeded&#x60;: the organization stayed over its plan&#39;s limits after the grace period, its API is blocked until it upgrades. &#x60;plan_limit_reached&#x60;: creating the resource would go over the plan&#39;s limit |  -  |
**403** | &#x60;token_not_allowed&#x60;: the endpoint doesn&#39;t accept tokens, or not of this type. &#x60;insufficient_scope&#x60;: the token lacks the permission. &#x60;no_active_organization&#x60; or &#x60;forbidden&#x60;: the session has no organization, or isn&#39;t a member of the one requested |  -  |
**404** | Product not found |  -  |
**422** | &#x60;validation_error&#x60;: invalid path, query or body, with the &#x60;issues&#x60; |  -  |
**429** | &#x60;rate_limited&#x60;: the API key made more than 10 requests in the last second. Wait for the &#x60;Retry-After&#x60; seconds |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

# **get_product_stats**
> ProductStats get_product_stats(id)

Get the stats of a product

Counts of the licenses and machines of the product, number of licenses created each day over the last 30 days and each month over the last 12 months, overall and per policy, revenue per currency over the same periods, and successful activations each day over the last 30 days. Days and months are in UTC.

### Example

* Api Key Authentication (apiKey):

```python
import licensemanager
from licensemanager.models.product_stats import ProductStats
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
    api_instance = licensemanager.ProductsApi(api_client)
    id = 'x7Kp2QaZ' # str | 

    try:
        # Get the stats of a product
        api_response = api_instance.get_product_stats(id)
        print("The response of ProductsApi->get_product_stats:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling ProductsApi->get_product_stats: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **id** | **str**|  | 

### Return type

[**ProductStats**](ProductStats.md)

### Authorization

[apiKey](../README.md#apiKey)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details

| Status code | Description | Response headers |
|-------------|-------------|------------------|
**200** | Stats of the product |  -  |
**401** | &#x60;unauthorized&#x60;: no credentials. &#x60;invalid_api_key&#x60;: the API key doesn&#39;t exist, was revoked or has expired. &#x60;invalid_token&#x60;: the token&#39;s signature is invalid, it has expired, or the resource it&#39;s scoped to was deleted |  -  |
**402** | &#x60;plan_limit_exceeded&#x60;: the organization stayed over its plan&#39;s limits after the grace period, its API is blocked until it upgrades. &#x60;plan_limit_reached&#x60;: creating the resource would go over the plan&#39;s limit |  -  |
**403** | &#x60;token_not_allowed&#x60;: the endpoint doesn&#39;t accept tokens, or not of this type. &#x60;insufficient_scope&#x60;: the token lacks the permission. &#x60;no_active_organization&#x60; or &#x60;forbidden&#x60;: the session has no organization, or isn&#39;t a member of the one requested |  -  |
**404** | Product not found |  -  |
**422** | &#x60;validation_error&#x60;: invalid path, query or body, with the &#x60;issues&#x60; |  -  |
**429** | &#x60;rate_limited&#x60;: the API key made more than 10 requests in the last second. Wait for the &#x60;Retry-After&#x60; seconds |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

# **list_products**
> ProductList list_products(page=page, page_size=page_size, sort=sort, search=search, slug=slug, is_test=is_test)

List products

### Example

* Api Key Authentication (apiKey):

```python
import licensemanager
from licensemanager.models.product_list import ProductList
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
    api_instance = licensemanager.ProductsApi(api_client)
    page = 1 # int | Page to return. Pages are numbered from 1: `1` is the first page. A page past the last one returns an empty `data`, not an error. Defaults to `1`. (optional) (default to 1)
    page_size = 20 # int | Maximum number of items per page, from 1 to 100. Every page holds this many items except the last one, which can hold fewer. Defaults to `20`. (optional) (default to 20)
    sort = '-createdAt' # str | Field to sort by, prefixed with `-` for descending order. Defaults to `-createdAt`. (optional) (default to '-createdAt')
    search = 'pro' # str | Case-insensitive text the name or slug contains. (optional)
    slug = 'acme-pro' # str | Only returns the product with this exact slug. (optional)
    is_test = 'false' # str | Only returns the test products with `true`, the live ones with `false`. API keys only list the products of their own mode. (optional)

    try:
        # List products
        api_response = api_instance.list_products(page=page, page_size=page_size, sort=sort, search=search, slug=slug, is_test=is_test)
        print("The response of ProductsApi->list_products:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling ProductsApi->list_products: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **page** | **int**| Page to return. Pages are numbered from 1: &#x60;1&#x60; is the first page. A page past the last one returns an empty &#x60;data&#x60;, not an error. Defaults to &#x60;1&#x60;. | [optional] [default to 1]
 **page_size** | **int**| Maximum number of items per page, from 1 to 100. Every page holds this many items except the last one, which can hold fewer. Defaults to &#x60;20&#x60;. | [optional] [default to 20]
 **sort** | **str**| Field to sort by, prefixed with &#x60;-&#x60; for descending order. Defaults to &#x60;-createdAt&#x60;. | [optional] [default to &#39;-createdAt&#39;]
 **search** | **str**| Case-insensitive text the name or slug contains. | [optional] 
 **slug** | **str**| Only returns the product with this exact slug. | [optional] 
 **is_test** | **str**| Only returns the test products with &#x60;true&#x60;, the live ones with &#x60;false&#x60;. API keys only list the products of their own mode. | [optional] 

### Return type

[**ProductList**](ProductList.md)

### Authorization

[apiKey](../README.md#apiKey)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details

| Status code | Description | Response headers |
|-------------|-------------|------------------|
**200** | One page of the products of the organization |  -  |
**401** | &#x60;unauthorized&#x60;: no credentials. &#x60;invalid_api_key&#x60;: the API key doesn&#39;t exist, was revoked or has expired. &#x60;invalid_token&#x60;: the token&#39;s signature is invalid, it has expired, or the resource it&#39;s scoped to was deleted |  -  |
**402** | &#x60;plan_limit_exceeded&#x60;: the organization stayed over its plan&#39;s limits after the grace period, its API is blocked until it upgrades. &#x60;plan_limit_reached&#x60;: creating the resource would go over the plan&#39;s limit |  -  |
**403** | &#x60;token_not_allowed&#x60;: the endpoint doesn&#39;t accept tokens, or not of this type. &#x60;insufficient_scope&#x60;: the token lacks the permission. &#x60;no_active_organization&#x60; or &#x60;forbidden&#x60;: the session has no organization, or isn&#39;t a member of the one requested |  -  |
**422** | &#x60;validation_error&#x60;: invalid path, query or body, with the &#x60;issues&#x60; |  -  |
**429** | &#x60;rate_limited&#x60;: the API key made more than 10 requests in the last second. Wait for the &#x60;Retry-After&#x60; seconds |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

# **reset_product**
> Product reset_product(id)

Reset a test product

Deletes the customers, licenses, machines, policies and releases of the test product, with their events, then copies the policies, releases, portal settings and `autoMachineChange` of its live product again. Its id, name and slug are kept, but the copied policies get new ids. The tokens of its customers, licenses and machines stop working.

**Required role permission**: `product:update` when called with a session, granted by the member's role. API keys aren't limited by roles.

### Example

* Api Key Authentication (apiKey):

```python
import licensemanager
from licensemanager.models.product import Product
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
    api_instance = licensemanager.ProductsApi(api_client)
    id = 'x7Kp2QaZ' # str | 

    try:
        # Reset a test product
        api_response = api_instance.reset_product(id)
        print("The response of ProductsApi->reset_product:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling ProductsApi->reset_product: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **id** | **str**|  | 

### Return type

[**Product**](Product.md)

### Authorization

[apiKey](../README.md#apiKey)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details

| Status code | Description | Response headers |
|-------------|-------------|------------------|
**200** | Reset product |  -  |
**400** | &#x60;not_test_product&#x60;: the product is a live product |  -  |
**401** | &#x60;unauthorized&#x60;: no credentials. &#x60;invalid_api_key&#x60;: the API key doesn&#39;t exist, was revoked or has expired. &#x60;invalid_token&#x60;: the token&#39;s signature is invalid, it has expired, or the resource it&#39;s scoped to was deleted |  -  |
**402** | &#x60;plan_limit_exceeded&#x60;: the organization stayed over its plan&#39;s limits after the grace period, its API is blocked until it upgrades. &#x60;plan_limit_reached&#x60;: creating the resource would go over the plan&#39;s limit |  -  |
**403** | &#x60;token_not_allowed&#x60;: the endpoint doesn&#39;t accept tokens, or not of this type. &#x60;insufficient_scope&#x60;: the token lacks the permission. &#x60;no_active_organization&#x60; or &#x60;forbidden&#x60;: the session has no organization, or isn&#39;t a member of the one requested |  -  |
**404** | Product not found |  -  |
**422** | &#x60;validation_error&#x60;: invalid path, query or body, with the &#x60;issues&#x60; |  -  |
**429** | &#x60;rate_limited&#x60;: the API key made more than 10 requests in the last second. Wait for the &#x60;Retry-After&#x60; seconds |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

# **update_product**
> Product update_product(id, update_product)

Update a product

A product can't be turned into a test product, or back: `isTestFromProductId` can't be changed.

**Required role permission**: `product:update` when called with a session, granted by the member's role. API keys aren't limited by roles.

### Example

* Api Key Authentication (apiKey):

```python
import licensemanager
from licensemanager.models.product import Product
from licensemanager.models.update_product import UpdateProduct
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
    api_instance = licensemanager.ProductsApi(api_client)
    id = 'x7Kp2QaZ' # str | 
    update_product = licensemanager.UpdateProduct() # UpdateProduct | 

    try:
        # Update a product
        api_response = api_instance.update_product(id, update_product)
        print("The response of ProductsApi->update_product:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling ProductsApi->update_product: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **id** | **str**|  | 
 **update_product** | [**UpdateProduct**](UpdateProduct.md)|  | 

### Return type

[**Product**](Product.md)

### Authorization

[apiKey](../README.md#apiKey)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details

| Status code | Description | Response headers |
|-------------|-------------|------------------|
**200** | Updated product |  -  |
**401** | &#x60;unauthorized&#x60;: no credentials. &#x60;invalid_api_key&#x60;: the API key doesn&#39;t exist, was revoked or has expired. &#x60;invalid_token&#x60;: the token&#39;s signature is invalid, it has expired, or the resource it&#39;s scoped to was deleted |  -  |
**402** | &#x60;plan_limit_exceeded&#x60;: the organization stayed over its plan&#39;s limits after the grace period, its API is blocked until it upgrades. &#x60;plan_limit_reached&#x60;: creating the resource would go over the plan&#39;s limit |  -  |
**403** | &#x60;token_not_allowed&#x60;: the endpoint doesn&#39;t accept tokens, or not of this type. &#x60;insufficient_scope&#x60;: the token lacks the permission. &#x60;no_active_organization&#x60; or &#x60;forbidden&#x60;: the session has no organization, or isn&#39;t a member of the one requested |  -  |
**404** | Product not found |  -  |
**409** | &#x60;slug_taken&#x60;: slug already used by another product of the organization |  -  |
**422** | &#x60;validation_error&#x60;: invalid path, query or body, with the &#x60;issues&#x60; |  -  |
**429** | &#x60;rate_limited&#x60;: the API key made more than 10 requests in the last second. Wait for the &#x60;Retry-After&#x60; seconds |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

# **upload_product_logo**
> Product upload_product_logo(id, file)

Upload a product logo

Replaces the logo of the product, shown in the web app and the customer portal. The previous logo is deleted.

Accepts WebP, PNG, JPEG and SVG images up to 1 MB, recognized by their content. Logos are shown in squares: use square images, 256×256 pixels for bitmaps. The web app crops and resizes images to this size, and converts them to WebP, before uploading them.

**Required role permission**: `product:update` when called with a session, granted by the member's role. API keys aren't limited by roles.

### Example

* Api Key Authentication (apiKey):

```python
import licensemanager
from licensemanager.models.product import Product
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
    api_instance = licensemanager.ProductsApi(api_client)
    id = 'x7Kp2QaZ' # str | 
    file = None # bytes | WebP, PNG, JPEG or SVG image, up to 1 MB.

    try:
        # Upload a product logo
        api_response = api_instance.upload_product_logo(id, file)
        print("The response of ProductsApi->upload_product_logo:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling ProductsApi->upload_product_logo: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **id** | **str**|  | 
 **file** | **bytes**| WebP, PNG, JPEG or SVG image, up to 1 MB. | 

### Return type

[**Product**](Product.md)

### Authorization

[apiKey](../README.md#apiKey)

### HTTP request headers

 - **Content-Type**: multipart/form-data
 - **Accept**: application/json

### HTTP response details

| Status code | Description | Response headers |
|-------------|-------------|------------------|
**200** | Product with its new logo |  -  |
**401** | &#x60;unauthorized&#x60;: no credentials. &#x60;invalid_api_key&#x60;: the API key doesn&#39;t exist, was revoked or has expired. &#x60;invalid_token&#x60;: the token&#39;s signature is invalid, it has expired, or the resource it&#39;s scoped to was deleted |  -  |
**402** | &#x60;plan_limit_exceeded&#x60;: the organization stayed over its plan&#39;s limits after the grace period, its API is blocked until it upgrades. &#x60;plan_limit_reached&#x60;: creating the resource would go over the plan&#39;s limit |  -  |
**403** | &#x60;token_not_allowed&#x60;: the endpoint doesn&#39;t accept tokens, or not of this type. &#x60;insufficient_scope&#x60;: the token lacks the permission. &#x60;no_active_organization&#x60; or &#x60;forbidden&#x60;: the session has no organization, or isn&#39;t a member of the one requested |  -  |
**404** | Product not found |  -  |
**413** | &#x60;logo_too_large&#x60;: the image is larger than 1 MB |  -  |
**415** | &#x60;unsupported_logo_type&#x60;: the file isn&#39;t a WebP, PNG, JPEG or SVG image |  -  |
**422** | &#x60;validation_error&#x60;: invalid path, query or body, with the &#x60;issues&#x60; |  -  |
**429** | &#x60;rate_limited&#x60;: the API key made more than 10 requests in the last second. Wait for the &#x60;Retry-After&#x60; seconds |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

