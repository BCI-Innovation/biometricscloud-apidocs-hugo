---
title: 'Note Items Endpoints'
date: 2019-02-11T19:27:37+10:00
draft: false
weight: 21
summary: "The retrieve endpoints for the notes data."
---


# **Create Note Item**
##### Description
This endpoint will create note item for an existing note.

##### URL

`https://bionotescloud.net/api/v1/note-items`

##### Method

`POST`

##### URL Params

None

##### Data Params

Field | Required | Example | Description
--------- | ----------- | ----------- | -----------
`note_id` | Yes | 1 | The ID of the note that this note item belongs to.
`content` | Yes | This is a note. | The content of the first `note_item`.
`state` | Yes | 1 | The state of the note. Options `1`, `2`, `3`, `4`. (See below)
`move_index` | Yes | 1 | The order position that this note belongs to.


##### Success Response

  * **Status**: `200`
  * **Content**:
    ```json
    {
        "id": 1,
        "uuid": "1d1fd475-bff2-42bc-bcab-45ac0798295b",
        "tenant_id": 2,
        "note_id": 1,
        "user_id": 2,
        "content": "This is a test comment.",
        "move_index": 1,
        "state": 4,
        "created_by_user_id": 1,
        "created_by_name_name": "Frank Herbert",
        "created_time": "2022-09-23T01:58:24.898176Z",
        "modified_by_user_id": 1,
        "modified_by_name_name": "Frank Herbert",
        "modified_time": "2022-09-23T04:39:32.211117Z"
    }
    ```

##### Sample Call

Run the following in your terminal:

```shell
curl -X POST \
    -H "Content-Type: application/json" \
    -H "Authorization: Bearer $BIOMETRICSCLOUD_ACCESS_TOKEN" \
    -d '{"note_id":1, "move_index":1, "title":"Note Item Hello World", "content":"This is a note item.", "state":1}' \
    https://bionotescloud.net/api/v1/note-items
```

**OR**

```shell
curl -X POST \
    -H "Content-Type: application/json" \
    -H "Authorization: Bearer $BIOMETRICSCLOUD_ACCESS_TOKEN" \
    -d '{"note_id":1, "move_index":1, "title":"Note Item Hello World", "content":"This is a note item.", "state":1}' \
    http://127.0.0.1:8000/api/v1/note-items
```

##### Notes

* state `1` = Patient and clinician can see the note.
* state `2` = Patient cannot see but clinician can.
* state `3` = Patient cannot see and archived by clinician.
* state `4` = Patient can see but archived by clinician.


# **List Notes**
##### Description
This endpoint will return a list of notes that have granted permission to the current logged in user.

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

##### Required

None

##### Data Params

None

##### Success Response

  * **Status**: `200`
  * **Content**:
    ```json
    {
        "next_offset": 2,
        "count": 2,
        "results": [
            {
                "id": 1,
                "uuid": "1d1fd475-bff2-42bc-bcab-45ac0798295b",
                "tenant_id": 2,
                "note_id": 1,
                "user_id": 2,
                "content": "This is a test comment.",
                "move_index": 1,
                "state": 4,
                "created_by_user_id": 1,
                "created_by_name_name": "Frank Herbert",
                "created_time": "2022-09-23T01:58:24.898176Z",
                "modified_by_user_id": 1,
                "modified_by_name_name": "Frank Herbert",
                "modified_time": "2022-09-23T04:39:32.211117Z"
            },
            {
                "id": 2,
                "uuid": "f63f9fc8-3a05-4021-8a3b-6ae6af5a1a6b",
                "tenant_id": 2,
                "note_id": 1,
                "user_id": 2,
                "content": "I am doing fine, thank you!",
                "move_index": 1,
                "state": 1,
                "created_by_user_id": 1,
                "created_by_name_name": "Frank Herbert",
                "created_time": "2022-09-23T04:00:37.255142Z",
                "modified_by_user_id": 1,
                "modified_by_name_name": "Frank Herbert",
                "modified_time": "2022-09-23T04:00:37.255142Z"
            }
        ]
    }
    ```

##### Sample Call

Run the following in your terminal:

```shell
curl "https://bionotescloud.net/api/v1/note-items" \
    -H "Authorization: Bearer $BIOMETRICSCLOUD_ACCESS_TOKEN" \
    -H "Content-Type: application/json"
```

**OR**

```shell
curl "http://127.0.0.1:8000/api/v1/note-items?note_id=1" \
    -H "Authorization: Bearer $BIOMETRICSCLOUD_ACCESS_TOKEN" \
    -H "Content-Type: application/json"
```

##### Notes

None


# **Update Note**
##### Description
This endpoint will Update note for an existing user.

##### URL

`https://bionotescloud.net/api/v1/note-item/1`

##### Method

`PUT`

##### URL Params

None

##### Data Params

Field | Required | Example | Description
--------- | ----------- | ----------- | -----------
`note_id` | Yes | 1 | The ID of the note that this note item belongs to.
`content` | Yes | This is a note. | The content of the first `note_item`.
`state` | Yes | 1 | The state of the note. Options `1`, `2`, `3`, `4`. (See below)
`move_index` | Yes | 1 | The order position that this note belongs to.

##### Success Response

  * **Status**: `200`
  * **Content**:
    ```json
    {
        "id": 1,
        "uuid": "1d1fd475-bff2-42bc-bcab-45ac0798295b",
        "tenant_id": 2,
        "note_id": 1,
        "user_id": 2,
        "content": "This is a test comment.",
        "move_index": 1,
        "state": 4,
        "created_by_user_id": 1,
        "created_by_name_name": "Frank Herbert",
        "created_time": "2022-09-23T01:58:24.898176Z",
        "modified_by_user_id": 1,
        "modified_by_name_name": "Frank Herbert",
        "modified_time": "2022-09-23T04:39:32.211117Z"
    }
    ```

##### Sample Call

Run the following in your terminal:

```shell
curl -X PUT \
    -H "Content-Type: application/json" \
    -H "Authorization: Bearer $BIOMETRICSCLOUD_ACCESS_TOKEN" \
    -d '{"note_id":1, "move_index":1, "title":"Note Item #1", "content":"This is a note item.", "state":1}' \
    https://bionotescloud.net/api/v1/note-item/1
```

**OR**

```shell
curl -X PUT \
    -H "Content-Type: application/json" \
    -H "Authorization: Bearer $BIOMETRICSCLOUD_ACCESS_TOKEN" \
    -d '{"note_id":1, "move_index":1, "title":"Note Item #1", "content":"This is a note item.", "state":1}' \
    http://127.0.0.1:8000/api/v1/note-item/1
```

##### Notes

* state `1` = Patient and clinician can see the note.
* state `2` = Patient cannot see but clinician can.
* state `3` = Patient cannot see and archived by clinician.
* state `4` = Patient can see but archived by clinician.


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
