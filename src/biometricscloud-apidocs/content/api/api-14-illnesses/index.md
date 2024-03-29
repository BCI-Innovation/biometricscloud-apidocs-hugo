---
title: 'Illness Endpoints'
date: 2019-02-11T19:27:37+10:00
draft: false
weight: 14
summary: "The retrieve endpoints for the illness data."
---

# **List Illnesses**
##### Description
This endpoint will return a list of illnesses tracked by the system.

##### URL

`https://biometricscloud.net/api/v1/illnesses`

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
        "count": 3,
        "results": [
            {
                "id": 1,
                "text": "Abdominal aortic aneurysm"
            },
            {
                "id": 2,
                "text": "Acne"
            },
            {
                "id": 3,
                "text": "Acute cholecystitis"
            }
        ]
    }
    ```

##### Sample Call

Run the following in your terminal:

```shell
curl "https://biometricscloud.net/api/v1/illnesses" \
    -H "Authorization: Bearer $BIOMETRICSCLOUD_ACCESS_TOKEN" \
    -H "Content-Type: application/json"
```

**OR**

```shell
curl "http://127.0.0.1:8000/api/v1/illnesses" \
    -H "Authorization: Bearer $BIOMETRICSCLOUD_ACCESS_TOKEN" \
    -H "Content-Type: application/json"
```

##### Notes

None

# **Create User-Illness**
##### Description
This endpoint will create user-illness for an existing user.

##### URL

`https://bionotescloud.net/api/v1/user-illnesses`

##### Method

`POST`

##### URL Params

None

##### Data Params

Field | Required | Example | Description
--------- | ----------- | ----------- | -----------
illness_id | Yes | 1 | The id of the illness.
user_id | Yes | 1 | The id of the user.

##### Success Response

  * **Status**: `200`
  * **Content**:
    ```json
    {
    }
    ```

##### Sample Call

Run the following in your terminal:

```shell
curl -X POST \
    -H "Content-Type: application/json" \
    -H "Authorization: Bearer $BIOMETRICSCLOUD_ACCESS_TOKEN" \
    -d '{"illness_id":"1","user_id":"1"}' \
    https://bionotescloud.net/api/v1/user-illnesses
```

**OR**

```shell
curl -X POST \
    -H "Content-Type: application/json" \
    -H "Authorization: Bearer $BIOMETRICSCLOUD_ACCESS_TOKEN" \
    -d '{"illness_id":"1","user_id":"1"}' \
    http://127.0.0.1:8000/api/v1/user-illnesses
```

##### Notes

None


# **List User Illness**
##### Description
This endpoint will return a list of user illnesses that have granted permission to the current logged in user.

##### URL

`https://bionotescloud.net/api/v1/user-illnesses`

##### Method

`GET`

##### URL Params

Query Parameters | Description
--------- | -----------
`offset` | The `ID` of the record in the list which will be used as to filter any records less then this value.
`limit` | The maximum number of entries to return in the pagination.
`sort_order` | Either the `asc` (ascending) or `desc` (descending) order to return the results as.
`sort_field` | The column to sort by.
`search` | The keywords to search through.

##### Required

None

##### Data Params

None

##### Success Response

  * **Status**: `200`
  * **Content**:
    ```json

    ```

##### Sample Call

Run the following in your terminal:

```shell
curl "https://bionotescloud.net/api/v1/user-illnesses" \
    -H "Authorization: Bearer $BIOMETRICSCLOUD_ACCESS_TOKEN" \
    -H "Content-Type: application/json"
```

**OR**

```shell
curl "http://127.0.0.1:8000/api/v1/user-illnesses" \
    -H "Authorization: Bearer $BIOMETRICSCLOUD_ACCESS_TOKEN" \
    -H "Content-Type: application/json"
```

##### Notes

None

# **Retrieve User Illness**
##### Description
This endpoint will get user illness for an existing user.

##### URL

`https://bionotescloud.net/api/v1/user-illness/1`

##### Method

`GET`

##### URL Params

None

##### Data Params

Field | Required | Example | Description
--------- | ----------- | ----------- | -----------


##### Success Response

  * **Status**: `200`
  * **Content**:
    ```json
    {
    }
    ```

##### Sample Call

Run the following in your terminal:

```shell
curl -X GET \
    -H "Content-Type: application/json" \
    -H "Authorization: Bearer $BIOMETRICSCLOUD_ACCESS_TOKEN" \
    https://bionotescloud.net/api/v1/user-illness/1
```

**OR**

```shell
curl -X GET \
    -H "Content-Type: application/json" \
    -H "Authorization: Bearer $BIOMETRICSCLOUD_ACCESS_TOKEN" \
    http://127.0.0.1:8000/api/v1/user-illness/1
```

##### Notes

None

# **Update User Illness**
##### Description
This endpoint will update user illness for an existing user.

##### URL

`https://bionotescloud.net/api/v1/user-illness/1`

##### Method

`PUT`

##### URL Params

None

##### Data Params

Field | Required | Example | Description
--------- | ----------- | ----------- | -----------
illness_id | Yes | 1 | The id of the illness.
user_id | Yes | 1 | The id of the user.

##### Success Response

  * **Status**: `200`
  * **Content**:
    ```json
    {
    }
    ```

##### Sample Call

Run the following in your terminal:

```shell
curl -X PUT \
    -H "Content-Type: application/json" \
    -H "Authorization: Bearer $BIOMETRICSCLOUD_ACCESS_TOKEN" \
    -d '{"illness_id":"1","user_id":"1"}' \
    https://bionotescloud.net/api/v1/user-illness/1
```

**OR**

```shell
curl -X PUT \
    -H "Content-Type: application/json" \
    -H "Authorization: Bearer $BIOMETRICSCLOUD_ACCESS_TOKEN" \
    -d '{"illness_id":"1","user_id":"1"}' \
    http://127.0.0.1:8000/api/v1/user-illness/1
```

##### Notes

None


# **Delete Note**
##### Description
-

##### URL

`https://bionotescloud.net/api/v1/user-illness/1`

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
curl -X DELETE "https://bionotescloud.net/api/v1/user-illness/1" \
     -H "Authorization: Bearer $BIOMETRICSCLOUD_ACCESS_TOKEN"
```

**OR**

```shell
curl -X DELETE "http://127.0.0.1:8000/api/v1/user-illness/1" \
     -H "Authorization: Bearer $BIOMETRICSCLOUD_ACCESS_TOKEN"
```

##### Notes

None
