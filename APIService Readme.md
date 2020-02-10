<p align="center"><img src="https://unidevelopers.net/img/logos/logo.png" width="400"></p>

# Documentation for API endpoints published by the Uni Dev Service.

## base url http://api_gateway_link/
## Content
- [Authentication](#auth)
    - [Register](#register)
    - [Login](#login)
    - [Refresh Token](#refresh_token)


- [Collection or Deposits](#collection)
    - [Request Collection](#request_collection)
    - [Collection Status](#collection_status)


- [Disbursement or Withdrawal](#disbursement)
    - [Request Collection](#request_disbursement)
    - [Collection Status](#disbursement_status)

# <a name="auth"></a>Authentication

## <a name="register"></a>Registration


### Get  application and all the keys

**URL** : `api/v1/register`

**Method** : `POST`

**Data constraints** : 
```json

{
    "name": {"type": "string", "required": true},
    "description": {"type": "string", "required": false},
    "user_id": {"type": "int", "required": true},
    "email": {"type": "string", "required": true},
    "username": {"type": "string", "required": true},
    "password": {"type": "string", "required": true}

}

```

##### Success Code: `201`
##### Sample success responses body

```json
{
  "name": "Uni Devs",
  "description": "leading tech",
  "email": "nice@gmail.com",
  "username": "xeuskings",
  "id": 33,
  "updated_at": "2020-02-10 18:04:03",
  "created_at": "2020-02-10 18:04:03"
}
```

## <a name="login"></a>Login
### Login 

**URL** : `/api/v1/login`

**Method** : `POST`

**Data constraints** : 
```json

{
    "client_id": {"type": "int", "required": true},
    "client_secret": {"type": "string", "required": true},
    "username": {"type": "string", "required": true},
    "password": {"type": "string", "required": true}

}

```

##### Success Code: `200`
##### Sample success responses body


```json
{
  "token_type": "Bearer",
  "expires_in": 31622400,
  "access_token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiJ9.eyJhdWQiOiIxIiwianRpDdlZmQxN2ZOjE1Nzk1NDI4NjQsIm5iZiI6MTU3OTU0Mjg2NCwiZXhwIjoxNjExMTY1MjY0LCJzdWIiOiIzIiwic2NvcGVzIjpbXX0.hJDIY2DmUe8tgkqTo-1O5pbpWqKHLiSQBk_0Wq-UU9k4PxPDAmUgTNVTrIgE-fCUEl9Fg1yy0anLLn737gPrq6h-olV3KrYwsmFyTPUdqNJJcOGSMtjq7M9HvABiCxIQwBp3y7VQDRST6_YRyV8zA_2BmcunxF7qKJ30kAJUV1j8Rl-95Nx3PH-MIRX_mOnTl58wLkDQBYG1k9Y9N1cI5Ehd_qiptxcQM0Zd0nI0QU6Nr3yB4IwOnlmBqlEXQ2J-jGv0OFeYPgyrOPwUnvWZTXmJ21rg29hoj7UfHTIV8OcXSITeeSSiHY7tAJSWWi4kPgYdp1MsQ1h8Bh6hbSOCmMDEsSBRsfYO96HeicUOn716gQBSdQpf57vdKUVaeTpgZKb5C8vTmDdljqPfN6wj_P4PZE4nvZ1FPcK089NhUso69w1xQjqiIej5FijVJH16s-i3hnk3xaVtIW6S-fnPZkrO4BG8uDko_yasZqoJCi89tQTH-1hSglkTuB5SiSodJSkpboxe41LWGivs4s-4SIJG33sICX_HoKBEaLXl1NcW9TCsgzVPjw8ECDx6M3D7vbzNl65fAVm_R9XqwSspX7bAhgVgEVYJhbmWZG8WPzqeLjX8f2wNdvYIKRRY7YCtKkV9WlOPmr9aGNwSbO5BdpfZsQrUsMOHXy8amGJIrxk",
  "refresh_token": "def502006405dc73cb3108385928a2f1accba1e5c6070cb4a4fec5810270ae28c235e8cb6b1de1cde10fe079f9492e0d1d38b51735629bc70559cbd6c2b59e1297277a8a61e062d4d433747879f971e88ed0920e8a90f2b3c96109c4c2e3fa15ce266ba198131472dd7d6590d6ef1f229d62cd0ea8c412834b1eb2dda1c825497504549ba7fda52adc4ed0eaedffb452fcb146be2114d3200f696f1cb224214f59a47b7fa6766c0f380f74131f3de1903f2341a88552dce0d64753b0b4989bf4d7d14981625018cc6239d67505c928837f11c81b7365f5a71e8f9107b7aaf00989934688adcf5a8efe617832a84384c8cc2c585b5590d579c9b4a40e1355d0781cf8d2e665ad5348d69a75855879fe0411f96ef2a92f96f5241a7f79813456b1e7d5d8e210f4cf64701babb811bdace2be3de9e46f544872f686"
}
```

## <a name="refresh_token"></a>Refresh Token
### Refresh Token

**URL** : `/api/v1/refresh_token`

**Method** : `POST`

**Data constraints** : 
```json

{
    "client_id": {"type": "int", "required": true},
    "client_secret": {"type": "string", "required": true},
    "refresh_token": {"type": "string", "required": true}

}
```
##### Success Code: `200`
##### Sample success responses body

```json
{
  "token_type": "Bearer",
  "expires_in": 31622400,
  "access_token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiJ9.eyJhdWQiOiIxIiwianRpDdlZmQxN2ZOjE1Nzk1NDI4NjQsIm5iZiI6MTU3OTU0Mjg2NCwiZXhwIjoxNjExMTY1MjY0LCJzdWIiOiIzIiwic2NvcGVzIjpbXX0.hJDIY2DmUe8tgkqTo-1O5pbpWqKHLiSQBk_0Wq-UU9k4PxPDAmUgTNVTrIgE-fCUEl9Fg1yy0anLLn737gPrq6h-olV3KrYwsmFyTPUdqNJJcOGSMtjq7M9HvABiCxIQwBp3y7VQDRST6_YRyV8zA_2BmcunxF7qKJ30kAJUV1j8Rl-95Nx3PH-MIRX_mOnTl58wLkDQBYG1k9Y9N1cI5Ehd_qiptxcQM0Zd0nI0QU6Nr3yB4IwOnlmBqlEXQ2J-jGv0OFeYPgyrOPwUnvWZTXmJ21rg29hoj7UfHTIV8OcXSITeeSSiHY7tAJSWWi4kPgYdp1MsQ1h8Bh6hbSOCmMDEsSBRsfYO96HeicUOn716gQBSdQpf57vdKUVaeTpgZKb5C8vTmDdljqPfN6wj_P4PZE4nvZ1FPcK089NhUso69w1xQjqiIej5FijVJH16s-i3hnk3xaVtIW6S-fnPZkrO4BG8uDko_yasZqoJCi89tQTH-1hSglkTuB5SiSodJSkpboxe41LWGivs4s-4SIJG33sICX_HoKBEaLXl1NcW9TCsgzVPjw8ECDx6M3D7vbzNl65fAVm_R9XqwSspX7bAhgVgEVYJhbmWZG8WPzqeLjX8f2wNdvYIKRRY7YCtKkV9WlOPmr9aGNwSbO5BdpfZsQrUsMOHXy8amGJIrxk",
  "refresh_token": "def502006405dc73cb3108385928a2f1accba1e5c6070cb4a4fec5810270ae28c235e8cb6b1de1cde10fe079f9492e0d1d38b51735629bc70559cbd6c2b59e1297277a8a61e062d4d433747879f971e88ed0920e8a90f2b3c96109c4c2e3fa15ce266ba198131472dd7d6590d6ef1f229d62cd0ea8c412834b1eb2dda1c825497504549ba7fda52adc4ed0eaedffb452fcb146be2114d3200f696f1cb224214f59a47b7fa6766c0f380f74131f3de1903f2341a88552dce0d64753b0b4989bf4d7d14981625018cc6239d67505c928837f11c81b7365f5a71e8f9107b7aaf00989934688adcf5a8efe617832a84384c8cc2c585b5590d579c9b4a40e1355d0781cf8d2e665ad5348d69a75855879fe0411f96ef2a92f96f5241a7f79813456b1e7d5d8e210f4cf64701babb811bdace2be3de9e46f544872f686"
}
```


##### Error Code: `422` 
##### Error Message: `Unprocessable Entity` 
##### Sample error responses body

```json
{
  "token_type": [
    "The token_type field is required."
  ],
  "client_secret": [
    "The client_secret field is required."
  ]
}
```



# <a name="collection"></a>Collection or Deposits


## <a name="request_collection"></a>Registration
### Collection or Deposits
### Request Collection or Deposit
**URL** : `/api/v1/collection/mtn`

**Method** : `POST`

**Data constraints** : 
```json

{
    "phone": {"type": "string", "required": true},
    "user_id": {"type": "int", "required": true},
    "amount": {"type": "string", "required": true}
}

```

**Headers constraints** : 
```json

{
    "Authorization": {"type": "string", "required": true}
}
```

##### Success Code: `200`
##### Sample success responses body

```json
{
  "transaction_id": 5,
  "phone": "679320186",
  "amount": "100",
  "application_id": 1,
  "updated_at": "2020-01-27 02:39:16",
  "created_at": "2020-01-27 02:39:16",
  "id": 2
}
```

## <a name="collection_status"></a>Collection Status
### Collection Status
**URL** : `api/v1/collection/mtn/{transaction_id}`

**Method** : `GET`

**Data constraints** : `{}`

**Headers constraints** : 
```json

{
    "Authorization": {"type": "string", "required": true}
}
```

##### Success Code: `200`
##### Sample success responses body

```json
{
  "transaction_id": "5",
  "amount": "100",
  "phone": "679320186",
  "status": "SUCCESSFUL"
}
```




# <a name="disbursement"></a>Disbursement or Withdrawal


## <a name="request_disbursement"></a>Disbursement
### Disbursement or Withdrawal
### Request Disbursement or Withdrawal
**URL** : `/api/v1/disbursemnt/mtn`

**Method** : `POST`

**Data constraints** : 
```json

{
    "phone": {"type": "string", "required": true},
    "user_id": {"type": "int", "required": true},
    "amount": {"type": "string", "required": true}
}

```

**Headers constraints** : 
```json

{
    "Authorization": {"type": "string", "required": true}
}
```

##### Success Code: `200`
##### Sample success responses body

```json
{
  "transaction_id": 5,
  "phone": "679320186",
  "amount": "100",
  "application_id": 1,
  "updated_at": "2020-01-27 02:39:16",
  "created_at": "2020-01-27 02:39:16",
  "id": 2
}
```

## <a name="disbursement_status"></a>Disbursement Status
### Disbursement Status
**URL** : `api/v1/disbursement/mtn/{transaction_id}`

**Method** : `GET`

**Data constraints** : `{}`

**Headers constraints** : 
```json

{
    "Authorization": {"type": "string", "required": true}
}
```

##### Success Code: `200`
##### Sample success responses body

```json
{
  "transaction_id": "5",
  "amount": "100",
  "phone": "679320186",
  "status": "SUCCESSFUL"
}
```


