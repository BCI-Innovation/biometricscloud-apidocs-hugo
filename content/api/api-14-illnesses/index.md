---
title: 'Illness Endpoints'
date: 2019-02-11T19:27:37+10:00
draft: false
weight: 15
summary: "The retrieve endpoints for the illness data."
---

# **List Illnesses**
##### Description
This endpoint will return a list of illnesses tracked by the system.

##### URL

`https://biometricscloud.net/api/v1/illnesses`

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
curl "https://biometricscloud.net/api/v1/illnesses" \
    -H "Authorization: Bearer $BIOMETRICSCLOUD_ACCESS_TOKEN" \
    -H "Content-Type: application/json"
```

**OR**

```shell
curl "http://127.0.0.1:8000/api/v1/illnesses" \
    -H "Authorization: Bearer $BIOMETRICSCLOUD_ACCESS_TOKEN" \
    -H "Content-Type: application/json"
```

##### Notes

None
