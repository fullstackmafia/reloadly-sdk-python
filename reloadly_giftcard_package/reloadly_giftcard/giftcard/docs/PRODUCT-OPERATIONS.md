# Product Operations

Retrieves all available gift card products. Filters can be added for specific search result. 
The response is paginated and the maximum page size is 200 per request.

```python
from reloadly_core.core.enums.Environment  import Environment
from reloadly_giftcard.giftcard.sdk.client.GiftcardAPI import GiftCards

giftcardAPI = GiftCards(clientId="*****", clientSecret="*****", environment=Environment.GIFTCARD_SANDBOX)

# List Products with Filter
page_idx = 1
page_size =5
filter= QueryFilter().withPage(page_idx, page_size)
listResponse = giftcardAPI.products().List_with_filter(filter)
print(listResponse)

# List Products without Filter
listResponse2 = giftcardAPI.products().List_without_filter()
print(listResponse2)

# Fetch Products with Product ID
productId = 10
fetchResponse = giftcardAPI.products().getById(productId)
print(fetchResponse)

# Fetch Products with Product ISO code
countryCode = "US"
fetchResponse = giftcardAPI.products().getByISO(countryCode)
print(fetchResponse)
```
