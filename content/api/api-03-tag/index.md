---
title: 'Tag Endpoints'
date: 2019-02-11T19:27:37+10:00
draft: false
weight: 5
summary: "CRUD endpoints pertaining Tags."
---
The following endpoints provide CRUD operations on our Tags.


# **Create Tag**
##### Description
xxx

##### URL

`https://biometricscloud.net/api/v1/tags`

##### Method

`POST`

##### URL Params

None

##### Data Params

Field | Required | Example | Description
--------- | ----------- | ----------- | -----------
`text` | Yes | Martial Arts Trainer | The name of the tag.

##### Success Response

  * **Status**: `200`
  * **Content**:
    ```json
    {
        "id": 1,
        "uuid": "099b0948-693e-4209-88c6-0703db4a3d45",
        "tenant_id": 1,
        "text": "Martial Arts Trainer",
        "created_time": "2022-09-07T16:56:49.617358Z",
        "created_by_user_id": 1,
        "created_by_user_name": "Frank Herbert",
        "modified_by_user_id": 1,
        "modified_by_user_name": "Frank Herbert",
        "modified_time": "2022-09-07T16:56:49.617358Z"
    }
    ```

##### Sample Call

Run the following in your terminal:

```shell
curl -X POST \
    -H "Content-Type: application/json" \
    -H "Authorization: Bearer $BIOMETRICSCLOUD_ACCESS_TOKEN" \
    -d '{"text":"Healthy"}' \
    https://biometricscloud.net/api/v1/tags
```

**OR**

```shell
curl -X POST \
    -H "Content-Type: application/json" \
    -H "Authorization: Bearer $BIOMETRICSCLOUD_ACCESS_TOKEN" \
    -d '{"text":"Healthy"}' \
    http://127.0.0.1:8000/api/v1/tags
```

##### Notes

**IMPORTANT:** Please save the `client_id`, `client_secret` and `redirect_url` values as you will not be getting them again. If you lose these values then you will need to create a new Tag and delete the existing one.

# **List Tags**
##### Description
This endpoint will return a list of Tags.

##### URL

`https://biometricscloud.net/api/v1/tags`

##### Method

`GET`

##### URL Params

Query Parameters | Required | Default Value | Description
--------- | ----------- | ----------- | -----------
`offset` | No | 0 | The `ID` of the record in the list which will be used as to filter any records less then this value.
`limit` | No | 100 | The maximum number of entries to return in the pagination.
`sort_order` | No| asc | Either the `asc` (ascending) or `desc` (descending) order to return the results as.
`sort_field` | No| id | The column to sort by.

##### Data Params

None

##### Success Response

  * **Status**: `200`
  * **Content**:
    ```json
    {
        "next_id": 2,
        "count": 2,
        "results": [
            {
                "id": 1,
                "manufacturer": "Apple",
                "code": "iPhone1,1",
                "product_name": "iPhone",
                "state": 1
            },
            {
                "id": 2,
                "manufacturer": "Apple",
                "code": "Watch1,1",
                "product_name": "Apple Watch 38mm case",
                "state": 1
            }
        ]
    }
    ```

##### Sample Call

Run the following in your terminal:

```shell
curl "https://biometricscloud.net/api/v1/tags" \
    -H "Authorization: Bearer $BIOMETRICSCLOUD_ACCESS_TOKEN" \
    -H "Content-Type: application/json"
```

**OR**

```shell
curl "http://127.0.0.1:8000/api/v1/tags" \
    -H "Authorization: Bearer $BIOMETRICSCLOUD_ACCESS_TOKEN" \
    -H "Content-Type: application/json"
```

##### Notes

None

# **Retrieve Tag**
##### Description
This endpoint will retrieve the Tag detail.

##### URL

`https://biometricscloud.net/api/v1/tag/1`

##### Method

`GET`

##### URL Params

Query Parameters | Required | Default Value | Description
--------- | ----------- | ----------- | -----------
`tag_id` | Yes  | - | The Tag identification that belongs to the user.

##### Data Params

None

##### Success Response

  * **Status**: `200`
  * **Content**:
    ```json
    {
        "id": 1,
        "uuid": "099b0948-693e-4209-88c6-0703db4a3d45",
        "tenant_id": 1,
        "text": "Martial Arts Trainer",
        "created_time": "2022-09-07T16:56:49.617358Z",
        "created_by_user_id": 1,
        "created_by_user_name": "Frank Herbert",
        "modified_by_user_id": 1,
        "modified_by_user_name": "Frank Herbert",
        "modified_time": "2022-09-07T16:56:49.617358Z"
    }
    ```

##### Sample Call

Run the following in your terminal:

```shell
curl "https://biometricscloud.net/api/v1/tag/1" \
    -H "Authorization: Bearer $BIOMETRICSCLOUD_ACCESS_TOKEN" \
    -H "Content-Type: application/json"
```

**OR**


```shell
curl "http://localhost:8000/api/v1/tag/1" \
    -H "Authorization: Bearer $BIOMETRICSCLOUD_ACCESS_TOKEN" \
    -H "Content-Type: application/json"
```

##### Notes

None


# **Delete Tag**
##### Description
This endpoint will disconnect/disable the Tag. To reconnect the Tag, please see the [Tag authorize](#Tag-authorization) endpoint.

##### URL

`https://biometricscloud.net/api/v1/data-submission/Tag-authorize`

##### Method

`DELETE`

##### URL Params

Query Parameters | Required | Default Value | Description
--------- | ----------- | ----------- | -----------
`Tag_id` | Yes  | - | The Tag identification that belongs to the user.

##### Data Params

None

##### Success Response

  * **Status**: `204`
  * **Content**: None

##### Sample Call

Run the following in your terminal:

```shell
curl -X DELETE "https://biometricscloud.net/api/v1/tag/1" \
     -H "Authorization: Bearer $BIOMETRICSCLOUD_ACCESS_TOKEN"
```

**OR**

```shell
curl -X DELETE "http://127.0.0.1:8000/api/v1/tag/1" \
     -H "Authorization: Bearer $BIOMETRICSCLOUD_ACCESS_TOKEN"
```

##### Notes

None
