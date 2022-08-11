# Operators Operations

Apart from supporting Over 140 Countries, Reloadly also supports 600+ Operators. The SDK operators options allows for
the retrieval complete detail of each operator, including what type of operator this is, what topup types it support and
even details on the commissions for the operator.

Within the reloadly platform, There exists two types of Operators. One that support Range values (Anything between the
minimum and maximum range). While the other that support Fixed values (Only a certain values are supported). Reloadly
will return you the type of the operator within the response in denominationType variable. If this is set to ```RANGE```
you will receive the minimum and maximum values in the minAmount and maxAmount variables for that operator. However, if
the denomination type is ```FIXED``` you will not get these values but rather get an array of all values supported in
the fixedAmounts variable. **Now a point to remember here is that these values are already converted into your account's
currency**.

```python
from reloadly_core.core.enums.Environment  import Environment
from reloadly_airtime.airtime.sdk.client.AirtimeAPI import AirtimeAPI
from reloadly_core.core.internal.Filter.OperatorFilter import OperatorFilter

airtimeAPI = AirtimeAPI(clientId="*****", clientSecret="*****", environment=Environment.AIRTIME_SANDBOX)

# List Operators with Filter
page_idx = 1
page_size =5

filter1 = OperatorFilter()
    .withPage(page_idx, page_size)
    .includeBundles(True) # Whether to include bundle operators in the returned resource list. See field "bundle" on the [API Docs](https://developers.reloadly.com/api.html#list-all-operators).
    .includeData(True) # Whether to include data (internet) operators in the returned resource list. See field "data" on the [API Docs](https://developers.reloadly.com/api.html#list-all-operators).
    .includeFixedDenominationType(True) # Whether to include operators with denomination type FIXED in the returned resource list. See field "denominationType" on the [API Docs](https://developers.reloadly.com/api.html#list-all-operators).
    .includePin(True) # Whether to include PIN based operators in the returned resource list. See field "pin" on the [API Docs](https://developers.reloadly.com/api.html#list-all-operators).
    .includeRangeDenominationType(True) # Whether to include operators with denomination type RANGE in the returned resource list. See field "denominationType" on the [API Docs](https://developers.reloadly.com/api.html#list-all-operators).
    .includeSuggestedAmounts(True) # Whether to populate the suggestedAmounts field on the operators in the returned resource list, this only applies to operators where denominationType is RANGE. See field "suggestedAmounts" on the [API Docs](https://developers.reloadly.com/api.html#list-all-operators).
    .includeSuggestedAmountsMap(True) # Whether to populate the suggestedAmountsMap field on the operators in the returned resource list. This field represents a map of international amounts to local amounts for a given operator where applicable. See field "suggestedAmountsMap" on the [API Docs](https://developers.reloadly.com/api.html#list-all-operators).

listResponse = airtimeAPI.operators().List_with_filter(filter1)
print(listResponse)

# List Operators without Filter
listResponse2 = airtimeAPI.operators().List_without_filter()
print(listResponse2)

# Fetch Operator with ID with Filters
operatorId = 174
filter2 = OperatorFilter().includeSuggestedAmountsMap(True)
fetchResponse = airtimeAPI.operators().getById_with_filter(operatorId, filter2)
print(fetchResponse)

# Fetch Operator with ID without Filters
operatorId = 174
fetchResponse2 = airtimeAPI.operators().getById_without_filter(operatorId)
print(fetchResponse2)

# Fetch Operator with Country Code with Filters
filter3 = OperatorFilter().includeBundles(True).includeSuggestedAmountsMap(True)
fetchResponse3 = airtimeAPI.operators().listByCountryCode_with_Filters("HT", filter3)
print(fetchResponse3)

# Fetch Operator with Country Code without Filters
fetchResponse4 = airtimeAPI.operators().listByCountryCode_without_Filters("HT")
print(fetchResponse4)

# autodetect
phone = "+50936377111"
countryCode = "HT"
autoDetectResponse = airtimeAPI.operators().autoDetect(phone, countryCode)
print(autoDetectResponse)

# In order to estimate what amount will be received on the receiver end. For example, If your account is in US Dollar and you are trying to send a transaction to a nigerian operator, you can quickly calculate what amount you will receive in Nigerian Naira.
amount = 5.00
operatorId = 174
fxRateResponse = airtimeAPI.operators().calculateFxRate(operatorId, amount)
print(fxRateResponse)
```
