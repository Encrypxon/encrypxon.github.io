---
weight: 15
title: Authenticate
---

# Authenticate

These methods are used to use 2FA to authenticate a user.

## Start 2FA authentication

```csharp
var config = new EncrypxonClientConfiguration {ApiKey = "YourApiKey"};
var client = new Encrypxon2FaClient(config);
var body = new Start2FaRequest { Email = "customerEmail"}
var res = await client.Start2FaAuthenticationAsync(body);
string requestId = res.Result.Result;
```

> The request body should be

```json
{
    "email": "useremail@somedomain.com"
}
```


> The above command returns JSON structured like this:

```json
{
  "isError" : false,
  "message" : "Success",
  "exceptionMessage" : "some message about what went wrong",
  "result" : "requestId"
}
```

This endpoint starts the 2FA authentication process for a user. You shoudl tell the user to open the Encrypxon app and go to the Authorise 2FA menu option. 
Here they will click on the item for your website, indicated by your favicon and domain name.

When they click on this the app will negotiate the 2FA request with the Encrypxon server and if this is the users enrolled device the 2FA authentication will be confirmed.

### HTTP Request

`POST http://api.encrypxon.com/2fa/Initiate2Fa`

The request body contains a single parameter which is the identifier of the customer to be enrolled.

### HTTP Response

The reponse provides a unique request ID that is used in the endpoint which checks if the authorisation has been successful.

<aside class="success">
Remember — the identifier must be the same string value as used in the enrollment.
</aside>



## Check 2FA authentication status

```csharp
var config = new EncrypxonClientConfiguration {ApiKey = "YourApiKey"};
var client = new Encrypxon2FaClient(config);
var res = await client.Get2FaAuthorisationStateAsync(secondFactorId);
bool auth = res.Result.Result;
```



> The above command returns JSON structured like this:

```json
{
  "isError" : false,
  "message" : "Success",
  "exceptionMessage" : "some message about what went wrong",
  "result" : true
}
```

This endpoint tests whether or not a user has successfully responded to the 2FA authorisation. 

The result is `true` if the user is enrolled or `false` otherwise.

The parameter required is the ID returned in the Start 2FA Authentication call.

### HTTP Request

`POST http://api.encrypxon.com/2fa/Authorisation?secondFactorId={requestId}`


<aside class="success">
Remember — the identifier must be the same string value as returned in the Start Authorisation request.
</aside>