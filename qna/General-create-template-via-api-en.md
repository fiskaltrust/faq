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

```powershell
$headers = @{ accountid = "your-account-id" ; accesstoken = "your-access-token" }
$uri = "https://helipad-sandbox.fiskaltrust.cloud/api/Configuration"
# Read from template.json and escape JSON string
$template = (Get-Content .\template.json -Raw).Replace('\', '\\').Replace('"', '\"')

Invoke-WebRequest -uri  $uri -Headers $headers -Method POST -ContentType "application/json" -Body "`"$template`""
```

### Parametrization
Additionally, you can add variables to the query string of the URL that will then be automatically replaced in the template you sent. For example, altering the URL above to the value `https://helipad.fiskaltrust.cloud/api/configuration?my_variable=123` will replace all occurrences of `|[my_variable]|` in the template text with `123` before executing it.

Some variables are automatically set if they are not specified in the query string:

| Variable      | Default value  |
| ------------- |-------------| 
| outlet_number | `{max(outlets used in account's existing cashboxes) + 1}`     |
| description      | `ft{yyyyMMddHHmmss}` |
| cashbox_description      | `ft{yyyyMMddHHmmss}` |
| cashbox_id     | Random GUID      |
| cashbox_ipaddress | Empty string      |
| scu{0-9}_id | Random GUID     |
| scu{0-9}_description | `{description}`      |
| scu{0-9}_url | `net.pipe://localhost/{scu_id}`      |
| helper{0-9}_id | Random GUID     |
| helper{0-9}_description | `{description}`      |
| helper{0-9}_url | `net.pipe://localhost/{helper_id}`      |
| queue{0-9}_id | Random GUID     |
| queue{0-9}_id_base64withoutspecialchars | `{queue_id}`, converted to Base64 without special characters    |
| queue{0-9}_description | `{description}`      |
| queue{0-9}_url | `http://localhost:1200/fiskaltrust` for the first queue, `http://localhost:1200/fiskaltrust{1-9}` for others      |

_Dynamic values are highlighted via {} in this table._
