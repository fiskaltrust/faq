## Question
How can I automate or script creating Cashboxes via templates?

## Metadata tags
lang-en, market-all, middleware, cashbox management, PosDealer, PosCreator

## Answer
Executing templates can be easily automated via our HTTP API, which should be supported in all common scripting and programming languages. All you need is the template as a string (e.g. read from a file), your _account ID_, and your _access token_. Both are displayed in the [fiskaltrust.Portal](https://portal.fiskaltrust.de/AccountProfile). 

The request should look like this:
- _Method_: **POST**
- _Headers_: 
  - `accountid`: `<your-account-id>`
  - `accesstoken`: `<your-access-token>`
- _Body_: JSON template
- _URLs_: 
  - Sandbox: `https://helipad-sandbox.fiskaltrust.cloud/api/configuration`
  - Production: `https://helipad.fiskaltrust.cloud/api/configuration`

The following example illustrates how a template can be sent to our API:

```ps
$headers = @{ accesstoken = "<access-token>" ; accountid = "<account-id>" }
$uri = "https://helipad-sandbox.fiskaltrust.cloud/api/Configuration"
$template = Get-Content .\template.json -Raw 

Invoke-WebRequest -uri  $uri -Headers $headers -Method POST -Body $template
```


