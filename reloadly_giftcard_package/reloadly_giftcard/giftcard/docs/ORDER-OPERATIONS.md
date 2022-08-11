# Order Operations

You can make a request to purchase any of the gift card products made available via Reloadly. The redeem card details 
would be sent to the recipient information provided (email, phone or both if provided) once the order is successful.

```python
from reloadly_core.core.enums.Environment  import Environment
from reloadly_giftcard.giftcard.sdk.client.giftcardAPI import GiftCards

giftcardAPI = GiftCards(clientId="*****", clientSecret="*****", environment=Environment.GIFTCARD_SANDBOX)

# Create new order
params = {
            "productId": 120,
            "countryCode": "US",
            "quantity": 1,
            "unitPrice": 59.99,
            "customIdentifier": "obucks13",
            "senderName": "Jane Doe",
            "recipientEmail": "anyone@email.com",
            "recipientPhoneDetails": {
                "countryCode": "NG",
                "phoneNumber": "2348931234567"
            }
        }
orderResponse = giftcardAPI.order().send(params)
print(orderResponse)

# Fetch Instruction
transactionId = 574
fetchRedeemResponse = giftcardAPI.order().getCode(transactionId)
print(fetchResponse)
```