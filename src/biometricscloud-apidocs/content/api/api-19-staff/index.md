---
title: 'Staff Endpoints'
date: 2019-02-11T19:27:37+10:00
draft: false
weight: 19
summary: "The retrieve endpoints for the staff data."
---

# **List Staff**
##### Description
This endpoint will return a list of staff members.

##### URL

`https://biometricscloud.net/api/v1/staves`

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
        "next_id": 2,
        "count": 1,
        "results": [
            {
                "id": 2,
                "uuid": "f1caca64-c687-4610-bd6f-b593ef4be448",
                "tenant_id": 1,
                "username": "bherbert",
                "email": "bherbert@dune.com",
                "first_name": "Brian",
                "last_name": "Herbert",
                "name": "Brian Herbert",
                "lexical_name": "Herbert, Brian",
                "state": 1,
                "account_type": 1,
                "account_sub_type": 1,
                "account_sub_type_other": "Gym Instructor",
                "organization_name": "Elite Physical Training",
                "timezone": "UTC",
                "language": "en",
                "country": "Canada",
                "country_tel_code": "1",
                "telephone": "(123) 456-7899",
                "agree_tos": true,
                "created_time": "2022-09-19T15:53:10.172183Z",
                "modified_time": "2022-09-19T15:53:10.172183Z",
                "joined_time": "0001-01-01T00:00:00Z",
                "salt": "ff0d486697",
                "pr_expiry_time": "0001-01-01T00:00:00Z",
                "avatar_s3_key": null,
                "avatar_title": null,
                "avatar_file_url": null,
                "date_of_birth": null,
                "gender": null,
                "marital_status": null,
                "children_count": null,
                "blood_group": null,
                "height_in_meters": 0,
                "weight_in_kg": 0,
                "body_mass_index": 0,
                "body_fat_percentage": 0,
                "allergies": null,
                "illnesses": null,
                "metrics": null,
                "tags": null
            }
        ]
    }
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

# **Create Staff**
##### Description
This endpoint will create a staff member.

##### URL

`https://biometricscloud.net/api/v1/staves`

##### Method

`POST`

##### URL Params

Query Parameters | Description
--------- | -----------
`username` | The unique username for the account.
`first_name` | The first name of the staff member.
`middle_name` | The middle man of the staff member.
`last_name` | The last man of the staff member.
`email` | The email of the staff member.
`password` | The password in plaintext for the staff member.
`password_repeat` | The password to repeat in plaintext for the staff member.
`country` | The country that the staff member belongs to.
`country_tel_code` | The country code (ex. USA is +1) for the staff member.
`telephone` | The telephone of the staff member.
`agree_tos` | Whether the staff member agreed to the term of service (TOS). Only acceptable options is "true".

##### Required

None

##### Data Params

None

##### Success Response

  * **Status**: `200`
  * **Content**:
    ```json
    {
        "next_id": 2,
        "count": 1,
        "results": [
            {
                "id": 2,
                "uuid": "f1caca64-c687-4610-bd6f-b593ef4be448",
                "tenant_id": 1,
                "username": "bherbert",
                "email": "bherbert@dune.com",
                "first_name": "Brian",
                "last_name": "Herbert",
                "name": "Brian Herbert",
                "lexical_name": "Herbert, Brian",
                "state": 1,
                "account_type": 1,
                "account_sub_type": 1,
                "account_sub_type_other": "Gym Instructor",
                "organization_name": "Elite Physical Training",
                "timezone": "UTC",
                "language": "en",
                "country": "Canada",
                "country_tel_code": "1",
                "telephone": "(123) 456-7899",
                "agree_tos": true,
                "created_time": "2022-09-19T15:53:10.172183Z",
                "modified_time": "2022-09-19T15:53:10.172183Z",
                "joined_time": "0001-01-01T00:00:00Z",
                "salt": "ff0d486697",
                "pr_expiry_time": "0001-01-01T00:00:00Z",
                "avatar_s3_key": null,
                "avatar_title": null,
                "avatar_file_url": null,
                "date_of_birth": null,
                "gender": null,
                "marital_status": null,
                "children_count": null,
                "blood_group": null,
                "height_in_meters": 0,
                "weight_in_kg": 0,
                "body_mass_index": 0,
                "body_fat_percentage": 0,
                "allergies": null,
                "illnesses": null,
                "metrics": null,
                "tags": null
            }
        ]
    }
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

# **Get Staff**
##### Description
This endpoint will get the staff member.

##### URL

`https://biometricscloud.net/api/v1/staff/1`

##### Method

`GET`

##### URL Params

Query Parameters | Description
--------- | -----------


##### Required

None

##### Data Params

None

##### Success Response

  * **Status**: `200`
  * **Content**:
    ```json
    {
        "id": 2,
        "uuid": "f1caca64-c687-4610-bd6f-b593ef4be448",
        "tenant_id": 1,
        "username": "bherbert",
        "email": "bherbert@dune.com",
        "first_name": "Brian",
        "last_name": "Herbert",
        "name": "Brian Herbert",
        "lexical_name": "Herbert, Brian",
        "state": 1,
        "account_type": 1,
        "account_sub_type": 1,
        "account_sub_type_other": "Gym Instructor",
        "organization_name": "Elite Physical Training",
        "timezone": "UTC",
        "language": "en",
        "country": "Canada",
        "country_tel_code": "1",
        "telephone": "(123) 456-7899",
        "agree_tos": true,
        "created_time": "2022-09-19T15:53:10.172183Z",
        "modified_time": "2022-09-19T15:53:10.172183Z",
        "joined_time": "0001-01-01T00:00:00Z",
        "salt": "ff0d486697",
        "pr_expiry_time": "0001-01-01T00:00:00Z",
        "avatar_s3_key": null,
        "avatar_title": null,
        "avatar_file_url": null,
        "date_of_birth": null,
        "gender": null,
        "marital_status": null,
        "children_count": null,
        "blood_group": null,
        "height_in_meters": 0,
        "weight_in_kg": 0,
        "body_mass_index": 0,
        "body_fat_percentage": 0,
        "allergies": null,
        "illnesses": null,
        "metrics": null,
        "tags": null
    }
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
curl "http://127.0.0.1:8000/api/v1/staff/1" \
    -H "Authorization: Bearer $BIOMETRICSCLOUD_ACCESS_TOKEN" \
    -H "Content-Type: application/json"
```

##### Notes

None


# **Update Staff**
##### Description
This endpoint will Update a staff member.

##### URL

`https://biometricscloud.net/api/v1/staff/1`

##### Method

`PUT`

##### URL Params

Query Parameters | Description
--------- | -----------
`username` | The unique username for the account.
`first_name` | The first name of the staff member.
`middle_name` | The middle man of the staff member.
`last_name` | The last man of the staff member.
`email` | The email of the staff member.
`password` | The password in plaintext for the staff member.
`password_repeat` | The password to repeat in plaintext for the staff member.
`country` | The country that the staff member belongs to.
`country_tel_code` | The country code (ex. USA is +1) for the staff member.
`telephone` | The telephone of the staff member.
`agree_tos` | Whether the staff member agreed to the term of service (TOS). Only acceptable options is "true".

##### Required

None

##### Data Params

None

##### Success Response

  * **Status**: `200`
  * **Content**:
    ```json
    {
        "id": 2,
        "uuid": "f1caca64-c687-4610-bd6f-b593ef4be448",
        "tenant_id": 1,
        "username": "bherbert",
        "email": "bherbert@dune.com",
        "first_name": "Brian",
        "last_name": "Herbert",
        "name": "Brian Herbert",
        "lexical_name": "Herbert, Brian",
        "state": 1,
        "account_type": 1,
        "account_sub_type": 1,
        "account_sub_type_other": "Gym Instructor",
        "organization_name": "Elite Physical Training",
        "timezone": "UTC",
        "language": "en",
        "country": "Canada",
        "country_tel_code": "1",
        "telephone": "(123) 456-7899",
        "agree_tos": true,
        "created_time": "2022-09-19T15:53:10.172183Z",
        "modified_time": "2022-09-19T15:53:10.172183Z",
        "joined_time": "0001-01-01T00:00:00Z",
        "salt": "ff0d486697",
        "pr_expiry_time": "0001-01-01T00:00:00Z",
        "avatar_s3_key": null,
        "avatar_title": null,
        "avatar_file_url": null,
        "date_of_birth": null,
        "gender": null,
        "marital_status": null,
        "children_count": null,
        "blood_group": null,
        "height_in_meters": 0,
        "weight_in_kg": 0,
        "body_mass_index": 0,
        "body_fat_percentage": 0,
        "allergies": null,
        "illnesses": null,
        "metrics": null,
        "tags": null
    }
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

# **Delete Client**
##### Description
This endpoint delete a staff member of the API endpoint.

##### URL

`https://biometricscloud.net/api/v1/staff/1`

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
