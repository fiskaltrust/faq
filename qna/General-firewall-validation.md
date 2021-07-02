## Question
How can I test the connection to fiskaltrust's cloud services in case the fiskaltrust.Middleware has connection issues?

## Metadata tags
lang-en, market-all, middleware, PosDealer, PosOperator

## Answer
If the Middleware is showing errors which suggest connection issues to one of our cloud services (e.g. "configuration cannot be downloaded" or "an error occured while uploading data"), it might be a firewall problem.
Pinging our servers won't work, as they are configured to not respond to those requests - but users should try to run the following requests in Powershell:

```ps
Invoke-RestMethod 'https://helipad.fiskaltrust.cloud/version'
Invoke-RestMethod 'https://packages.fiskaltrust.cloud/version'
```

If one of those fails, it's most likely a network or firewall issue and is not related to a malfunction of the Middlware. Please refer to our respective documentation about how to configure the [Windows Firewall](https://link.fiskaltrust.cloud/de/firewall).
