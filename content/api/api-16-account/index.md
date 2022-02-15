---
title: 'Account Endpoints'
date: 2019-02-11T19:27:37+10:00
draft: false
weight: 17
summary: "The endpoints pertaining to account operations."
---

# **Retrieve Account**
##### Description
This endpoint will return the account details of the current authenticated user account.

##### URL

`https://biometricscloud.net/api/v1/account`

##### Method

`GET`

##### URL Params

None

##### Required

None

##### Data Params

None

##### Success Response

  * **Status**: `200`
  * **Content**:
    ```json
    {
        "id": 1,
        "uuid": "ace76284-7268-4e20-bfa6-f6bf589c24f2",
        "email": "fherbert@dune.com",
        "first_name": "Frank",
        "last_name": "Herbert",
        "name": "Frank Herbert",
        "lexical_name": "Herbert, Frank",
        "state": 1,
        "timezone": "UTC",
        "language": "en",
        "country": "Canada",
        "country_tel_code": "1",
        "telephone": "(123) 456-7898",
        "agree_tos": true,
        "created_time": "2022-01-27T23:56:57.617698-05:00",
        "modified_time": "2022-01-29T13:31:55.362209-05:00",
        "joined_time": "0000-12-31T18:42:28-05:17",
        "avatar_title": "avatar.png",
        "avatar_file_url": "https://ipreqnancy-qa.nyc3.digitaloceanspaces.com/tenant/1/private/uploads/test-8ce0162b-c9bb-48b3-b517-5ff279430c70-lalal.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=ECYCCCUHLER27NMNI5OE%2F20220126%2Fus-east-3%2Fs3%2Faws4_request&X-Amz-Date=20220126T071952Z&X-Amz-Expires=900&X-Amz-SignedHeaders=host&X-Amz-Signature=ecbf85062c7ab37a1f3e1c50ff86818e50cb221ed8268a6e13cd1fa8132fa01c",
        "date_of_birth": "1990-01-01T00:00:00Z",
        "gender": null,
        "marital_status": "married",
        "children_count": 1,
        "blood_group": "O+",
        "height_in_meters": 123,
        "weight_in_kg": 90,
        "body_mass_index": null,
        "body_fat_percentage": 10,
        "allergies": [
            {
                "id": 1,
                "text": "Balsam of Peru"
            },
            {
                "id": 2,
                "text": "Buckwheat"
            },
            {
                "id": 3,
                "text": "Celery"
            }
        ],
        "illnesses": [
            {
                "id": 1,
                "text": "Abdominal aortic aneurysm"
            },
            {
                "id": 2,
                "text": "Acne"
            },
            {
                "id": 3,
                "text": "Acute cholecystitis"
            }
        ]
    }
    ```

##### Sample Call

Run the following in your terminal:

```shell
curl "https://biometricscloud.net/api/v1/account" \
    -H "Authorization: Bearer _YFuLvb5S0Ok4xUOv-nojA" \
    -H "Content-Type: application/json"
```

**OR**

```shell
curl "http://127.0.0.1:8000/api/v1/account" \
    -H "Authorization: Bearer _YFuLvb5S0Ok4xUOv-nojA" \
    -H "Content-Type: application/json"
```

##### Notes

None

# **Avatar Upload Operation**
##### Description
This endpoint uploads the user profile picture.

*Note (1): [This app](https://www.w3docs.com/tools/image-base64) which will convert images to `base64`.*

*Note (2): Replace `\u0026` with `&` in your `avatar_file_url"` field if it exists.*

##### URL

`https://biometricscloud.net/api/v1/account/avatar`

##### Method

`POST`

##### URL Params

None

##### Required

None

##### Data Params

Field | Description
--------- | -----------
`upload_content` | The `base64` content of the image.
`upload_filename` | The file name of the image.

##### Success Response

  * **Status**: `200`
  * **Content**:
    ```json
    {
        "id": 1,
        "uuid": "ace76284-7268-4e20-bfa6-f6bf589c24f2",
        "email": "fherbert@dune.com",
        "first_name": "Frank",
        "last_name": "Herbert",
        "name": "Frank Herbert",
        "lexical_name": "Herbert, Frank",
        "state": 1,
        "timezone": "UTC",
        "language": "en",
        "country": "Canada",
        "country_tel_code": "1",
        "telephone": "(123) 456-7898",
        "agree_tos": true,
        "created_time": "2022-01-27T23:56:57.617698-05:00",
        "modified_time": "2022-01-29T13:31:55.362209-05:00",
        "joined_time": "0000-12-31T18:42:28-05:17",
        "avatar_title": "avatar.png",
        "avatar_file_url": "https://ipreqnancy-qa.nyc3.digitaloceanspaces.com/tenant/1/private/uploads/test-8ce0162b-c9bb-48b3-b517-5ff279430c70-lalal.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=ECYCCCUHLER27NMNI5OE%2F20220126%2Fus-east-3%2Fs3%2Faws4_request&X-Amz-Date=20220126T071952Z&X-Amz-Expires=900&X-Amz-SignedHeaders=host&X-Amz-Signature=ecbf85062c7ab37a1f3e1c50ff86818e50cb221ed8268a6e13cd1fa8132fa01c",
        "date_of_birth": "1990-01-01T00:00:00Z",
        "gender": null,
        "marital_status": "married",
        "children_count": 1,
        "blood_group": "O+",
        "height_in_meters": 123,
        "weight_in_kg": 90,
        "body_mass_index": null,
        "body_fat_percentage": 10,
        "allergies": [
            {
                "id": 1,
                "text": "Balsam of Peru"
            },
            {
                "id": 2,
                "text": "Buckwheat"
            },
            {
                "id": 3,
                "text": "Celery"
            }
        ],
        "illnesses": [
            {
                "id": 1,
                "text": "Abdominal aortic aneurysm"
            },
            {
                "id": 2,
                "text": "Acne"
            },
            {
                "id": 3,
                "text": "Acute cholecystitis"
            }
        ]
    }
    ```

##### Sample Call

Run the following in your terminal:

```shell
curl -X POST \
     -H "Content-Type: application/json" \
     -H "Authorization: Bearer VSvXrNLlQCeCdTJjGUJgKw" \
     -d '{"upload_content":"xyz","upload_filename":"lalal.png"}' \
     https://biometricscloud.net/api/v1/account/avatar
```

**OR**

```shell
curl -X POST \
     -H "Content-Type: application/json" \
     -H "Authorization: Bearer VSvXrNLlQCeCdTJjGUJgKw" \
     -d '{"upload_content":"xyz","upload_filename":"lalal.png"}' \
     http://127.0.0.1:8000/api/v1/account/avatar
```

##### Notes

None

# **Update Account**
##### Description
This endpoint will update the existing application.

##### URL

`https://biometricscloud.net/api/v1/account`

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
`scope`  | Only accepted value is `all`.
`redirect_url` | The URL that the user will be redirected to once successful `authorization grant` was completed by the user.
`image_url` | The URL of the thumbnail that will be displayed for third-party application.

##### Success Response

  * **Status**: `200`
  * **Content**:
    ```json
    {
        "id": 1,
        "uuid": "ace76284-7268-4e20-bfa6-f6bf589c24f2",
        "email": "fherbert@dune.com",
        "first_name": "Frank",
        "last_name": "Herbert",
        "name": "Frank Herbert",
        "lexical_name": "Herbert, Frank",
        "state": 1,
        "timezone": "UTC",
        "language": "en",
        "country": "Canada",
        "country_tel_code": "1",
        "telephone": "(123) 456-7898",
        "agree_tos": true,
        "created_time": "2022-01-27T23:56:57.617698-05:00",
        "modified_time": "2022-01-29T13:31:55.362209-05:00",
        "joined_time": "0000-12-31T18:42:28-05:17",
        "avatar_title": "avatar.png",
        "avatar_file_url": "https://ipreqnancy-qa.nyc3.digitaloceanspaces.com/tenant/1/private/uploads/test-8ce0162b-c9bb-48b3-b517-5ff279430c70-lalal.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=ECYCCCUHLER27NMNI5OE%2F20220126%2Fus-east-3%2Fs3%2Faws4_request&X-Amz-Date=20220126T071952Z&X-Amz-Expires=900&X-Amz-SignedHeaders=host&X-Amz-Signature=ecbf85062c7ab37a1f3e1c50ff86818e50cb221ed8268a6e13cd1fa8132fa01c",
        "date_of_birth": "1990-01-01T00:00:00Z",
        "gender": null,
        "marital_status": "married",
        "children_count": 1,
        "blood_group": "O+",
        "height_in_meters": 123,
        "weight_in_kg": 90,
        "body_mass_index": null,
        "body_fat_percentage": 10,
        "allergies": [
            {
                "id": 1,
                "text": "Balsam of Peru"
            },
            {
                "id": 2,
                "text": "Buckwheat"
            },
            {
                "id": 3,
                "text": "Celery"
            }
        ],
        "illnesses": [
            {
                "id": 1,
                "text": "Abdominal aortic aneurysm"
            },
            {
                "id": 2,
                "text": "Acne"
            },
            {
                "id": 3,
                "text": "Acute cholecystitis"
            }
        ]
    }
    ```

##### Sample Call

Run the following in your terminal:

```shell
clear; curl -X POST \
    -H "Content-Type: application/json" \
    -H "Authorization: Bearer 2lXO_fRkTZaK2bMesxdoMA" \
    -d '{"email":"fherbert@dune.com","first_name":"Frank","last_name":"Herbert","country":"Canada","country_tel_code":"1","telephone":"(123) 456-7898","date_of_birth":"1990-01-01","marital_status":"married","children_count":1,"blood_group":"O+","height_in_meters":123,"weight_in_kg":90,"body_mass_index":null,"body_fat_percentage":10,"illnesses":null,"allergies":null,"allergy_pks":[1,2,3], "illness_pks":[1,2,3]}' \
    https://biometricscloud.net/api/v1/account;
```

**OR**

```shell
clear; curl -X POST \
    -H "Content-Type: application/json" \
    -H "Authorization: Bearer 2lXO_fRkTZaK2bMesxdoMA" \
    -d '{"email":"fherbert@dune.com","first_name":"Frank","last_name":"Herbert","country":"Canada","country_tel_code":"1","telephone":"(123) 456-7898","date_of_birth":"1990-01-01","marital_status":"married","children_count":1,"blood_group":"O+","height_in_meters":123,"weight_in_kg":90,"body_mass_index":null,"body_fat_percentage":10,"illnesses":null,"allergies":null,"allergy_pks":[1,2,3], "illness_pks":[1,2,3]}' \
    http://127.0.0.1:8000/api/v1/account;
```

##### Notes

None

# **Vitals**
##### Description
This endpoint will return the vitals of the user's account at the present.

##### URL

`https://biometricscloud.net/api/v1/account/vitals`

##### Method

`GET`

##### URL Params

None

##### Required

None

##### Data Params

None

##### Success Response

  * **Status**: `200`
  * **Content**:
    ```json
    {
        "legend": [
            0,
            1,
            2,
            3,
            4,
            5,
            6
        ],
        "results": [
            {
                "name": "Blood Pressure",
                "type": "bloodPressure",
                "unit": "mm Hg",
                "data": []
            },
            {
                "name": "Heart Rate",
                "type": "heartRate",
                "unit": "bpm",
                "data": [
                    {
                        "timestamp": "2022-01-29T00:00:00-05:00",
                        "value": 48.924244
                    },
                    {
                        "timestamp": "2022-01-28T00:00:00-05:00",
                        "value": 47.96347
                    },
                    {
                        "timestamp": "2022-01-27T00:00:00-05:00",
                        "value": 49.113926
                    },
                    {
                        "timestamp": "2022-01-26T00:00:00-05:00",
                        "value": 52.83486
                    },
                    {
                        "timestamp": "2022-01-25T00:00:00-05:00",
                        "value": 50.986786
                    },
                    {
                        "timestamp": "2022-01-24T00:00:00-05:00",
                        "value": 50.99565
                    }
                ]
            },
            {
                "name": "Location",
                "type": "location",
                "unit": "latitude,longitude",
                "data": []
            },
            {
                "name": "Steps Count",
                "type": "stepCount",
                "data": []
            }
        ]
    }
    ```

##### Sample Call

Run the following in your terminal:

```shell
curl "https://biometricscloud.net/api/v1/account/vitals" \
    -H "Authorization: Bearer _YFuLvb5S0Ok4xUOv-nojA" \
    -H "Content-Type: application/json"
```

**OR**

```shell
curl "http://127.0.0.1:8000/api/v1/account/vitals" \
    -H "Authorization: Bearer _YFuLvb5S0Ok4xUOv-nojA" \
    -H "Content-Type: application/json"
```

##### Notes

None
