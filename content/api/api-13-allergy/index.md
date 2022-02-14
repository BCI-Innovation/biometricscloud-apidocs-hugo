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

`https://ipregnancy.ws/api/v1/allergies`

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
curl "https://ipregnancy.ws/api/v1/allergies" \
    -H "Authorization: Bearer _H33gILGSHecEEI0mcPkMA" \
    -H "Content-Type: application/json"
```

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

##### Notes

None
