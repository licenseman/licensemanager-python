# LicenseManager Python SDK

[![PyPI version](https://img.shields.io/pypi/v/licenseman-sdk)](https://pypi.org/project/licenseman-sdk/)
[![Python versions](https://img.shields.io/pypi/pyversions/licenseman-sdk)](https://pypi.org/project/licenseman-sdk/)
[![PyPI downloads](https://img.shields.io/pypi/dm/licenseman-sdk)](https://pypi.org/project/licenseman-sdk/)
[![License](https://img.shields.io/github/license/licenseman/licensemanager-python)](https://github.com/licenseman/licensemanager-python/blob/main/LICENSE)
[![Documentation](https://img.shields.io/badge/docs-licensemanager.dev-blue)](https://licensemanager.dev/docs/sdks/python)

The official Python SDK for the [LicenseManager](https://licensemanager.dev) API: issue, manage and validate software licenses. Typed client with Pydantic models.

**[Documentation](https://licensemanager.dev/docs/sdks/python)** · **[API reference](https://api.licensemanager.dev/docs)** · **[Changelog](CHANGELOG.md)**

## Requirements

Python 3.10 or later.

## Installation

```sh
pip install licenseman-sdk
```

## Usage

Create an API key in the LicenseManager app, then create a license after a sale:

```python
import os

import licensemanager

configuration = licensemanager.Configuration(
    api_key={"apiKey": os.environ["LICENSEMANAGER_API_KEY"]},
)

with licensemanager.ApiClient(configuration) as api_client:
    licenses = licensemanager.LicensesApi(api_client)
    license = licenses.create_license(
        product_id="x7Kp2QaZ",
        create_license=licensemanager.CreateLicense(email="jane@example.com"),
    )
```

And validate it from your application, which needs no API key:

```python
import licensemanager

with licensemanager.ApiClient() as api_client:
    licenses = licensemanager.LicensesApi(api_client)
    license_token = licenses.validate_key(
        product_id="x7Kp2QaZ",
        validate_key=licensemanager.ValidateKey(key="7KQ2M-X9ZPA-H4TRC-WN6EY-B3JDF", fingerprint="4c:32:75:8f:9a:1e", version="1.4.2"),
    )
```

## Authentication

Most endpoints take an organization API key: keep it on your servers. The endpoints your application calls directly, like validating a key, take no credentials or a token scoped to a customer, license or machine. See [authentication](https://licensemanager.dev/docs/api/authentication) and [scoped tokens](https://licensemanager.dev/docs/api/scoped-tokens).

```python
# With an API key, from your backend:
configuration = licensemanager.Configuration(api_key={"apiKey": os.environ["LICENSEMANAGER_API_KEY"]})

# With a token scoped to a customer, license or machine:
configuration = licensemanager.Configuration(access_token=token)
```

## Errors

Failed requests answer an error with a stable `code` to branch on, listed for each endpoint in the [API reference](https://api.licensemanager.dev/docs). See [errors](https://licensemanager.dev/docs/api/errors).

```python
try:
    licenses.get_license(id="l3Nv8KwB")
except licensemanager.ApiException as error:
    # The body is { "error": { "code", "message" } }.
    print(error.status, error.body)
```

## Reference

Every method is documented, with its parameters and responses, in the [`docs`](docs) folder:

| Class | Methods |
| --- | --- |
| [`LicensesApi`](docs/LicensesApi.md) | `validate_key`, `list_licenses`, `create_license`, `list_customer_licenses`, `get_license`, `delete_license`, `update_license`, `get_license_stats`, `cancel_license`, `send_license_keys`, `get_signing_key` |
| [`PortalApi`](docs/PortalApi.md) | `get_portal`, `request_portal_link`, `create_portal_link`, `send_portal_link` |
| [`ProductsApi`](docs/ProductsApi.md) | `list_products`, `create_product`, `get_product`, `delete_product`, `update_product`, `reset_product`, `upload_product_logo`, `delete_product_logo`, `get_product_stats` |
| [`PoliciesApi`](docs/PoliciesApi.md) | `list_policies`, `create_policy`, `get_policy`, `delete_policy`, `update_policy` |
| [`CustomersApi`](docs/CustomersApi.md) | `list_customers`, `create_customer`, `get_customer`, `delete_customer`, `update_customer` |
| [`MachinesApi`](docs/MachinesApi.md) | `list_machines`, `get_machine`, `deactivate_machine` |
| [`ReleasesApi`](docs/ReleasesApi.md) | `list_releases`, `create_release`, `get_release`, `delete_release`, `update_release` |
| [`TokensApi`](docs/TokensApi.md) | `create_customer_token`, `create_license_token`, `create_machine_token` |
| [`EventsApi`](docs/EventsApi.md) | `list_policy_events`, `list_license_events` |
| [`IntegrationsApi`](docs/IntegrationsApi.md) | `get_stripe_integration`, `connect_stripe`, `disconnect_integration`, `update_integration`, `check_integration`, `list_stripe_prices`, `create_stripe_mapping`, `delete_stripe_mapping`, `update_stripe_mapping` |

## Versioning

This SDK follows [semantic versioning](https://semver.org) and is generated from the [OpenAPI document](openapi.json) of the API: each release is listed in the [changelog](CHANGELOG.md). Please don't open pull requests, they would be overwritten by the next release: [open an issue](https://github.com/licenseman/licensemanager-python/issues) instead.

## License

See [LICENSE](LICENSE).
