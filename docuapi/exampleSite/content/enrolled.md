---
weight: 10
title: Enrolled
---

# Enrolled

## Check whether a user is enrolled in 2FA

```csharp
var config = new EncrypxonClientConfiguration {ApiKey = "YourApiKey"};
var client = new Encrypxon2FaClient(config);
var res = await client.GetEnrolledAsync();
bool enrolled = res.Result.Result;
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

This endpoint tests whether or not a user is enrolled in 2FA. 

The result is `true` if the user is enrolled or `false` otherwise.

You should use this during the login process to decide whether or not to start a 2FA authorisation or not.

Addiitionally you might want to use this method to decide whether or not to offer enrollment in the users profile page in your website.

### HTTP Request

`POST http://api.encrypxon.com/2fa/enrolled?userId={customerId}`

### URL Parameters

Parameter | Description
--------- | -----------
userId | The ID of the customer to check enrollment status for

<aside class="success">
Remember — the identifier must be the same string value ass used in the enrollment.
</aside>