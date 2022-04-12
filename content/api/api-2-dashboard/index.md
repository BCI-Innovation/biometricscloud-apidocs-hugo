---
title: 'Dashboard Endpoints'
date: 2019-02-11T19:27:37+10:00
draft: false
weight: 3
summary: "The dashboard related endpoints are found here."
---

The dashboard related endpoints are found here.

# **Retrieve Dashboard**
##### Description
This endpoint will return the user's dashboard based on their running consumer wearables and time-series calculations.

*Developers note: If you are a third-party app developer, do not use this API for user login, please use the oAuth 2.0 [`password grant`](#password-grant) credentials*

##### URL

`https://biometricscloud.net/api/v1/dashboard`

##### Method

`GET`

##### URL Params

None

##### Data Params

None

##### Success Response

  * **Status**: `200`
  * **Content**:
    ```json
    {
      "metrics": [
        {
          "id": 4,
          "uuid": "22a1de82-cd2c-4b64-9cfe-acaf74ad2271",
          "tenant_id": 3,
          "device_id": 2,
          "device_uuid": "bf3dad8b-029d-4630-8912-44456460bf26",
          "user_id": 2,
          "type": "bloodPressure",
          "unit": "mm Hg",
          "application_id": null,
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
        },
        {
          "id": 3,
          "uuid": "3b6d487f-7da4-4159-99b8-f712f21343cb",
          "tenant_id": 3,
          "device_id": 2,
          "device_uuid": "bf3dad8b-029d-4630-8912-44456460bf26",
          "user_id": 2,
          "type": "heartRate",
          "unit": "bpm",
          "application_id": null,
          "avg_yesterday": 50.241076740035695,
          "avg_today": 49.07717231222386,
          "avg_this_week": 50.44312393887946,
          "avg_last_week": 49.01323360184119,
          "avg_this_month": 49.07717231222386,
          "avg_last_month": 50.241076740035695,
          "avg_this_year": 49.10269799825936,
          "avg_last_year": 50.007514334065824,
          "latest_results_str": null,
          "latest_value": 60,
          "latest_timestamp": "2022-01-16T15:43:53.141696-05:00",
          "latest_data": [
            {
              "metric_id": 3,
              "timestamp": "2022-01-16T15:43:53.141696-05:00",
              "value": 60
            },
            {
              "metric_id": 3,
              "timestamp": "2022-01-16T15:40:00-05:00",
              "value": 91
            },
            {
              "metric_id": 3,
              "timestamp": "2022-01-16T15:35:00-05:00",
              "value": 29
            },
            {
              "metric_id": 3,
              "timestamp": "2022-01-16T15:30:00-05:00",
              "value": 35
            },
            {
              "metric_id": 3,
              "timestamp": "2022-01-16T15:25:00-05:00",
              "value": null
            },
            {
              "metric_id": 3,
              "timestamp": "2022-01-16T15:20:00-05:00",
              "value": 57
            },
            {
              "metric_id": 3,
              "timestamp": "2022-01-16T15:15:00-05:00",
              "value": null
            },
            {
              "metric_id": 3,
              "timestamp": "2022-01-16T15:10:00-05:00",
              "value": 13
            },
            {
              "metric_id": 3,
              "timestamp": "2022-01-16T15:05:00-05:00",
              "value": null
            },
            {
              "metric_id": 3,
              "timestamp": "2022-01-16T15:00:00-05:00",
              "value": 22
            }
          ]
        },
        {
          "id": 2,
          "uuid": "9124ffea-5649-49e0-b620-053d076a5fe1",
          "tenant_id": 3,
          "device_id": 1,
          "device_uuid": "166bb639-0ff8-4a25-b35f-419d43b56f43",
          "user_id": 2,
          "type": "location",
          "unit": "latitude,longitude",
          "application_id": null,
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
        },
        {
          "id": 1,
          "uuid": "c799605c-7716-4fe2-bb3e-48553f4d8c3e",
          "tenant_id": 3,
          "device_id": 1,
          "device_uuid": "166bb639-0ff8-4a25-b35f-419d43b56f43",
          "user_id": 2,
          "type": "stepCount",
          "application_id": null,
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
      ],
      "user": {
          "id": 1,
          "uuid": "ace76284-7268-4e20-bfa6-f6bf589c24f2",
          "email": "fherbert@dune.com",
          "first_name": "Frank",
          "last_name": "Herbert",
          "name": "Frank Herbert",
          "lexical_name": "Herbert, Frank",
          "state": 1,
          "timezone": "UTC",
          "language": "en",
          "country": "Canada",
          "country_tel_code": "1",
          "telephone": "(123) 456-7898",
          "agree_tos": true,
          "created_time": "2022-01-27T23:56:57.617698-05:00",
          "modified_time": "2022-01-29T13:31:55.362209-05:00",
          "joined_time": "0000-12-31T18:42:28-05:17",
          "avatar_title": "avatar.png",
          "avatar_file_url": "https://ipreqnancy-qa.nyc3.digitaloceanspaces.com/tenant/1/private/uploads/test-8ce0162b-c9bb-48b3-b517-5ff279430c70-lalal.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=ECYCCCUHLER27NMNI5OE%2F20220126%2Fus-east-3%2Fs3%2Faws4_request&X-Amz-Date=20220126T071952Z&X-Amz-Expires=900&X-Amz-SignedHeaders=host&X-Amz-Signature=ecbf85062c7ab37a1f3e1c50ff86818e50cb221ed8268a6e13cd1fa8132fa01c",
          "date_of_birth": "1990-01-01T00:00:00Z",
          "gender": null,
          "marital_status": "married",
          "children_count": 1,
          "blood_group": "O+",
          "height_in_meters": 123,
          "weight_in_kg": 90,
          "body_mass_index": null,
          "body_fat_percentage": 10,
          "allergies": [
              {
                  "id": 1,
                  "text": "Balsam of Peru"
              },
              {
                  "id": 2,
                  "text": "Buckwheat"
              },
              {
                  "id": 3,
                  "text": "Celery"
              }
          ],
          "illnesses": [
              {
                  "id": 1,
                  "text": "Abdominal aortic aneurysm"
              },
              {
                  "id": 2,
                  "text": "Acne"
              },
              {
                  "id": 3,
                  "text": "Acute cholecystitis"
              }
          ]
      }
    }
    ```

##### Sample Call

Run the following in your terminal:

```shell
curl "https://biometricscloud.net/api/v1/dashboard" \
    -H "Authorization: Bearer $BIOMETRICSCLOUD_ACCESS_TOKEN" \
    -H "Content-Type: application/json"
```

**OR**

```shell
curl "http://127.0.0.1:8000/api/v1/dashboard" \
    -H "Authorization: Bearer $BIOMETRICSCLOUD_ACCESS_TOKEN" \
    -H "Content-Type: application/json"
```
