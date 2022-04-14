---
title: 'Metric Endpoints'
date: 2019-02-11T19:27:37+10:00
draft: false
weight: 6
summary: "CRUD endpoints pertaining device metrics"
---
The following endpoints provide CRUD operations on our metrics.

# **Create Metric**
##### Description
This endpoint will create metric for an existing device.

##### URL

`https://biometricscloud.net/api/v1/metrics`

##### Method

`POST`

##### URL Params

None

##### Data Params

Field | Required | Example | Description
--------- | ----------- | ----------- | -----------
`device_id` | Yes | 1 | The device ID that the metric belongs to.
`name` | Yes | Heart Rate Monitor | The name of the metric.
`sample_type` | Yes | heartRate | The type of measurement or reading being conducted. Please use identifiers as found on [Apple's HealthKit](https://developer.apple.com/documentation/healthkit) if you are using an Apple device.
`sample_type_other` | No | hospitalHeartRateMachine | (Optional) Custom type of measurement not specified by the device's manufacturer.
`quantity_type`| No | bpm | The unit of measure for metric. A complete list can be found via [wikipedia](https://en.wikipedia.org/wiki/International_System_of_Units).
`quantity_type_other` | Yes | bph | The custom unit of measure not specified by the device's manufacturer.
`is_continuous_data` | Yes | false | Specifies if the data is continuous or discrete.

##### Success Response

  * **Status**: `200`
  * **Content**:
    ```json
    {
        "id": 1,
        "uuid": "ef8ebfd0-2f23-4bd2-a3f0-0457f070e6af",
        "tenant_id": 1,
        "device_id": 1,
        "device_uuid": "7a88177e-62dc-4e6a-b472-606defdcf375",
        "device_name": "iPhone",
        "user_id": 2,
        "name": "Heart Rate Monitor",
        "sample_type": "heartRate",
        "quantity_type": "bpm",
        "application_id": null,
        "application_name": null,
        "avg_yesterday": null,
        "avg_today": null,
        "avg_this_week": null,
        "avg_last_week": null,
        "avg_this_month": null,
        "avg_last_month": null,
        "avg_this_year": null,
        "avg_last_year": null,
        "latest_results_str": null,
        "latest_value": null,
        "latest_timestamp": null
    }
    ```

##### Sample Call

Run the following in your terminal:

```shell
curl -X POST \
    -H "Content-Type: application/json" \
    -H "Authorization: Bearer $BIOMETRICSCLOUD_ACCESS_TOKEN" \
    -d '{"device_id":1,"name":"Heart Rate Monitor", "sample_type":"heartRate","quantity_type":"bpm","is_continuous_data":false}' \
    https://biometricscloud.net/api/v1/metrics
```

**OR**

```shell
curl -X POST \
    -H "Content-Type: application/json" \
    -H "Authorization: Bearer $BIOMETRICSCLOUD_ACCESS_TOKEN" \
    -d '{"device_id":1,"name":"Heart Rate Monitor", "sample_type":"heartRate","quantity_type":"bpm","is_continuous_data":false}' \
    http://127.0.0.1:8000/api/v1/metrics
```

##### Notes

None

# **List Metrics**
##### Description
This endpoint will return a list of metrics being tracked by the system.

##### URL

`https://biometricscloud.net/api/v1/metrics`

##### Method

`GET`

##### URL Params

Query Parameters | Required | Default | Description
--------- | ----------- | ----------- | -----------
`offset` | Yes | 0 | The `ID` of the record in the list which will be used as to filter any records less then this value.
`limit` | Yes | 100 | The maximum number of entries to return in the pagination.
`sort_order` | Yes | asc | Either the `asc` (ascending) or `desc` (descending) order to return the results as.
`sort_field` | Yes | id | The column to sort by.

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
                "uuid": "ef8ebfd0-2f23-4bd2-a3f0-0457f070e6af",
                "tenant_id": 1,
                "device_id": 1,
                "device_uuid": "7a88177e-62dc-4e6a-b472-606defdcf375",
                "device_name": "iPhone",
                "user_id": 2,
                "name": "Heart Rate Monitor",
                "sample_type": "heartRate",
                "quantity_type": "bpm",
                "application_id": null,
                "application_name": null,
                "avg_yesterday": null,
                "avg_today": null,
                "avg_this_week": null,
                "avg_last_week": null,
                "avg_this_month": null,
                "avg_last_month": null,
                "avg_this_year": null,
                "avg_last_year": null,
                "latest_results_str": null,
                "latest_value": null,
                "latest_timestamp": null,
                "created_time": "2022-02-06T01:05:13.443195-05:00",
                "modified_time": "2022-02-06T01:05:13.443195-05:00"
            }
        ]
    }
    ```

##### Sample Call

Run the following in your terminal:

```shell
curl "https://biometricscloud.net/api/v1/metrics" \
    -H "Authorization: Bearer $BIOMETRICSCLOUD_ACCESS_TOKEN" \
    -H "Content-Type: application/json"
```

**OR**

```shell
curl "http://127.0.0.1:8000/api/v1/metrics" \
    -H "Authorization: Bearer $BIOMETRICSCLOUD_ACCESS_TOKEN" \
    -H "Content-Type: application/json"
```

##### Notes

None


# **Retrieve Metric**
##### Description
This endpoint will retrieve the metric detail.

##### URL

`https://biometricscloud.net/api/v1/metric/1`

##### Method

`POST`

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
        "uuid": "ef8ebfd0-2f23-4bd2-a3f0-0457f070e6af",
        "tenant_id": 1,
        "device_id": 1,
        "device_uuid": "7a88177e-62dc-4e6a-b472-606defdcf375",
        "device_name": "iPhone",
        "user_id": 2,
        "name": "Heart Rate Monitor",
        "sample_type": "heartRate",
        "quantity_type": "bpm",
        "application_id": null,
        "application_name": null,
        "avg_yesterday": null,
        "avg_today": null,
        "avg_this_week": null,
        "avg_last_week": null,
        "avg_this_month": null,
        "avg_last_month": null,
        "avg_this_year": null,
        "avg_last_year": null,
        "latest_results_str": null,
        "latest_value": null,
        "latest_timestamp": null
    }
    ```

##### Sample Call

Run the following in your terminal:

```shell
curl "https://biometricscloud.net/api/v1/metric/1" \
    -H "Authorization: Bearer $BIOMETRICSCLOUD_ACCESS_TOKEN" \
    -H "Content-Type: application/json"
```

**OR**


```shell
curl "http://127.0.0.1:8000/api/v1/metric/1" \
    -H "Authorization: Bearer $BIOMETRICSCLOUD_ACCESS_TOKEN" \
    -H "Content-Type: application/json"
```

##### Notes

None
