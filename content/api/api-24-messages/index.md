---
title: 'Message Threads Endpoints'
date: 2019-02-11T19:27:37+10:00
draft: false
weight: 24
summary: "The endpoints for the messages and their replies."
---

# **Create Message**
##### Description
This endpoint enables organization staff and their patients to send messages between each other. Messages work like **WhatsApp** in which every message chain is between the patient and an organization; therefore, when you (as a patient) send a message, it is to an organization and not a specific user! When you (as an organization staff) sends a message, that message is specific for the user.

##### URL

`https://bionotescloud.net/api/v1/messages`

##### Method

`POST`

##### URL Params

None

##### Data Params

Field | Required | Example | Description
--------- | ----------- | ----------- | -----------
`tenant_id` | Yes | 2 | The organization that the patient belongs to. How do you know what organizations the patient belongs to? Please see [TODO API]().
`user_id` | Yes | 2 | Staff Perspective: The user to send this message to. Patient Perspective: My user id.
`title` | Yes | Hey | The title to display in the message.
`content` | Yes | How are you doing? | The content of the message.

##### Success Response

  * **Status**: `200`
  * **Content**:
    ```json
    {
        "id": 1,
        "uuid": "0a2c4f1e-8568-4967-a43f-802e8eed4b70",
        "tenant_id": 2,
        "tenant_name": "Elite Physical Training",
        "user_id": 2,
        "user_name": "Brian Herbert",
        "title": "Hey",
        "content": "How are you doing?",
        "state": 1,
        "created_by_user_id": 1,
        "created_by_user_name": "Frank Herbert",
        "created_time": "2022-09-22T17:49:19.196524Z",
        "modified_by_user_id": 1,
        "modified_by_user_name": "Frank Herbert",
        "modified_time": "2022-09-22T17:49:19.196524Z"
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
    -d '{"tenant_id":2, "user_id":2, "title":"Hey","content":"How are you doing?"}' \
    http://127.0.0.1:8000/api/v1/messages
```

##### Notes

None

<!-- ####################################################################### -->

# **List Messages**
##### Description
This endpoint will work depending on whether the logged in user is patient or staff member.

**Patients**
Endpoint will list all the medical organizations that the user is a patient of and the most recent message sent/received for that organization.

**Staff**
Endpoint will list all the users that are patients of this organization and show the most recent message sent/received by every user.

##### URL

`https://bionotescloud.net/api/v1/messages`

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
        "next_offset": 1,
        "count": 2,
        "results": [
            {
                "id": 2,
                "uuid": "7139f7d0-6fbd-4371-ae68-6ad82856255a",
                "tenant_id": 2,
                "tenant_name": "Elite Training",
                "user_id": 2,
                "user_name": "Brian Herbert",
                "role_id": 3,
                "state": 1,
                "latest_message": {
                    "id": 1,
                    "uuid": "ad38e8ee-fac0-45b5-ba9d-15d303e6a96a",
                    "tenant_id": 2,
                    "tenant_name": "Elite Physical Training",
                    "user_id": 2,
                    "user_name": "Brian Herbert",
                    "title": "Hey",
                    "content": "How are you doing?",
                    "state": 1,
                    "created_by_user_id": 2,
                    "created_by_user_name": "Brian Herbert",
                    "created_time": "2022-09-22T20:13:29.817923Z",
                    "modified_by_user_id": 1,
                    "modified_by_user_name": "Frank Herbert",
                    "modified_time": "2022-09-22T21:42:07.186885755Z"
                },
                "created_time": "2022-09-22T20:11:10.612241Z",
                "created_by_user_id": 2,
                "created_by_user_name": "Brian Herbert",
                "modified_by_user_id": 1,
                "modified_by_user_name": "Frank Herbert",
                "modified_time": "2022-09-22T21:42:07.188418Z"
            },
            {
                "id": 1,
                "uuid": "a8fcd7cc-16fe-4c45-a744-fd37dc50be81",
                "tenant_id": 2,
                "tenant_name": "Elite Training",
                "user_id": 1,
                "user_name": "Frank Herbert",
                "role_id": 1,
                "state": 1,
                "latest_message": null,
                "created_time": "2022-09-22T20:08:37.284309Z",
                "created_by_user_id": 1,
                "created_by_user_name": "Frank Herbert",
                "modified_by_user_id": 1,
                "modified_by_user_name": "Frank Herbert",
                "modified_time": "2022-09-22T20:08:37.284309Z"
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
curl "http://127.0.0.1:8000/api/v1/messages" \
    -H "Authorization: Bearer $BIOMETRICSCLOUD_ACCESS_TOKEN" \
    -H "Content-Type: application/json"
```

##### Notes

None

<!-- ####################################################################### -->

# **List Messages Details**
##### Description
Endpoint will list all the messages sent/received between this patient and the organization.

##### URL

`https://bionotescloud.net/api/v1/message-details`

##### Method

`GET`

##### URL Params

Query Parameters | Description
--------- | -----------
`tenant_id` | The tenant that the user belongs to.
`user_id` | Optional parameter to be added by staff when they want to list all the messages between staff and user that belongs to the tenant.
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
        "next_offset": 1,
        "count": 1,
        "results": [
            {
                "id": 1,
                "uuid": "ad38e8ee-fac0-45b5-ba9d-15d303e6a96a",
                "tenant_id": 2,
                "tenant_name": "Elite Physical Training",
                "user_id": 2,
                "user_name": "Brian Herbert",
                "title": "Hey",
                "content": "How are you doing?",
                "state": 1,
                "created_by_user_id": 2,
                "created_by_user_name": "Brian Herbert",
                "created_time": "2022-09-22T20:13:29.817923Z",
                "modified_by_user_id": 1,
                "modified_by_user_name": "Frank Herbert",
                "modified_time": "2022-09-22T21:51:36.002113Z"
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
curl "http://127.0.0.1:8000/api/v1/message-details?tenant_id=2&user_id=2" \
    -H "Authorization: Bearer $BIOMETRICSCLOUD_ACCESS_TOKEN" \
    -H "Content-Type: application/json"
```

##### Notes

None

<!-- ####################################################################### -->

# **Update Message Detail**
##### Description
This endpoint enables organization staff and their patients update their previously sent messages.

##### URL

`https://bionotescloud.net/api/v1/message-detail/1`

##### Method

`PUT`

##### URL Params

None

##### Data Params

Field | Required | Example | Description
--------- | ----------- | ----------- | -----------
`tenant_id` | Yes | 2 | The organization that the patient belongs to. How do you know what organizations the patient belongs to? Please see [TODO API]().
`user_id` | Yes | 2 | Staff Perspective: The user to send this message to. Patient Perspective: My user id.
`title` | Yes | Hey | The title to display in the message.
`content` | Yes | How are you doing? | The content of the message.

##### Success Response

  * **Status**: `200`
  * **Content**:
    ```json
    {
        "id": 1,
        "uuid": "0a2c4f1e-8568-4967-a43f-802e8eed4b70",
        "tenant_id": 2,
        "tenant_name": "Elite Physical Training",
        "user_id": 2,
        "user_name": "Brian Herbert",
        "title": "Hey",
        "content": "How are you doing?",
        "state": 1,
        "created_by_user_id": 1,
        "created_by_user_name": "Frank Herbert",
        "created_time": "2022-09-22T17:49:19.196524Z",
        "modified_by_user_id": 1,
        "modified_by_user_name": "Frank Herbert",
        "modified_time": "2022-09-22T17:49:19.196524Z"
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
    -d '{"tenant_id":2, "user_id":2, "title":"Hey","content":"How are you doing?"}' \
    http://127.0.0.1:8000/api/v1/message-detail/1
```

##### Notes

None

<!-- ####################################################################### -->
# **Delete Message Detail**
##### Description
This endpoint will archive a single message. Calling this endpoint on an already archived message will unarchive it.

##### URL

`https://bionotescloud.net/api/v1/message-detail/1`

##### Method

`DELETE`

##### URL Params

None

##### Data Params

Field | Required | Example | Description
--------- | ----------- | ----------- | -----------
None

##### Success Response

  * **Status**: `204`
  * **Content**: None

##### Sample Call

Run the following in your terminal:

```shell
#...
```

**OR**

```shell
curl -X DELETE \
    -H "Content-Type: application/json" \
    -H "Authorization: Bearer $BIOMETRICSCLOUD_ACCESS_TOKEN" \
    http://127.0.0.1:8000/api/v1/message-detail/1
```

##### Notes

None

<!-- ####################################################################### -->
