# Account Operations

Use the account operations to perform account related actions.

## Retrieve account balance info

```python
from reloadly_core.core.enums.Environment  import Environment
from reloadly_airtime.airtime.sdk.client.AirtimeAPI import AirtimeAPI

airtimeAPI = AirtimeAPI(clientId="*****", clientSecret="*****", environment=Environment.AIRTIME_SANDBOX)  
response = airtimeAPI.accounts().getBalance()
print (response)
```