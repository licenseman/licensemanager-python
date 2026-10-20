# licensemanager.LicensesApi

All URIs are relative to *https://api.licensemanager.dev*

Method | HTTP request | Description
------------- | ------------- | -------------
[**create_license**](LicensesApi.md#create_license) | **POST** /v1/products/{productId}/licenses | Create a license
[**delete_license**](LicensesApi.md#delete_license) | **DELETE** /v1/licenses/{id} | Delete a license
[**get_license**](LicensesApi.md#get_license) | **GET** /v1/licenses/{id} | Get a license
[**get_license_stats**](LicensesApi.md#get_license_stats) | **GET** /v1/licenses/{id}/stats | Get the stats of a license
[**get_signing_key**](LicensesApi.md#get_signing_key) | **GET** /v1/signing-key | Get the organization&#39;s signing key
[**list_customer_licenses**](LicensesApi.md#list_customer_licenses) | **GET** /v1/customers/{customerId}/licenses | List the licenses of a customer
[**list_licenses**](LicensesApi.md#list_licenses) | **GET** /v1/products/{productId}/licenses | List the licenses of a product
[**send_license_keys**](LicensesApi.md#send_license_keys) | **POST** /v1/licenses/send-keys | Email license keys to their customers
[**update_license**](LicensesApi.md#update_license) | **PATCH** /v1/licenses/{id} | Update a license
[**validate_key**](LicensesApi.md#validate_key) | **POST** /v1/products/{productId}/validate-key | Validate a license key


# **create_license**
> License create_license(product_id, create_license)

Create a license

Without a `key`, the license gets a random one, like `7KQ2M-X9ZPA-H4TRC-WN6EY-B3JDF`: 5 groups of 5 characters separated by dashes, each character an upper case letter or a digit other than `O`, `0`, `I` and `1`. That's 32 possible characters encoding 5 bits each, for 125 random bits.

Without a `policyId`, the license follows the product's default policy.

Without an `expiresAt`, the license expires after the duration of its policy, or never when the policy has none. `expiresAt: null` makes it never expire.

Without a `price`, the price paid for the license is unknown: it's left out of the revenue stats.

The values of `maxVersion` left out are taken from the max version of the policy: its hard-coded version, or the times after the creation of the license its versions lock.

The license belongs to the product's customer with the given `email`, which is created when there's none.

With `sendKey: true`, the key is emailed to the customer once the license is created.

The license copies the settings of its policy when it's created: later changes to the policy don't affect it. Its key, policy and customer can't be changed afterwards.

**Required role permission**: `license:create` when called with a session, granted by the member's role. API keys aren't limited by roles.

### Example

* Api Key Authentication (apiKey):

```python
import licensemanager
from licensemanager.models.create_license import CreateLicense
from licensemanager.models.license import License
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
    api_instance = licensemanager.LicensesApi(api_client)
    product_id = 'x7Kp2QaZ' # str | 
    create_license = licensemanager.CreateLicense() # CreateLicense | 

    try:
        # Create a license
        api_response = api_instance.create_license(product_id, create_license)
        print("The response of LicensesApi->create_license:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling LicensesApi->create_license: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **product_id** | **str**|  | 
 **create_license** | [**CreateLicense**](CreateLicense.md)|  | 

### Return type

[**License**](License.md)

### Authorization

[apiKey](../README.md#apiKey)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details

| Status code | Description | Response headers |
|-------------|-------------|------------------|
**201** | Created license |  -  |
**401** | &#x60;unauthorized&#x60;: no credentials. &#x60;invalid_api_key&#x60;: the API key doesn&#39;t exist, was revoked or has expired. &#x60;invalid_token&#x60;: the token&#39;s signature is invalid, it has expired, or the resource it&#39;s scoped to was deleted |  -  |
**402** | &#x60;plan_limit_exceeded&#x60;: the organization stayed over its plan&#39;s limits after the grace period, its API is blocked until it upgrades. &#x60;plan_limit_reached&#x60;: creating the resource would go over the plan&#39;s limit |  -  |
**403** | &#x60;token_not_allowed&#x60;: the endpoint doesn&#39;t accept tokens, or not of this type. &#x60;insufficient_scope&#x60;: the token lacks the permission. &#x60;no_active_organization&#x60; or &#x60;forbidden&#x60;: the session has no organization, or isn&#39;t a member of the one requested |  -  |
**404** | &#x60;not_found&#x60;: product not found. &#x60;policy_not_found&#x60;: the product has no policy with this &#x60;policyId&#x60; |  -  |
**409** | &#x60;key_taken&#x60;: key already used by another license of the product |  -  |
**422** | &#x60;validation_error&#x60;: invalid path, query or body, with the &#x60;issues&#x60; |  -  |
**429** | &#x60;rate_limited&#x60;: the API key made more than 10 requests in the last second. Wait for the &#x60;Retry-After&#x60; seconds |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

# **delete_license**
> delete_license(id)

Delete a license

Deletes the license along with its deactivated machines. A license used on active machines can't be deleted: deactivate them first. The tokens scoped to the license or its machines stop working, but the license tokens `validateKey` already returned stay valid until they expire. Its events can no longer be listed.

**Required role permission**: `license:delete` when called with a session, granted by the member's role. API keys aren't limited by roles.

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
    api_instance = licensemanager.LicensesApi(api_client)
    id = 'l3Nv8KwB' # str | 

    try:
        # Delete a license
        api_instance.delete_license(id)
    except Exception as e:
        print("Exception when calling LicensesApi->delete_license: %s\n" % e)
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
**404** | License not found |  -  |
**409** | &#x60;license_in_use&#x60;: the license is used on active machines |  -  |
**422** | &#x60;validation_error&#x60;: invalid path, query or body, with the &#x60;issues&#x60; |  -  |
**429** | &#x60;rate_limited&#x60;: the API key made more than 10 requests in the last second. Wait for the &#x60;Retry-After&#x60; seconds |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

# **get_license**
> License get_license(id)

Get a license

**Token access**: customer, license, machine tokens with the `license:read` permission (or the matching write one). A token reaches the license it's scoped to, the licenses of its customer, or the license of its machine.

### Example

* Api Key Authentication (apiKey):
* Bearer (JWT) Authentication (token):

```python
import licensemanager
from licensemanager.models.license import License
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
    api_instance = licensemanager.LicensesApi(api_client)
    id = 'l3Nv8KwB' # str | 

    try:
        # Get a license
        api_response = api_instance.get_license(id)
        print("The response of LicensesApi->get_license:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling LicensesApi->get_license: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **id** | **str**|  | 

### Return type

[**License**](License.md)

### Authorization

[apiKey](../README.md#apiKey), [token](../README.md#token)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details

| Status code | Description | Response headers |
|-------------|-------------|------------------|
**200** | License |  -  |
**401** | &#x60;unauthorized&#x60;: no credentials. &#x60;invalid_api_key&#x60;: the API key doesn&#39;t exist, was revoked or has expired. &#x60;invalid_token&#x60;: the token&#39;s signature is invalid, it has expired, or the resource it&#39;s scoped to was deleted |  -  |
**402** | &#x60;plan_limit_exceeded&#x60;: the organization stayed over its plan&#39;s limits after the grace period, its API is blocked until it upgrades. &#x60;plan_limit_reached&#x60;: creating the resource would go over the plan&#39;s limit |  -  |
**403** | &#x60;token_not_allowed&#x60;: the endpoint doesn&#39;t accept tokens, or not of this type. &#x60;insufficient_scope&#x60;: the token lacks the permission. &#x60;no_active_organization&#x60; or &#x60;forbidden&#x60;: the session has no organization, or isn&#39;t a member of the one requested |  -  |
**404** | License not found |  -  |
**422** | &#x60;validation_error&#x60;: invalid path, query or body, with the &#x60;issues&#x60; |  -  |
**429** | &#x60;rate_limited&#x60;: the API key made more than 10 requests in the last second. Wait for the &#x60;Retry-After&#x60; seconds |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

# **get_license_stats**
> LicenseStats get_license_stats(id)

Get the stats of a license

Daily number of successful activations of the license over the last 90 days, today included, per machine and per version of the application. Days are in UTC.

### Example

* Api Key Authentication (apiKey):

```python
import licensemanager
from licensemanager.models.license_stats import LicenseStats
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
    api_instance = licensemanager.LicensesApi(api_client)
    id = 'l3Nv8KwB' # str | 

    try:
        # Get the stats of a license
        api_response = api_instance.get_license_stats(id)
        print("The response of LicensesApi->get_license_stats:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling LicensesApi->get_license_stats: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **id** | **str**|  | 

### Return type

[**LicenseStats**](LicenseStats.md)

### Authorization

[apiKey](../README.md#apiKey)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details

| Status code | Description | Response headers |
|-------------|-------------|------------------|
**200** | Stats of the license |  -  |
**401** | &#x60;unauthorized&#x60;: no credentials. &#x60;invalid_api_key&#x60;: the API key doesn&#39;t exist, was revoked or has expired. &#x60;invalid_token&#x60;: the token&#39;s signature is invalid, it has expired, or the resource it&#39;s scoped to was deleted |  -  |
**402** | &#x60;plan_limit_exceeded&#x60;: the organization stayed over its plan&#39;s limits after the grace period, its API is blocked until it upgrades. &#x60;plan_limit_reached&#x60;: creating the resource would go over the plan&#39;s limit |  -  |
**403** | &#x60;token_not_allowed&#x60;: the endpoint doesn&#39;t accept tokens, or not of this type. &#x60;insufficient_scope&#x60;: the token lacks the permission. &#x60;no_active_organization&#x60; or &#x60;forbidden&#x60;: the session has no organization, or isn&#39;t a member of the one requested |  -  |
**404** | License not found |  -  |
**422** | &#x60;validation_error&#x60;: invalid path, query or body, with the &#x60;issues&#x60; |  -  |
**429** | &#x60;rate_limited&#x60;: the API key made more than 10 requests in the last second. Wait for the &#x60;Retry-After&#x60; seconds |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

# **get_signing_key**
> SigningKey get_signing_key()

Get the organization's signing key

Public key verifying the license tokens returned by `validateKey`, to embed in applications. Created the first time it's needed, and never rotated. The organization has a single key, signing the tokens of its live and test products alike: check the tokens' `aud` to tell them apart.

### Example

* Api Key Authentication (apiKey):

```python
import licensemanager
from licensemanager.models.signing_key import SigningKey
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
    api_instance = licensemanager.LicensesApi(api_client)

    try:
        # Get the organization's signing key
        api_response = api_instance.get_signing_key()
        print("The response of LicensesApi->get_signing_key:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling LicensesApi->get_signing_key: %s\n" % e)
```



### Parameters

This endpoint does not need any parameter.

### Return type

[**SigningKey**](SigningKey.md)

### Authorization

[apiKey](../README.md#apiKey)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details

| Status code | Description | Response headers |
|-------------|-------------|------------------|
**200** | Signing key |  -  |
**401** | &#x60;unauthorized&#x60;: no credentials. &#x60;invalid_api_key&#x60;: the API key doesn&#39;t exist, was revoked or has expired. &#x60;invalid_token&#x60;: the token&#39;s signature is invalid, it has expired, or the resource it&#39;s scoped to was deleted |  -  |
**402** | &#x60;plan_limit_exceeded&#x60;: the organization stayed over its plan&#39;s limits after the grace period, its API is blocked until it upgrades. &#x60;plan_limit_reached&#x60;: creating the resource would go over the plan&#39;s limit |  -  |
**403** | &#x60;token_not_allowed&#x60;: the endpoint doesn&#39;t accept tokens, or not of this type. &#x60;insufficient_scope&#x60;: the token lacks the permission. &#x60;no_active_organization&#x60; or &#x60;forbidden&#x60;: the session has no organization, or isn&#39;t a member of the one requested |  -  |
**422** | &#x60;validation_error&#x60;: invalid path, query or body, with the &#x60;issues&#x60; |  -  |
**429** | &#x60;rate_limited&#x60;: the API key made more than 10 requests in the last second. Wait for the &#x60;Retry-After&#x60; seconds |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

# **list_customer_licenses**
> LicenseList list_customer_licenses(customer_id, page=page, page_size=page_size, sort=sort, search=search, key=key, policy_id=policy_id, machine_version=machine_version, status=status, created_from=created_from, created_to=created_to, last_activated_from=last_activated_from, last_activated_to=last_activated_to, never_activated=never_activated, expires_from=expires_from, expires_to=expires_to, never_expires=never_expires, currency=currency, price=price, price_min=price_min, price_max=price_max, has_price=has_price)

List the licenses of a customer

Sorting by `lastActivatedAt` puts the licenses never activated last in both orders. Sorting by `price` compares the amounts whatever their currency, and puts the licenses without a price last in both orders.

**Token access**: customer tokens with the `license:read` permission (or the matching write one). A customer token reaches its own licenses.

### Example

* Api Key Authentication (apiKey):
* Bearer (JWT) Authentication (token):

```python
import licensemanager
from licensemanager.models.license_list import LicenseList
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
    api_instance = licensemanager.LicensesApi(api_client)
    customer_id = 'c9Wd3RtE' # str | 
    page = 1 # int | Page to return. Pages are numbered from 1: `1` is the first page. A page past the last one returns an empty `data`, not an error. Defaults to `1`. (optional) (default to 1)
    page_size = 20 # int | Maximum number of items per page, from 1 to 100. Every page holds this many items except the last one, which can hold fewer. Defaults to `20`. (optional) (default to 20)
    sort = '-createdAt' # str | Field to sort by, prefixed with `-` for descending order. Defaults to `-createdAt`. (optional) (default to '-createdAt')
    search = 'X9ZPA' # str | Case-insensitive text the key contains. (optional)
    key = '7KQ2M-X9ZPA-H4TRC-WN6EY-B3JDF' # str | Only returns the license with this exact key, case included. Keys of test products start with `TEST-`. (optional)
    policy_id = 'p4Rt8LmQ' # str | Only returns the licenses following this policy. (optional)
    machine_version = '2.3.1' # str | Only returns the licenses with at least one active machine running this version of the product. (optional)
    status = licensemanager.LicenseStatus() # LicenseStatus | Only returns the licenses with this status. (optional)
    created_from = '2026-01-01T00:00:00.000Z' # datetime | Only returns the licenses created at or after this date. (optional)
    created_to = '2026-02-01T00:00:00.000Z' # datetime | Only returns the licenses created at or before this date. (optional)
    last_activated_from = '2026-01-01T00:00:00.000Z' # datetime | Only returns the licenses last activated at or after this date. Licenses never activated are left out. (optional)
    last_activated_to = '2026-02-01T00:00:00.000Z' # datetime | Only returns the licenses last activated at or before this date. Licenses never activated are left out. (optional)
    never_activated = 'true' # str | `true` only returns the licenses never activated, `false` only the ones activated at least once. (optional)
    expires_from = '2026-01-01T00:00:00.000Z' # datetime | Only returns the licenses expiring at or after this date. Licenses that never expire are left out. (optional)
    expires_to = '2026-02-01T00:00:00.000Z' # datetime | Only returns the licenses expiring at or before this date. Licenses that never expire are left out. (optional)
    never_expires = 'true' # str | `true` only returns the licenses that never expire, `false` only the ones with an expiration date. (optional)
    currency = 'USD' # str | Only returns the licenses paid in this currency. (optional)
    price = 49.99 # float | Only returns the licenses paid exactly this amount, in major units of its currency: combine with `currency` to compare amounts of one currency. Licenses without a price are left out. (optional)
    price_min = 49.99 # float | Only returns the licenses paid at least this amount, in major units of its currency: combine with `currency` to compare amounts of one currency. Licenses without a price are left out. (optional)
    price_max = 49.99 # float | Only returns the licenses paid at most this amount, in major units of its currency: combine with `currency` to compare amounts of one currency. Licenses without a price are left out. (optional)
    has_price = 'true' # str | `true` only returns the licenses with a price, `false` only the ones without. (optional)

    try:
        # List the licenses of a customer
        api_response = api_instance.list_customer_licenses(customer_id, page=page, page_size=page_size, sort=sort, search=search, key=key, policy_id=policy_id, machine_version=machine_version, status=status, created_from=created_from, created_to=created_to, last_activated_from=last_activated_from, last_activated_to=last_activated_to, never_activated=never_activated, expires_from=expires_from, expires_to=expires_to, never_expires=never_expires, currency=currency, price=price, price_min=price_min, price_max=price_max, has_price=has_price)
        print("The response of LicensesApi->list_customer_licenses:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling LicensesApi->list_customer_licenses: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **customer_id** | **str**|  | 
 **page** | **int**| Page to return. Pages are numbered from 1: &#x60;1&#x60; is the first page. A page past the last one returns an empty &#x60;data&#x60;, not an error. Defaults to &#x60;1&#x60;. | [optional] [default to 1]
 **page_size** | **int**| Maximum number of items per page, from 1 to 100. Every page holds this many items except the last one, which can hold fewer. Defaults to &#x60;20&#x60;. | [optional] [default to 20]
 **sort** | **str**| Field to sort by, prefixed with &#x60;-&#x60; for descending order. Defaults to &#x60;-createdAt&#x60;. | [optional] [default to &#39;-createdAt&#39;]
 **search** | **str**| Case-insensitive text the key contains. | [optional] 
 **key** | **str**| Only returns the license with this exact key, case included. Keys of test products start with &#x60;TEST-&#x60;. | [optional] 
 **policy_id** | **str**| Only returns the licenses following this policy. | [optional] 
 **machine_version** | **str**| Only returns the licenses with at least one active machine running this version of the product. | [optional] 
 **status** | [**LicenseStatus**](.md)| Only returns the licenses with this status. | [optional] 
 **created_from** | **datetime**| Only returns the licenses created at or after this date. | [optional] 
 **created_to** | **datetime**| Only returns the licenses created at or before this date. | [optional] 
 **last_activated_from** | **datetime**| Only returns the licenses last activated at or after this date. Licenses never activated are left out. | [optional] 
 **last_activated_to** | **datetime**| Only returns the licenses last activated at or before this date. Licenses never activated are left out. | [optional] 
 **never_activated** | **str**| &#x60;true&#x60; only returns the licenses never activated, &#x60;false&#x60; only the ones activated at least once. | [optional] 
 **expires_from** | **datetime**| Only returns the licenses expiring at or after this date. Licenses that never expire are left out. | [optional] 
 **expires_to** | **datetime**| Only returns the licenses expiring at or before this date. Licenses that never expire are left out. | [optional] 
 **never_expires** | **str**| &#x60;true&#x60; only returns the licenses that never expire, &#x60;false&#x60; only the ones with an expiration date. | [optional] 
 **currency** | **str**| Only returns the licenses paid in this currency. | [optional] 
 **price** | **float**| Only returns the licenses paid exactly this amount, in major units of its currency: combine with &#x60;currency&#x60; to compare amounts of one currency. Licenses without a price are left out. | [optional] 
 **price_min** | **float**| Only returns the licenses paid at least this amount, in major units of its currency: combine with &#x60;currency&#x60; to compare amounts of one currency. Licenses without a price are left out. | [optional] 
 **price_max** | **float**| Only returns the licenses paid at most this amount, in major units of its currency: combine with &#x60;currency&#x60; to compare amounts of one currency. Licenses without a price are left out. | [optional] 
 **has_price** | **str**| &#x60;true&#x60; only returns the licenses with a price, &#x60;false&#x60; only the ones without. | [optional] 

### Return type

[**LicenseList**](LicenseList.md)

### Authorization

[apiKey](../README.md#apiKey), [token](../README.md#token)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details

| Status code | Description | Response headers |
|-------------|-------------|------------------|
**200** | One page of the licenses of the customer |  -  |
**401** | &#x60;unauthorized&#x60;: no credentials. &#x60;invalid_api_key&#x60;: the API key doesn&#39;t exist, was revoked or has expired. &#x60;invalid_token&#x60;: the token&#39;s signature is invalid, it has expired, or the resource it&#39;s scoped to was deleted |  -  |
**402** | &#x60;plan_limit_exceeded&#x60;: the organization stayed over its plan&#39;s limits after the grace period, its API is blocked until it upgrades. &#x60;plan_limit_reached&#x60;: creating the resource would go over the plan&#39;s limit |  -  |
**403** | &#x60;token_not_allowed&#x60;: the endpoint doesn&#39;t accept tokens, or not of this type. &#x60;insufficient_scope&#x60;: the token lacks the permission. &#x60;no_active_organization&#x60; or &#x60;forbidden&#x60;: the session has no organization, or isn&#39;t a member of the one requested |  -  |
**404** | Customer not found |  -  |
**422** | &#x60;validation_error&#x60;: invalid path, query or body, with the &#x60;issues&#x60; |  -  |
**429** | &#x60;rate_limited&#x60;: the API key made more than 10 requests in the last second. Wait for the &#x60;Retry-After&#x60; seconds |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

# **list_licenses**
> LicenseList list_licenses(product_id, page=page, page_size=page_size, sort=sort, search=search, key=key, policy_id=policy_id, customer_id=customer_id, machine_version=machine_version, status=status, created_from=created_from, created_to=created_to, last_activated_from=last_activated_from, last_activated_to=last_activated_to, never_activated=never_activated, expires_from=expires_from, expires_to=expires_to, never_expires=never_expires, currency=currency, price=price, price_min=price_min, price_max=price_max, has_price=has_price)

List the licenses of a product

Sorting by `lastActivatedAt` puts the licenses never activated last in both orders. Sorting by `price` compares the amounts whatever their currency, and puts the licenses without a price last in both orders.

### Example

* Api Key Authentication (apiKey):

```python
import licensemanager
from licensemanager.models.license_list import LicenseList
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
    api_instance = licensemanager.LicensesApi(api_client)
    product_id = 'x7Kp2QaZ' # str | 
    page = 1 # int | Page to return. Pages are numbered from 1: `1` is the first page. A page past the last one returns an empty `data`, not an error. Defaults to `1`. (optional) (default to 1)
    page_size = 20 # int | Maximum number of items per page, from 1 to 100. Every page holds this many items except the last one, which can hold fewer. Defaults to `20`. (optional) (default to 20)
    sort = '-createdAt' # str | Field to sort by, prefixed with `-` for descending order. Defaults to `-createdAt`. (optional) (default to '-createdAt')
    search = 'X9ZPA' # str | Case-insensitive text the key contains. (optional)
    key = '7KQ2M-X9ZPA-H4TRC-WN6EY-B3JDF' # str | Only returns the license with this exact key, case included. Keys of test products start with `TEST-`. (optional)
    policy_id = 'p4Rt8LmQ' # str | Only returns the licenses following this policy. (optional)
    customer_id = 'c9Wd3RtE' # str | Only returns the licenses of this customer. (optional)
    machine_version = '2.3.1' # str | Only returns the licenses with at least one active machine running this version of the product. (optional)
    status = licensemanager.LicenseStatus() # LicenseStatus | Only returns the licenses with this status. (optional)
    created_from = '2026-01-01T00:00:00.000Z' # datetime | Only returns the licenses created at or after this date. (optional)
    created_to = '2026-02-01T00:00:00.000Z' # datetime | Only returns the licenses created at or before this date. (optional)
    last_activated_from = '2026-01-01T00:00:00.000Z' # datetime | Only returns the licenses last activated at or after this date. Licenses never activated are left out. (optional)
    last_activated_to = '2026-02-01T00:00:00.000Z' # datetime | Only returns the licenses last activated at or before this date. Licenses never activated are left out. (optional)
    never_activated = 'true' # str | `true` only returns the licenses never activated, `false` only the ones activated at least once. (optional)
    expires_from = '2026-01-01T00:00:00.000Z' # datetime | Only returns the licenses expiring at or after this date. Licenses that never expire are left out. (optional)
    expires_to = '2026-02-01T00:00:00.000Z' # datetime | Only returns the licenses expiring at or before this date. Licenses that never expire are left out. (optional)
    never_expires = 'true' # str | `true` only returns the licenses that never expire, `false` only the ones with an expiration date. (optional)
    currency = 'USD' # str | Only returns the licenses paid in this currency. (optional)
    price = 49.99 # float | Only returns the licenses paid exactly this amount, in major units of its currency: combine with `currency` to compare amounts of one currency. Licenses without a price are left out. (optional)
    price_min = 49.99 # float | Only returns the licenses paid at least this amount, in major units of its currency: combine with `currency` to compare amounts of one currency. Licenses without a price are left out. (optional)
    price_max = 49.99 # float | Only returns the licenses paid at most this amount, in major units of its currency: combine with `currency` to compare amounts of one currency. Licenses without a price are left out. (optional)
    has_price = 'true' # str | `true` only returns the licenses with a price, `false` only the ones without. (optional)

    try:
        # List the licenses of a product
        api_response = api_instance.list_licenses(product_id, page=page, page_size=page_size, sort=sort, search=search, key=key, policy_id=policy_id, customer_id=customer_id, machine_version=machine_version, status=status, created_from=created_from, created_to=created_to, last_activated_from=last_activated_from, last_activated_to=last_activated_to, never_activated=never_activated, expires_from=expires_from, expires_to=expires_to, never_expires=never_expires, currency=currency, price=price, price_min=price_min, price_max=price_max, has_price=has_price)
        print("The response of LicensesApi->list_licenses:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling LicensesApi->list_licenses: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **product_id** | **str**|  | 
 **page** | **int**| Page to return. Pages are numbered from 1: &#x60;1&#x60; is the first page. A page past the last one returns an empty &#x60;data&#x60;, not an error. Defaults to &#x60;1&#x60;. | [optional] [default to 1]
 **page_size** | **int**| Maximum number of items per page, from 1 to 100. Every page holds this many items except the last one, which can hold fewer. Defaults to &#x60;20&#x60;. | [optional] [default to 20]
 **sort** | **str**| Field to sort by, prefixed with &#x60;-&#x60; for descending order. Defaults to &#x60;-createdAt&#x60;. | [optional] [default to &#39;-createdAt&#39;]
 **search** | **str**| Case-insensitive text the key contains. | [optional] 
 **key** | **str**| Only returns the license with this exact key, case included. Keys of test products start with &#x60;TEST-&#x60;. | [optional] 
 **policy_id** | **str**| Only returns the licenses following this policy. | [optional] 
 **customer_id** | **str**| Only returns the licenses of this customer. | [optional] 
 **machine_version** | **str**| Only returns the licenses with at least one active machine running this version of the product. | [optional] 
 **status** | [**LicenseStatus**](.md)| Only returns the licenses with this status. | [optional] 
 **created_from** | **datetime**| Only returns the licenses created at or after this date. | [optional] 
 **created_to** | **datetime**| Only returns the licenses created at or before this date. | [optional] 
 **last_activated_from** | **datetime**| Only returns the licenses last activated at or after this date. Licenses never activated are left out. | [optional] 
 **last_activated_to** | **datetime**| Only returns the licenses last activated at or before this date. Licenses never activated are left out. | [optional] 
 **never_activated** | **str**| &#x60;true&#x60; only returns the licenses never activated, &#x60;false&#x60; only the ones activated at least once. | [optional] 
 **expires_from** | **datetime**| Only returns the licenses expiring at or after this date. Licenses that never expire are left out. | [optional] 
 **expires_to** | **datetime**| Only returns the licenses expiring at or before this date. Licenses that never expire are left out. | [optional] 
 **never_expires** | **str**| &#x60;true&#x60; only returns the licenses that never expire, &#x60;false&#x60; only the ones with an expiration date. | [optional] 
 **currency** | **str**| Only returns the licenses paid in this currency. | [optional] 
 **price** | **float**| Only returns the licenses paid exactly this amount, in major units of its currency: combine with &#x60;currency&#x60; to compare amounts of one currency. Licenses without a price are left out. | [optional] 
 **price_min** | **float**| Only returns the licenses paid at least this amount, in major units of its currency: combine with &#x60;currency&#x60; to compare amounts of one currency. Licenses without a price are left out. | [optional] 
 **price_max** | **float**| Only returns the licenses paid at most this amount, in major units of its currency: combine with &#x60;currency&#x60; to compare amounts of one currency. Licenses without a price are left out. | [optional] 
 **has_price** | **str**| &#x60;true&#x60; only returns the licenses with a price, &#x60;false&#x60; only the ones without. | [optional] 

### Return type

[**LicenseList**](LicenseList.md)

### Authorization

[apiKey](../README.md#apiKey)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details

| Status code | Description | Response headers |
|-------------|-------------|------------------|
**200** | One page of the licenses of the product |  -  |
**401** | &#x60;unauthorized&#x60;: no credentials. &#x60;invalid_api_key&#x60;: the API key doesn&#39;t exist, was revoked or has expired. &#x60;invalid_token&#x60;: the token&#39;s signature is invalid, it has expired, or the resource it&#39;s scoped to was deleted |  -  |
**402** | &#x60;plan_limit_exceeded&#x60;: the organization stayed over its plan&#39;s limits after the grace period, its API is blocked until it upgrades. &#x60;plan_limit_reached&#x60;: creating the resource would go over the plan&#39;s limit |  -  |
**403** | &#x60;token_not_allowed&#x60;: the endpoint doesn&#39;t accept tokens, or not of this type. &#x60;insufficient_scope&#x60;: the token lacks the permission. &#x60;no_active_organization&#x60; or &#x60;forbidden&#x60;: the session has no organization, or isn&#39;t a member of the one requested |  -  |
**404** | Product not found |  -  |
**422** | &#x60;validation_error&#x60;: invalid path, query or body, with the &#x60;issues&#x60; |  -  |
**429** | &#x60;rate_limited&#x60;: the API key made more than 10 requests in the last second. Wait for the &#x60;Retry-After&#x60; seconds |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

# **send_license_keys**
> send_license_keys(send_license_keys)

Email license keys to their customers

Emails each customer the keys of its licenses among `ids`, with their expiration date: one email per customer, whatever their number of licenses. The licenses can belong to different products of the organization.

Test products only email the members of the organization, so testing never emails real customers: nothing is sent when a license of a test product belongs to a customer whose email isn't a member's.

**Required role permission**: `license:send` when called with a session, granted by the member's role. API keys aren't limited by roles.

### Example

* Api Key Authentication (apiKey):

```python
import licensemanager
from licensemanager.models.send_license_keys import SendLicenseKeys
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
    api_instance = licensemanager.LicensesApi(api_client)
    send_license_keys = licensemanager.SendLicenseKeys() # SendLicenseKeys | 

    try:
        # Email license keys to their customers
        api_instance.send_license_keys(send_license_keys)
    except Exception as e:
        print("Exception when calling LicensesApi->send_license_keys: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **send_license_keys** | [**SendLicenseKeys**](SendLicenseKeys.md)|  | 

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
**204** | Keys emailed |  -  |
**401** | &#x60;unauthorized&#x60;: no credentials. &#x60;invalid_api_key&#x60;: the API key doesn&#39;t exist, was revoked or has expired. &#x60;invalid_token&#x60;: the token&#39;s signature is invalid, it has expired, or the resource it&#39;s scoped to was deleted |  -  |
**402** | &#x60;plan_limit_exceeded&#x60;: the organization stayed over its plan&#39;s limits after the grace period, its API is blocked until it upgrades. &#x60;plan_limit_reached&#x60;: creating the resource would go over the plan&#39;s limit |  -  |
**403** | &#x60;token_not_allowed&#x60;: the endpoint doesn&#39;t accept tokens, or not of this type. &#x60;insufficient_scope&#x60;: the token lacks the permission. &#x60;no_active_organization&#x60; or &#x60;forbidden&#x60;: the session has no organization, or isn&#39;t a member of the one requested |  -  |
**404** | &#x60;not_found&#x60;: one of the licenses wasn&#39;t found |  -  |
**409** | &#x60;test_recipient_not_member&#x60;: a license of a test product belongs to a customer whose email isn&#39;t a member&#39;s of the organization |  -  |
**422** | &#x60;validation_error&#x60;: invalid path, query or body, with the &#x60;issues&#x60; |  -  |
**429** | &#x60;rate_limited&#x60;: the API key made more than 10 requests in the last second. Wait for the &#x60;Retry-After&#x60; seconds |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

# **update_license**
> License update_license(id, update_license)

Update a license

The key, policy and customer of a license can't be changed: sending them does nothing.

The changes apply to the next validations of the key, not to the license tokens `validateKey` already returned, which stay valid until they expire. Lowering `maxMachines` doesn't deactivate machines: the ones already active keep validating, and new ones are refused until enough are deactivated.

**Required role permission**: `license:update` when called with a session, granted by the member's role. API keys aren't limited by roles.

### Example

* Api Key Authentication (apiKey):

```python
import licensemanager
from licensemanager.models.license import License
from licensemanager.models.update_license import UpdateLicense
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
    api_instance = licensemanager.LicensesApi(api_client)
    id = 'l3Nv8KwB' # str | 
    update_license = licensemanager.UpdateLicense() # UpdateLicense | 

    try:
        # Update a license
        api_response = api_instance.update_license(id, update_license)
        print("The response of LicensesApi->update_license:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling LicensesApi->update_license: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **id** | **str**|  | 
 **update_license** | [**UpdateLicense**](UpdateLicense.md)|  | 

### Return type

[**License**](License.md)

### Authorization

[apiKey](../README.md#apiKey)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details

| Status code | Description | Response headers |
|-------------|-------------|------------------|
**200** | Updated license |  -  |
**401** | &#x60;unauthorized&#x60;: no credentials. &#x60;invalid_api_key&#x60;: the API key doesn&#39;t exist, was revoked or has expired. &#x60;invalid_token&#x60;: the token&#39;s signature is invalid, it has expired, or the resource it&#39;s scoped to was deleted |  -  |
**402** | &#x60;plan_limit_exceeded&#x60;: the organization stayed over its plan&#39;s limits after the grace period, its API is blocked until it upgrades. &#x60;plan_limit_reached&#x60;: creating the resource would go over the plan&#39;s limit |  -  |
**403** | &#x60;token_not_allowed&#x60;: the endpoint doesn&#39;t accept tokens, or not of this type. &#x60;insufficient_scope&#x60;: the token lacks the permission. &#x60;no_active_organization&#x60; or &#x60;forbidden&#x60;: the session has no organization, or isn&#39;t a member of the one requested |  -  |
**404** | License not found |  -  |
**422** | &#x60;validation_error&#x60;: invalid path, query or body, with the &#x60;issues&#x60; |  -  |
**429** | &#x60;rate_limited&#x60;: the API key made more than 10 requests in the last second. Wait for the &#x60;Retry-After&#x60; seconds |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

# **validate_key**
> LicenseToken validate_key(product_id, validate_key)

Validate a license key

Checks the license key of the product on a machine and returns a token the application can verify offline with the organization's public key. Doesn't need authentication.

The license must allow the `version`: up to its `maxVersion.version` when it has one, like `"2.3"` for every 2.3.z version and older. Its `maxVersion.lockMajorAt` and `maxVersion.lockMinorAt` are enforced once they hard-code `maxVersion.version`, within the hour they're reached. When it doesn't, the error's `latestAllowedVersion` is the latest release of the product the license allows, so the application can offer to install it.

The machine with the `fingerprint` is created when the license has none, and activated when it's deactivated, unless the license is already active on its maximum number of machines. A machine that's already active is never refused for the maximum number of machines, even when it was lowered below the number of active machines. Its `version`, and its `name` and `platform` when given, are updated: they can't be cleared.

The checks run in this order, and the first one failing answers: the license has expired, then it doesn't allow the version, then it's on its maximum number of machines. Each failure is recorded as a `license.validation_failed` event, except for keys that don't exist.

Changes to the license, like deactivating the machine or shortening its expiration, don't revoke the tokens already returned: the application only sees them when it validates its key again, at the latest when its token expires.

### Example


```python
import licensemanager
from licensemanager.models.license_token import LicenseToken
from licensemanager.models.validate_key import ValidateKey
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
    api_instance = licensemanager.LicensesApi(api_client)
    product_id = 'x7Kp2QaZ' # str | 
    validate_key = licensemanager.ValidateKey() # ValidateKey | 

    try:
        # Validate a license key
        api_response = api_instance.validate_key(product_id, validate_key)
        print("The response of LicensesApi->validate_key:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling LicensesApi->validate_key: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **product_id** | **str**|  | 
 **validate_key** | [**ValidateKey**](ValidateKey.md)|  | 

### Return type

[**LicenseToken**](LicenseToken.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details

| Status code | Description | Response headers |
|-------------|-------------|------------------|
**200** | Signed license token |  -  |
**402** | &#x60;plan_limit_exceeded&#x60;: the organization stayed over its plan&#39;s limits after the grace period |  -  |
**403** | &#x60;license_expired&#x60;: the license has expired. &#x60;version_not_allowed&#x60;: the license doesn&#39;t allow the version, with the &#x60;latestAllowedVersion&#x60;. &#x60;machine_limit_reached&#x60;: the license is already active on its maximum number of machines |  -  |
**404** | &#x60;not_found&#x60;: the product doesn&#39;t exist, or has no license with this key |  -  |
**422** | &#x60;validation_error&#x60;: invalid body |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

