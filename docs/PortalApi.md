# licensemanager.PortalApi

All URIs are relative to *https://api.licensemanager.dev*

Method | HTTP request | Description
------------- | ------------- | -------------
[**create_portal_link**](PortalApi.md#create_portal_link) | **POST** /v1/customers/{id}/portal-links | Create a link to the customer portal
[**get_portal**](PortalApi.md#get_portal) | **GET** /v1/portal/{productId} | Get the customer portal of a product
[**request_portal_link**](PortalApi.md#request_portal_link) | **POST** /v1/portal/{productId}/request-link | Email a link to the customer portal
[**send_portal_link**](PortalApi.md#send_portal_link) | **POST** /v1/customers/{id}/portal-links/send | Email a link to the customer portal to the customer


# **create_portal_link**
> PortalLink create_portal_link(id, create_portal_link)

Create a link to the customer portal

Link letting the customer see their licenses and deactivate their machines in the customer portal, without signing in. Anyone with the link can, until it expires or the customer is deleted: it can't be revoked otherwise. The token also works with the API endpoints that accept customer tokens.

Links can be created while the product's customer portal is disabled, but the portal answers `404` until it's enabled, and `sendPortalLink` refuses to email them.

**Required role permission**: `portalLink:create` when called with a session, granted by the member's role. API keys aren't limited by roles.

### Example

* Api Key Authentication (apiKey):

```python
import licensemanager
from licensemanager.models.create_portal_link import CreatePortalLink
from licensemanager.models.portal_link import PortalLink
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
    api_instance = licensemanager.PortalApi(api_client)
    id = 'c9Wd3RtE' # str | 
    create_portal_link = licensemanager.CreatePortalLink() # CreatePortalLink | 

    try:
        # Create a link to the customer portal
        api_response = api_instance.create_portal_link(id, create_portal_link)
        print("The response of PortalApi->create_portal_link:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling PortalApi->create_portal_link: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **id** | **str**|  | 
 **create_portal_link** | [**CreatePortalLink**](CreatePortalLink.md)|  | 

### Return type

[**PortalLink**](PortalLink.md)

### Authorization

[apiKey](../README.md#apiKey)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details

| Status code | Description | Response headers |
|-------------|-------------|------------------|
**201** | Created link |  -  |
**401** | &#x60;unauthorized&#x60;: no credentials. &#x60;invalid_api_key&#x60;: the API key doesn&#39;t exist, was revoked or has expired. &#x60;invalid_token&#x60;: the token&#39;s signature is invalid, it has expired, or the resource it&#39;s scoped to was deleted |  -  |
**402** | &#x60;plan_limit_exceeded&#x60;: the organization stayed over its plan&#39;s limits after the grace period, its API is blocked until it upgrades. &#x60;plan_limit_reached&#x60;: creating the resource would go over the plan&#39;s limit |  -  |
**403** | &#x60;token_not_allowed&#x60;: the endpoint doesn&#39;t accept tokens, or not of this type. &#x60;insufficient_scope&#x60;: the token lacks the permission. &#x60;no_active_organization&#x60; or &#x60;forbidden&#x60;: the session has no organization, or isn&#39;t a member of the one requested |  -  |
**404** | Customer not found |  -  |
**422** | &#x60;validation_error&#x60;: invalid path, query or body, with the &#x60;issues&#x60; |  -  |
**429** | &#x60;rate_limited&#x60;: the API key made more than 10 requests in the last second. Wait for the &#x60;Retry-After&#x60; seconds |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

# **get_portal**
> Portal get_portal(product_id, return_url=return_url)

Get the customer portal of a product

Names of the product and of its organization, colors of the customer portal, and link back to the product's website. Answers `404` when the product's customer portal is disabled: with the `portal_disabled` code and the slugs of the product and its organization when signed in as a member of the organization, so they can enable it. Doesn't need authentication.

### Example


```python
import licensemanager
from licensemanager.models.portal import Portal
from licensemanager.rest import ApiException
from pprint import pprint

# Defining the host is optional and defaults to https://api.licensemanager.dev
# See configuration.py for a list of all supported configuration parameters.
configuration = licensemanager.Configuration(
    host = "https://api.licensemanager.dev"
)


# Enter a context with an instance of the API client
with licensemanager.ApiClient(configuration) as api_client:
    # Create an instance of the API class
    api_instance = licensemanager.PortalApi(api_client)
    product_id = 'x7Kp2QaZ' # str | 
    return_url = 'https://example.com/account' # str | Link back to your website to show, used when its domain is one of the product's `returnDomains`. (optional)

    try:
        # Get the customer portal of a product
        api_response = api_instance.get_portal(product_id, return_url=return_url)
        print("The response of PortalApi->get_portal:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling PortalApi->get_portal: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **product_id** | **str**|  | 
 **return_url** | **str**| Link back to your website to show, used when its domain is one of the product&#39;s &#x60;returnDomains&#x60;. | [optional] 

### Return type

[**Portal**](Portal.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details

| Status code | Description | Response headers |
|-------------|-------------|------------------|
**200** | Customer portal |  -  |
**404** | &#x60;not_found&#x60;: product not found, or its customer portal is disabled. &#x60;portal_disabled&#x60;: its customer portal is disabled, for members of its organization |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

# **request_portal_link**
> request_portal_link(product_id, request_portal_link)

Email a link to the customer portal

Emails the customer of the product with this email a link to the customer portal, working for 1 hour. Answers `404` when the product's customer portal is disabled. Answers the same whether the customer exists or not, so the API doesn't tell which emails are customers. Test products only email the members of the organization: the link isn't sent to other customers, with the same answer. Doesn't need authentication.

### Example


```python
import licensemanager
from licensemanager.models.request_portal_link import RequestPortalLink
from licensemanager.rest import ApiException
from pprint import pprint

# Defining the host is optional and defaults to https://api.licensemanager.dev
# See configuration.py for a list of all supported configuration parameters.
configuration = licensemanager.Configuration(
    host = "https://api.licensemanager.dev"
)


# Enter a context with an instance of the API client
with licensemanager.ApiClient(configuration) as api_client:
    # Create an instance of the API class
    api_instance = licensemanager.PortalApi(api_client)
    product_id = 'x7Kp2QaZ' # str | 
    request_portal_link = licensemanager.RequestPortalLink() # RequestPortalLink | 

    try:
        # Email a link to the customer portal
        api_instance.request_portal_link(product_id, request_portal_link)
    except Exception as e:
        print("Exception when calling PortalApi->request_portal_link: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **product_id** | **str**|  | 
 **request_portal_link** | [**RequestPortalLink**](RequestPortalLink.md)|  | 

### Return type

void (empty response body)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details

| Status code | Description | Response headers |
|-------------|-------------|------------------|
**204** | Link emailed, if the customer exists |  -  |
**404** | &#x60;not_found&#x60;: product not found, or its customer portal is disabled |  -  |
**422** | Validation error |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

# **send_portal_link**
> send_portal_link(id, send_portal_link)

Email a link to the customer portal to the customer

Emails a link created with `createPortalLink` to the customer's email. Fails while the product's customer portal is disabled, and, in test products, when the customer's email isn't a member's of the organization: test products only email members, so testing never emails real customers.

**Required role permission**: `portalLink:create` when called with a session, granted by the member's role. API keys aren't limited by roles.

### Example

* Api Key Authentication (apiKey):

```python
import licensemanager
from licensemanager.models.send_portal_link import SendPortalLink
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
    api_instance = licensemanager.PortalApi(api_client)
    id = 'c9Wd3RtE' # str | 
    send_portal_link = licensemanager.SendPortalLink() # SendPortalLink | 

    try:
        # Email a link to the customer portal to the customer
        api_instance.send_portal_link(id, send_portal_link)
    except Exception as e:
        print("Exception when calling PortalApi->send_portal_link: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **id** | **str**|  | 
 **send_portal_link** | [**SendPortalLink**](SendPortalLink.md)|  | 

### Return type

void (empty response body)

### Authorization

[apiKey](../README.md#apiKey)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details

| Status code | Description | Response headers |
|-------------|-------------|------------------|
**204** | Link emailed |  -  |
**401** | &#x60;unauthorized&#x60;: no credentials. &#x60;invalid_api_key&#x60;: the API key doesn&#39;t exist, was revoked or has expired. &#x60;invalid_token&#x60;: the token&#39;s signature is invalid, it has expired, or the resource it&#39;s scoped to was deleted |  -  |
**402** | &#x60;plan_limit_exceeded&#x60;: the organization stayed over its plan&#39;s limits after the grace period, its API is blocked until it upgrades. &#x60;plan_limit_reached&#x60;: creating the resource would go over the plan&#39;s limit |  -  |
**403** | &#x60;token_not_allowed&#x60;: the endpoint doesn&#39;t accept tokens, or not of this type. &#x60;insufficient_scope&#x60;: the token lacks the permission. &#x60;no_active_organization&#x60; or &#x60;forbidden&#x60;: the session has no organization, or isn&#39;t a member of the one requested |  -  |
**404** | Customer not found |  -  |
**409** | &#x60;portal_disabled&#x60;: the product&#39;s customer portal is disabled. &#x60;test_recipient_not_member&#x60;: the product is a test product, and the customer&#39;s email isn&#39;t a member&#39;s of the organization |  -  |
**422** | &#x60;validation_error&#x60;: invalid body. &#x60;invalid_token&#x60;: the token isn&#39;t valid, has expired, or isn&#39;t a customer token of this customer |  -  |
**429** | &#x60;rate_limited&#x60;: the API key made more than 10 requests in the last second. Wait for the &#x60;Retry-After&#x60; seconds |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

