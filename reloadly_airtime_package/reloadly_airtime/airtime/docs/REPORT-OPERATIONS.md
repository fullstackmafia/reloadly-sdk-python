# Report Operations

Retrieve various reports such as transaction history etc...

```python
from reloadly_core.core.enums.Environment  import Environment
from reloadly_airtime.airtime.sdk.client.AirtimeAPI import AirtimeAPI

airtimeAPI = AirtimeAPI(clientId="*****", clientSecret="*****", environment=Environment.AIRTIME_SANDBOX)  

# List with Filter
page_idx = 1
page_size =5
filter1= TransactionHistoryFilter().withPage(page_idx, page_size)
listResponse = airtimeAPI.reports().transactionHistory().List_with_filter(filter1)
print(listResponse)

# List without Filter
listResponse2 = airtimeAPI.reports().transactionHistory().List_without_filter()
print(listResponse2)

# Fetch with ID
transactionId = 10657
fetchResponse = airtimeAPI.reports().transactionHistory().getById(transactionId)
print(fetchResponse)
```