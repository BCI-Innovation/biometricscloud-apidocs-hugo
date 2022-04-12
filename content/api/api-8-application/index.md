---
title: 'Application Endpoints'
date: 2019-02-11T19:27:37+10:00
draft: false
weight: 9
summary: "CRUD endpoints pertaining to applications."
---

BiometricsCloud supports third-party applications powered by the internal `oAuth 2.0` server.

# **Create Application**
##### Description
This endpoint will create a application in [BiometricsCloud](https://ipregnancy.app), so your third-party application may access all resource endpoints on behalf of client using `authorization grant` credentials, powered by `oAuth 2.0`.

##### URL

`https://biometricscloud.net/api/v1/applications`

##### Method

`POST`

##### URL Params

None

##### Required

None

##### Data Params

Field | Description
--------- | -----------
`name` | The name of the third-party application to display to users.
`description` | The description of the third-party application to display to users.
`website_url` | The URL of the brochure website the user will be redirected to from their dashboard.
`scope`  | Only accepted value is `all`.
`redirect_url` | The URL that the user will be redirected to once successful `authorization grant` was completed by the user.
`image_url` | The URL of the thumbnail that will be displayed for third-party application.

##### Success Response

  * **Status**: `200`
  * **Content**:
    ```json
    {
        "id": 2,
        "uuid": "ba1af7d2-d373-4a4c-b8a3-0d16ab8f54a0",
        "tenant_id": 2,
        "name": "Third Party App",
        "description": "An example of a third party app which lives on www.ipregnancy.tech",
        "website_url": "https://ipregnancy.tech",
        "scope": "all",
        "redirect_url": "https://ipregnancy.tech/appauth/code",
        "image_url": "https://ipregnancy.tech/static/logo.png",
        "state": 5,
        "client_id": "1f60a74bab4c21bc",
        "client_secret": "lalalalalalala",
        "created_time": "2022-01-19T03:59:08.704325Z",
        "modified_time": "2022-01-19T03:59:08.704325Z"
    }
    ```

##### Sample Call

Run the following in your terminal:

```shell
curl -X POST \
    -H "Content-Type: application/json" \
    -H "Authorization: Bearer VSvXrNLlQCeCdTJjGUJgKw" \
    -d '{"name":"Third Party App","description":"An example of a third party app which lives on www.ipregnancy.tech","website_url":"https://ipregnancy.tech","scope":"all","redirect_url":"https://ipregnancy.tech/appauth/code","image_url":"https://ipregnancy.tech/static/logo.png"}' \
    https://biometricscloud.net/api/v1/applications
```

**OR**

```shell
curl -X POST \
    -H "Content-Type: application/json" \
    -H "Authorization: Bearer VSvXrNLlQCeCdTJjGUJgKw" \
    -d '{"name":"Third Party App","description":"An example of a third party app which lives on www.ipregnancy.tech","website_url":"https://ipregnancy.tech","scope":"all","redirect_url":"https://ipregnancy.tech/appauth/code","image_url":"https://ipregnancy.tech/static/logo.png"}' \
    http://127.0.0.1:8000/api/v1/applications
```

##### Notes

Please save the "client_id", "client_secret" and "redirect_url" values as you will not be getting them again. If you lose these values then you will need to create a new application.

# **List Applications**
##### Description
This endpoint will return a list of active applications.

##### URL

`https://biometricscloud.net/api/v1/applications`

##### Method

`GET`

##### URL Params

Query Parameters | Description
--------- | -----------
`offset` | The `ID` of the record in the list which will be used as to filter any records less then this value.
`limit` | The maximum number of entries to return in the pagination.
`sort_order` | Either the `asc` (ascending) or `desc` (descending) order to return the results as.
`sort_field` | The column to sort by.
`user_id` | Apply filter to only return the applications based on the specified `user_id` value.

##### Required

None

##### Data Params

None

##### Success Response

  * **Status**: `200`
  * **Content**:
    ```json
    {
      "next_id": 1,
      "count": 1,
      "results": [
        {
          "id": 1,
          "name": "Third Party App",
          "scope": "all",
          "image_url": "https://ipregnancy.tech/static/logo.png",
          "state": 5
        }
      ]
    }
    ```

##### Sample Call

Run the following in your terminal:

```shell
curl "https://biometricscloud.net/api/v1/applications" \
    -H "Authorization: Bearer VSvXrNLlQCeCdTJjGUJgKw" \
    -H "Content-Type: application/json"
```

**OR**

```shell
curl "http://127.0.0.1:8000/api/v1/applications" \
    -H "Authorization: Bearer VSvXrNLlQCeCdTJjGUJgKw" \
    -H "Content-Type: application/json"
```

##### Notes

None

# **Retrieve Application**
##### Description
This endpoint will retrieve the application detail.

##### URL

`https://biometricscloud.net/api/v1/application/1`

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
      "uuid": "f9cca4ab-bbd8-4ed7-b928-489e8a17e1b7",
      "tenant_id": 3,
      "name": "Third Party App",
      "description": "Third Party App",
      "website_url": "http://127.0.0.1:8000",
      "scope": "all",
      "redirect_url": "http://127.0.0.1:8001/appauth/code",
      "image_url": "http://127.0.0.1:8001/static/logo.png",
      "state": 5,
      "client_id": "210f819bdf5c68d8",
      "created_time": "2022-01-18T18:55:56.176972-05:00",
      "modified_time": "2022-01-18T18:55:56.176972-05:00"
    }
    ```

##### Notes

None

# **Update Application**
##### Description
This endpoint will update the existing application.

##### URL

`https://biometricscloud.net/api/v1/application/1`

##### Method

`PUT`

##### URL Params

None

##### Required

None

##### Data Params

Field | Description
--------- | -----------
`name` | The name of the third-party application to display to users.
`description` | The description of the third-party application to display to users.
`website_url` | The URL of the brochure website the user will be redirected to from their dashboard.
`scope` | Only accepted value is `all`.
`redirect_url` | The URL that the user will be redirected to once successful `authorization grant` was completed by the user.
`image_url` | The URL of the thumbnail that will be displayed for third-party application.


##### Sample Call

Run the following in your terminal:

```shell
curl -X PUT \
    -H "Content-Type: application/json" \
    -H "Authorization: Bearer VSvXrNLlQCeCdTJjGUJgKw" \
    -d '{"name":"Third Party App","description":"Third Party App","website_url":"http://127.0.0.1:8000","scope":"all","redirect_url":"http://127.0.0.1:8001/appauth/code","image_url":"http://127.0.0.1:8001/static/logo.png"}' \
    https://biometricscloud.net/api/v1/application/1
```

##### Success Response

  * **Status**: `200`
  * **Content**:
    ```json
    {
      "id": 1,
      "uuid": "f9cca4ab-bbd8-4ed7-b928-489e8a17e1b7",
      "tenant_id": 3,
      "name": "Third Party App",
      "description": "Third Party App",
      "website_url": "http://127.0.0.1:8000",
      "scope": "all",
      "redirect_url": "http://127.0.0.1:8001/appauth/code",
      "image_url": "http://127.0.0.1:8001/static/logo.png",
      "state": 5,
      "created_time": "2022-01-18T18:55:56.176972-05:00",
      "modified_time": "2022-01-18T18:55:56.176972-05:00"
    }
    ```

##### Notes

None

# **Delete Application**
##### Description
This endpoint will disable the application; as a result, third-party application won't have access to the user's resources.

##### URL

`https://biometricscloud.net/api/v1/application/1`

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
curl -X DELETE "https://biometricscloud.net/api/v1/application/1" \
     -H "Authorization: Bearer VSvXrNLlQCeCdTJjGUJgKw"
```

##### Success Response

  * **Status**: `204`
  * **Content**: None

##### Notes

None
