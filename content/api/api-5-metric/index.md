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

`https://ipregnancy.ws/api/v1/metrics`

##### Method

`POST`

##### URL Params

None

##### Required

None

##### Data Params

Field | Example | Description
--------- | ----------- | -----------
`device_id` | 1 | The device ID that the metric belongs to.
`name` | Heart Rate Monitor | The name of the metric.
`sample_type` | heartRate | The type of measurement or reading being conducted.  Please use identifiers as found on Apple's HealthKit if you are using an Apple device.
`sample_type_other` | hospitalHeartRateMachine | (Optiona) Custom type of measurement not specified by the device's manufacturer.
`quantity_type` | bpm | The unit of measure.
`quantity_type_other` | bph | The custom unit of measure not specified by the device's manufacturer.
`is_continuous_data` | false | Specifies if the data is continuous or discrete.

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
    -H "Authorization: Bearer _H33gILGSHecEEI0mcPkMA" \
    -d '{"device_id":2,"name":"Heart Rate Monitor", "sample_type":"heartRate","quantity_type":"bpm","is_continuous_data":false}' \
    https://ipregnancy.ws/api/v1/applications
```

**OR**

```shell
curl -X POST \
    -H "Content-Type: application/json" \
    -H "Authorization: Bearer _H33gILGSHecEEI0mcPkMA" \
    -d '{"device_id":1,"name":"Heart Rate Monitor", "sample_type":"heartRate","quantity_type":"bpm","is_continuous_data":false}' \
    http://127.0.0.1:8000/api/v1/metrics
```

##### Notes

None

# **List Metrics**
##### Description
This endpoint will return a list of metrics being tracked by the system.

##### URL

`https://ipregnancy.ws/api/v1/metrics`

##### Method

`GET`

##### URL Params

Query Parameters | Description
--------- | -----------
`offset` | The `ID` of the record in the list which will be used as to filter any records less then this value.
`limit` | The maximum number of entries to return in the pagination.
`sort_order` | Either the `asc` (ascending) or `desc` (descending) order to return the results as.
`sort_field` | The column to sort by.


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
curl "https://ipregnancy.ws/api/v1/metrics" \
    -H "Authorization: Bearer _H33gILGSHecEEI0mcPkMA" \
    -H "Content-Type: application/json"
```

**OR**

```shell
curl "http://127.0.0.1:8000/api/v1/metrics" \
    -H "Authorization: Bearer _H33gILGSHecEEI0mcPkMA" \
    -H "Content-Type: application/json"
```

##### Notes

None


# **Retrieve Metric**
##### Description
This endpoint will retrieve the metric detail.

##### URL

`https://ipregnancy.ws/api/v1/metric/1`

##### Method

`POST`

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
curl "https://ipregnancy.ws/api/v1/metric/1" \
    -H "Authorization: Bearer _H33gILGSHecEEI0mcPkMA" \
    -H "Content-Type: application/json"
```

**OR**


```shell
curl "http://127.0.0.1:8000/api/v1/metric/1" \
    -H "Authorization: Bearer _H33gILGSHecEEI0mcPkMA" \
    -H "Content-Type: application/json"
```

##### Notes

None
