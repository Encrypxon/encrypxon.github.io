---
weight: 10
title: API Reference
---

# Introduction

Welcome to the Encrypxon 2FA API! You can use our API to add 2FA into your web application.

We have language bindings in Shell, javascript and C# with more to come!

You can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.

# How the 2FA process works

The enrollment process works by notifying the Encrypxon app on the device to be used as the customers 2FA device that an enrollment request has been generated.

The QRCode that is scanned by the users device has a unique identifier for the enrollment. When the QRCode is scanned, the device generates a new key pair to encrypt the data used later in the 2FA authentication process. The public key of this key pair is sent to the Encrypxon server along with unique enrollment code. The private key is held in secure storage in the customers device. It never leaves the device. 

Using this mechanism of scanning a QRCode ensures that the user has the phone in proximity of your web application during the enrollment process.

When a 2FA is requested by your application, the Encrypxon server sends some entropy encrypted with the public key of the users device, generated during the enrollment process.
The device can decrypt this entropy using its private key. The decrypted entropy is sent back to the Encrypxon server and compared with the entropy sent to the device. If this matches then the 2FA is successful and your application can be notified that the user should be allowed to log in.

A separate key pair is generated on the device for every website using the Encrypxon 2FA process. 

Every 2FA request is stored on the Encrypxon server for audit purposes. 


# API Authentication

> To authorize, use this code:



```shell
# With shell, you can just pass the correct header with each request
curl "https://api.encrypxon.com"
  -H "X-API-Key: YourApiKey"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
```

```csharp
var config = new EncrypxonClientConfiguration {ApiKey = "YourApiKey"};
var client = new Encrypxon2FaClient(config);
```

> Make sure to replace `YourApiKey` with your API key.

Encrypxon uses API keys to allow access to the API. You can get a new Encrypxon API key by emailing us at [developer support](mailto:info@encrypxon.com).

Encrypxon expects for the API key to be included in all API requests to the server in a header that looks like the following:

`X_API_Key: YourApiKey`

<aside class="notice">
You must replace <code>YourApiKey</code> with your personal API key.
</aside>
