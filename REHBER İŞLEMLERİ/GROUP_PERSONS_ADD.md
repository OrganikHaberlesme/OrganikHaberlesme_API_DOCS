# Gruplarınıza Yeni Kişiler Ekleme

```
request_name = groupcontentadd
```

`POST` ile kayıtlı gruplarınıza yeni kişileri ekleyebilirsiniz.

### `POST` ile Gruplara Yeni Kişiler Ekleme

`POST` URL Şablonu:
> /v2/`api_key`/**request_name**/`response_request_type`/**response_type**/
**POST** HTTP/1.1

Örnek `POST` URL'si:
> https://organikapi.com/v2/ce136df4c9c92d1428e828aba07d3b05/groupcontentadd/

# Örnek İstek Gövdeleri:
## JSON
Request Headers:
```
Method: POST
Host:   organikapi.com
URL:    /v2/ce136df4c9c92d1428e828aba07d3b05/groupcontentadd/json/
Accept: application/json
```
Form Data:
```
{
    "data": {
        "persons": [
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

Request Headers:
```
Method: POST
Host:   organikapi.com
URL:    /v2/ce136df4c9c92d1428e828aba07d3b05/groupcontentadd/xml/
Accept: application/xml
```
Form Data:
```
<?xml version="1.0" encoding="UTF-8"?>
<document>
<data>

	<persons>
	   <group_id>100</group_id>
	   <name>Ahmet</name>
	   <surname>Sert</surname>
	   <gsm>905321000001</gsm>
	   <birthday>1975-12-30</birthday>
	</persons>
	<persons>
	   <group_id>905001234568</group_id>
	   <name>Mustafa</name>
	   <surname>Dere</surname>
	   <gsm>905321000002</gsm>
	   <birthday>1974-12-30</birthday>
	</persons>

</data>
</document>
```


|Değişken|Gereklilik|Tip|Açıklama|
|-|-|-|-|
|persons|Zorunlu|Array|İster tek ister dizi ile birden çok kişi bilgilerini gönderebilirsiniz.|
|group_id|Zorunlu|integer|ilgili kişinin hangi grup numarasına kayıt edileceğini bildirirsiniz. her bir kişiyi ayrı ayrı gruplara kayıt edebilirsiniz.|
|name|opsiyonel|string(50)|Grup içerisine kayıt etmek istediğiniz kişinin adı.|
|surname|opsiyonel|string(50)|Grup içerisine kayıt etmek istediğiniz kişinin soyadı.|
|gsm|Zorunlu|integer(13)|Grup içerisine kayıt etmek istediğiniz kişinin cep telefon numarası. GSM numara formatına uygun değilse işleme alınmayacaktır.|
|birthday|opsiyonel|date(string)|Grup içerisine kayıt etmek istediğiniz kişinin doğum tarihi. (Yıl-Ay-Gün)|


# Başarılı Yanıt:
## JSON
Response Headers:
```
Method:       POST
Status:       200 OK
URL:          /v2/ce136df4c9c92d1428e828aba07d3b05/groupcontentadd/json/
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
                "group_id": 100,
                "name": "Ahmet",
                "surname": "Sert",
                "gsm": 905321000001,
                "birthday": "1975-12-30"
            },
            {
                "id": 2,
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
URL:          /v2/ce136df4c9c92d1428e828aba07d3b05/groupcontentadd/xml/
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
    	   <group_id>100</group_id>
	   <name>Ahmet</name>
	   <surname>Sert</surname>
	   <gsm>905321000001</gsm>
	   <birthday>1975-12-30</birthday>           
	</item>
	<item>
         <id>2</id>
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
|result|Boolean / Int|Yanıt işleminin durumunu belirtir.`true`/`false`değerlerini alır.`XML`yanıt gövdelerinde bu değer`Int`olur ve 0 / 1 değerlerini alır.|
|data.id|Integer|Kişinin ait olduğu benzersiz ID'si.|
|data.group_id|Integer|Kişinin ait olduğu grubun benzersiz ID'si.|
|data.name|String|Kayıtlı kişinin adı.|
|data.surname|String|Kayıtlı kişinin soyadı.|
|data.gsm|Integer|Kayıtlı kişinin GSM numarası.|
|data.birthday|Date|Kayıtlı kişinin doğum tarihi.|
