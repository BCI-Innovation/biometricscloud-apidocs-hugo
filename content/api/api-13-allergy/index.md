---
title: 'Allergy Endpoints'
date: 2019-02-11T19:27:37+10:00
draft: false
weight: 14
summary: "The retrieve endpoints for the allergy data."
---

# **List Allergies**
##### Description
This endpoint will return a list of allergies tracked by the system.

##### URL

`https://biometricscloud.net/api/v1/allergies`

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
        "count": 3,
        "results": [
            {
                "id": 1,
                "text": "Balsam of Peru"
            },
            {
                "id": 2,
                "text": "Buckwheat"
            },
            {
                "id": 35,
                "text": "Cat"
            }        
        ]
    }
    ```

##### Sample Call

Run the following in your terminal:

```shell
curl "https://biometricscloud.net/api/v1/allergies" \
    -H "Authorization: Bearer $BIOMETRICSCLOUD_ACCESS_TOKEN" \
    -H "Content-Type: application/json"
```

**OR**

```shell
curl "http://127.0.0.1:8000/api/v1/allergies" \
    -H "Authorization: Bearer $BIOMETRICSCLOUD_ACCESS_TOKEN" \
    -H "Content-Type: application/json"
```

##### Notes

None
