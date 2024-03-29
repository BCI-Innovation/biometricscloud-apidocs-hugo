---
title: 'Quantity Sample Analyses Endpoints'
date: 2019-02-11T19:27:37+10:00
draft: false
weight: 7
summary: "The retrieve endpoints pertaining to quantity sample analyses."
---

## **List Calculations**
##### Description
This endpoint will return a list of sample calculations.

##### URL

`https://biometricscloud.net/api/v1/quantity-sample-calculations`

##### Method

`GET`

##### URL Params

Query Parameters | Description
--------- | -----------
`offset` | The index of the record in the list which will be used as to filter any records less then this value.
`limit` | The maximum number of entries to return in the pagination. Backend will not allow any value larger then 1000.
`function` | Only accepted value is `1` for *Average*.
`frequency` | Only accepted values are: `1` for *Day*, `2` for *Week*, `3` for *Frequency*, and `4` for *Year*.
`start_gt` | Filter calculations which has a start timestamp greater then inputed value.
`start_gte` | Filter calculations which has a start timestamp greater and or equal to inputed value.
`finish_lt` | Filter calculations which has a finish timestamp less then inputed value.
`finish_lte` | Filter calculations which has a finish timestamp less than or equal to inputed value.
`metric_id` | Filter based on the metric.

##### Required

* `metric_id`
* `function`

##### Data Params

None

##### Success Response

  * **Status**: `200`
  * **Content**:
    ```json
    {
        "next_timestamp": "2022-01-22T17:20:00-05:00",
        "count": 3,
        "results": ["..."]
    }
    ```

##### Sample Call

Run the following in your terminal:

```shell
curl "https://biometricscloud.net/api/v1/quantity-sample-calculations?metric_id=1" \
    -H "Authorization: Bearer $BIOMETRICSCLOUD_ACCESS_TOKEN" \
    -H "Content-Type: application/json"
```

**OR**

```shell
curl "http://127.0.0.1:8000/api/v1/quantity-sample-calculations?metric_id=1" \
    -H "Authorization: Bearer $BIOMETRICSCLOUD_ACCESS_TOKEN" \
    -H "Content-Type: application/json"
```

##### Notes

None
