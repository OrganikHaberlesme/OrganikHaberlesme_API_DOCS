# Grubun Kişilerini Listeleme

```
request_name = groupcontent
```

`POST` ile kayıtlı grupların kişilerini listeleme örneği aşağıda anlatılmıştır.

### `POST` ile Kayıtlı Grupları Listeleme

`POST` URL Şablonu:
> /v2/`api_key`/**request_name**/`response_request_type`/**response_type**/
**POST** HTTP/1.1

Örnek `POST` URL'si:
> https://organikapi.com/v2/ce136df4c9c92d1428e828aba07d3b05/groupcontent/

# Örnek İstek Gövdeleri:
## JSON
Request Headers:
```
Method: POST
Host:   organikapi.com
URL:    /v2/ce136df4c9c92d1428e828aba07d3b05/groupcontent/json/
Accept: application/json
```
Form Data:
```
{
    "data": {
        "group_ids": [
            100,
            101
        ]
    }
}
```

## XML

Request Headers:
```
Method: POST
Host:   organikapi.com
URL:    /v2/ce136df4c9c92d1428e828aba07d3b05/groupcontent/xml/
Accept: application/xml
```
Form Data:
```
<?xml version="1.0" encoding="UTF-8"?>
<document>
<data>
   <group_ids>100</group_ids>
   <group_ids>101</group_ids>
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
URL:          /v2/ce136df4c9c92d1428e828aba07d3b05/groupcontent/json/
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
                "group_id": 100,
                "name": "Ahmet",
                "surname": "Sert",
                "gsm": 905321000001,
                "birthday": "1975-12-30"
            },
            {
                "group_id": 101,
                "name": "Mustafa",
                "surname": "Dere",
                "gsm": 905321000002,
                "birthday": "1974-12-30"
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
URL:          /v2/ce136df4c9c92d1428e828aba07d3b05/groupcontent/xml/
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
	   <group_id>100</group_id>
	   <name>Ahmet</name>
	   <surname>Sert</surname>
	   <gsm>905321000001</gsm>
	   <birthday>1975-12-30</birthday>           
	</item>
	<item>
	   <group_id>905001234568</group_id>
	   <name>Mustafa</name>
	   <surname>Dere</surname>
	   <gsm>905321000002</gsm>
	   <birthday>1974-12-30</birthday>           
	</item>               
  </data>
</response>
```

|Node|Tip|Açıklama|
|-|-|-|
|result|Boolean / Int|Yanıt işleminin durumunu belirtir. true / false değerlerini alır. XML yanıt gövdelerinde bu değer Int olur ve 0 / 1 değerlerini alır.|
|data.group_id|Integer|Kişinin ait olduğu grubun benzersiz ID'si.|
|data.name|String|Kayıtlı kişinin adı.|
|data.surname|String|Kayıtlı kişinin soyadı.|
|data.gsm|Integer|Kayıtlı kişinin GSM numarası.|
|data.birthday|Date|Kayıtlı kişinin doğum tarihi.|
