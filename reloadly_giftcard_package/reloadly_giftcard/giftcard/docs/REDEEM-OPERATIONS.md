# Redeem Operations

You can retrieve information on how to redeem any purchased gift card brand product.

```python
from reloadly_core.core.enums.Environment  import Environment
from reloadly_giftcard.giftcard.sdk.client.GiftcardAPI import GiftCards

giftcardAPI = GiftCards(clientId="*****", clientSecret="*****", environment=Environment.GIFTCARD_SANDBOX)

# List redeem Instructions
listResponse = giftcardAPI.redeem_instructions().List()
print(listResponse)

# Fetch Instruction
brandId = 4
fetchResponse = giftcardAPI.redeem_instructions().getById(brandId)
print(fetchResponse)
```
