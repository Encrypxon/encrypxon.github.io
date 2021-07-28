---
weight: 10
title: Enroll
---

# Enroll

## Enroll a user in 2FA

```csharp
var config = new EncrypxonClientConfiguration {ApiKey = "YourApiKey"};
var client = new Encrypxon2FaClient(config);
var body = new EnrollRequest {Emaiil = "customerEmail"};
var res = await client.Enroll2faAsync();
var qrcodeImageBase64Encoded = res.Result.Result.QrCode;
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
  "result" : {
    "qrcode" : "base64 encoded string"
  }
}
```

This endpoint enrolls a user in 2FA. 

The request tells Encrypxon the customer identifier.

The response provides a QRCode in a base64 encoded string. This should be displayed to your user.

You can use the following html to display the decoded image.

`
<img src="data:image/jpeg;base64, {the base64 encoded data}]">
`

You application should inform the user to open the Encrypxon app on their phone and go to the Enroll 2FA menu option. Here they must scan the QRCode. Once done they are enrolled as a 2FA user.

### HTTP Request

`POST http://api.encrypxon.com/2fa/enroll`

The request body contains a single parameter which is the identifier of the customer to be enrolled.


<aside class="success">
Remember — the identifier can be any string value as long as it is unique for your customers.
</aside>