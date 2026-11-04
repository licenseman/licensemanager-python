# LicenseCustomer

Customer the license belongs to, the one of `customerId`.

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**id** | **str** |  | 
**email** | **str** |  | 
**name** | **str** | Display name of the customer. &#x60;null&#x60; when unknown. | 

## Example

```python
from licensemanager.models.license_customer import LicenseCustomer

# TODO update the JSON string below
json = "{}"
# create an instance of LicenseCustomer from a JSON string
license_customer_instance = LicenseCustomer.from_json(json)
# print the JSON string representation of the object
print(LicenseCustomer.to_json())

# convert the object into a dict
license_customer_dict = license_customer_instance.to_dict()
# create an instance of LicenseCustomer from a dict
license_customer_from_dict = LicenseCustomer.from_dict(license_customer_dict)
```
[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)


