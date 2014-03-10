# Pivotal MySQL Dev v1.1.0.0 Release Notes

### Summary: MySQL Dev v1.1.0.0 includes minor bug fixes and updates. 

### Changes since v1.0.0.2:

* Updated the format of metadata fields in the broker catalog endpoint and added additional fields. For more information, see Catalog Metadata.
* Updated Ruby to version 2.0.0p353 to fix a vulnerability in 1.9.3p448.
* Requests to delete a service instance or binding now get a 200 response with an empty JSON body instead of a 204.
* The broker now returns a clear error when there is no more capacity for additional instances during a provision request. The response has status code 507 and the user-facing error message is "Service plan capacity has been reached"

## The following components will be redeployed:
* cf-mysql-broker
* mysql
