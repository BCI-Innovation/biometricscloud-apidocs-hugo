---
title: 'Message Threads Endpoints'
date: 2019-02-11T19:27:37+10:00
draft: false
weight: 14
summary: "The retrieve endpoints for the message threads and their replies."
---


<!-- ####################################################################### -->

# **Create Message Thread**
##### Description
This endpoint will xyz.

##### URL

`https://bionotescloud.net/api/v1/messages`

##### Method

`POST`

##### URL Params

None

##### Data Params

Field | Required | Example | Description
--------- | ----------- | ----------- | -----------
`to_user_id` | Yes | 2 | The user to send this message to.
`title` | Yes | Hey | The title to display in the message.
`content` | Yes | How are you doing? | The content of the message.

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
    -d '{"to_user_id":2, "title":"Hey","content":"How are you doing?", "onset_date":"1990-01-01T00:00:00Z","interaction_date":"1990-01-01T00:00:00Z"}' \
    http://127.0.0.1:8000/api/v1/messages
```

##### Message Threads

None

<!-- ####################################################################### -->

# **List Message Threads**
##### Description
This endpoint will return a list of notes that have granted permission to the current logged in user.

##### URL

`https://bionotescloud.net/api/v1/messages`

##### Method

`GET`

##### URL Params

Query Parameters | Description
--------- | -----------
`type_id` | Available choices: `sent` or `received`. `sent` will display all the messages that you sent to other users. `received` will display all the message that where sent to you.
`offset` | The `ID` of the record in the list which will be used as to filter any records less then this value.
`limit` | The maximum number of entries to return in the pagination.
`sort_order` | Either the `asc` (ascending) or `desc` (descending) order to return the results as.
`sort_field` | The column to sort by.
`search` | The keywords to search through.

##### Required

* `type_id`

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
                "uuid": "e48ff395-cb81-4396-9743-fcaf36a1f4db",
                "tenant_id": 1,
                "from_user_id": 1,
                "to_user_id": 2,
                "title": "Hey",
                "content": "How are you doing?",
                "state": 1,
                "created_by_user_id": 1,
                "created_by_name_name": "Frank Herbert",
                "created_time": "2022-09-19T16:27:29.617639Z",
                "modified_by_user_id": 1,
                "modified_by_name_name": "Frank Herbert",
                "modified_time": "2022-09-19T16:27:29.617639Z"
            }
        ]
    }
    ```

##### Sample Call

Run the following in your terminal:

```shell
# ...
```

**OR**

```shell
curl "http://127.0.0.1:8000/api/v1/messages?type_id=sent" \
    -H "Authorization: Bearer $BIOMETRICSCLOUD_ACCESS_TOKEN" \
    -H "Content-Type: application/json"
```

##### Message Threads

None

<!-- ####################################################################### -->

# **Retrieve Message Thread**

##### Description
This endpoint will Update note for an existing user.

##### URL

`https://bionotescloud.net/api/v1/message/1`

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
        "uuid": "e48ff395-cb81-4396-9743-fcaf36a1f4db",
        "tenant_id": 1,
        "from_user_id": 1,
        "to_user_id": 2,
        "title": "Hey",
        "content": "How are you doing?",
        "state": 1,
        "created_by_user_id": 1,
        "created_by_name_name": "Frank Herbert",
        "created_time": "0001-01-01T00:00:00Z",
        "modified_by_user_id": 1,
        "modified_by_name_name": "Frank Herbert",
        "modified_time": "2022-09-19T16:27:29.617639Z"
    }
    ```

##### Sample Call

Run the following in your terminal:

```shell
curl -X GET \
    -H "Content-Type: application/json" \
    -H "Authorization: Bearer $BIOMETRICSCLOUD_ACCESS_TOKEN" \
    https://bionotescloud.net/api/v1/message/1
```

**OR**

```shell
curl -X GET \
    -H "Content-Type: application/json" \
    -H "Authorization: Bearer $BIOMETRICSCLOUD_ACCESS_TOKEN" \
    http://127.0.0.1:8000/api/v1/message/1
```

##### Message Threads

None

<!-- ####################################################################### -->

# **Create Message Reply**
##### Description
This endpoint will xyz.

##### URL

`https://bionotescloud.net/api/v1/message/1/replies`

##### Method

`POST`

##### URL Params

None

##### Data Params

Field | Required | Example | Description
--------- | ----------- | ----------- | -----------
`to_user_id` | Yes | 2 | The user to send this message to.
`title` | Yes | Hey | The title to display in the message.
`content` | Yes | How are you doing? | The content of the message.

##### Success Response

  * **Status**: `200`
  * **Content**:
    ```json
    {
        "id": 1,
        "uuid": "e48ff395-cb81-4396-9743-fcaf36a1f4db",
        "tenant_id": 1,
        "from_user_id": 1,
        "to_user_id": 2,
        "title": "Hey",
        "content": "How are you doing?",
        "state": 2,
        "created_by_user_id": 1,
        "created_by_name_name": "Frank Herbert",
        "created_time": "0001-01-01T00:00:00Z",
        "modified_by_user_id": 2,
        "modified_by_name_name": "Brian Herbert",
        "modified_time": "2022-09-19T16:54:41.389789Z",
        "message_replies": [
            {
                "id": 2,
                "uuid": "609516a8-6c76-435e-bedf-6612bbd647de",
                "tenant_id": 1,
                "message_thread_id": 1,
                "from_user_id": 1,
                "to_user_id": 2,
                "title": "Hey",
                "content": "I am doing good, thank you. How are you?",
                "state": 1,
                "created_by_user_id": 2,
                "created_by_name_name": "Brian Herbert",
                "created_time": "2022-09-19T18:57:54.126863Z",
                "modified_by_user_id": 2,
                "modified_by_name_name": "Brian Herbert",
                "modified_time": "2022-09-19T18:57:54.126863Z"
            },
            {
                "id": 1,
                "uuid": "e4344470-0cde-4dd2-9250-f46c14f7b86c",
                "tenant_id": 1,
                "message_thread_id": 1,
                "from_user_id": 1,
                "to_user_id": 2,
                "title": "Hey",
                "content": "How are you doing?",
                "state": 1,
                "created_by_user_id": 2,
                "created_by_name_name": "Brian Herbert",
                "created_time": "2022-09-19T16:48:40.910413Z",
                "modified_by_user_id": 1,
                "modified_by_name_name": "Frank Herbert",
                "modified_time": "2022-09-19T16:50:55.032108Z"
            }
        ]
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
    -d '{"to_user_id":2, "title":"Hey","content":"I am doing good, thank you. How are you?"}' \
    http://127.0.0.1:8000/api/v1/message/1/replies
```

##### Notes

None

<!-- ####################################################################### -->


# **Update Message Reply**
##### Description
This endpoint will xyz.

##### URL

`https://bionotescloud.net/api/v1/message/1/replies`

##### Method

`PUT`

##### URL Params

None

##### Data Params

Field | Required | Example | Description
--------- | ----------- | ----------- | -----------
`to_user_id` | Yes | 2 | The user to send this message to.
`title` | Yes | Hey | The title to display in the message.
`content` | Yes | How are you doing? | The content of the message.

##### Success Response

  * **Status**: `200`
  * **Content**:
    ```json
    {
        "id": 1,
        "uuid": "e48ff395-cb81-4396-9743-fcaf36a1f4db",
        "tenant_id": 1,
        "from_user_id": 1,
        "to_user_id": 2,
        "title": "Hey",
        "content": "How are you doing?",
        "state": 2,
        "created_by_user_id": 1,
        "created_by_name_name": "Frank Herbert",
        "created_time": "0001-01-01T00:00:00Z",
        "modified_by_user_id": 2,
        "modified_by_name_name": "Brian Herbert",
        "modified_time": "2022-09-19T16:54:41.389789Z",
        "message_replies": [
            {
                "id": 2,
                "uuid": "609516a8-6c76-435e-bedf-6612bbd647de",
                "tenant_id": 1,
                "message_thread_id": 1,
                "from_user_id": 1,
                "to_user_id": 2,
                "title": "Hey",
                "content": "I am doing good, thank you. How are you?",
                "state": 1,
                "created_by_user_id": 2,
                "created_by_name_name": "Brian Herbert",
                "created_time": "2022-09-19T18:57:54.126863Z",
                "modified_by_user_id": 2,
                "modified_by_name_name": "Brian Herbert",
                "modified_time": "2022-09-19T18:57:54.126863Z"
            },
            {
                "id": 1,
                "uuid": "e4344470-0cde-4dd2-9250-f46c14f7b86c",
                "tenant_id": 1,
                "message_thread_id": 1,
                "from_user_id": 1,
                "to_user_id": 2,
                "title": "Hey",
                "content": "How are you doing?",
                "state": 1,
                "created_by_user_id": 2,
                "created_by_name_name": "Brian Herbert",
                "created_time": "2022-09-19T16:48:40.910413Z",
                "modified_by_user_id": 1,
                "modified_by_name_name": "Frank Herbert",
                "modified_time": "2022-09-19T16:50:55.032108Z"
            }
        ]
    }
    ```

##### Sample Call

Run the following in your terminal:

```shell
#...
```

**OR**

```shell
curl -X PUT \
    -H "Content-Type: application/json" \
    -H "Authorization: Bearer $BIOMETRICSCLOUD_ACCESS_TOKEN" \
    -d '{"to_user_id":2, "title":"Hey","content":"I am doing good, thank you. How are you?"}' \
    http://127.0.0.1:8000/api/v1/message/1/replies
```

##### Notes

None

<!-- ####################################################################### -->
