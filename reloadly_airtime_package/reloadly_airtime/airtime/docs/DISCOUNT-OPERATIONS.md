# Discounts Operations

Discounts or commissions are a way for you to check what percentage discount rate will you get for each operator when
you send a successful top-up. These operations can be used to calculate your profits. All Commissions are paid instantly
when a top-up is processed.

One thing to note on the response is that All Operators provide two types of discounts, One is the international
discount, and the other is the local discount. These are returned as the internationalPercentage and localPercentage
fields in the response object. Depending on your account currency the country you are sending the topup to, you are
eligible for either one of these discounts. For example if you're sending from the US to Canada you will be eligible for
the international discount for the Canadian operator. While sending within the same country you will be eligible for the
local discount of the operator **if available**. Note that, local discount may not always be available; in which case
the international discount will be applied.

```python
from reloadly_core.core.enums.Environment  import Environment
from reloadly_airtime.airtime.sdk.client.AirtimeAPI import AirtimeAPI
from reloadly_core.core.internal.Filter.OperatorFilter import OperatorFilter

airtimeAPI = AirtimeAPI(clientId="*****", clientSecret="*****", environment=Environment.AIRTIME_SANDBOX)  

# Get by operator ID
operatorId = 174
response = airtimeAPI.discounts().getByOperatorId(operatorId)

# List
listResponse = airtimeAPI.discounts().List_without_filter()
print(listResponse)

# List with Filters

page_idx=1
page_size=5

filter = OperatorFilter().withPage(page_idx,page_size).includeSuggestedAmountsMap(True).includeSuggestedAmounts(True)
filterResponse = airtimeAPI.discounts().List_with_filter(filter)
print(filterResponse)
```
