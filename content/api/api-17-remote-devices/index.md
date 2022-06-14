---
title: 'Remote Devices Endpoints'
date: 2019-02-11T19:27:37+10:00
draft: false
weight: 9
summary: "CRUD endpoints pertaining to applications."
---

BiometricsCloud supports third-party applications powered by the internal `oAuth 2.0` server.

# **List Supported Remote Devices (Pre-Registration)**
##### Description
List all the third-party remote devices that are supported by the platform.

##### URL

`https://biometricscloud.net/api/v1/remote-devices/register`

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
        "ouraring":"https://cloud.ouraring.com/oauth/authorize?client_id=B6CM2DCLF2E2YV4G&client_secret=KMIC4NJ5B5DIO7T3A4CVVBZ3EZDOURGU&state=1-1&redirect_uri=https%3A%2F%2Fbiometricscloud.net%2Fapi%2Fv1%2Fcallback%2Fouraring&response_type=code",
        "healthkit":"https://apps.apple.com/ca/app/remote-health-data-uploader/id1617375216"
    }
    ```

##### Sample Call

Run the following in your terminal:

```shell
curl -X GET \
    -H "Content-Type: application/json" \
    -H "Authorization: Bearer $BIOMETRICSCLOUD_ACCESS_TOKEN" \
    https://biometricscloud.net/api/v1/remote-devices/register
```

**OR**

```shell
curl -X GET \
    -H "Content-Type: application/json" \
    -H "Authorization: Bearer $BIOMETRICSCLOUD_ACCESS_TOKEN" \
    http://localhost:8000/api/v1/remote-devices/register
```

##### Notes

None


# **Register OURA Ring Remote Device**
##### Description
The callback URL that OURA Ring web-services used in the `oAuth 2.0` authentication flow.

##### URL

`https://biometricscloud.net/api/v1/remote-devices/register/ouraring`

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

    ```

##### Sample Call

Run the following in your terminal:

```shell
curl -X GET \
    -H "Content-Type: application/json" \
    -H "Authorization: Bearer $BIOMETRICSCLOUD_ACCESS_TOKEN" \
    https://biometricscloud.net/api/v1/remote-devices/register/ouraring
```

**OR**

```shell
curl -X GET \
    -H "Content-Type: application/json" \
    -H "Authorization: Bearer $BIOMETRICSCLOUD_ACCESS_TOKEN" \
    http://localhost:8000/api/v1/remote-devices/register/ouraring
```

##### Notes

None
