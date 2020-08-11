# Başlık Sorgulama

```
request_name = balance
```

Bakiye sorgulama metodu ile kalan SMS kredilerinizi ve TL bakiyenizi öğrenebilirsiniz. Bu metot `GET` ile çalışır ve herhangi bir parametre göndermenize gerek yoktur. Yanıt tipini belirtmezseniz varsayılan olarak `JSON` dönüş yapılır.


`GET` URL Şablonu:
> /v2/`api_key`/**request_name**/`request_response_type`/
**GET** HTTP/1.1

Örnek `GET` URL'si:
> https://organikapi.com/v2/ce136df4c9c92d1428e828aba07d3b05/headers/

### Başarılı `JSON` Yanıt:
#### JSON
Response Headers:
```
Method:       GET
Status:       200 OK
URL:          /v2/ce136df4c9c92d1428e828aba07d3b05/headers/
Host:         organikapi.com
Content-Type: application/json
```
Reponse Body:
```
{
   "response": {
      "result": true,
      "data": [
         {
            "id": 1,
            "name": "Başlık 1"
         },
         {
            "id": 2,
            "name": "Başlık 2"
         }        
      ]
   }
}
```

> /v2/`api_key`/**headers**/`xml`/
### Başarılı `XML` Yanıt:
#### XML
Response Headers:
```
Method:       GET
Status:       200 OK
URL:          /v2/ce136df4c9c92d1428e828aba07d3b05/headers/xml/
Host:         organikapi.com
Content-Type: application/xml
```
Reponse Body:
```
<?xml version="1.0" encoding="UTF-8"?>
<response>
  <result>1</result>
  <data>
     <item>
        <id>1</id>
        <name>Başlık 1</name>
     </item>
     <item>
        <id>2</id>
        <name>Başlık 2</name>
     </item>     
  </data>
</response>
```



## XML

Response Headers:
```
Method:       POST
Status:       200 OK
URL:          /v2/ce136df4c9c92d1428e828aba07d3b05/blacklistremove/xml/
Host:         organikapi.com
Content-Type: application/xml
```
Reponse Body:
```
<?xml version="1.0" encoding="UTF-8"?>
<response>
   <result>1</result>
</response>
```
