---
title: 'Staff Endpoints'
date: 2019-02-11T19:27:37+10:00
draft: false
weight: 31
summary: "CRUD endpoints pertaining staff members."
---
The following endpoints provide CRUD operations on our staff.


# **Create Staff**
##### Description
xxx

##### URL

`https://biometricscloud.net/api/v1/staves`

##### Method

`POST`

##### URL Params

None

##### Data Params


Field | Required | Description
--------- | ----------- | -----------
`username` | Yes | The  unique name to identify your account.
`first_name` | Yes | The first name of the user.
`middle_name` | No | The middle name of the user.
`last_name` | Yes | The last name of the user.  
`country` | Yes | The country of origin for the user.
`country_tel_code` Yes | | The country code for the telephone.
`telephone` | Yes | The telephone number for the user.
`email` | Yes | The email address for the user.  
`agree_tos` | Yes | True or false value depending if the user agreed to the terms of service.
`password` | Yes | The password to use for securing the user account.
`password_repeat` | Yes | The password repeated to ensure user entered correct password.
`account_type` | Yes | The type of user account to setup. Options: `1`=**Personal** and `2`=**Professional**.
`account_sub_type` | Yes | If you selected `account_type=2` then you need to fill this out. Select from `1`=**Other**, `2`=**Practitioner** and `3`=**Clinician**.
`account_sub_type_other` | Yes | If you selected `account_type=2` and `account_sub_type=1` then you need to fill this out. Please write your profession, ex: "Gym

##### Success Response

  * **Status**: `200`
  * **Content**:
    ```json

    ```

##### Sample Call

Run the following in your terminal:

```shell
curl -X POST \
    -H "Content-Type: application/json" \
    -H "Authorization: Bearer $BIOMETRICSCLOUD_ACCESS_TOKEN" \
    -d '{"text":"Healthy"}' \
    https://biometricscloud.net/api/v1/staves
```

**OR**

```shell
curl -X POST \
    -H "Content-Type: application/json" \
    -H "Authorization: Bearer $BIOMETRICSCLOUD_ACCESS_TOKEN" \
    -d '{"text":"Healthy"}' \
    http://127.0.0.1:8000/api/v1/staves
```

##### Notes

None

# **List Staff**
##### Description
This endpoint will return a list of staff.

##### URL

`https://biometricscloud.net/api/v1/staves`

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

    ```

##### Sample Call

Run the following in your terminal:

```shell
curl "https://biometricscloud.net/api/v1/staves" \
    -H "Authorization: Bearer $BIOMETRICSCLOUD_ACCESS_TOKEN" \
    -H "Content-Type: application/json"
```

**OR**

```shell
curl "http://127.0.0.1:8000/api/v1/staves" \
    -H "Authorization: Bearer $BIOMETRICSCLOUD_ACCESS_TOKEN" \
    -H "Content-Type: application/json"
```

##### Notes

None

# **Retrieve Tag**
##### Description
This endpoint will retrieve the Tag detail.

##### URL

`https://biometricscloud.net/api/v1/staff/1`

##### Method

`GET`

##### URL Params

Query Parameters | Required | Default Value | Description
--------- | ----------- | ----------- | -----------
`staff_id` | Yes  | - | The staff identification that belongs to the user.

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
curl "https://biometricscloud.net/api/v1/staff/1" \
    -H "Authorization: Bearer $BIOMETRICSCLOUD_ACCESS_TOKEN" \
    -H "Content-Type: application/json"
```

**OR**


```shell
curl "http://localhost:8000/api/v1/staff/1" \
    -H "Authorization: Bearer $BIOMETRICSCLOUD_ACCESS_TOKEN" \
    -H "Content-Type: application/json"
```

##### Notes

None


# **Update Staff**
##### Description
Update the staff detail.

##### URL

`https://biometricscloud.net/api/v1/staff/1`

##### Method

`PUT`

##### URL Params

None

##### Data Params


Field | Required | Description
--------- | ----------- | -----------
`username` | Yes | The  unique name to identify your account.
`first_name` | Yes | The first name of the user.
`middle_name` | No | The middle name of the user.
`last_name` | Yes | The last name of the user.  
`country` | Yes | The country of origin for the user.
`country_tel_code` Yes | | The country code for the telephone.
`telephone` | Yes | The telephone number for the user.
`email` | Yes | The email address for the user.  
`agree_tos` | Yes | True or false value depending if the user agreed to the terms of service.
`account_type` | Yes | The type of user account to setup. Options: `1`=**Personal** and `2`=**Professional**.
`account_sub_type` | Yes | If you selected `account_type=2` then you need to fill this out. Select from `1`=**Other**, `2`=**Practitioner** and `3`=**Clinician**.
`account_sub_type_other` | Yes | If you selected `account_type=2` and `account_sub_type=1` then you need to fill this out. Please write your profession, ex: "Gym

##### Success Response

  * **Status**: `200`
  * **Content**:
    ```json

    ```

##### Sample Call

Run the following in your terminal:

```shell
curl -X POST \
    -H "Content-Type: application/json" \
    -H "Authorization: Bearer $BIOMETRICSCLOUD_ACCESS_TOKEN" \
    -d '{"text":"Healthy"}' \
    https://biometricscloud.net/api/v1/staff/1
```

**OR**

```shell
curl -X POST \
    -H "Content-Type: application/json" \
    -H "Authorization: Bearer $BIOMETRICSCLOUD_ACCESS_TOKEN" \
    -d '{"text":"Healthy"}' \
    http://127.0.0.1:8000/api/v1/staff/1
```

##### Notes

None

# **Delete Tag**
##### Description
This endpoint will delete the staff.

##### URL

`https://biometricscloud.net/api/v1/staff/1`

##### Method

`DELETE`

##### URL Params

Query Parameters | Required | Default Value | Description
--------- | ----------- | ----------- | -----------
`staff_id` | Yes  | - | The staff identification that belongs to the user.

##### Data Params

None

##### Success Response

  * **Status**: `204`
  * **Content**: None

##### Sample Call

Run the following in your terminal:

```shell
curl -X DELETE "https://biometricscloud.net/api/v1/staff/1" \
     -H "Authorization: Bearer $BIOMETRICSCLOUD_ACCESS_TOKEN"
```

**OR**

```shell
curl -X DELETE "http://127.0.0.1:8000/api/v1/staff/1" \
     -H "Authorization: Bearer $BIOMETRICSCLOUD_ACCESS_TOKEN"
```

##### Notes

None
