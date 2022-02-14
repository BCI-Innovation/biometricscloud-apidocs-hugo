---
title: 'oAuth 2.0 Endpoints'
date: 2019-02-11T19:27:37+10:00
draft: false
weight: 12
summary: "Endpoints pertaining to oAuth 2.0 handling."
---

BiometricsCloud supports the `OAuth 2.0 Authorization Framework` as specified in [rfc6749](https://datatracker.ietf.org/doc/html/rfc6749). Please note [BiometricsCloud oAuth 2.0](https://ipregnancy.app) supports the following grant types and refresh token code is supported:

* **Password Grant**
* **Authorization Grant**
* **Client Credentials Grant**
* **Refresh Token**

When you create an application, you must use the `oAuth 2.0` system.

To help the following section make sense, please note dummy values:

* `client_id` - 1f60a74bab4c21bc
* `client_secret` - lalalalalalala
* `redirect_url` - https://ipregnancy.tech/appauth/code

# **Password Grant**
##### Description
This endpoint is used to obtain both access tokens and refresh tokens by resource owner password credentials grant type.

<!-- https://backstage.forgerock.com/knowledge/kb/article/a45882528 -->

##### URL

`https://ipregnancy.ws/token`

##### Method

`POST`

##### URL Params

None

##### Required
HTTP Password Authentication

Parameter | Description
--------- | -----------
`username` | Client ID
`password` | Client Secret

##### Data Params
Query Parameter | Description
--------- | -----------
`grant_type` | Required `password` value.
`username` | The `email` address of the user that wants to authenticate with the system.
`password` | The `password` of the user's account.
`scope`  | Requires `all` value.

##### Success Response

  * **Status**: `200`
  * **Content**:
    ```json
    {
        "access_token": "6CB8pz2qSEmTVW-ijqqCfA",
        "email": "fherbert@dune.com",
        "expires_in": 3600,
        "first_name": "Frank",
        "language": "en",
        "last_name": "Herbert",
        "refresh_token": "rGedIkXHQiqfLLr_2AiEXw",
        "role_id": 2,
        "scope": "all",
        "tenant_id": 2,
        "token_type": "Bearer",
        "user_id": 2,
        "user_uuid": "616e8bfa-52c3-464f-9343-dbd0b3e433b0"
    }
    ```

##### Sample Call

Run the following in your terminal:

```shell
curl -X POST -u "1f60a74bab4c21bc:lalalalalalala" -d "grant_type=password&username=fherbert@dune.com&password=pleasechangeme&scope=all" https://ipregnancy.ws/token
```

##### Notes

* Native app developers / third-party application developers can utilize this endpoint to build "Sign-in with BiometricsCloud" authentication in their projects.


# **Client Credentials Grant**
##### Description
This endpoint will provide access token for the client credentials grant type.
<!-- https://backstage.forgerock.com/knowledge/kb/article/a45882528 -->


##### URL

`https://ipregnancy.ws/token`

##### Method

`POST`

##### URL Params

None

##### Required
HTTP Password Authentication

Parameter | Description
--------- | -----------
`username` | Client ID
`password` | Client Secret

##### Data Params

None

##### Success Response

  * **Status**: `200`
  * **Content**:
    ```json
    {
        "access_token": "DAGdS3YbRDKT8yCd2PRphQ",
        "email": "",
        "expires_in": 3600,
        "first_name": "",
        "language": "",
        "last_name": "",
        "refresh_token": "Ep4e7XpURte6jg1ThEnrow",
        "role_id": 2,
        "scope": "all",
        "tenant_id": 2,
        "token_type": "Bearer",
        "user_id": 2,
        "user_uuid": "616e8bfa-52c3-464f-9343-dbd0b3e433b0"
    }
    ```

##### Sample Call

Run the following in your terminal:

```shell
curl -X POST -u "1f60a74bab4c21bc:lalalalalalala" -d "grant_type=client_credentials" https://ipregnancy.ws/token
```

##### Notes

* Native app developers utilize this endpoint to have continuous access to the user's account without having a need for the user to enter their password again.

# **Authorization Code Grant**
##### Description
This endpoint will provide access and refresh tokens by the authorization code grant type. Please note that we are using a three-legged approach to authentication. The steps are outlines as follows in an example:

**Leg 1:** Before utilizing this endpoint, your third-party application needs to redirect the user in the browser to the following URL: `https://ipregnancy.ws/authorize?client_id=1f60a74bab4c21bc&redirect_uri=https%3A%2F%2Fipregnancy.tech%2Fappauth%2Fcode&response_type=code&scope=all`.

* `client_id=1f60a74bab4c21bc` - This is the client ID of your third party app which was provided to you during the create.
* `redirect_uri=https%3A%2F%2Fipregnancy.tech%2Fappauth%2Fcode` - This is the redirect URL back to your third-party app's authorization code handler.
* `response_type` - This is specifying you want a `code` response.
* `scope` - This `all` value means your third-party app will have access to all the users data.

**Leg 2:** Once the the user successfully enters their credentials to grant permission, the server will redirect the user in the browser to the following URL:https://ipregnancy.tech/appauth/code?code=al-3_gq7SfKHE1nveCfdbw&email=fherbert%40dune.com&first_name=Frank&language=en&last_name=Herbert&role_id=2&state=&tenant_id=2&user_id=2&user_uuid=616e8bfa-52c3-464f-9343-dbd0b3e433b0.

* `code=al-3_gq7SfKHE1nveCfdbw` - This is the code you must include when calling this endpoint.
* `email=fherbert%40dune.com&first_name=Frank&language=en&last_name=Herbert&role_id=2&state=&tenant_id=2&user_id=2&user_uuid=616e8bfa-52c3-464f-9343-dbd0b3e433b0` - This is user profile info provided by the server.

**Leg 3:** This API can now be used, see the `curl` example.

<!-- https://backstage.forgerock.com/knowledge/kb/article/a45882528 -->

##### URL

`https://ipregnancy.ws/token`

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
        "access_token": "DAGdS3YbRDKT8yCd2PRphQ",
        "email": "",
        "expires_in": 3600,
        "first_name": "",
        "language": "",
        "last_name": "",
        "refresh_token": "Ep4e7XpURte6jg1ThEnrow",
        "role_id": 2,
        "scope": "all",
        "tenant_id": 2,
        "token_type": "Bearer",
        "user_id": 2,
        "user_uuid": "616e8bfa-52c3-464f-9343-dbd0b3e433b0"
    }
    ```

##### Sample Call

Run the following in your terminal:

```shell
curl -X POST -H "Content-Type: application/x-www-form-urlencoded" -d "grant_type=authorization_code&code=al-3_gq7SfKHE1nveCfdbw&client_id=1f60a74bab4c21bc&client_secret=lalalalalalala&state=xyz&redirect_uri=https://ipregnancy.tech/appauth/code" https://ipregnancy.ws/token
```

##### Notes

* Third-party application developers utilize this endpoint to allow users to authorize their application to access their data.


# **Refresh Token**
##### Description
This endpoint will, according to RFC 6749, will take the valid refresh token and return new access and refresh tokens.

<!-- https://backstage.forgerock.com/knowledge/kb/article/a45882528 -->

##### URL

`https://ipregnancy.ws/token`

##### Method

`POST`

##### URL Params

None

##### Required

HTTP Password Authentication

Parameter | Description
--------- | -----------
`username` | Client ID
`password` | Client Secret

##### Data Params

None

##### Success Response

  * **Status**: `200`
  * **Content**:
    ```json
    {
        "access_token": "DAGdS3YbRDKT8yCd2PRphQ",
        "email": "",
        "expires_in": 3600,
        "first_name": "",
        "language": "",
        "last_name": "",
        "refresh_token": "Ep4e7XpURte6jg1ThEnrow",
        "role_id": 2,
        "scope": "all",
        "tenant_id": 2,
        "token_type": "Bearer",
        "user_id": 2,
        "user_uuid": "616e8bfa-52c3-464f-9343-dbd0b3e433b0"
    }
    ```

##### Sample Call

Run the following in your terminal:

```shell
curl -X POST -u "1f60a74bab4c21bc:lalalalalalala" -d "grant_type=refresh_token&refresh_token=rGedIkXHQiqfLLr_2AiEXw" https://ipregnancy.ws/token

```

##### Notes

* Native app developers utilize this endpoint to have continuous access to the user's account without having a need for the user to enter their password again.
