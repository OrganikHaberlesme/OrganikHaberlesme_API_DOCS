# Kara Listeye Kayıt Ekleme

```
request_name = blacklistadd
```

`POST` ile istenilen numara ya da numaraları kara listeye ekleme örneği aşağıda anlatılmıştır.

### `POST` ile Kara Listeye Kayıt Ekleme

`POST` URL Şablonu:
> /v2/`api_key`/**request_name**/`response_request_type`/**response_type**/
**POST** HTTP/1.1

Örnek `POST` URL'si:
> https://organikapi.com/v2/ce136df4c9c92d1428e828aba07d3b05/blacklistadd/

# Örnek İstek Gövdeleri:
## JSON
Request Headers:
```
Method: POST
Host:   organikapi.com
URL:    /v2/ce136df4c9c92d1428e828aba07d3b05/blacklistadd/json/
Accept: application/json
```
Form Data:
```
{
    "data": {
        "gsms": [
            "05301000000",
            "05301000001",
            "05301000002"
        ]
    }
}
```

## XML

Request Headers:
```
Method: POST
Host:   organikapi.com
URL:    /v2/ce136df4c9c92d1428e828aba07d3b05/blacklistadd/xml/
Accept: application/xml
```
Form Data:
```
<?xml version="1.0" encoding="UTF-8"?>
<document>
<data>
   <gsms>05301000000</gsms>
   <gsms>05301000001</gsms>
   <gsms>05301000002</gsms>
</data>
</document>
```


|Değişken|Gereklilik|Tip|Açıklama|
|-|-|-|-|
|persons|Zorunlu|Array|Bu değişkeni göndererek ister tek ister "," ile ayırarak birden çok GSM numarasını aynı anda kara listeye ekleyebilirsiniz. Bu değişkenin gönderilmesi zorunludur.|



# Başarılı Yanıt:
## JSON
Response Headers:
```
Method:       POST
Status:       200 OK
URL:          /v2/ce136df4c9c92d1428e828aba07d3b05/blacklistadd/json/
Host:         organikapi.com
Content-Type: application/json
```
Reponse Body:
```
{
    "response": {
        "result": true
    }
}
```

## XML

Response Headers:
```
Method:       POST
Status:       200 OK
URL:          /v2/ce136df4c9c92d1428e828aba07d3b05/blacklistadd/xml/
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

|Node|Tip|Açıklama|
|-|-|-|
|result|Boolean / Int|Yanıt işleminin durumunu belirtir.`true`/`false`değerlerini alır.`XML`yanıt gövdelerinde bu değer`Int`olur ve 0 / 1 değerlerini alır.|
