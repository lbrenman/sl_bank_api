# sl_bank_api
Stoplight OAS Bank Mock API

Based on Bank of America [CashPro® API's](https://developer.bankofamerica.com/CPODevPortal/apidocs/public/#/home)

Includes:

* [Account Information](https://developer.bankofamerica.com/CPODevPortal/apidocs/public/#/api/account-information)
* [Payments](https://developer.bankofamerica.com/CPODevPortal/apidocs/public/#/api/payments)

Mock using Prism as follows:

```
prism mock -d <Path to OAS Document>/Account-Information.json
```

OR

```
docker run --init --rm -v $(pwd):<Path to OAS Document> -p 4010:4010 stoplight/prism:4.10.1 mock -d -h 0.0.0.0 "<Path to OAS Document>/Account-Information.json"
```
