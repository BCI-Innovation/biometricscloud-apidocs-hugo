---
title: 'Photo Samples Endpoints'
date: 2019-02-11T19:27:37+10:00
draft: false
weight: 8
summary: "The create and retrieve endpoints pertaining to photo samples."
---

Photo samples represent a single uploaded photo sample from a consumer wearable device (ex: Raspberry Pi Camera Module).

# **Create Photo Sample**
##### Description
This endpoint will create sample for an existing device and metric.

##### URL

`https://biometricscloud.net/api/v1/photo-samples`

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
`photo` | Yes | 60 | The value that was read by the sample.
`sample_motion_context` | No | Sedentary | (Optional) Specify any context related information pertaining to this sample, for example: active, Active, NotSet, Sedentary. For more information see [Apple HealthKit docs](https://developer.apple.com/documentation/healthkit/hkheartratemotioncontext).
`sample_sensor_location` | No | 2 |  The location ID of where on the body was this sample reading taken from. Options: (1) Chest (2) Wrist (3) Finger (4) Hand (5) EarLobe (6) Foot (0) Other. For more information see [Apple HealthKit docs](https://developer.apple.com/documentation/healthkit/hkmetadatakeyheartratesensorlocation).
`sample_sensor_location_other` | No | Neural interface | (Optional) The sensor location in a location that specified by the hardware manufacturer.
`upload_content` | The `base64` content of the image.
`upload_filename` | The file name of the image.

* *Note: Dates must be formatted using ["RFC3339"](https://golang.org/src/time/format.go) date/time standard or else API will return error.*

##### Success Response

  * **Status**: `201`
  * **Content**: None

##### Sample Call

Run the following in your terminal.

```shell
curl -X POST \
    -H "Content-Type: application/json" \
    -H "Authorization: Bearer $BIOMETRICSCLOUD_ACCESS_TOKEN" \
    -d '{"metric_id":1,"start_date":"2022-01-12T06:33:26.696888Z", "end_date":"2022-01-12T06:33:26.696888Z","photo":123,"sample_motion_context":"Active","sample_sensor_location":2, "upload_content":"<SEE NOTES BELOW>", "upload_filename":"lalal.png"}' \
    https://biometricscloud.net/api/v1/photo-samples
```

**OR**

```shell
curl -X POST \
    -H "Content-Type: application/json" \
    -H "Authorization: Bearer $BIOMETRICSCLOUD_ACCESS_TOKEN" \
    -d '{"metric_id":1,"start_date":"2022-01-12T06:33:26.696888Z", "end_date":"2022-01-12T06:33:26.696888Z","photo":123,"sample_motion_context":"Active","sample_sensor_location":2, "upload_content":"<SEE NOTES BELOW>", "upload_filename":"lalal.png"}' \
    http://127.0.0.1:8000/api/v1/photo-samples
```

##### Notes

* Article to help explain `RFC3339` format via link: [Understanding about RFC 3339 for Datetime and Timezone Formatting in Software Engineering
](https://medium.com/easyread/understanding-about-rfc-3339-for-datetime-formatting-in-software-engineering-940aa5d5f68a)
* Please note, you will need to run a [base64 encode](https://base64.guru/converter/encode/file) on the file you want to upload, copy and paste the `Data URI - data:content/type;base64` value into your sample and then run the command.
* You can use the following sample content for testing purposes only:

```text
iVBORw0KGgoAAAANSUhEUgAAABAAAAAPCAYAAADtc08vAAAABGdBTUEAANbY1E9YMgAAABl0RVh0U29mdHdhcmUAQWRvYmUgSW1hZ2VSZWFkeXHJZTwAAAKjSURBVHjadJNfSFNRGMC/e8/uxnVbVtoqJW1sBlFW9F8jtyIisHqIQQ9LDAqjggIfYhpFL6GDekkqhhU1/2SYkKKRLhCcL1OSwgfptoYo2l227V51Dtmf0zmbja3yg++ee78/v/N93zmXwRhDptjtdrDZbJfPnTp6I6/QWBSU5GXfxJdlJYcUnFZX4Xa7vZnxisyPlpZW9Lq9zeFoqL1kNBrguOUa3G+wQ2mRFqSQBPNs/iYSlgVgaAU1NTUQXorA8OBAZ/MLp8XrFUD8OgLms1Wg4hDEf46DgsFw+1FX3VbDtsZYLEo2a0kRKIBlmWMFunUdd29WYVkKYc/oJ3zk0F58omwnftNUjydcz7BvyIkvWk4K6/M2sGazOZlHNdmCJocvK9FvMe0wFsHIh1YApITKit0QjKpBo9VCPJGAcGQZzldWlAgz89c3FxQ0ZbXAMAxH3kuvXjjTf+uKJX9hcQkYFsG0Xwbd2hxQqThgSIBKyYGjcxAcbT2N81KojgLYFVCU6Njb90MdQTlMsKTveAKKN+YmkwJSOAmjkqdRwoIs9f2pgM2c6FxQvvPE2TPJq5QpKoGQ+YB3SgRhRoJoLAa6/FzqCvwXQER61eWy+aZFQCjlisbisG97MZh2FSbDV+Dq1QAQi8dd7tHxJVp6elAsSx9pIA1bFUBEFueCCyz7r0uhQPDDH6AEf9ZNNBgMKRpJ+u6bBERW5q9kamMBQzCCkVqz5jQxNacBHo8nGaQlZ26rq1d7Bnt5uhtHFCGycgqgR/u4te/Xx1Hh5cED+2ezKigvL09XIIpiQpKk2qft/Q9Nh/fkzs5Mw7gwFXg3MNyLEX+vurp60mq1Zv9MgiBkVrtI9LnLM2Ed++aP8Dz/oLu7+zOxhfR6Pb10Wa39FmAAqAgNiwPnYuoAAAAASUVORK5CYII=
```

# **List Data**
##### Description
This endpoint will return a list of time-series data.

##### URL

`https://biometricscloud.net/api/v1/photo-samples`

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
                "photo": 123,
                "photo_type": "bpm",
                "is_continuous_data": false
            }
        ]
    }
    ```

##### Sample Call

Run the following in your terminal:

```shell
curl "https://biometricscloud.net/api/v1/photo-samples?metric_id=1" \
    -H "Authorization: Bearer $BIOMETRICSCLOUD_ACCESS_TOKEN" \
    -H "Content-Type: application/json"
```

**OR**

```shell
curl "http://127.0.0.1:8000/api/v1/photo-samples?metric_id=1" \
    -H "Authorization: Bearer $BIOMETRICSCLOUD_ACCESS_TOKEN" \
    -H "Content-Type: application/json"
```

##### Notes

None
