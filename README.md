# sl_bank_api
Stoplight OAS Bank Mock API

Based on Bank of America [CashPro® API's](https://developer.bankofamerica.com/CPODevPortal/apidocs/public/#/home)

Includes:

* [Account Information](https://developer.bankofamerica.com/CPODevPortal/apidocs/public/#/api/account-information)
* [Payments](https://developer.bankofamerica.com/CPODevPortal/apidocs/public/#/api/payments)

## Mock using Prism

```
prism mock -d https://raw.githubusercontent.com/lbrenman/sl_bank_api/master/reference/Account-Information.json
```

OR

```
docker run --init --rm -p 4010:4010 stoplight/prism:4.10.1 mock -d -h 0.0.0.0 "https://raw.githubusercontent.com/lbrenman/sl_bank_api/master/reference/Account-Information.json"
```

## Test

```
curl --location --request POST 'http://127.0.0.1:4010/reporting/v1/balance-inquiries/previous-day' \
--header 'Content-Type: application/json' \
--header 'Authorization: Bearer {{token}}' \
--data-raw '{
 "accounts": [
  {
   "accountNumber": "601022222222",
   "bankId": "BOFAFRPP"
  }
 ],
 "balanceAsOfDate": "2017-07-04"
}'
```

with sample response:

```
{
    "accountBalances": {
        "accountNumber": "89837046",
        "balances": [
            {
                "transactionCode": "6229",
                "amount": "431.67",
                "transactionDescription": "Home Loan Account",
                "lastUpdatedDate": "2022-07-20"
            },
            {
                "lastUpdatedDate": "2022-07-19",
                "transactionCode": "4426",
                "transactionDescription": "Money Market Account",
                "amount": "182.98"
            },
            {
                "lastUpdatedDate": "2022-07-19",
                "transactionDescription": "Investment Account",
                "transactionCode": "5625",
                "amount": "558.93"
            }
        ],
        "bankId": "BOFAFRPP",
        "currency": "USD"
    }
}
```
