
# Yeni Gruplar Oluşturma

```
request_name = groupadd
```

`POST` ile yeni gruplar oluşturma örneği aşağıda anlatılmıştır.

### `POST` ile Yeni Gruplar Oluşturma.

`POST` URL Şablonu:
> /v2/`api_key`/**request_name**/`response_request_type`/**response_type**/
**POST** HTTP/1.1

Örnek `POST` URL'si:
> https://organikapi.com/v2/ce136df4c9c92d1428e828aba07d3b05/groupadd/

# Örnek İstek Gövdeleri:
## JSON
Request Headers:
```
Method: POST
Host:   organikapi.com
URL:    /v2/ce136df4c9c92d1428e828aba07d3b05/groupadd/json/
Accept: application/json
```
Form Data:
```
{
    "data": {
        "groups": [
            "deneme grup 1",
            "deneme grup 2",
            "deneme grup 3"
        ]
    }
}
```

## XML

Request Headers:
```
Method: POST
Host:   organikapi.com
URL:    /v2/ce136df4c9c92d1428e828aba07d3b05/groupadd/xml/
Accept: application/xml
```
Form Data:
```
<?xml version="1.0" encoding="UTF-8"?>
<document>
<data>
   <groups>deneme grup 1</groups>
   <groups>deneme grup 2</groups>
   <groups>deneme grup 3</groups>
 </data>
</document>
```


|Değişken|Gereklilik|Tip|Açıklama|
|-|-|-|-|
|groups	|Zorunlu|Array|İster tek ister dizi halinde "," ile ayırarak birden çok yeni grup adı gönderebilirsiniz.|

# Başarılı Yanıt:
## JSON
Response Headers:
```
Method:       POST
Status:       200 OK
URL:          /v2/ce136df4c9c92d1428e828aba07d3b05/groupadd/json/
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
                "name": "deneme grup 1"
            },
            {
                "id": 101,
                "name": "deneme grup 2"
            },
             {
                "id": 102,
                "name": "deneme grup 3"
            }

        ]
    }
}
```

## XML

Response Headers:
```
Method:       POST
Status:       200 OK
URL:          /v2/ce136df4c9c92d1428e828aba07d3b05/groupadd/xml/
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
	   <name>deneme grup 1</name>
	</item>
         	<item>
	   <id>101</id>
	   <name>deneme grup 2</name>
	</item>
             	<item>
	   <id>103</id>
	   <name>deneme grup 3</name>
	</item>
  </data>
</response>
```

|Node|Tip|Açıklama|
|-|-|-|
|result|Boolean / Int|Yanıt işleminin durumunu belirtir.`true`/`false`değerlerini alır.`XML`yanıt gövdelerinde bu değer`Int`olur ve 0 / 1 değerlerini alır.|
|data.id |Integer|grubun benzersiz ID'si.|
|data.name	String	grup adı.|
