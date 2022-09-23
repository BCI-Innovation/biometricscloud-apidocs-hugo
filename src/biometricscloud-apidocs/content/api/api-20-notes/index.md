---
title: 'Notes Endpoints'
date: 2019-02-11T19:27:37+10:00
draft: false
weight: 20
summary: "The retrieve endpoints for the notes data."
---


# **Create Note**
##### Description
This endpoint will create note for an existing user.

##### URL

`https://bionotescloud.net/api/v1/notes`

##### Method

`POST`

##### URL Params

None

##### Data Params

Field | Required | Example | Description
--------- | ----------- | ----------- | -----------
`category` | Yes | Medical | The custom text to categorize the note by.
`content` | Yes | This is a note. | The content of the first note
`state` | Yes | 1 | The state of the note. Options 1, 2, 3, 4. (See notes below)
`title` | Yes | Example Note | The title for this note.
`user_id` | Yes | 2 | The user to attach this note to.
`tenant_id` | Yes | 2 | The organization to attach this note to. How do you know what organizations the patient belongs to? Please see [TODO API]().

##### Success Response

  * **Status**: `200`
  * **Content**:
    ```json
    {
        "id": 1,
        "uuid": "dfc40a05-79e1-4c31-81ef-1e7cc3374afb",
        "tenant_id": 2,
        "user_id": 2,
        "title": "HealthKit",
        "category": "HealthKit",
        "state": 1,
        "created_by_user_id": 1,
        "created_by_name_name": "Frank Herbert",
        "created_time": "2022-09-22T23:25:39.354877Z",
        "modified_by_user_id": 1,
        "modified_by_name_name": "Frank Herbert",
        "modified_time": "2022-09-22T23:25:39.354878Z",
        "note_items": [
            {
                "id": 1,
                "uuid": "28b2341c-e3e5-4804-bc77-db82c427ed87",
                "tenant_id": 2,
                "note_id": 1,
                "user_id": 2,
                "title": "HealthKit",
                "content": "Data is missing!",
                "move_index": 1,
                "state": 1,
                "created_by_user_id": 1,
                "created_by_name_name": "Frank Herbert",
                "created_time": "2022-09-22T23:25:39.41477Z",
                "modified_by_user_id": 1,
                "modified_by_name_name": "Frank Herbert",
                "modified_time": "2022-09-22T23:25:39.414771Z"
            }
        ]
    }
    ```

##### Sample Call

Run the following in your terminal:

```shell
curl -X POST \
    -H "Content-Type: application/json" \
    -H "Authorization: Bearer $BIOMETRICSCLOUD_ACCESS_TOKEN" \
    -d '{"title":"Test Note #1","content":"This is a test.", "state":1, "user_id":"2","tenant_id":"2"}' \
    https://bionotescloud.net/api/v1/notes
```

**OR**

```shell
curl -X POST \
    -H "Content-Type: application/json" \
    -H "Authorization: Bearer $BIOMETRICSCLOUD_ACCESS_TOKEN" \
    -d '{"title":"Test Note #1","content":"This is a test.", "state":1, "user_id":"2","tenant_id":"2"}' \
    http://127.0.0.1:8000/api/v1/notes
```

##### Notes

* state `1` = Patient and clinician can see the note.
* state `2` = Patient cannot see but clinician can.
* state `3` = Patient cannot see and archived by clinician.
* state `4` = Patient can see but archived by clinician.

# **List Notes**
##### Description
This endpoint will return a list of notes based on the logged in user role of organization staff or client (aka patient).

**Patient**
If logged in use is patient then this endpoint will return all the notes that belong to the user across all the organizations.

**Staff**
If logged in as an organization staff member then this endpoint will return all the notes that belong to the specific organization. The staff member can filter down notes of a specific user by using the `user_id` URL parameter filter.

##### URL

`https://bionotescloud.net/api/v1/notes`

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
`user_id` | Apply filter to only return notes belong to the user with this `user_id` value.

##### Required

None

##### Data Params

None

##### Success Response

  * **Status**: `200`
  * **Content**:
    ```json
    {
        "next_offset": 1,
        "count": 1,
        "results": [
            {
                "id": 1,
                "uuid": "dfc40a05-79e1-4c31-81ef-1e7cc3374afb",
                "tenant_id": 2,
                "user_id": 2,
                "title": "HealthKit",
                "content": "Data is missing!",
                "category": "HealthKit",
                "state": 1,
                "created_by_user_id": 1,
                "created_by_name_name": "Frank Herbert",
                "created_time": "2022-09-22T23:25:39.354877Z",
                "modified_by_user_id": 1,
                "modified_by_name_name": "Frank Herbert",
                "modified_time": "2022-09-22T23:25:39.354878Z"
            }
        ]
    }
    ```

##### Sample Call

Run the following in your terminal:

```shell
curl "https://bionotescloud.net/api/v1/notes" \
    -H "Authorization: Bearer $BIOMETRICSCLOUD_ACCESS_TOKEN" \
    -H "Content-Type: application/json"
```

**OR**

```shell
curl "http://127.0.0.1:8000/api/v1/notes" \
    -H "Authorization: Bearer $BIOMETRICSCLOUD_ACCESS_TOKEN" \
    -H "Content-Type: application/json"
```

##### Notes

None

# **Retrieve Note**
##### Description
This endpoint will return the full note thread for an existing user. This API endpoint is available to both organization staff member and the client as long as they both belong to the correct organization.

##### URL

`https://bionotescloud.net/api/v1/note/1`

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
        "id": 1,
        "uuid": "dfc40a05-79e1-4c31-81ef-1e7cc3374afb",
        "tenant_id": 2,
        "user_id": 2,
        "title": "HealthKit",
        "content": "Data is missing!",
        "category": "HealthKit",
        "state": 1,
        "created_by_user_id": 1,
        "created_by_name_name": "Frank Herbert",
        "created_time": "2022-09-22T23:25:39.354877Z",
        "modified_by_user_id": 1,
        "modified_by_name_name": "Frank Herbert",
        "modified_time": "2022-09-22T23:25:39.354878Z",
        "note_items": [
            {
                "id": 1,
                "uuid": "28b2341c-e3e5-4804-bc77-db82c427ed87",
                "tenant_id": 2,
                "note_id": 1,
                "user_id": 2,
                "title": "HealthKit",
                "content": "Data is missing!",
                "move_index": 1,
                "state": 1,
                "created_by_user_id": 1,
                "created_by_name_name": "Frank Herbert",
                "created_time": "2022-09-22T23:25:39.41477Z",
                "modified_by_user_id": 1,
                "modified_by_name_name": "Frank Herbert",
                "modified_time": "2022-09-22T23:25:39.414771Z"
            }
        ]
    }
    ```

##### Sample Call

Run the following in your terminal:

```shell
curl -X GET \
    -H "Content-Type: application/json" \
    -H "Authorization: Bearer $BIOMETRICSCLOUD_ACCESS_TOKEN" \
    https://bionotescloud.net/api/v1/note/1
```

**OR**

```shell
curl -X GET \
    -H "Content-Type: application/json" \
    -H "Authorization: Bearer $BIOMETRICSCLOUD_ACCESS_TOKEN" \
    http://127.0.0.1:8000/api/v1/note/1
```

##### Notes

None

# **Update Note**
##### Description
This endpoint will Update note for an existing user.

##### URL

`https://bionotescloud.net/api/v1/note/1`

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
curl -X PUT \
    -H "Content-Type: application/json" \
    -H "Authorization: Bearer $BIOMETRICSCLOUD_ACCESS_TOKEN" \
    -d '{"title":"Test Note #1","content":"This is a yet another test.", "state":1}' \
    https://bionotescloud.net/api/v1/note/1
```

**OR**

```shell
curl -X PUT \
    -H "Content-Type: application/json" \
    -H "Authorization: Bearer $BIOMETRICSCLOUD_ACCESS_TOKEN" \
    -d '{"title":"Test Note #1","content":"This is a yet another test.", "state":1}' \
    http://127.0.0.1:8000/api/v1/note/1
```

##### Notes

None









# **Delete Note**
##### Description
This endpoint will sever the link between the logged in user (ex: Clinician) and the client.

##### URL

`https://bionotescloud.net/api/v1/client/1`

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
curl -X DELETE "https://bionotescloud.net/api/v1/client/1" \
     -H "Authorization: Bearer $BIOMETRICSCLOUD_ACCESS_TOKEN"
```

**OR**

```shell
curl -X DELETE "http://127.0.0.1:8000/api/v1/client/1" \
     -H "Authorization: Bearer $BIOMETRICSCLOUD_ACCESS_TOKEN"
```

##### Notes

None
