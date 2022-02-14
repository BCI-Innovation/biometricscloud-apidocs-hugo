---
title: 'Device Endpoints'
date: 2019-02-11T19:27:37+10:00
draft: false
weight: 5
summary: "CRUD endpoints pertaining devices."
---
The following endpoints provide CRUD operations on our devices.


# **Create Device**
##### Description
This endpoint will create device in the user's profile to allow `sample` data to be submitted.

Once the device(s) have been authorized, this endpoint will return `oauth2_client_id`, `oauth2_client_secret`, and `oauth2_redirect_url` values which must be stored securely. You may use this to get new access tokens. The access tokens are made by calling [`/token`](/api/api-9-oauth2/#refresh-token) endpoint. See `oAuth 2.0 Client Credentials Grant` flow.

##### URL

`https://ipregnancy.ws/api/v1/devices`

##### Method

`POST`

##### URL Params

None

##### Required

None

##### Data Params

Field | Example | Description
--------- | ----------- | -----------
`manufacturer` | Apple | The organization name which built the device. Available options: `Apple`.
`device_code` | iPhone1,1 | The device code given by the manufacturer. The code Apple provides to identify their hardware model. See [this link for more info](https://gist.github.com/adamawolf/3048717).
`is_test_mode` | false | Specify either `true` or `false` value to indicate this device, and all the included metrics (and their data) is either real production data or test data. Please note, you need to set the value `true` if you want to run a simulator on any of the metrics in this device.

##### Success Response

  * **Status**: `200`
  * **Content**:
    ```json
    {
        "id": 1,
        "uuid": "7a88177e-62dc-4e6a-b472-606defdcf375",
        "oauth2_client_id": "c30a3f16653951e7",
        "oauth2_client_secret": "bfb446ce6e334d69fa0a1850c6062546e8d737ea241311b7c3086de4918fda47adc5a546fe0d63b3d61a81ed82ef32e976d0965ac6ba6ebaaede1da60e03be03f5f288307ee5da5f826cdcb6687d24d821560acc3bc6e4b0d7d6d5a33e19a6ac0e17045b1ac5ee9e5de42c90029dc69a4bab61bf7112d62cab1b780f0c60c0b",
        "oauth2_redirect_url": "http://127.0.0.1:8000/appauth/code"
    }
    ```

##### Sample Call

Run the following in your terminal:

```shell
curl -X POST \
    -H "Content-Type: application/json" \
    -H "Authorization: Bearer _H33gILGSHecEEI0mcPkMA" \
    -d '{"manufacturer":"Apple","device_code":"iPhone1,1"}' \
    https://ipregnancy.ws/api/v1/applications
```

**OR**

```shell
curl -X POST \
    -H "Content-Type: application/json" \
    -H "Authorization: Bearer _H33gILGSHecEEI0mcPkMA" \
    -d '{"manufacturer":"Apple","device_code":"iPhone1,1"}' \
    http://127.0.0.1:8000/api/v1/devices
```

##### Notes

Please save the "client_id", "client_secret" and "redirect_url" values as you will not be getting them again. If you lose these values then you will need to create a new application.

# **List Devices**
##### Description
This endpoint will return a list of devices.

##### URL

`https://ipregnancy.ws/api/v1/devices`

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
curl "https://ipregnancy.ws/api/v1/devices" \
    -H "Authorization: Bearer _H33gILGSHecEEI0mcPkMA" \
    -H "Content-Type: application/json"
```

**OR**

```shell
curl "http://127.0.0.1:8000/api/v1/devices" \
    -H "Authorization: Bearer _H33gILGSHecEEI0mcPkMA" \
    -H "Content-Type: application/json"
```

##### Notes

None

# **Retrieve Device**
##### Description
This endpoint will retrieve the device detail.

##### URL

`https://ipregnancy.ws/api/v1/device/1`

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
curl "https://ipregnancy.ws/api/v1/device/1" \
    -H "Authorization: Bearer _H33gILGSHecEEI0mcPkMA" \
    -H "Content-Type: application/json"
```

**OR**


```shell
curl "http://localhost:8000/api/v1/device/1" \
    -H "Authorization: Bearer _H33gILGSHecEEI0mcPkMA" \
    -H "Content-Type: application/json"
```

##### Notes

None


# **Delete Device**
##### Description
This endpoint will disconnect/disable the device. To reconnect the device, please see the [device authorize](#device-authorization) endpoint.

##### URL

`https://ipregnancy.ws/api/v1/data-submission/device-authorize`

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
curl -X DELETE "https://ipregnancy.ws/api/v1/device/1" \
     -H "Authorization: Bearer _H33gILGSHecEEI0mcPkMA"
```

**OR**

```shell
curl -X DELETE "http://127.0.0.1:8000/api/v1/device/1" \
     -H "Authorization: Bearer _H33gILGSHecEEI0mcPkMA"
```

##### Notes

None
