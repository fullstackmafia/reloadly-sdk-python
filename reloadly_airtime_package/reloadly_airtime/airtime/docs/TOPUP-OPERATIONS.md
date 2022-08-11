# Topup Operations

In order to send a successful topup. There are a few prerequisites to the system. We need to know the phone number to
send the topup to, the operator id of the phone number, the country of the operator, the amount for the topup.

Reloadly also provides the ability to top up using local values. By default, the values will be available in your
account’s currency, but you can maintain one wallet and top up in different local values from many countries. **Please
note that this is only possible when local values are supported in Reloadly system**. If you want to send exact amounts
in Local/Operator's/Receiver's currency, then simply set the `.UseLocalAmount(true)` on the request object. This
will tell the platform that you are sending the amount in local currency and not in your dashboard's currency or
international pipe. Not all operator's support a local amount yet so make sure to check the operator's details to know
whether it supports local or not.

Reloadly also supports Nauta Cuba for top-ups. However the process is a bit different from sending phone topups. Instead
of using `PhoneTopupRequest` use `EmailTopupRequest`, substitute `RecipientPhone(phone)` with
`RecipientEmail(email)` and that's it. The rest of the process is exactly the same as sending any other topup.

Note, There are two types of email domains that are allowed for Nauta Cuba Top-up : `@nauta.com.cu`
and `@nauta.co.cu`.

```python
from reloadly_core.core.enums.Environment  import Environment
from reloadly_airtime.airtime.sdk.client.AirtimeAPI import AirtimeAPI

airtimeAPI = AirtimeAPI(clientId="*****", clientSecret="*****", environment=Environment.AIRTIME_SANDBOX)

#Phone TopUps
amount = 500.00
operatorId = 173
phoneTopupRequest = PhoneTopupRequest(amount, operatorId).recipientPhone(Phone("+50936377111", "HT")).value
phoneTopUpResponse = airtimeAPI.topups().send(phoneTopupRequest)
print(phoneTopUpResponse)

# Email TopUps for Nauta Cuba TopUps
amount = 5000.00
operatorId = 683
emailTopupRequest = EmailTopupRequest(amount, operatorId, "testing@nauta.com.cu").value
emailTopupResponse = airtimeAPI.topups().asyncTopUp(emailTopupRequest)
print(emailTopupResponse)
```

> The .status method can be used to get the status of a topup. It can be used as seen below.

```
transactionID = ""
statusRequest = airtimeAPI.topups().status(transactionID)
```