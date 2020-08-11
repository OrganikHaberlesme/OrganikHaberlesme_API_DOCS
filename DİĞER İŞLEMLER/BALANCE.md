# Bakiye Sorgulama

```
request_name = balance
```

Bakiye sorgulama metodu ile kalan SMS kredilerinizi ve TL bakiyenizi öğrenebilirsiniz. Bu metot `GET` ile çalışır ve herhangi bir parametre göndermenize gerek yoktur. Yanıt tipini belirtmezseniz varsayılan olarak `JSON` dönüş yapılır.


`GET` URL Şablonu:
> /v2/`api_key`/**request_name**/`request_response_type`/
**GET** HTTP/1.1

Örnek `GET` URL'si:
> https://organikapi.com/v2/ce136df4c9c92d1428e828aba07d3b05/balance/

### Başarılı `JSON` Yanıt:
#### JSON
Response Headers:
```
Method:       GET
Status:       200 OK
URL:          /v2/ce136df4c9c92d1428e828aba07d3b05/balance/
Host:         organikapi.com
Content-Type: application/json
```
Reponse Body:
```
{
   "response": {
      "result": true,
      "data": {
        "tl": 125,
        "credit": 325761 
      }
   }
}
```
