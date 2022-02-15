---
title: 'File Endpoints'
date: 2019-02-11T19:27:37+10:00
draft: false
weight: 16
summary: "The CRUD endpoints pertaining to files."
---

Perform storage operations (ex: Save, Retrieve, etc) of user medical records.

# **Create File**
##### Description
This endpoint will create a medical record with the file saved to the remote file server.

##### URL

`https://biometricscloud.net/api/v1/files`

##### Method

`POST`

##### URL Params

None

##### Required

None

##### Data Params

Field | Description
--------- | -----------
`description` | The description of the medical record.
type | The type of medical record this is. Options: (1) Medical (2) Dental (3) Hospital/Specialist (4) Pharmacy (5) Other.
`upload_content` | The `base64` content of the image.
`upload_filename` | The file name of the image.

##### Success Response

  * **Status**: `200`
  * **Content**:
    ```json
    {
        "description": "This is a sample record",
        "type": 1,
        "state": 1,
        "file_name": "lalal.png",
        "file_url": "https://ipreqnancy-qa.nyc3.digitaloceanspaces.com/tenant/1/private/uploads/07b90d0b-07c4-4dfb-a9da-459d647c18e9-lalal.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=ECYCCCUHLER27NMNI5OE%2F20220130%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20220130T052448Z&X-Amz-Expires=900&X-Amz-SignedHeaders=host&X-Amz-Signature=21b2bded890fa5be5122a2804de170844f56ed47c54985ed14780740a6429e50"
    }
    ```

##### Sample Call

Run the following in your terminal:

```shell
curl -X POST \
    -H "Content-Type: application/json" \
    -H "Authorization: Bearer VSvXrNLlQCeCdTJjGUJgKw" \
    -d '{"description":"This is a sample record","type":1,"upload_content":"xyz","upload_filename":"lalal.png"}
' \
    https://biometricscloud.net/api/v1/files
```

**OR**

```shell
curl -X POST \
    -H "Content-Type: application/json" \
    -H "Authorization: Bearer VSvXrNLlQCeCdTJjGUJgKw" \
    -d '{"description":"This is a sample record","type":1,"upload_content":"xyz","upload_filename":"lalal.png"}
' \
    http://127.0.0.1:8000/api/v1/files
```

##### Notes

* Please note the "file_url" will only be valid for 15 minutes and will expiry to become unavailable - you will need to call the retrieve endpoint to get a new "file_url".

# **List Files**
##### Description
This endpoint will return a list of medical records.

##### URL

`https://biometricscloud.net/api/v1/files`

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
        "next_id": 3,
        "count": 1,
        "results": [
            {
                "id": 3,
                "uuid": "5fe0f10d-cb3c-4232-9f61-5e1b5b1c8f2c",
                "tenant_id": 1,
                "user_id": 1,
                "description": "This is a sample record",
                "type": 1,
                "state": 1,
                "created_time": "2022-01-30T00:24:48.259289-05:00",
                "file_name": "lalal.png"
            }
        ]
    }
    ```

##### Sample Call

Run the following in your terminal:

```shell
curl "https://biometricscloud.net/api/v1/files" \
    -H "Authorization: Bearer VSvXrNLlQCeCdTJjGUJgKw" \
    -H "Content-Type: application/json"
```

**OR**

```shell
curl "http://127.0.0.1:8000/api/v1/files" \
    -H "Authorization: Bearer VSvXrNLlQCeCdTJjGUJgKw" \
    -H "Content-Type: application/json"
```

##### Notes

None

# **Retrieve File**
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
        "description": "This is a sample record",
        "type": 1,
        "state": 1,
        "file_name": "lalal.png",
        "file_url": "https://ipreqnancy-qa.nyc3.digitaloceanspaces.com/tenant/1/private/uploads/07b90d0b-07c4-4dfb-a9da-459d647c18e9-lalal.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=ECYCCCUHLER27NMNI5OE%2F20220130%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20220130T055123Z&X-Amz-Expires=900&X-Amz-SignedHeaders=host&X-Amz-Signature=95ef70ae19e5a93716e264a67f1cece09ed873bde6631ed615523dc699d86e2b"
    }
    ```

##### Sample Call

Run the following in your terminal:

```shell
curl "https://biometricscloud.net/api/v1/file/1" \
    -H "Authorization: Bearer VSvXrNLlQCeCdTJjGUJgKw" \
    -H "Content-Type: application/json"
```

**OR**

```shell
curl "http://127.0.0.1:8000/api/v1/file/1" \
    -H "Authorization: Bearer VSvXrNLlQCeCdTJjGUJgKw" \
    -H "Content-Type: application/json"
```

##### Notes

None

# **Update File**
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

Field | Description
--------- | -----------
`description` | The description of the medical record.
`type` | The type of medical record this is. Options: (1) Medical (2) Dental (3) Hospital/Specialist (4) Pharmacy (5) Other.
`upload_filename` | The file name of the image.

##### Success Response

  * **Status**: `200`
  * **Content**:
    ```json
    {
        "description": "This is a sample record",
        "type": 1,
        "state": 1,
        "file_name": "lalal.png",
        "file_url": "https://ipreqnancy-qa.nyc3.digitaloceanspaces.com/tenant/1/private/uploads/07b90d0b-07c4-4dfb-a9da-459d647c18e9-lalal.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=ECYCCCUHLER27NMNI5OE%2F20220130%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20220130T055123Z&X-Amz-Expires=900&X-Amz-SignedHeaders=host&X-Amz-Signature=95ef70ae19e5a93716e264a67f1cece09ed873bde6631ed615523dc699d86e2b"
    }
    ```

##### Sample Call

Run the following in your terminal:

```shell
curl -X PUT \
    -H "Content-Type: application/json" \
    -H "Authorization: Bearer VSvXrNLlQCeCdTJjGUJgKw" \
    -d '{"description":"This is a sample record","type":1,"upload_filename":"lalal.png"}' \
    https://biometricscloud.net/api/v1/file/1
```

**OR**

```shell
curl -X PUT \
    -H "Content-Type: application/json" \
    -H "Authorization: Bearer VSvXrNLlQCeCdTJjGUJgKw" \
    -d '{"description":"This is a sample record","type":1,"upload_filename":"lalal.png"}' \
    http://127.0.0.1:8000/api/v1/file/1
```

##### Notes

None


# **Delete File**
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
