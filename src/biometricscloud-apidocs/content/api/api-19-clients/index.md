---
title: 'Clients Endpoints'
date: 2019-02-11T19:27:37+10:00
draft: false
weight: 19
summary: "The retrieve endpoints for the clients data."
---

# **List Clients**
##### Description
This endpoint will return a list of clients that have granted permission to the current logged in user.

##### URL

`https://biometricscloud.net/api/v1/clients`

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
curl "https://biometricscloud.net/api/v1/clients" \
    -H "Authorization: Bearer $BIOMETRICSCLOUD_ACCESS_TOKEN" \
    -H "Content-Type: application/json"
```

**OR**

```shell
curl "http://127.0.0.1:8000/api/v1/clients" \
    -H "Authorization: Bearer $BIOMETRICSCLOUD_ACCESS_TOKEN" \
    -H "Content-Type: application/json"
```

##### Notes

None


# **Delete Client**
##### Description
This endpoint will sever the link between the logged in user (ex: Clinician) and the client.

##### URL

`https://biometricscloud.net/api/v1/client/1`

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
curl -X DELETE "https://biometricscloud.net/api/v1/client/1" \
     -H "Authorization: Bearer $BIOMETRICSCLOUD_ACCESS_TOKEN"
```

**OR**

```shell
curl -X DELETE "http://127.0.0.1:8000/api/v1/client/1" \
     -H "Authorization: Bearer $BIOMETRICSCLOUD_ACCESS_TOKEN"
```

##### Notes

None
