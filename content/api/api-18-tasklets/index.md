---
title: 'Tasklets Endpoints'
date: 2019-02-11T19:27:37+10:00
draft: false
weight: 9
summary: "CRUD endpoints pertaining to tasklets."
---

BiometricsCloud supports individual users sending `tasklets` to other users. A `tasklet` is a task item that requires an action by a user.


# **Create Tasklet #1**
##### Description

This endpoint create a `tasklet #1` for a user. `Tasklet #1` is a system request to share data. The other user will receive a message prompt in their dashboard.

##### URL

`https://biometricscloud.net/api/v1/tasklets/1`

##### Method

`POST`

##### URL Params

None

##### Data Params

Parameter | Required | Description
--------- | ------- | -----------
`email` | Yes | The email address of the user that wants to get access for the current logged in user that made the API call.
`message` | Yes | The message to send to the user.

##### Success Response

  * **Status**: `201`
  * **Content**: None

##### Sample Call

Run the following in your terminal:

```shell
curl -X POST \
     -H "Content-Type: application/json" \
     -H "Authorization: Bearer $BIOMETRICSCLOUD_ACCESS_TOKEN" \
     -d '{"email": "fherbert@dune.com", "message": "Hey I wanna be your doctor."}' \
     https://biometricscloud.net/api/v1/tasklets/1
```

**OR**

```shell
curl -X POST \
     -H "Content-Type: application/json" \
     -H "Authorization: Bearer $BIOMETRICSCLOUD_ACCESS_TOKEN" \
     -d '{"email": "fherbert@dune.com", "message": "Hey I wanna be your doctor."}' \
     http://localhost:8000/api/v1/tasklets/1
```

# **Respond to Tasklet #1**
##### Description

This endpoint responds to a `tasklet #1`. If the user accepts then data is shared between the users, else data is rejected.

##### URL

`https://biometricscloud.net/api/v1/tasklets/1/close`

##### Method

`POST`

##### URL Params

None

##### Data Params

Parameter | Required | Description
--------- | ------- | -----------
`tasklet_id` | Yes | The unique identification of the tasklet that was provided in the dashboard API.
`is_accepted` | Yes | The `true` or `false` choice made by the user.


##### Success Response

  * **Status**: `201`
  * **Content**: None

##### Sample Call

Run the following in your terminal:

```shell
curl -X POST \
     -H "Content-Type: application/json" \
     -H "Authorization: Bearer $BIOMETRICSCLOUD_ACCESS_TOKEN" \
     -d '{"is_accepted": true,"tasklet_id":13435}' \
     https://biometricscloud.net/api/v1/tasklets/1/close
```

**OR**

```shell
curl -X POST \
     -H "Content-Type: application/json" \
     -H "Authorization: Bearer $BIOMETRICSCLOUD_ACCESS_TOKEN" \
     -d '{"is_accepted": true,"tasklet_id":2}' \
     http://localhost:8000/api/v1/tasklets/1/close
```

# **Mark Tasklet as Read**
##### Description

This endpoint will make the `tasklet` as read and not appear in the user's dashboard.

##### URL

`https://biometricscloud.net/api/v1/tasklets/mark-read`

##### Method

`POST`

##### URL Params

None

##### Data Params

Parameter | Required | Description
--------- | ------- | -----------
`tasklet_id` | Yes | The unique identification of the tasklet that was provided in the dashboard API.

##### Success Response

  * **Status**: `201`
  * **Content**: None

##### Sample Call

Run the following in your terminal:

```shell
curl -X POST \
     -H "Content-Type: application/json" \
     -H "Authorization: Bearer $BIOMETRICSCLOUD_ACCESS_TOKEN" \
     -d '{"tasklet_id": 1234}' \
     https://biometricscloud.net/api/v1/tasklets/mark-read
```

**OR**

```shell
curl -X POST \
     -H "Content-Type: application/json" \
     -H "Authorization: Bearer $BIOMETRICSCLOUD_ACCESS_TOKEN" \
     -d '{"tasklet_id": 1234}' \
     http://localhost:8000/api/v1/tasklets/mark-read
```
