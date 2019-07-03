---
description: The import object and its fields
---

# Imports

Imports are very handy resources that let you asynchronously import SKUs, prices, and stock items into your organization's environment.
After creating an import, you can poll the resource until the import is complete to get its reports.
Import errors and warnings, if any, are reported through the `errors_count`, `errors_log`, `warnings_count`, and `warnings_log` attributes.
When you import a list of resources, you can choose to delete any record that is not included in the list, by setting the `cleanup_records` variable to `true`.
In case, after the import is complete you also get the number of destroyed records through the `destroyed_count` attribute.


### The import object

An **import** object is returned as part of the response body of each successful
/api-reference/resources/imports/create_import,
/api-reference/resources/imports/list_imports,
/api-reference/resources/imports/retrieve_import,
or /api-reference/resources/imports/update_import API call.

| Field | Type | Description |
| :--- | :--- | :--- |
| **type** | `string` | `imports` |
| **id** | `string` | The import unique identifier |
| links.**self** | `string` | The import endpoint URL |
| attributes.**resource_type** | `string` | The type of resource being imported. One of 'skus', 'prices', or 'stock_items' |
| attributes.**parent_resource_id** | `integer` | The ID of the parent resource. It can be the 'shipping_category_id' for 'skus', the 'price_list_id' for 'prices', or the 'stock_location_id' for 'stock_items' |
| attributes.**status** | `string` | The import job status. One of 'pending' (default), 'started', or 'completed' |
| attributes.**started_at** | `datetime` | Time at which the import was started. |
| attributes.**completed_at** | `datetime` | Time at which the import was completed. |
| attributes.**inputs** | `object` | Array of objects representing the resources that are being imported. |
| attributes.**errors_count** | `integer` | Indicates the number of import errors, if any. |
| attributes.**warnings_count** | `integer` | Indicates the number of import warnings, if any. |
| attributes.**destroyed_count** | `integer` | Indicates the number of records that have been destroyed, if any. |
| attributes.**errors_log** | `object` | Contains the import errors, if any. |
| attributes.**warnings_log** | `object` | Contains the import warnings, if any. |
| attributes.**cleanup_records** | `boolean` | Indicates if the import should cleanup records that are not included in the inputs array. |
| attributes.**id** | `string` | Unique identifier for the resource (hash). |
| attributes.**created_at** | `datetime` | Time at which the resource was created. |
| attributes.**updated_at** | `datetime` | Time at which the resource was last updated. |
| attributes.**reference** | `string` | A string that you can use to add your own identifier to the resource. This can be useful for intergrating the resource to an external system, like an ERP, a marketing tool or a CRM. |
| attributes.**metadata** | `object` | Set of key-value pairs that you can attach to the resource. This can be useful for storing additional information about the resource in a structured format. |
| meta.**mode** | `string` | The resource environment \(can be one of `test` or `live`\) |
