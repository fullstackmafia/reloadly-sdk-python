# Report Operations

Retrieve various reports such as transaction history etc...

```python
from reloadly_core.core.enums.Environment  import Environment
from reloadly_giftcard.giftcard.sdk.client.giftcardAPI import GiftCards

giftcardAPI = GiftCards(clientId="*****", clientSecret="*****", environment=Environment.GIFTCARD_SANDBOX) 

# List with Filter
page_idx = 1
page_size =5
filter1= TransactionHistoryFilter().withPage(page=page_idx, pageSize=page_size)
listResponse = giftcardAPI.reports().transactionHistory().List_with_filter(filter1)
print(listResponse)

# List without Filter
listResponse2 = giftcardAPI.reports().transactionHistory().List_without_filter()
print(listResponse2)

# Fetch with ID
transactionId = 573
fetchResponse = giftcardAPI.reports().transactionHistory().getById(transactionId)
print(fetchResponse)
```