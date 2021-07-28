---
weight: 20
title: Errors

---

# Errors



The Encrypxon 2FA API uses the following error codes:


Error Code | Meaning
---------- | -------
400 | Bad Request -- Your request sucks
401 | Unauthorized -- Your API key is wrong
404 | Not Found -- The path you specified does not exist
405 | Method Not Allowed -- You tried to use invalid method
406 | Not Acceptable -- You requested a format that isn't json
500 | Internal Server Error -- We had a problem with our server. Try again later.
503 | Service Unavailable -- We're temporarially offline for maintenance. Please try again later.
