---
title: 'Authorized Application Endpoints'
date: 2019-02-11T19:27:37+10:00
draft: false
weight: 10
summary: "The endpoints pertaining to authorized applications"
---

The following endpoints support the user to view what authorized applications that are attached to their account. Please note, user's cannot create an authorized application as the `authorization code grant` operation handles the creation.

# **List Authorized Applications**
##### Description
This endpoint will return a list of user's authorized applications.

##### URL

`https://biometricscloud.net/api/v1/authorized-applications`

##### Method

`GET`

##### URL Params

Query Parameters | Default Value | Description
--------- | ----------- | -----------
`offset` | 0 | The `ID` of the record in the list which will be used as to filter any records less then this value.
`limit` | 100 | The maximum number of entries to return in the pagination.
`sort_order` | asc | Either the `asc` (ascending) or `desc` (descending) order to return the results as.
`sort_field` | id | The column to sort by.

##### Required

None

##### Data Params

None

##### Sample Call

Run the following in your terminal:

```shell
curl "https://biometricscloud.net/api/v1/authorized-applications" \
    -H "Authorization: Bearer VSvXrNLlQCeCdTJjGUJgKw" \
    -H "Content-Type: application/json"
```

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
                "application_id": 1,
                "state": 1
            }
        ]
    }
    ```

##### Notes

None

# **Retrieve Authorized Application**
##### Description
This endpoint will retrieve the authorized application detail.

##### URL

`https://biometricscloud.net/api/v1/authorized-application/1`

##### Method

`GET`

##### URL Params

None

##### Required

None

##### Data Params

None

##### Sample Call

Run the following in your terminal:

```shell
curl "https://biometricscloud.net/api/v1/application/1" \
    -H "Authorization: Bearer VSvXrNLlQCeCdTJjGUJgKw" \
    -H "Content-Type: application/json"
```

##### Success Response

  * **Status**: `200`
  * **Content**:
    ```json
    {
        "id": 1,
        "uuid": "x7cca4ab-bbd8-4ed7-b928-489e8a17e1b7",
        "tenant_id": 3,
        "application_id": 1,
        "user_id": 1,
        "state": 1,
        "created_time": "2022-01-20T06:45:44.205855-05:00",
        "modified_time": "2022-01-20T06:45:44.205855-05:00"
    }
    ```

##### Notes

None



# **Delete Authorized Application**
##### Description
This endpoint will delete the authorized application.

##### URL

`https://biometricscloud.net/api/v1/authorized-application/1`

##### Method

`DELETE`

##### URL Params

None

##### Required

None

##### Data Params

None

##### Sample Call

Run the following in your terminal:

```shell
curl -X DELETE "https://biometricscloud.net/api/v1/authorized-application/1" \
     -H "Authorization: Bearer VSvXrNLlQCeCdTJjGUJgKw"
```

##### Success Response

  * **Status**: `204`
  * **Content**: None

##### Notes

Third-party applications will be unable to access the any of user's resources until the user authorizes again with the third-party.
