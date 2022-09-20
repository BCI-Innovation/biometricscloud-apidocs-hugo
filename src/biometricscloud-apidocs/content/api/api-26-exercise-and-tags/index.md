---
title: 'Exercise Endpoints'
date: 2019-02-11T19:27:37+10:00
draft: false
weight: 26
summary: ""
---


# **List Exercises**
##### Description
This endpoint will return a list of exercises.

##### URL

`https://bioexercisescloud.net/api/v1/exercises`

##### Method

`GET`

##### URL Params

Query Parameters | Description
--------- | -----------
`offset` | The `ID` of the record in the list which will be used as to filter any records less then this value.
`limit` | The maximum number of entries to return in the pagination.
`sort_order` | Either the `asc` (ascending) or `desc` (descending) order to return the results as.
`sort_field` | The column to sort by.
`tag_search` | The keywords to search the tags through. Ex: `mainMuscle`.

##### Required

None

##### Data Params

None

##### Success Response

  * **Status**: `200`
  * **Content**:
    ```json
    {}
    ```

##### Sample Call

Run the following in your terminal:

```shell
curl "https://bioexercisescloud.net/api/v1/exercises" \
    -H "Authorization: Bearer $BIOMETRICSCLOUD_ACCESS_TOKEN" \
    -H "Content-Type: application/json"
```

**OR**

```shell
curl "http://127.0.0.1:8000/api/v1/exercises" \
    -H "Authorization: Bearer $BIOMETRICSCLOUD_ACCESS_TOKEN" \
    -H "Content-Type: application/json"
```

##### Exercises

None

# **Retrieve Exercise**
##### Description
This endpoint will Update exercise for an existing user.

##### URL

`https://bioexercisescloud.net/api/v1/exercise/1`

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
    https://bioexercisescloud.net/api/v1/exercise/1
```

**OR**

```shell
curl -X GET \
    -H "Content-Type: application/json" \
    -H "Authorization: Bearer $BIOMETRICSCLOUD_ACCESS_TOKEN" \
    http://127.0.0.1:8000/api/v1/exercise/1
```

##### Exercises

None

# **List Exercise Tags**
##### Description
This endpoint will return a list of exercise tags.

##### URL

`https://bioexercisescloud.net/api/v1/exercise-tags`

##### Method

`GET`

##### URL Params

Query Parameters | Description
--------- | -----------
`offset` | The `ID` of the record in the list which will be used as to filter any records less then this value.
`limit` | The maximum number of entries to return in the pagination.
`sort_order` | Either the `asc` (ascending) or `desc` (descending) order to return the results as.
`sort_field` | The column to sort by.
`type` | The `type` filter to the results by. Example: `mainMuscle` or `equipment`.

##### Required

None

##### Data Params

None

##### Success Response

  * **Status**: `200`
  * **Content**:
    ```json
    {}
    ```

##### Sample Call

Run the following in your terminal:

```shell
curl "https://bioexercisescloud.net/api/v1/exercise-tags" \
    -H "Authorization: Bearer $BIOMETRICSCLOUD_ACCESS_TOKEN" \
    -H "Content-Type: application/json"
```

**OR**

```shell
curl "http://127.0.0.1:8000/api/v1/exercise-tags" \
    -H "Authorization: Bearer $BIOMETRICSCLOUD_ACCESS_TOKEN" \
    -H "Content-Type: application/json"
```

##### Exercises

None
