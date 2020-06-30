# Put Verb

Use PUT APIs primarily **to update existing resource** (if the resource does not exist, API may decide whether to create a new resource or not). If a new resource has been created by the PUT API, the origin server MUST inform the user agent via the HTTP response code `201 (Created)` response, and if an existing resource is modified, either the `200 (OK)` or `204 (No Content`) response codes should be sent to indicate successful completion of the request.

If the request passes through a cache and the Request-URI identifies one or more currently cached entities, those entries SHOULD be treated as stale. Responses to this method are **not cacheable**.

The difference between the POST and PUT APIs can be observed in request URIs. POST requests are made on resource collections, whereas PUT requests are made on an individual resource.

## 1.      Put data into LU table

http://IP address:PORT/api/[VERSION_NO]/lu/LU Name/iid/TABLE_NAME&token=token name&[format=json/xml]

| **Component** | **Description**                               | **Mandatory** | **Example**      | **Default**    |
| ------------- | --------------------------------------------- | ------------- | ---------------- | -------------- |
| Domain name   | Domain name                                   | Y             | localhost        |                |
| PORT          | PORT                                          | Y             | 3213             |                |
| api           | API                                           | Y             | api              |                |
| VERSION_NO    | Version number                                | N             | V1.4             | Latest version |
| LU Name       | Logical unit name or COMMON for common tables | Y             | CUSTOMER  COMMON |                |
| Iid           | Instance Id                                   | Y             | 1                |                |
| TABLE_NAME    | Table name for data creation                  | Y             | PAYMENT          |                |
| token         | Token Name                                    | Y             |                  |                |
| format        | Response format                               | Y             | JSON/XML/CSV     | JSON           |

**Examples:**

http://localhost:3213/api/v1.0/lu/CUSTOMER/1/INVOICE?token=ABC

Update data on CUSTOMER LU instance id 1, CUSTOMER table

Request Body
```
 {
	"row" : {"LAST_NAME":"TEST1"},
	"where":"CUSTOMER=1 or ADDRESS='Betsey'"
}                    
```
 

## 2.      Put data into common table

http://Domain name:PORT/api/[VERSION_NO]/COMMON/COMMON TABLE NAME&token=token name&[format=json/xml]

| **Component**     | **Description**              | **Mandatory** | **Example**   | **Default** |
| ----------------- | ---------------------------- | ------------- | ------------- | ----------- |
| Domain name       | Domain name                  | Y             | localhost     |             |
| PORT              | PORT                         | Y             | 3213          |             |
| api               | API                          | Y             | api           |             |
| COMMON            | Specify that scope is common | Y             | COMMON        |             |
| COMMON TABLE NAME | Common table name            | N             | ADDRESSES     |             |
| token             | Token Name                   | Y             |               |             |
| format            | Response format              | Y             | JSON/XML/YAML | JSON        |

**Examples:**

http://localhost:3213/api/v1.0/COMMON?CITIES&token=ABC

update data in common ADDRESSES table
```
Request Body

 {
	"row" : {"ADDRESS_NAME":"YOQNEAM"} ,
	"where":"ADDRESS_ID=3"
}
```
 

## 3.      Put custom Web-Service 

http://Domain name:PORT/api/[VERSION_NO]/{customized Web-Service name?token=token name&[format=json/xml]

parameters should be populated on the body in the following structure:
```
{
“parameter name 1”:”value”,
“parameter name 2”:”value”
}
```
 

| **Component**               | **Description**                        | **Mandatory** | **Example**   | **Default**    |
| --------------------------- | -------------------------------------- | ------------- | ------------- | -------------- |
| Domain name                 | Domain name                            | Y             | localhost     |                |
| PORT                        | PORT                                   | Y             | 3213          |                |
| Api                         | API                                    | Y             | api           |                |
| VERSION_NO                  | Version number                         | N             | V1.4          | Latest version |
| Customized Web-Service name | Name of the Web-Service to be executed | Y             | Orders        |                |
| Format                      | Response format                        | Y             | JSON/XML/YAML | JSON           |

## 4.         Request Header

| **Parameter**             | **Mandatory** | **Value**                                                   |
| ------------------------- | ------------- | ----------------------------------------------------------- |
| Token                     | Y             | Token name                                                  |
| Accept                    | Y             | Json/XML/RAW/YAML/CSV                                       |
| Any additional parameters | N             | Parameter=value&     Can be provided on both URL and header |

**Examples:**

http://localhost:3213/api/v1.0/Orders/1/Open?token=ABC&format=json

In the body request put:
```
{
 "i_order_id": "1",
 "i_order_status": "Open"
}
```
Call Web-Service Orders and bring output structure in json format according to input parameters i_order_id = 1 and i_order_status=Open

[![Previous](/articles/images/Previous.png)](/articles/15_web_services/13_Supported_Verbs_Post.md)[<img align="right" width="60" height="54" src="/articles/images/Next.png">](/articles/15_web_services/15_Supported_Verbs_Delete.md)

