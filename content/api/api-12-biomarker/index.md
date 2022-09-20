---
title: 'Biomarker Endpoints'
date: 2019-02-11T19:27:37+10:00
draft: false
weight: 12
summary: "The retrieve endpoints for the biomarker data."
---

# **List Allergies**
##### Description
This endpoint will return a list of allergies tracked by the system.

##### URL

`https://biometricscloud.net/api/v1/biomarkers`

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

    }
    ```

##### Sample Call

Run the following in your terminal:

```shell
curl "https://biometricscloud.net/api/v1/biomarkers" \
    -H "Authorization: Bearer $BIOMETRICSCLOUD_ACCESS_TOKEN" \
    -H "Content-Type: application/json"
```

**OR**

```shell
curl "http://127.0.0.1:8000/api/v1/biomarkers" \
    -H "Authorization: Bearer $BIOMETRICSCLOUD_ACCESS_TOKEN" \
    -H "Content-Type: application/json"
```

##### Notes

None
