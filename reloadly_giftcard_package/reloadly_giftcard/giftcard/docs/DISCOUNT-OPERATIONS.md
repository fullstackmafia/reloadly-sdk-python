# Discounts Operations

Discounts or commissions are a way for you to check what percentage discount rate will you get for each product when
you send a successful order. These operations can be used to calculate your profits. All Commissions are paid instantly
when an order is processed.

```python
from reloadly_core.core.enums.Environment  import Environment
from reloadly_giftcard.giftcard.sdk.client.GiftcardAPI import GiftCards
from reloadly_core.core.internal.Filter.QueryFilter import QueryFilter

giftcardAPI = GiftCards(clientId="*****", clientSecret="*****", environment=Environment.GIFTCARD_SANDBOX) 


# Get by operator ID
discountId = 174
response = giftcardAPI.discounts().getById(discountId)

# List
listResponse = giftcardAPI.discounts().List_without_filter()
print(listResponse)

# List with Filters
page_idx=1
page_size=5
filter = QueryFilter().withPage(page_idx,page_size)
filterResponse = giftcardAPI.discounts().List_with_filter(filter)
print(filterResponse)
```
