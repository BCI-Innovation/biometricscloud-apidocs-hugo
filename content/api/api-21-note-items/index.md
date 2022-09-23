---
title: 'Note Items Endpoints'
date: 2019-02-11T19:27:37+10:00
draft: false
weight: 21
summary: "The endpoints for the notes items."
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
`note_id` | Yes | 1 | The note that this item belongs to.
`content` | Yes | This is a note. | The content of the first note
`state` | Yes | 1 | The state of the note. Options 1, 2, 3, 4. (See notes below)
`move_index` | Yes | 1 | The index to set the note in.

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
    -d '{"note_id":1,"content":"This is a note item.","state":"1","move_index":"1"}' \
    https://bionotescloud.net/api/v1/note-items
```

**OR**

```shell
curl -X POST \
    -H "Content-Type: application/json" \
    -H "Authorization: Bearer $BIOMETRICSCLOUD_ACCESS_TOKEN" \
    -d '{"note_id":1,"content":"This is a note item.","state":"1","move_index":"1"}' \
    http://127.0.0.1:8000/api/v1/note-items
```

##### Notes

None

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
    {"next_offset":3,"count":3,"results":[{"id":1,"uuid":"142a436e-8547-42a8-8989-c6e40942801c","tenant_id":1,"user_id":1,"title":"Test Note #1","content":"This is a test.","state":1,"created_by_user_id":1,"created_by_name_name":"Frank Herbert","created_time":"2022-06-21T23:34:48.191946Z","modified_by_user_id":1,"modified_by_name_name":"Frank Herbert","modified_time":"2022-06-21T23:34:48.191946Z"},{"id":2,"uuid":"3a6f5bf1-2bb8-4b7c-9f35-b5ff62886817","tenant_id":1,"user_id":1,"title":"Test Note #1","content":"This is a test.","state":1,"created_by_user_id":1,"created_by_name_name":"Frank Herbert","created_time":"2022-06-21T23:36:34.021615Z","modified_by_user_id":1,"modified_by_name_name":"Frank Herbert","modified_time":"2022-06-21T23:36:34.021615Z"},{"id":3,"uuid":"6c27cf83-e2b1-4a9b-ad55-9488b6a30dc5","tenant_id":1,"user_id":1,"title":"Test Note #1","content":"This is a test.","state":1,"created_by_user_id":1,"created_by_name_name":"Frank Herbert","created_time":"2022-06-21T23:36:56.979505Z","modified_by_user_id":1,"modified_by_name_name":"Frank Herbert","modified_time":"2022-06-21T23:36:56.979505Z"}]}
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
    -d '{"note_id":1,"content":"This is a note item.","state":"1","move_index":"1"}' \
    https://bionotescloud.net/api/v1/note-item/1
```

**OR**

```shell
curl -X PUT \
    -H "Content-Type: application/json" \
    -H "Authorization: Bearer $BIOMETRICSCLOUD_ACCESS_TOKEN" \
    -d '{"note_id":1,"content":"This is a note item.","state":"1","move_index":"1"}' \
    http://127.0.0.1:8000/api/v1/note-item/1
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
