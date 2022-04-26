---
title: 'Gateway Endpoints'
date: 2019-02-11T19:27:37+10:00
weight: 2
summary: "The API gateway deals with registration and login of users along with other misc functions."
---

The API gateway deals with registration and login of users along with other misc functions.

# **Version**

##### Description

This endpoint will return the version of the platform.

##### URL

`https://biometricscloud.net/api/v1/version`

##### Method

`GET`

##### URL Params

None

##### Data Params

None

##### Success Response

  * **Status**: `200`
  * **Content**:
    ```text
    BiometricsCloud Backend v1.0
    ```

##### Sample Call

Run the following in your terminal:
```shell
curl "https://biometricscloud.net/api/v1/version"
```

**OR**

Run the following in your terminal for your **developer** instance:
```shell
curl "http://localhost:8000/api/v1/version"
```

##### Notes
If you are implementing our API for your third-party app, this is a useful API to try to get working with your system before proceeding forwards.

# **Greeting**
##### Description

This endpoint return a greeting for the specified name.

##### URL

`https://biometricscloud.net/api/v1/greeting`

##### Method

`POST`

##### URL Params

None

##### Data Params

Parameter | Required | Description
--------- | ------- | -----------
`name` | Yes | The name to test out with the API endpoint.

##### Success Response

  * **Status**: `200`
  * **Content**:
    ```json
    {"message":"Hello,Frank Herbert"}
    ```

##### Sample Call

Run the following in your terminal:

```shell
curl -X POST -H "Content-Type: application/json" \
     -d '{"name": "Frank Herbert"}' \
     https://biometricscloud.net/api/v1/greeting
```

**OR**

```shell
curl -X POST -H "Content-Type: application/json" \
     -d '{"name": "Frank Herbert"}' \
     http://localhost:8000/api/v1/greeting
```

# **Registration**
##### Description

This endpoint registers a new user in our system.

##### URL

`https://biometricscloud.net/api/v1/register`

##### Method

`POST`

##### URL Params

None

##### Data Params

Field | Required | Description
--------- | ----------- | -----------
`username` | Yes | The  unique name to identify your account.
`first_name` | Yes | The first name of the user.
`middle_name` | No | The middle name of the user.
`last_name` | Yes | The last name of the user.  
`country` | Yes | The country of origin for the user.
`country_tel_code` Yes | | The country code for the telephone.
`telephone` | Yes | The telephone number for the user.
`email` | Yes | The email address for the user.  
`agree_tos` | Yes | True or false value depending if the user agreed to the terms of service.
`password` | Yes | The password to use for securing the user account.
`password_repeat` | Yes | The password repeated to ensure user entered correct password.

##### Success Response

  * **Status**: `200`
  * **Content**:
    ```json
    {
      "username": "fherbert",
      "tenant_id": 2,
      "tenant_schema_name": "",
      "first_name": "Frank",
      "middle_name": "",
      "last_name": "Herbert",
      "email": "fherbert@dune.com",
      "role_id": 2,
      "language": "en",
      "country_tel_code": "",
      "telephone": "",
      "agree_tos": false,
      "access_token": "ugvzcBY-QxO4BkRFrF9FuQ",
      "token_type": "Bearer",
      "refresh_token": "2vR8dicaSdOpFJqfSZuQRw",
      "expiry": "2022-01-18T04:19:13.236475225Z"
    }
    ```

##### Sample Call

Run the following in your terminal:

```shell
curl -X POST -H "Content-Type: application/json" \
     -d '{"username":"fherbert","agree_tos":true,"country":"Canada","country_tel_code":"1","email":"fherbert@dune.com","first_name":"Frank","last_name":"Herbert","password":"pleasechangeme","password_repeat":"pleasechangeme","telephone":"(123) 456-7898"}' \
     https://biometricscloud.net/api/v1/register
```

**OR**


```shell
curl -X POST -H "Content-Type: application/json" \
     -d '{"username":"fherbert","agree_tos":true,"country":"Canada","country_tel_code":"1","email":"fherbert@dune.com","first_name":"Frank","last_name":"Herbert","password":"pleasechangeme","password_repeat":"pleasechangeme","telephone":"(123) 456-7898"}' \
     http://localhost:8000/api/v1/register
```


##### Notes

You are provided the access tokens so you can immediately start making calls to the protected API endpoints without logging in.

Please note except username, all other fields get saved to the database using `AES` encryption. This platform utilizes data at rest encryption.

For the remainder of this tutorial, please use enviornment variables for the `access_token` and `refresh_token` by running the following:

```bash
export BIOMETRICSCLOUD_ACCESS_TOKEN=ugvzcBY-QxO4BkRFrF9FuQ
export BIOMETRICSCLOUD_REFRESH_TOKEN=2vR8dicaSdOpFJqfSZuQRw
```


# **Login**
##### Description
This endpoint will authenticate the user account for the provided `email` and `password` fields.

*Developers note: If you are a third-party app developer, do not use this API for user login, please use the oAuth 2.0 [`password grant`](#password-grant) credentials*

##### URL

`https://biometricscloud.net/api/v1/login`

##### Method

`POST`

##### URL Params

None

##### Required

None

##### Data Params

Field | Required | Description
--------- | ----------- | -----------
`username` | Yes | The unique name for the user account.  
`password` | Yes | The password to use for securing the user account.

##### Success Response

  * **Status**: `200`
  * **Content**:
    ```json
    {
      "username": "fherbert",
      "tenant_id": 2,
      "first_name": "Frank",
      "middle_name": "",
      "last_name": "Herbert",
      "email": "fherbert@dune.com",
      "role_id": 2,
      "language": "en",
      "country_tel_code": "",
      "telephone": "",
      "agree_tos": false,
      "access_token": "vm08NdRnRh6LnYLSUbjjdA",
      "token_type": "Bearer",
      "refresh_token": "r0RGyWZ0RueI6rs3oJigPw",
      "expiry": "2022-01-18T04:50:38.5650741Z"
    }
    ```

##### Sample Call

Run the following in your terminal:

```shell
curl -X POST -H "Content-Type: application/json" \
     -d '{"username":"fherbert","password":"pleasechangeme"}' \
      https://biometricscloud.net/api/v1/login
```

**OR**

```shell
curl -X POST -H "Content-Type: application/json" \
     -d '{"username":"fherbert","password":"pleasechangeme"}' \
      http://localhost:8000/api/v1/login
```

##### Notes
If the access token is about to expiry then please call the refresh API endpoint token to get the latest access token, else the user will have to log in again.

For the remainder of this tutorial, please use enviornment variables for the `access_token` and `refresh_token` by running the following:

```bash
export BIOMETRICSCLOUD_ACCESS_TOKEN=vm08NdRnRh6LnYLSUbjjdA
export BIOMETRICSCLOUD_REFRESH_TOKEN=r0RGyWZ0RueI6rs3oJigPw
```

# **Refresh Token (Frontend Only)**
##### Description
This endpoint will grant you new a `access_token` and `refresh_token` to use.

*Developers note: If you are a third-party app developer, do not use this API for user login, please use the oAuth 2.0 [`password grant`](#password-grant) credentials*

##### URL

`https://biometricscloud.net/api/v1/refresh-token`

##### Method

`POST`

##### URL Params

None

##### Data Params

Field | Required | Description
--------- | ----------- | -----------
`refresh_token` | Yes | The `refresh_token` which was provided from either the login or registration API endpoint.

##### Success Response

  * **Status**: `200`
  * **Content**:
    ```json
    {
      "access_token": "$BIOMETRICSCLOUD_ACCESS_TOKEN",
      "expires_in": 3600,
      "refresh_token": "G_oPoG_kTZirzdReu0VgQw",
      "scope": "all",
      "token_type": "Bearer",
    }
    ```

##### Sample Call

Run the following in your terminal:

```shell
curl -X POST -H "Content-Type: application/json" \
     -d '{"refresh_token":"r0RGyWZ0RueI6rs3oJigPw"}' \
      https://biometricscloud.net/api/v1/refresh-token
```

**OR**

```shell
curl -X POST -H "Content-Type: application/json" \
     -d '{"refresh_token":"t9a0bknDRgifRGq7-qXT0w"}' \
      http://localhost:8000/api/v1/refresh-token
```

##### Notes
Only call this API if you are working for the frontend, else go to oAuth 2.0 section and use the refresh token endpoint there.
