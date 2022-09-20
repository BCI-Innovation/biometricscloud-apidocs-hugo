---
title: 'Device Endpoints'
date: 2019-02-11T19:27:37+10:00
draft: false
weight: 4
summary: "CRUD endpoints pertaining devices."
---
The following endpoints provide CRUD operations on our devices.


# **Create Device**
##### Description
This endpoint will create device in the user's profile to allow `sample` data to be submitted.

Once the device(s) have been authorized, this endpoint will return `oauth2_client_id`, `oauth2_client_secret`, and `oauth2_redirect_url` values which must be stored securely. You may use this to get new access tokens. The access tokens are made by calling [`/token`](/api/api-9-oauth2/#refresh-token) endpoint. See `oAuth 2.0 Client Credentials Grant` flow.

##### URL

`https://biometricscloud.net/api/v1/devices`

##### Method

`POST`

##### URL Params

None

##### Data Params

Field | Required | Example | Description
--------- | ----------- | ----------- | -----------
`manufacturer` | Yes | Apple | The organization name which built the device. Available options: `Apple`.
`device_code` | Yes | iPhone1,1 | The device code given by the manufacturer. The code Apple provides to identify their hardware model. See [this link for more info](https://gist.github.com/adamawolf/3048717).
`is_test_mode` | No | false | Specify either `true` or `false` value to indicate this device, and all the included metrics (and their data) is either real production data or test data. Please note, you need to set the value `true` if you want to run a simulator on any of the metrics in this device.

##### Success Response

  * **Status**: `200`
  * **Content**:
    ```json
    {
        "id": 1,
        "uuid": "7a88177e-62dc-4e6a-b472-606defdcf375",
        "oauth2_client_id": "06a52a46bbad72a6",
        "oauth2_client_secret": "946bfb0372d38c8495a445f9432debec279de2ae4e1dd2ac14cd26b49c2113f03e5000298782e5e2a9ce358e54afbfc1dd671bed8c3be452bf63ded1752f9f44390356ef62a4d570b685411b81c80690e0601ea944f7129312487b669ef77956fdc2a7cff3ac112e6f1ebfc21944dd97baa8d02a6d5d0a09ca989b14920fbfa",
        "oauth2_redirect_url": "http://127.0.0.1:8000/appauth/code"
    }
    ```

##### Sample Call

Run the following in your terminal:

```shell
curl -X POST \
    -H "Content-Type: application/json" \
    -H "Authorization: Bearer $BIOMETRICSCLOUD_ACCESS_TOKEN" \
    -d '{"manufacturer":"Apple","device_code":"iPhone1,1"}' \
    https://biometricscloud.net/api/v1/devices
```

**OR**

```shell
curl -X POST \
    -H "Content-Type: application/json" \
    -H "Authorization: Bearer $BIOMETRICSCLOUD_ACCESS_TOKEN" \
    -d '{"manufacturer":"Apple","device_code":"iPhone1,1"}' \
    http://127.0.0.1:8000/api/v1/devices
```

##### Notes

**IMPORTANT:** Please save the `client_id`, `client_secret` and `redirect_url` values as you will not be getting them again. If you lose these values then you will need to create a new device and delete the existing one.

# **List Devices**
##### Description
This endpoint will return a list of devices.

##### URL

`https://biometricscloud.net/api/v1/devices`

##### Method

`GET`

##### URL Params

Query Parameters | Required | Default Value | Description
--------- | ----------- | ----------- | -----------
`offset` | No | 0 | The `ID` of the record in the list which will be used as to filter any records less then this value.
`limit` | No | 100 | The maximum number of entries to return in the pagination.
`sort_order` | No| asc | Either the `asc` (ascending) or `desc` (descending) order to return the results as.
`sort_field` | No| id | The column to sort by.

##### Data Params

None

##### Success Response

  * **Status**: `200`
  * **Content**:
    ```json
    {
        "next_id": 2,
        "count": 2,
        "results": [
            {
                "id": 1,
                "manufacturer": "Apple",
                "code": "iPhone1,1",
                "product_name": "iPhone",
                "state": 1
            },
            {
                "id": 2,
                "manufacturer": "Apple",
                "code": "Watch1,1",
                "product_name": "Apple Watch 38mm case",
                "state": 1
            }
        ]
    }
    ```

##### Sample Call

Run the following in your terminal:

```shell
curl "https://biometricscloud.net/api/v1/devices" \
    -H "Authorization: Bearer $BIOMETRICSCLOUD_ACCESS_TOKEN" \
    -H "Content-Type: application/json"
```

**OR**

```shell
curl "http://127.0.0.1:8000/api/v1/devices" \
    -H "Authorization: Bearer $BIOMETRICSCLOUD_ACCESS_TOKEN" \
    -H "Content-Type: application/json"
```

##### Notes

None

# **Retrieve Device**
##### Description
This endpoint will retrieve the device detail.

##### URL

`https://biometricscloud.net/api/v1/device/1`

##### Method

`GET`

##### URL Params

Query Parameters | Required | Default Value | Description
--------- | ----------- | ----------- | -----------
`device_id` | Yes  | - | The device identification that belongs to the user.

##### Data Params

None

##### Success Response

  * **Status**: `200`
  * **Content**:
    ```json
    {
        "id": 1,
        "uuid": "7a88177e-62dc-4e6a-b472-606defdcf375",
        "tenant_id": 1,
        "manufacturer": "Apple",
        "code": "iPhone1,1",
        "state": 1,
        "user_id": 2,
        "client_id": "c30a3f16653951e7",
        "created_time": "2022-02-06T00:54:45.249153-05:00",
        "modified_time": "2022-02-06T00:54:45.249154-05:00",
        "last_active_time": "2022-02-06T00:54:45.249154-05:00"
    }
    ```

##### Sample Call

Run the following in your terminal:

```shell
curl "https://biometricscloud.net/api/v1/device/1" \
    -H "Authorization: Bearer $BIOMETRICSCLOUD_ACCESS_TOKEN" \
    -H "Content-Type: application/json"
```

**OR**


```shell
curl "http://localhost:8000/api/v1/device/1" \
    -H "Authorization: Bearer $BIOMETRICSCLOUD_ACCESS_TOKEN" \
    -H "Content-Type: application/json"
```

##### Notes

None


# **Delete Device**
##### Description
This endpoint will disconnect/disable the device. To reconnect the device, please see the [device authorize](#device-authorization) endpoint.

##### URL

`https://biometricscloud.net/api/v1/data-submission/device-authorize`

##### Method

`DELETE`

##### URL Params

Query Parameters | Required | Default Value | Description
--------- | ----------- | ----------- | -----------
`device_id` | Yes  | - | The device identification that belongs to the user.

##### Data Params

None

##### Success Response

  * **Status**: `204`
  * **Content**: None

##### Sample Call

Run the following in your terminal:

```shell
curl -X DELETE "https://biometricscloud.net/api/v1/device/1" \
     -H "Authorization: Bearer $BIOMETRICSCLOUD_ACCESS_TOKEN"
```

**OR**

```shell
curl -X DELETE "http://127.0.0.1:8000/api/v1/device/1" \
     -H "Authorization: Bearer $BIOMETRICSCLOUD_ACCESS_TOKEN"
```

##### Notes

None
