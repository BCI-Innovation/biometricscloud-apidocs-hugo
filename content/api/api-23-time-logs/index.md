---
title: 'Time Logs Endpoints'
date: 2019-02-11T19:27:37+10:00
draft: false
weight: 23
summary: "The retrieve endpoints for the diagnosis data."
---


# **Create Time Log**
##### Description
This endpoint will create note for an existing user.

##### URL

`https://bionotescloud.net/api/v1/time-logs`

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
#...
```

**OR**

```shell
curl -X POST \
    -H "Content-Type: application/json" \
    -H "Authorization: Bearer $BIOMETRICSCLOUD_ACCESS_TOKEN" \
    -d '{"user_id":2, "icd_10_code":"yellow-5","description":"This is a description.", "onset_date":"1990-01-01T00:00:00Z","interaction_date":"1990-01-01T00:00:00Z","notes":"These are some notes..."}' \
    http://127.0.0.1:8000/api/v1/time-logs
```

##### Time Logs

None

# **List Time Logs**
##### Description
This endpoint will return a list of notes that have granted permission to the current logged in user.

##### URL

`https://bionotescloud.net/api/v1/time-logs`

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
curl "http://127.0.0.1:8000/api/v1/time-logs" \
    -H "Authorization: Bearer $BIOMETRICSCLOUD_ACCESS_TOKEN" \
    -H "Content-Type: application/json"
```

##### Time Logs

None



# **Retrieve Time Log**
##### Description
This endpoint will Update note for an existing user.

##### URL

`https://bionotescloud.net/api/v1/time-log/1`

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
    https://bionotescloud.net/api/v1/time-log/1
```

**OR**

```shell
curl -X GET \
    -H "Content-Type: application/json" \
    -H "Authorization: Bearer $BIOMETRICSCLOUD_ACCESS_TOKEN" \
    http://127.0.0.1:8000/api/v1/diagnosis/1
```

##### Time Logs

None

# **Update Time Log**
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
    http://127.0.0.1:8000/api/v1/time-log/1
```

##### Time Logs

None


<!-- # **Delete Time Log**
##### Description
xxxx

##### URL

`https://bionotescloud.net/api/v1/time-log/1`

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
curl -X DELETE "https://bionotescloud.net/api/v1/time-log/1" \
     -H "Authorization: Bearer $BIOMETRICSCLOUD_ACCESS_TOKEN"
```

**OR**

```shell
curl -X DELETE "http://127.0.0.1:8000/api/v1/time-log/1" \
     -H "Authorization: Bearer $BIOMETRICSCLOUD_ACCESS_TOKEN"
```

##### Time Logs

None -->
