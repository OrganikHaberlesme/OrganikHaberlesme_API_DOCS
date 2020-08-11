# Kayıtlı Grupları Listeleme

```
request_name = groups
```

`GET` ile kayıtlı grupları listeleme örneği aşağıda anlatılmıştır. Bu fonksiyonda herhangi bir parametre göndermenize gerek yoktur.

### `GET` ile Kayıtlı Grupları Listeleme

`GET` URL Şablonu:
> /v2/`api_key`/**request_name**/`response_request_type`/**response_type**/
**GET** HTTP/1.1

Örnek `GET` URL'si:
> https://organikapi.com/v2/ce136df4c9c92d1428e828aba07d3b05/groups/

# Başarılı Yanıt:
## JSON
Response Headers:
```
Method:       GET
Status:       200 OK
URL:          /v2/ce136df4c9c92d1428e828aba07d3b05/groups/json/
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
                "id": 100,
                "name": "Group Name 1",
                "count": 12550
            },
            {
                "id": 101,
                "name": "Group Name 2",
                "count": 2550
            }
        ]
    }
}
```

## XML

Response Headers:
```
Method:       GET
Status:       200 OK
URL:          /v2/ce136df4c9c92d1428e828aba07d3b05/groups/xml/
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
       <id>100</id>
       <name>Group Name 1</name>
       <count>12550</count>         
    </item>
    <item>
       <id>101</id>
       <name>Group Name 2</name>
       <count>2500</count>           
    </item>  
  </data>
</response>
```

|Node|Tip|Açıklama|
|-|-|-|
|result|Boolean / Int|Yanıt işleminin durumunu belirtir.`true`/`false`değerlerini alır.`XML`yanıt gövdelerinde bu değer`Int`olur ve 0 / 1 değerlerini alır.|
|data.id |Integer|Grubun benzersiz ID'si.|
|data.name|String|Grup adı.|
|data.count|Integer|Grubun içinde kayıtlı kişi sayısı.|
