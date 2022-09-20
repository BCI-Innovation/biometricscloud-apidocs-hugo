---
title: 'Metric Operation Endpoints'
date: 2019-02-11T19:27:37+10:00
draft: false
weight: 8
summary: "Perform various operations on the data within a metric."
---
Perform various operations on the data within a metric.

# **Create Simulator**
##### Description
This endpoint creates a metric simulator to run in the background and periodically create **random time-series data** for the particular metric. The background simulator will generate a random value in between the specified `max_value` and `min_value` fields; in addition, the `null_probability_percent` field controls whether the simulator adds nulls. Simulators allow you to fill random time-seres data for a particular metric.


##### URL

`https://biometricscloud.net/api/v1/metric-operations/simulators`

##### Method

`POST`

##### URL Params

None

##### Required

None

##### Data Params

Field | Description
--------- | -----------
`metric_id` | The `id` value of the metric you want to attach the simulator to. Please note `is_test_mode` needs to be enabled for the metric for this simulator to work.
`max_value`  |  xxx
`min_value` | xxx
`null_probability_percent` |  xxx

##### Success Response

  * **Status**: `200`
  * **Content**:
    ```json
    {
        "metric_id": 3,
        "min_value": 60,
        "max_value": 120,
        "null_probability_percent": 10
    }
    ```

##### Sample Call

Run the following in your terminal:

```shell
curl -X POST \
     -H "Content-Type: application/json" \
     -H "Authorization: Bearer $BIOMETRICSCLOUD_ACCESS_TOKEN" \
     -d '{"metric_id":1,"max_value":120,"min_value":60,"null_probability_percent":10}' \
     https://biometricscloud.net/api/v1/metric-operations/simulators
```

**OR**

```shell
curl -X POST \
     -H "Content-Type: application/json" \
     -H "Authorization: Bearer $BIOMETRICSCLOUD_ACCESS_TOKEN" \
     -d '{"metric_id":1,"max_value":120,"min_value":60,"null_probability_percent":10}' \
     http://127.0.0.1:8000/api/v1/metric-operations/simulators
```

##### Notes

None

# **List Simulators**
##### Description
This endpoint will return a list of active metric simulators.

##### URL

`https://biometricscloud.net/api/v1/metric-operations/simulators`

##### Method

`POST`

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
        "next_id": 1,
        "count": 1,
        "results": [
            {
               "metric_id": 3,
               "min_value": 60,
               "max_value": 120,
               "null_probability_percent": 10
            }
        ]
    }
    ```

##### Sample Call

Run the following in your terminal:

```shell
curl "https://biometricscloud.net/api/v1/metric-operations/simulators" \
    -H "Authorization: Bearer $BIOMETRICSCLOUD_ACCESS_TOKEN" \
    -H "Content-Type: application/json"
```

**OR**


```shell
curl "http://127.0.0.1:8000/api/v1/metric-operations/simulators" \
    -H "Authorization: Bearer $BIOMETRICSCLOUD_ACCESS_TOKEN" \
    -H "Content-Type: application/json"
```


##### Notes

None

# **Delete Simulator**
##### Description
This endpoint stops and deletes the simulator. Cannot resume later.

##### URL

`https://biometricscloud.net/api/v1/metric-operations/simulator/3`

##### Method

`DELETE`

##### URL Params

None

##### Required

None

##### Data Params

None

##### Sample Call

Run the following in your terminal:

##### Success Response

  * **Status**: `204`
  * **Content**: None

```shell
curl -X DELETE \
    -H "Content-Type: application/json" \
    -H "Authorization: Bearer $BIOMETRICSCLOUD_ACCESS_TOKEN" \
    https://biometricscloud.net/api/v1/metric-operations/simulator/3
```

**OR**

```shell
curl -X DELETE \
    -H "Content-Type: application/json" \
    -H "Authorization: Bearer $BIOMETRICSCLOUD_ACCESS_TOKEN" \
    http://127.0.0.1:8000/api/v1/metric-operations/simulator/3
```

##### Notes

None

# **Seed**
##### Description
This endpoint will load in the background 2 years worth of random data. The data will be randomly picked between the `min_value` and `max_value` field values specified at the call; in addition, random *null* values will be inserted based on the `null_probability_percent` field value.

##### URL

`https://biometricscloud.net/api/v1/metric-operations/seed`

##### Method

`POST`

##### URL Params

None

##### Required

None

##### Data Params

Field | Description
--------- | -----------
`metric_id` | The `id` value of the metric you want to attach the simulator to. Please note `is_test_mode` needs to be enabled for the metric for this simulator to work.
`max_value`  |  xxx
`min_value` | xxx
`null_probability_percent` |  xxx

##### Success Response

  * **Status**: `201`
  * **Content**: None

##### Sample Call

Run the following in your terminal:

```shell
curl -X POST \
     -H "Content-Type: application/json" \
     -H "Authorization: Bearer $BIOMETRICSCLOUD_ACCESS_TOKEN" \
     -d '{"metric_id":"1","max_value":"120","min_value":"60","null_probability_percent":"10"}' \
     https://biometricscloud.net/api/v1/metric-operations/seed
```

**OR**

```shell
curl -X POST \
     -H "Content-Type: application/json" \
     -H "Authorization: Bearer $BIOMETRICSCLOUD_ACCESS_TOKEN" \
     -d '{"metric_id":"3","max_value":"120","min_value":"60","null_probability_percent":"10"}' \
     http://127.0.0.1:8000/api/v1/metric-operations/seed
```

##### Notes

None
