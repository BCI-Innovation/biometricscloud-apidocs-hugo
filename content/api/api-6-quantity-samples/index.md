---
title: 'Quantity Samples Endpoints'
date: 2019-02-11T19:27:37+10:00
draft: false
weight: 7
summary: "The create and retrieve endpoints pertaining to quantity samples."
---

Quantity samples represent a single health datapoint sample from a consumer wearable device (ex: iWatch). A sample can be discrete or continuous datapoint.

# **Create Quantity Sample**
##### Description
This endpoint will create sample for an existing device and metric.

##### URL

`https://biometricscloud.net/api/v1/quantity-samples`

##### Method

`POST`

##### URL Params

None


##### Data Params

Field | Required | Example | Description
--------- | ----------- | ----------- | -----------
`metric_id` | Yes | 1 | The metric ID that this sample belongs to.
`start_date` | Yes | 2022-01-12T06:33:26.696888Z | The date that this sample reading was taken on.  
`end_date` | Yes | 2022-01-12T06:33:26.696888Z | The date that this sample reading finished.
`quantity` | Yes | 60 | The value that was read by the sample.
`sample_motion_context` | No | Sedentary | (Optional) Specify any context related information pertaining to this sample, for example: active, Active, NotSet, Sedentary. For more information see [Apple HealthKit docs](https://developer.apple.com/documentation/healthkit/hkheartratemotioncontext).
`sample_sensor_location` | No | 2 |  The location ID of where on the body was this sample reading taken from. Options: (1) Chest (2) Wrist (3) Finger (4) Hand (5) EarLobe (6) Foot (0) Other. For more information see [Apple HealthKit docs](https://developer.apple.com/documentation/healthkit/hkmetadatakeyheartratesensorlocation).
`sample_sensor_location_other` | No | Neural interface | (Optional) The sensor location in a location that specified by the hardware manufacturer.

* *Note: Dates must be formatted using ["RFC3339"](https://golang.org/src/time/format.go) date/time standard or else API will return error.*

##### Success Response

  * **Status**: `201`
  * **Content**: None

##### Sample Call

Run the following in your terminal:

```shell
curl -X POST \
    -H "Content-Type: application/json" \
    -H "Authorization: Bearer VSvXrNLlQCeCdTJjGUJgKw" \
    -d '{"metric_id":1,"start_date":"2022-01-12T06:33:26.696888Z", "end_date":"2022-01-12T06:33:26.696888Z","quantity":123,"sample_motion_context":"Active","sample_sensor_location":2}' \
    https://biometricscloud.net/api/v1/quantity-samples
```

**OR**

```shell
curl -X POST \
    -H "Content-Type: application/json" \
    -H "Authorization: Bearer VSvXrNLlQCeCdTJjGUJgKw" \
    -d '{"metric_id":1,"start_date":"2022-01-12T06:33:26.696888Z", "end_date":"2022-01-12T06:33:26.696888Z","quantity":123,"sample_motion_context":"Active","sample_sensor_location":2}' \
    http://127.0.0.1:8000/api/v1/quantity-samples
```

##### Notes

* Article to help explain `RFC3339` format via link: [Understanding about RFC 3339 for Datetime and Timezone Formatting in Software Engineering
](https://medium.com/easyread/understanding-about-rfc-3339-for-datetime-formatting-in-software-engineering-940aa5d5f68a)

# **List Data**
##### Description
This endpoint will return a list of time-series data.

##### URL

`https://biometricscloud.net/api/v1/quantity-samples`

##### Method

`GET`

##### URL Params

Query Parameters | Required | Default | Description
--------- | ----------- | ----------- | -----------
`metric_id`  | Yes | - | The unique identification of the metric that belongs to the user that you want to return all the samples for.  
`offset` | No | 0 | The index of the record in the list which will be used as to filter any records less then this value.
`limit`| No | 100 | The maximum number of entries to return in the pagination. Backend will not allow any value larger then 1000.
`start_date_gt` | No | - | Filter time-series data which has a timestamp greater then inputed value.
`start_date_gte` | No | - | Filter time-series data which has a timestamp greater and or equal to inputed value.
`end_date_lt` | No | - | Filter time-series data which has a timestamp less then inputed value.
`end_date_lte` | No | - | Filter time-series data which has a timestamp less than or equal to inputed value.

*Note (1): Query parameter inputted values must be **number of milliseconds since January 1, 1970 00:00:00** as found in the JavaScript [`getTime()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date/getTime) function.*

*Note (2): Try running `console.log(new Date().getTime())` in your console to get an example of how the query parameter inputted value looks like.*

##### Data Params

None

##### Success Response

  * **Status**: `200`
  * **Content**:
    ```json
    {
        "next_timestamp": "2022-01-12T01:33:26.696888-05:00",
        "count": 1,
        "results": [
            {
                "uuid": "75c43142-c05d-4c0d-8e0e-a7a251a95b1c",
                "tenant_id": 1,
                "user_id": 2,
                "device_id": 1,
                "device_uuid": "7a88177e-62dc-4e6a-b472-606defdcf375",
                "device_name": "iPhone",
                "metric_id": 1,
                "metric_uuid": "ef8ebfd0-2f23-4bd2-a3f0-0457f070e6af",
                "sample_type": "heartRate",
                "sample_motion_context": "Active",
                "sample_sensor_location": 2,
                "start_date": "2022-01-12T01:33:26.696888-05:00",
                "end_date": "2022-01-12T01:33:26.696888-05:00",
                "quantity": 123,
                "quantity_type": "bpm",
                "is_continuous_data": false
            }
        ]
    }
    ```

##### Sample Call

Run the following in your terminal:

```shell
curl "https://biometricscloud.net/api/v1/quantity-samples?metric_id=1" \
    -H "Authorization: Bearer VSvXrNLlQCeCdTJjGUJgKw" \
    -H "Content-Type: application/json"
```

**OR**

```shell
curl "http://127.0.0.1:8000/api/v1/quantity-samples?metric_id=1" \
    -H "Authorization: Bearer VSvXrNLlQCeCdTJjGUJgKw" \
    -H "Content-Type: application/json"
```

##### Notes

None
