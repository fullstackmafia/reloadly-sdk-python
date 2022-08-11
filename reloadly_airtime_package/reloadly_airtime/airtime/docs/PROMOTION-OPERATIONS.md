# Promotions Operations

Reloady also support operators promotions. These are provided by the operators and can be activated by sending a
specific topup amount as per the details of the promotion. Using the promotion operations you can retrieve all details
on the different operators promotions and to showcase these to your customers.

```python
from reloadly_core.core.enums.Environment  import Environment
from reloadly_airtime.airtime.sdk.client.AirtimeAPI import AirtimeAPI

airtimeAPI = AirtimeAPI(clientId="*****", clientSecret="*****", environment=Environment.AIRTIME_SANDBOX)  

# List Promotions with Filter
page_idx = 1
page_size =5
filter1= QueryFilter().withPage(page_idx, page_size)
listResponse = airtimeAPI.promotions().List_with_filter(Filter1)
print(listResponse)

# List Promotions without Filter
listResponse2 = airtimeAPI.promotions().List_without_filter()
print(listResponse2)

# Fetch Promotion with Promotion ID
promotionId = 5665
fetchResponse = airtimeAPI.promotions().getById(promotionId)
print(fetchResponse)

# Fetch Promotion with Country Code
countryCode = "HT"
fetchResponse2 = airtimeAPI.promotions().getByCountryCode(countryCode)
print(fetchResponse2)

# Fetch Promotion with Operator ID
operatorId = 173
fetchResponse3 = airtimeAPI.promotions().getByOperatorId(operatorId)
print(fetchResponse3)
```