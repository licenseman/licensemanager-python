# licensemanager.IntegrationsApi

All URIs are relative to *https://api.licensemanager.dev*

Method | HTTP request | Description
------------- | ------------- | -------------
[**check_integration**](IntegrationsApi.md#check_integration) | **POST** /v1/integrations/{id}/check | Check an integration
[**connect_stripe**](IntegrationsApi.md#connect_stripe) | **PUT** /v1/products/{productId}/integrations/stripe | Connect Stripe
[**create_stripe_mapping**](IntegrationsApi.md#create_stripe_mapping) | **POST** /v1/products/{productId}/integrations/stripe/mappings | Map a Stripe price to a policy
[**delete_stripe_mapping**](IntegrationsApi.md#delete_stripe_mapping) | **DELETE** /v1/integration-mappings/{id} | Delete a mapping
[**disconnect_integration**](IntegrationsApi.md#disconnect_integration) | **DELETE** /v1/integrations/{id} | Disconnect an integration
[**get_stripe_integration**](IntegrationsApi.md#get_stripe_integration) | **GET** /v1/products/{productId}/integrations/stripe | Get the Stripe integration of a product
[**list_stripe_prices**](IntegrationsApi.md#list_stripe_prices) | **GET** /v1/integrations/{id}/stripe/prices | List the Stripe prices of an integration
[**update_stripe_mapping**](IntegrationsApi.md#update_stripe_mapping) | **PATCH** /v1/integration-mappings/{id} | Change the policy of a mapping


# **check_integration**
> Integration check_integration(id)

Check an integration

Checks right away, as done every day, that the API key still works and can manage the webhook endpoint, which is pointed at the server's webhook URL again (or created again when it was deleted). Updates the status. Doesn't accept tokens: only API keys and sessions.

**Required role permission**: `integration:update` when called with a session, granted by the member's role. API keys aren't limited by roles.

### Example

* Api Key Authentication (apiKey):

```python
import licensemanager
from licensemanager.models.integration import Integration
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
    api_instance = licensemanager.IntegrationsApi(api_client)
    id = 'i8Fz4QnRt' # str | 

    try:
        # Check an integration
        api_response = api_instance.check_integration(id)
        print("The response of IntegrationsApi->check_integration:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling IntegrationsApi->check_integration: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **id** | **str**|  | 

### Return type

[**Integration**](Integration.md)

### Authorization

[apiKey](../README.md#apiKey)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details

| Status code | Description | Response headers |
|-------------|-------------|------------------|
**200** | Checked integration |  -  |
**401** | &#x60;unauthorized&#x60;: no credentials. &#x60;invalid_api_key&#x60;: the API key doesn&#39;t exist, was revoked or has expired. &#x60;invalid_token&#x60;: the token&#39;s signature is invalid, it has expired, or the resource it&#39;s scoped to was deleted |  -  |
**402** | &#x60;plan_limit_exceeded&#x60;: the organization stayed over its plan&#39;s limits after the grace period, its API is blocked until it upgrades. &#x60;plan_limit_reached&#x60;: creating the resource would go over the plan&#39;s limit |  -  |
**403** | &#x60;token_not_allowed&#x60;: the endpoint doesn&#39;t accept tokens, or not of this type. &#x60;insufficient_scope&#x60;: the token lacks the permission. &#x60;no_active_organization&#x60; or &#x60;forbidden&#x60;: the session has no organization, or isn&#39;t a member of the one requested |  -  |
**404** | Integration not found |  -  |
**409** | &#x60;webhook_url_unreachable&#x60;: Stripe can&#39;t reach the server&#39;s webhook URL |  -  |
**422** | &#x60;validation_error&#x60;: invalid path, query or body, with the &#x60;issues&#x60; |  -  |
**429** | &#x60;rate_limited&#x60;: the API key made more than 10 requests in the last second. Wait for the &#x60;Retry-After&#x60; seconds |  -  |
**502** | &#x60;provider_unavailable&#x60;: Stripe couldn&#39;t be reached |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

# **connect_stripe**
> StripeIntegration connect_stripe(product_id, connect_stripe)

Connect Stripe

Connects the Stripe account of the API key for the organization's products of the product's mode, or replaces the key of the existing connection. Checks the key works and has the required permissions, then creates a webhook endpoint on the account, telling the app about payments. Doesn't accept tokens: only API keys and sessions.

**Required role permission**: `integration:create` when called with a session, granted by the member's role. API keys aren't limited by roles.

### Example

* Api Key Authentication (apiKey):

```python
import licensemanager
from licensemanager.models.connect_stripe import ConnectStripe
from licensemanager.models.stripe_integration import StripeIntegration
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
    api_instance = licensemanager.IntegrationsApi(api_client)
    product_id = 'x7Kp2QaZ' # str | 
    connect_stripe = licensemanager.ConnectStripe() # ConnectStripe | 

    try:
        # Connect Stripe
        api_response = api_instance.connect_stripe(product_id, connect_stripe)
        print("The response of IntegrationsApi->connect_stripe:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling IntegrationsApi->connect_stripe: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **product_id** | **str**|  | 
 **connect_stripe** | [**ConnectStripe**](ConnectStripe.md)|  | 

### Return type

[**StripeIntegration**](StripeIntegration.md)

### Authorization

[apiKey](../README.md#apiKey)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details

| Status code | Description | Response headers |
|-------------|-------------|------------------|
**200** | Stripe integration |  -  |
**401** | &#x60;unauthorized&#x60;: no credentials. &#x60;invalid_api_key&#x60;: the API key doesn&#39;t exist, was revoked or has expired. &#x60;invalid_token&#x60;: the token&#39;s signature is invalid, it has expired, or the resource it&#39;s scoped to was deleted |  -  |
**402** | &#x60;plan_limit_exceeded&#x60;: the organization stayed over its plan&#39;s limits after the grace period, its API is blocked until it upgrades. &#x60;plan_limit_reached&#x60;: creating the resource would go over the plan&#39;s limit |  -  |
**403** | &#x60;token_not_allowed&#x60;: the endpoint doesn&#39;t accept tokens, or not of this type. &#x60;insufficient_scope&#x60;: the token lacks the permission. &#x60;no_active_organization&#x60; or &#x60;forbidden&#x60;: the session has no organization, or isn&#39;t a member of the one requested |  -  |
**404** | Product not found |  -  |
**409** | &#x60;webhook_url_unreachable&#x60;: Stripe can&#39;t reach the server&#39;s webhook URL |  -  |
**422** | &#x60;validation_error&#x60;: invalid body. &#x60;invalid_api_key&#x60;: not a Stripe secret or restricted key, or Stripe rejected it. &#x60;key_mode_mismatch&#x60;: a test mode key for a live product, or the opposite. &#x60;missing_permission&#x60;: the key lacks required permissions, listed in the message |  -  |
**429** | &#x60;rate_limited&#x60;: the API key made more than 10 requests in the last second. Wait for the &#x60;Retry-After&#x60; seconds |  -  |
**502** | &#x60;provider_unavailable&#x60;: Stripe couldn&#39;t be reached |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

# **create_stripe_mapping**
> IntegrationMapping create_stripe_mapping(product_id, create_integration_mapping)

Map a Stripe price to a policy

Paying the price then creates licenses of the product with the policy: one per unit bought. Doesn't accept tokens: only API keys and sessions.

**Required role permission**: `integration:update` when called with a session, granted by the member's role. API keys aren't limited by roles.

### Example

* Api Key Authentication (apiKey):

```python
import licensemanager
from licensemanager.models.create_integration_mapping import CreateIntegrationMapping
from licensemanager.models.integration_mapping import IntegrationMapping
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
    api_instance = licensemanager.IntegrationsApi(api_client)
    product_id = 'x7Kp2QaZ' # str | 
    create_integration_mapping = licensemanager.CreateIntegrationMapping() # CreateIntegrationMapping | 

    try:
        # Map a Stripe price to a policy
        api_response = api_instance.create_stripe_mapping(product_id, create_integration_mapping)
        print("The response of IntegrationsApi->create_stripe_mapping:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling IntegrationsApi->create_stripe_mapping: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **product_id** | **str**|  | 
 **create_integration_mapping** | [**CreateIntegrationMapping**](CreateIntegrationMapping.md)|  | 

### Return type

[**IntegrationMapping**](IntegrationMapping.md)

### Authorization

[apiKey](../README.md#apiKey)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details

| Status code | Description | Response headers |
|-------------|-------------|------------------|
**201** | Created mapping |  -  |
**401** | &#x60;unauthorized&#x60;: no credentials. &#x60;invalid_api_key&#x60;: the API key doesn&#39;t exist, was revoked or has expired. &#x60;invalid_token&#x60;: the token&#39;s signature is invalid, it has expired, or the resource it&#39;s scoped to was deleted |  -  |
**402** | &#x60;plan_limit_exceeded&#x60;: the organization stayed over its plan&#39;s limits after the grace period, its API is blocked until it upgrades. &#x60;plan_limit_reached&#x60;: creating the resource would go over the plan&#39;s limit |  -  |
**403** | &#x60;token_not_allowed&#x60;: the endpoint doesn&#39;t accept tokens, or not of this type. &#x60;insufficient_scope&#x60;: the token lacks the permission. &#x60;no_active_organization&#x60; or &#x60;forbidden&#x60;: the session has no organization, or isn&#39;t a member of the one requested |  -  |
**404** | &#x60;not_found&#x60;: product not found. &#x60;policy_not_found&#x60;: the product has no policy with this &#x60;policyId&#x60;. &#x60;price_not_found&#x60;: the Stripe account has no price with this &#x60;stripePriceId&#x60; |  -  |
**409** | &#x60;not_connected&#x60;: Stripe isn&#39;t connected in the product&#39;s mode. &#x60;price_mapped&#x60;: the price already creates licenses of a product |  -  |
**422** | &#x60;validation_error&#x60;: invalid body. &#x60;price_unusable&#x60;: the price is archived, or isn&#39;t a one-time price |  -  |
**429** | &#x60;rate_limited&#x60;: the API key made more than 10 requests in the last second. Wait for the &#x60;Retry-After&#x60; seconds |  -  |
**502** | &#x60;provider_unavailable&#x60;: Stripe couldn&#39;t be reached |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

# **delete_stripe_mapping**
> delete_stripe_mapping(id)

Delete a mapping

Paying the price no longer creates licenses. The licenses it created stay. Doesn't accept tokens: only API keys and sessions.

**Required role permission**: `integration:update` when called with a session, granted by the member's role. API keys aren't limited by roles.

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
    api_instance = licensemanager.IntegrationsApi(api_client)
    id = 'i8Fz4QnRt' # str | 

    try:
        # Delete a mapping
        api_instance.delete_stripe_mapping(id)
    except Exception as e:
        print("Exception when calling IntegrationsApi->delete_stripe_mapping: %s\n" % e)
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
**404** | Mapping not found |  -  |
**422** | &#x60;validation_error&#x60;: invalid path, query or body, with the &#x60;issues&#x60; |  -  |
**429** | &#x60;rate_limited&#x60;: the API key made more than 10 requests in the last second. Wait for the &#x60;Retry-After&#x60; seconds |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

# **disconnect_integration**
> disconnect_integration(id)

Disconnect an integration

Deletes the webhook endpoint from the Stripe account first, then the integration with its mappings, for every product. The endpoint is skipped when it's already gone or the key no longer works; otherwise, when it can't be deleted, the integration is kept. The licenses it created stay. Revoke the API key in Stripe afterwards. Doesn't accept tokens: only API keys and sessions.

**Required role permission**: `integration:delete` when called with a session, granted by the member's role. API keys aren't limited by roles.

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
    api_instance = licensemanager.IntegrationsApi(api_client)
    id = 'i8Fz4QnRt' # str | 

    try:
        # Disconnect an integration
        api_instance.disconnect_integration(id)
    except Exception as e:
        print("Exception when calling IntegrationsApi->disconnect_integration: %s\n" % e)
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
**204** | Disconnected |  -  |
**401** | &#x60;unauthorized&#x60;: no credentials. &#x60;invalid_api_key&#x60;: the API key doesn&#39;t exist, was revoked or has expired. &#x60;invalid_token&#x60;: the token&#39;s signature is invalid, it has expired, or the resource it&#39;s scoped to was deleted |  -  |
**402** | &#x60;plan_limit_exceeded&#x60;: the organization stayed over its plan&#39;s limits after the grace period, its API is blocked until it upgrades. &#x60;plan_limit_reached&#x60;: creating the resource would go over the plan&#39;s limit |  -  |
**403** | &#x60;token_not_allowed&#x60;: the endpoint doesn&#39;t accept tokens, or not of this type. &#x60;insufficient_scope&#x60;: the token lacks the permission. &#x60;no_active_organization&#x60; or &#x60;forbidden&#x60;: the session has no organization, or isn&#39;t a member of the one requested |  -  |
**404** | Integration not found |  -  |
**422** | &#x60;missing_permission&#x60;: the key can&#39;t delete the webhook endpoint |  -  |
**429** | &#x60;rate_limited&#x60;: the API key made more than 10 requests in the last second. Wait for the &#x60;Retry-After&#x60; seconds |  -  |
**502** | &#x60;provider_unavailable&#x60;: Stripe couldn&#39;t be reached |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

# **get_stripe_integration**
> StripeIntegration get_stripe_integration(product_id)

Get the Stripe integration of a product

The organization connects one Stripe account for its live products, and one in test mode for its test products. Its mappings tell which Stripe prices create licenses of the product. Doesn't accept tokens: only API keys and sessions.

### Example

* Api Key Authentication (apiKey):

```python
import licensemanager
from licensemanager.models.stripe_integration import StripeIntegration
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
    api_instance = licensemanager.IntegrationsApi(api_client)
    product_id = 'x7Kp2QaZ' # str | 

    try:
        # Get the Stripe integration of a product
        api_response = api_instance.get_stripe_integration(product_id)
        print("The response of IntegrationsApi->get_stripe_integration:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling IntegrationsApi->get_stripe_integration: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **product_id** | **str**|  | 

### Return type

[**StripeIntegration**](StripeIntegration.md)

### Authorization

[apiKey](../README.md#apiKey)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details

| Status code | Description | Response headers |
|-------------|-------------|------------------|
**200** | Stripe integration |  -  |
**401** | &#x60;unauthorized&#x60;: no credentials. &#x60;invalid_api_key&#x60;: the API key doesn&#39;t exist, was revoked or has expired. &#x60;invalid_token&#x60;: the token&#39;s signature is invalid, it has expired, or the resource it&#39;s scoped to was deleted |  -  |
**402** | &#x60;plan_limit_exceeded&#x60;: the organization stayed over its plan&#39;s limits after the grace period, its API is blocked until it upgrades. &#x60;plan_limit_reached&#x60;: creating the resource would go over the plan&#39;s limit |  -  |
**403** | &#x60;token_not_allowed&#x60;: the endpoint doesn&#39;t accept tokens, or not of this type. &#x60;insufficient_scope&#x60;: the token lacks the permission. &#x60;no_active_organization&#x60; or &#x60;forbidden&#x60;: the session has no organization, or isn&#39;t a member of the one requested |  -  |
**404** | Product not found |  -  |
**422** | &#x60;validation_error&#x60;: invalid path, query or body, with the &#x60;issues&#x60; |  -  |
**429** | &#x60;rate_limited&#x60;: the API key made more than 10 requests in the last second. Wait for the &#x60;Retry-After&#x60; seconds |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

# **list_stripe_prices**
> ListStripePrices200Response list_stripe_prices(id)

List the Stripe prices of an integration

Active one-time prices of active products of the Stripe account, the ones that can be mapped, up to 500. Doesn't accept tokens: only API keys and sessions.

### Example

* Api Key Authentication (apiKey):

```python
import licensemanager
from licensemanager.models.list_stripe_prices200_response import ListStripePrices200Response
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
    api_instance = licensemanager.IntegrationsApi(api_client)
    id = 'i8Fz4QnRt' # str | 

    try:
        # List the Stripe prices of an integration
        api_response = api_instance.list_stripe_prices(id)
        print("The response of IntegrationsApi->list_stripe_prices:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling IntegrationsApi->list_stripe_prices: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **id** | **str**|  | 

### Return type

[**ListStripePrices200Response**](ListStripePrices200Response.md)

### Authorization

[apiKey](../README.md#apiKey)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details

| Status code | Description | Response headers |
|-------------|-------------|------------------|
**200** | Prices |  -  |
**401** | &#x60;unauthorized&#x60;: no credentials. &#x60;invalid_api_key&#x60;: the API key doesn&#39;t exist, was revoked or has expired. &#x60;invalid_token&#x60;: the token&#39;s signature is invalid, it has expired, or the resource it&#39;s scoped to was deleted |  -  |
**402** | &#x60;plan_limit_exceeded&#x60;: the organization stayed over its plan&#39;s limits after the grace period, its API is blocked until it upgrades. &#x60;plan_limit_reached&#x60;: creating the resource would go over the plan&#39;s limit |  -  |
**403** | &#x60;token_not_allowed&#x60;: the endpoint doesn&#39;t accept tokens, or not of this type. &#x60;insufficient_scope&#x60;: the token lacks the permission. &#x60;no_active_organization&#x60; or &#x60;forbidden&#x60;: the session has no organization, or isn&#39;t a member of the one requested |  -  |
**404** | Integration not found |  -  |
**422** | &#x60;validation_error&#x60;: invalid path, query or body, with the &#x60;issues&#x60; |  -  |
**429** | &#x60;rate_limited&#x60;: the API key made more than 10 requests in the last second. Wait for the &#x60;Retry-After&#x60; seconds |  -  |
**502** | &#x60;provider_unavailable&#x60;: Stripe couldn&#39;t be reached, or refused the request |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

# **update_stripe_mapping**
> IntegrationMapping update_stripe_mapping(id, update_integration_mapping)

Change the policy of a mapping

Only affects the licenses created afterwards. Doesn't accept tokens: only API keys and sessions.

**Required role permission**: `integration:update` when called with a session, granted by the member's role. API keys aren't limited by roles.

### Example

* Api Key Authentication (apiKey):

```python
import licensemanager
from licensemanager.models.integration_mapping import IntegrationMapping
from licensemanager.models.update_integration_mapping import UpdateIntegrationMapping
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
    api_instance = licensemanager.IntegrationsApi(api_client)
    id = 'i8Fz4QnRt' # str | 
    update_integration_mapping = licensemanager.UpdateIntegrationMapping() # UpdateIntegrationMapping | 

    try:
        # Change the policy of a mapping
        api_response = api_instance.update_stripe_mapping(id, update_integration_mapping)
        print("The response of IntegrationsApi->update_stripe_mapping:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling IntegrationsApi->update_stripe_mapping: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **id** | **str**|  | 
 **update_integration_mapping** | [**UpdateIntegrationMapping**](UpdateIntegrationMapping.md)|  | 

### Return type

[**IntegrationMapping**](IntegrationMapping.md)

### Authorization

[apiKey](../README.md#apiKey)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details

| Status code | Description | Response headers |
|-------------|-------------|------------------|
**200** | Updated mapping |  -  |
**401** | &#x60;unauthorized&#x60;: no credentials. &#x60;invalid_api_key&#x60;: the API key doesn&#39;t exist, was revoked or has expired. &#x60;invalid_token&#x60;: the token&#39;s signature is invalid, it has expired, or the resource it&#39;s scoped to was deleted |  -  |
**402** | &#x60;plan_limit_exceeded&#x60;: the organization stayed over its plan&#39;s limits after the grace period, its API is blocked until it upgrades. &#x60;plan_limit_reached&#x60;: creating the resource would go over the plan&#39;s limit |  -  |
**403** | &#x60;token_not_allowed&#x60;: the endpoint doesn&#39;t accept tokens, or not of this type. &#x60;insufficient_scope&#x60;: the token lacks the permission. &#x60;no_active_organization&#x60; or &#x60;forbidden&#x60;: the session has no organization, or isn&#39;t a member of the one requested |  -  |
**404** | &#x60;not_found&#x60;: mapping not found. &#x60;policy_not_found&#x60;: its product has no policy with this &#x60;policyId&#x60; |  -  |
**422** | &#x60;validation_error&#x60;: invalid path, query or body, with the &#x60;issues&#x60; |  -  |
**429** | &#x60;rate_limited&#x60;: the API key made more than 10 requests in the last second. Wait for the &#x60;Retry-After&#x60; seconds |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

