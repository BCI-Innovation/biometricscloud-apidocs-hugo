---
title: 'Workout Exercise Endpoints'
date: 2019-02-11T19:27:37+10:00
draft: false
weight: 14
summary: "The retrieve endpoints for the workout exercise data."
---


# **Create Workout Exercise**
##### Description
This endpoint will create workout exercise for an existing user.

##### URL

`https://bionotescloud.net/api/v1/workout-exercises`

##### Method

`POST`

##### URL Params

None

##### Data Params

Field | Required | Example | Description
--------- | ----------- | ----------- | -----------
user_id | Yes | 1 | The user account that this workout belongs to.
name | Yes | Day 1 Workout | The name of this account.
type | Yes | 1 | The type of workout. Values: "regular" = `1`, "circuit" = `2`, "interval" = `3` and "video" = `4`.

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
    -d '{"user_id":1, "name":"xxx","Type":"1"}' \
    https://biometricsclouds.net/api/v1/workout-exercises
```

**OR**

```shell
curl -X POST \
    -H "Content-Type: application/json" \
    -H "Authorization: Bearer $BIOMETRICSCLOUD_ACCESS_TOKEN" \
    -d '{"user_id":1, "name":"xxx","Type":"1"}' \
    http://127.0.0.1:8000/api/v1/workout-exercises
```

##### Workouts

None

# **List Workouts**
##### Description
This endpoint will return a list of notes that have granted permission to the current logged in user.

##### URL

`https://bionotescloud.net/api/v1/workouts`

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
# ...
```

**OR**

```shell
curl "http://127.0.0.1:8000/api/v1/workouts" \
    -H "Authorization: Bearer $BIOMETRICSCLOUD_ACCESS_TOKEN" \
    -H "Content-Type: application/json"
```

##### Workouts

None



# **Retrieve Workout**
##### Description
This endpoint will Update note for an existing user.

##### URL

`https://bionotescloud.net/api/v1/workout/1`

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
    https://bionotescloud.net/api/v1/workout/1
```

**OR**

```shell
curl -X GET \
    -H "Content-Type: application/json" \
    -H "Authorization: Bearer $BIOMETRICSCLOUD_ACCESS_TOKEN" \
    http://127.0.0.1:8000/api/v1/diagnosis/1
```

##### Workouts

None

# **Update Workout**
##### Description
This endpoint will Update note for an existing user.

##### URL

`https://bionotescloud.net/api/v1/diagnosis/1`

##### Method

`POST`

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

```

**OR**

```shell
curl -X PUT \
    -H "Content-Type: application/json" \
    -H "Authorization: Bearer $BIOMETRICSCLOUD_ACCESS_TOKEN" \
    -d '{"user_id":2, "type":"initial meeting","duration_in_minutes":15, "session_time":"1990-01-01T00:00:00Z","start_time":"1990-01-01T00:00:00Z","end_time":"1990-01-01T00:00:00Z","is_myself":false,"praticitionar_name":"Bob Page","notes":"These are some notes..."}' \
    http://127.0.0.1:8000/api/v1/workout/1
```

##### Workouts

None


<!-- # **Delete Workout**
##### Description
xxxx

##### URL

`https://bionotescloud.net/api/v1/workout/1`

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
curl -X DELETE "https://bionotescloud.net/api/v1/workout/1" \
     -H "Authorization: Bearer $BIOMETRICSCLOUD_ACCESS_TOKEN"
```

**OR**

```shell
curl -X DELETE "http://127.0.0.1:8000/api/v1/workout/1" \
     -H "Authorization: Bearer $BIOMETRICSCLOUD_ACCESS_TOKEN"
```

##### Workouts

None -->
