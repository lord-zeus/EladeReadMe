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
