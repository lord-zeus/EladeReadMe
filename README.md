# Documentation for MynyX API GateWay 

**Important note:** *Every ReST call should contain the Auth token header: `Authorization'.
This would be used to authenticate and authorized the request.*
### Base Uri: http://mynyx.unidevelopers.net/api/v1/monetbil-services/
### Header:
```json
{
  "Authorization": "Token Here",
  "Content-Type": "application/json",


}
```
## Content
- [MonetBill Service](#monetbil)
    - [Make Payment](#placePayment)
    - [Check Payment Status](#checkPayment) 
    - [Get Auth Token](#oauthToken)
    


# <a name="monetbil"></a>MonetBill Service

### Make Payment

#### <a name="placePayment"></a>Make Payment

**URL** : `/placePayment`

**Method** : `POST`

**Data constraints** : 
```json
{
  "service": "26NjQNYyWJczoHJZRK3r8zEI3fpb3J0H",
  "amount": "100",
  "phonenumber": "679320186"
}

```
**Data Schema** :
```json
{
  "service": "Your Service Key from Monet bill",  
  "amount": "The Amount you want to pay",
  "phonenumber": "The mobile money number to remove the money from "
}
```


##### Success Code: `200`
##### Sample success responses body for MTN


```json
{
  "status": "REQUEST_ACCEPTED",
  "message": "payment pending",
  "flow": "FLOW_PIN_USSD",
  "channel_ussd": "*126#",
  "channel_name": "MTN Mobile Money",
  "channel": "CM_MTNMOBILEMONEY",
  "paymentId": "19082507131258787499"
}
```

#### Sample Error Code: `422`
#### SampleError Message: 
```json
{
  "service": [
    "The service field is required."
  ],
  "phonenumber": [
    "The phonenumber field is required."
  ],
  "amount": [
    "The amount field is required."
  ]
}
```


### Check Payment Status

#### <a name="checkPayment"></a>Check Payment

**URL** : `/checkPayment`

**Method** : `POST`

**Data constraints** : 
```json
{
  "paymentId": "19082423393376762214"
 }

```
**Data Schema** :
```json
{
  "paymentId": "The Transaction Id"
}
```


##### Success Code: `200`
##### Sample success responses body for MTN


```json
{
  "paymentId": "19082423393376762214",
  "message": "payment finish"
}
```

#### Sample Error Code: `422`
#### SampleError Message: 
```json
{
  "paymentId": [
    "The payment id field is required."
  ]
}
```



# <a name="oauthToken"></a>OAuth Token 

### Get Token

**URL** : `http://mynyx.unidevelopers.net/oauth/token`

**Method** : `POST`

```json

{
    "grant_type": {"type": "string", "required": true},
    "client_id": {"type": "integer", "required": true},
    "client_secret": {"type": "string", "required": true},
}

```

**Data constraints** : 

**Data Schema** :
```json
{
  "grant_type": "Your Type of Client",  
  "client_id": "Your Client Id",
  "client_secret": "Your Client Secret Key "
}
```

**Sample Response
```json
{
  "token_type": "Bearer",
  "expires_in": 31112400,
  "access_token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiIsImp0aSasdfI6IjIwNjU1MTdjMTJiZmI4OWM3ZWIyMzkzYjkzMzVmMzFjNmI2MGRiY2VkZjA1M2MxMTNkMWEyMDY2ZDY4NjJhMWZkY2RjNjIxYjdmYjc0NzM4In0.eyJhdWQiOiIzIiwianRpIjoiMjA2NTUxN2MxMmJmYjg5YzdlYjIzOTNiOTMzNWYzMWM2YjYwZGJjZWRmMDUzYzExM2QxYTIwNjZkNjg2MmExZmRjZGM2MjFiN2ZiNzQasdf3MzgiLCJpYXQiOjE1NjY3MTExNDMsIIm5iZiI6MTU2NjcxMTE0MywiZXhwIjoxNTk4MzMzNTQzLCJzdWIiOiIiLCJzY29wZXMiOltdfQ.o2Zy7GZvrawBr9u-vl-1bxlSRZpswW0QEdWeyM03JTPqJpzq3F8ICfTEQgGwEZkcI8Qqw9X6lbhwVCOzJ3Fn88xjjIaHfYTEDvxeQ2-jDAk8qrAwAW3uOLtHSAGQobasdfhU0Ol5uS3sOq19bAbbuntj2YFcEPp-k0YZNAZC5Aocy4O0Ft_w3B9Vp3tcuMOTNRwsaI45W8vD8k8KzRbZtHTw1PWEUAU_Wex4jV7slXrupiLwF6QdPwjy-pp-KNCDwsSgMlIEsL004eCGcVhYKhxIBnLGyGQI8XHhWnGmpAM-thBB8jdOnFQZInqdeNaPkQ96xn2oUt_gFGXiGgD4oZWfnz6E-oUSGhp5t4k87Kc5jtq8iQP4QI9ssgQZBERVlRpMjKWWSQrQ07xJuuhF_czv3MndZdrKf9c-KDD7tATb1WtBZXQczn5RYQu5woff-tPR9y367lcX2g1muSqZKvVU25BGpu-UvhINt_wHKH7zhWE1J8ec0SoqR5N7opu9HcGacCtIAyMt7RLBXXcZTjQj0MI1UOdtpAiAjZqkafVWwSYm1C1EPP94A2ExESrgicN_u7nlN8Cezs2d8N-6zkoIqx_YoQ2myxkoScPYiMQz_PO55cigHSu2fHHQ_PrM6Xl6c13-h8waqNmcL7QTX0mN90CsfHf1sodFGMiCYghHW8n8"
}

```
