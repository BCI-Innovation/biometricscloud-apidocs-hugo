---
title: 'Document Request Endpoints'
date: 2019-02-11T19:27:37+10:00
draft: false
weight: 17
summary: "The CRUD endpoints pertaining to document requests."
---

Document requests are uploaded documents that organizations can request from users. A document request has the organizations information and the template file to give to the user to download and fill out. When the user fills out the document then the user must submit through the [file api endpoint](/api/api-15-file/).

# **Create Document Request**
##### Description
This endpoint will create a document request with the file saved to the remote file server.

##### URL

`https://biometricscloud.net/api/v1/document-requests`

##### Method

`POST`

##### URL Params

None

##### Data Params

Field | Requied | Description
--------- | ----------- | -----------
`edition_date` | Yes | The document edition of the submission.
`title` | Yes | The name of the document.
`form_number` | Yes | The document ID that you want to assign to it.
`organization` | Yes | The organization that this document request belongs to.
`branch` | No | The branch of the organization.
`department` | No | The department of the branch.
`program` | No | The program that belongs.
`purpose` | Yes | The purpose of the document request.
`country` | No | The country that this document requests.
`province` | No | The province that this document belongs to.
`city` | No | The city that this belongs to.
`external_url` | No | Any external links this belongs to.
`upload_content` | The `base64` content of the file upload.
`upload_filename` | The file name of the upload.

##### Success Response

  * **Status**: `200`
  * **Content**:
    ```json
    {
        "tenant_id": 1,
        "id": 1,
        "uuid": "357b7bdb-874a-4766-a9ad-177a01147868",
        "edition_date": "2012/03",
        "title": "Health Card Renewal",
        "form_number": "014-4297-82",
        "organization": "Ontario Government",
        "branch": "Health",
        "department": "Operational Support and Analysis",
        "program": "Operational Support and Analysis",
        "purpose": "Form is generated by client communication system to have people come in to renew photo health card",
        "country": "Canada",
        "province": "Ontario",
        "city": "",
        "search_text": "",
        "external_url": "",
        "template_file_url": "https://biometricscloud.nyc3.digitaloceanspaces.com/tenant/1/private/uploads/3fb39952-2d02-420b-ac9e-cb81edf4d7db-test.txt?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=ECYCCCUHLER27NMNI5OE%2F20220215%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20220215T053922Z&X-Amz-Expires=900&X-Amz-SignedHeaders=host&X-Amz-Signature=a262db5406f7aafc5fbecaec5a1aa18b4fd9e7280121c5a101bed6ce9ba069e6",
        "state": 1
    }
    ```

##### Error Response

  * **Status**: `400`
  * **Content**:
    ```json
    {
        "branch": "missing value",
        "country": "missing value",
        "edition_date": "missing value",
        "form_number": "missing value",
        "organization": "missing value",
        "purpose": "missing value",
        "title": "missing value",
        "upload_content": "missing value",
        "upload_filename": "missing value"
    }
    ```

##### Sample Call

Run the following in your terminal:

```shell
curl -X POST \
    -H "Content-Type: application/json" \
    -H "Authorization: Bearer VSvXrNLlQCeCdTJjGUJgKw" \
    -d '{"edition_date":"2012/03","title":"Health Card Renewal","form_number":"014-4297-82","organization":"Ontario Government","branch":"Health","department":"Operational Support and Analysis","program":"Operational Support and Analysis","purpose":"Form is generated by client communication system to have people come in to renew photo health card","country":"Canada","province":"Ontario","city":"","external_url":"", "upload_content":"VGhpcyBpcyBhIHRlc3QgdGV4dCBmaWxlLg==", "upload_filename":"test.txt"}' \
    https://biometricscloud.net/api/v1/document-requests
```

**OR**

```shell
curl -X POST \
    -H "Content-Type: application/json" \
    -H "Authorization: Bearer VSvXrNLlQCeCdTJjGUJgKw" \
    -d '{"edition_date":"2012/03","title":"Health Card Renewal","form_number":"014-4297-82","organization":"Ontario Government","branch":"Health","department":"Operational Support and Analysis","program":"Operational Support and Analysis","purpose":"Form is generated by client communication system to have people come in to renew photo health card","country":"Canada","province":"Ontario","city":"","external_url":"", "upload_content":"VGhpcyBpcyBhIHRlc3QgdGV4dCBmaWxlLg==", "upload_filename":"test.txt"}' \
    http://127.0.0.1:8000/api/v1/document-requests
```

##### Notes

* Please note the "file_url" will only be valid for 15 minutes and will expiry to become unavailable - you will need to call the retrieve endpoint to get a new "file_url".
* To give a sample document, please checkout [this URL](https://www.forms.ssb.gov.on.ca/mbs/ssb/forms/ssbforms.nsf/FormDetail?OpenForm&ACT=RDR&TAB=PROFILE&ENV=WWE&NO=014-4297-82).
* To generate base64 string from a file for testing, [try this link](https://base64.guru/converter/encode/file).

# **List Document Requests**
##### Description
This endpoint will return a list of medical records.

##### URL

`https://biometricscloud.net/api/v1/document-requests`

##### Method

`GET`

##### URL Params

Query Parameters | Description
--------- | -----------
`offset` | The `ID` of the record in the list which will be used as to filter any records less then this value.
`limit` | The maximum number of entries to return in the pagination.
`sort_order` | Either the `asc` (ascending) or `desc` (descending) order to return the results as.
`sort_field` | The column to sort by.

##### Required

None

##### Data Params

None

##### Success Response

  * **Status**: `200`
  * **Content**:
    ```json
    {
        "next_id": 10,
        "count": 1,
        "results": [
            {
                "tenant_id": 1,
                "id": 10,
                "uuid": "ea781bb1-bfe9-4ac4-a790-3119b65bb061",
                "edition_date": "2012/03",
                "title": "Health Card Renewal",
                "form_number": "014-4297-82",
                "organization": "Ontario Government",
                "branch": "Health",
                "department": "Operational Support and Analysis",
                "program": "Operational Support and Analysis",
                "purpose": "Form is generated by client communication system to have people come in to renew photo health card",
                "country": "Canada",
                "province": "Ontario",
                "city": "",
                "search_text": "",
                "external_url": "",
                "template_file_title": "test.txt",
                "state": 1
            }
        ]
    }
    ```

##### Sample Call

Run the following in your terminal:

```shell
curl "https://biometricscloud.net/api/v1/document-requests" \
    -H "Authorization: Bearer VSvXrNLlQCeCdTJjGUJgKw" \
    -H "Content-Type: application/json"
```

**OR**

```shell
curl "http://127.0.0.1:8000/api/v1/document-requests" \
    -H "Authorization: Bearer VSvXrNLlQCeCdTJjGUJgKw" \
    -H "Content-Type: application/json"
```

##### Notes

None

# **Retrieve Document Request**
##### Description
This endpoint will retrieve the medical record detail.

##### URL

`https://biometricscloud.net/api/v1/file/1`

##### Method

`GET`

##### URL Params

None

##### Required

None

##### Data Params

None

##### Success Response

  * **Status**: `200`
  * **Content**:
    ```json
    {
        "tenant_id": 1,
        "id": 10,
        "uuid": "ea781bb1-bfe9-4ac4-a790-3119b65bb061",
        "edition_date": "2012/03",
        "title": "Health Card Renewal",
        "form_number": "014-4297-82",
        "organization": "Ontario Government",
        "branch": "Health",
        "department": "Operational Support and Analysis",
        "program": "Operational Support and Analysis",
        "purpose": "Form is generated by client communication system to have people come in to renew photo health card",
        "country": "Canada",
        "province": "Ontario",
        "city": "",
        "search_text": "",
        "external_url": "",
        "template_file_url": "https://biometricscloud.nyc3.digitaloceanspaces.com/tenant/1/private/uploads/b5a5845f-7dfd-41ea-869b-9376a204d210-test.txt?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=ECYCCCUHLER27NMNI5OE%2F20220215%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20220215T055019Z&X-Amz-Expires=900&X-Amz-SignedHeaders=host&X-Amz-Signature=c8ea2ebc5b6696b5bbcd68352f84ef78bb1d671490f54c0d118161479dbeebb5",
        "state": 1
    }
    ```

##### Sample Call

Run the following in your terminal:

```shell
curl "https://biometricscloud.net/api/v1/document-request/1" \
    -H "Authorization: Bearer VSvXrNLlQCeCdTJjGUJgKw" \
    -H "Content-Type: application/json"
```

**OR**

```shell
curl "http://127.0.0.1:8000/api/v1/document-request/1" \
    -H "Authorization: Bearer VSvXrNLlQCeCdTJjGUJgKw" \
    -H "Content-Type: application/json"
```

##### Notes

None

# **Update Document Request**
##### Description
This endpoint will update the existing medical record.

##### URL

``PUT https://biometricscloud.net/api/v1/file/1``

##### Method

`PUT`

##### URL Params

None

##### Required

None

##### Data Params

Field | Required | Description
--------- | ----------- | -----------
`edition_date` | Yes | The document edition of the submission.
`title` | Yes | The name of the document.
`form_number` | Yes | The document ID that you want to assign to it.
`organization` | Yes | The organization that this document request belongs to.
`branch` | No | The branch of the organization.
`department` | No | The department of the branch.
`program` | No | The program that belongs.
`purpose` | Yes | The purpose of the document request.
`country` | No | The country that this document requests.
`province` | No | The province that this document belongs to.
`city` | No | The city that this belongs to.
`external_url` | No | Any external links this belongs to.
`upload_content` | The `base64` content of the image.
`upload_filename` | The file name of the image.
 
##### Success Response

  * **Status**: `200`
  * **Content**:
    ```json
    {
        "tenant_id": 1,
        "id": 10,
        "uuid": "ea781bb1-bfe9-4ac4-a790-3119b65bb061",
        "edition_date": "2012/03",
        "title": "Health Card Renewal",
        "form_number": "014-4297-82",
        "organization": "Ontario Government",
        "branch": "Health",
        "department": "Operational Support and Analysis",
        "program": "Operational Support and Analysis",
        "purpose": "Form is generated by client communication system to have people come in to renew photo health card",
        "country": "Canada",
        "province": "Ontario",
        "city": "",
        "search_text": "",
        "external_url": "",
        "template_file_url": "https://biometricscloud.nyc3.digitaloceanspaces.com/tenant/1/private/uploads/b5a5845f-7dfd-41ea-869b-9376a204d210-test.txt?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=ECYCCCUHLER27NMNI5OE%2F20220215%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20220215T055019Z&X-Amz-Expires=900&X-Amz-SignedHeaders=host&X-Amz-Signature=c8ea2ebc5b6696b5bbcd68352f84ef78bb1d671490f54c0d118161479dbeebb5",
        "state": 1
    }
    ```

##### Sample Call

Run the following in your terminal:

```shell
curl -X PUT \
    -H "Content-Type: application/json" \
    -H "Authorization: Bearer VSvXrNLlQCeCdTJjGUJgKw" \
    -d '{"edition_date":"2012/03","title":"Health Card Renewal","form_number":"014-4297-82","organization":"Ontario Government","branch":"Health","department":"Operational Support and Analysis","program":"Operational Support and Analysis","purpose":"Form is generated by client communication system to have people come in to renew photo health card","country":"Canada","province":"Ontario","city":"","external_url":"", "upload_content":"VGhpcyBpcyBhIHRlc3QgdGV4dCBmaWxlLg==", "upload_filename":"test.txt"}' \
    https://biometricscloud.net/api/v1/file/1
```

**OR**

```shell
curl -X PUT \
    -H "Content-Type: application/json" \
    -H "Authorization: Bearer VSvXrNLlQCeCdTJjGUJgKw" \
    -d '{"edition_date":"2012/03","title":"Health Card Renewal","form_number":"014-4297-82","organization":"Ontario Government","branch":"Health","department":"Operational Support and Analysis","program":"Operational Support and Analysis","purpose":"Form is generated by client communication system to have people come in to renew photo health card","country":"Canada","province":"Ontario","city":"","external_url":"", "upload_content":"VGhpcyBpcyBhIHRlc3QgdGV4dCBmaWxlLg==", "upload_filename":"test.txt"}' \
    http://127.0.0.1:8000/api/v1/file/1
```

##### Notes

None


# **Delete Document Request**
##### Description
This endpoint will archive the medical record; as a result.

##### URL

`https://biometricscloud.net/api/v1/file/1`

##### Method

`DELETE`

##### URL Params

None

##### Required

None

##### Data Params

None

##### Success Response

  * **Status**: `204`
  * **Content**: None

##### Sample Call

Run the following in your terminal:

```shell
curl -X DELETE "https://biometricscloud.net/api/v1/file/1" \
     -H "Authorization: Bearer VSvXrNLlQCeCdTJjGUJgKw"
```

**OR**

```shell
curl -X DELETE "http://127.0.0.1:8000/api/v1/file/1" \
     -H "Authorization: Bearer VSvXrNLlQCeCdTJjGUJgKw"
```

##### Notes

None