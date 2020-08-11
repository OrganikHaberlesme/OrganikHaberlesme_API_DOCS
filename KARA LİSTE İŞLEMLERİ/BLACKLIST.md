
# Kara Liste Kayıtlarını Listeleme

```
request_name = blacklist
```

`GET` ile kara liste kayıtlarını listeleme örneği aşağıda anlatılmıştır. Bu fonksiyonda herhangi bir parametre göndermenize gerek yoktur.

### `GET` ile Kara Liste Kayıtlarını Listeleme

`GET` URL Şablonu:
> /v2/`api_key`/**request_name**/`response_request_type`/**response_type**/
**GET** HTTP/1.1

Örnek `GET` URL'si:
> https://organikapi.com/v2/ce136df4c9c92d1428e828aba07d3b05/blacklist/

## JSON
Response Headers:
```
Method:       GET
Status:       200 OK
URL:          /v2/ce136df4c9c92d1428e828aba07d3b05/blacklist/json/
Host:         organikapi.com
Content-Type: application/json
```
Response Body:
```
{
    "response": {
        "result": true,
        "data": [
            {
                "gsm": 905321000001,
                "date": "2017-01-05"
            },
            {
                "gsm": 905321000002,
                "date": "2017-01-05"
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
URL:          /v2/ce136df4c9c92d1428e828aba07d3b05/blacklist/xml/
Host:         organikapi.com
Content-Type: application/xml
```
Response Body:
```
<?xml version="1.0" encoding="UTF-8"?>
<response>
  <result>1</result>
  <data>
    <item>
       <gsm>905321000001</gsm>
       <date>2017-01-05</date>
    </item>
    <item>
       <gsm>905321000002</gsm>
       <date>2017-01-05</date>
    </item> 
  </data>
</response>
```
|Node|Tip|Açıklama|
|-|-|-|
|result|Boolean / Int|Yanıt işleminin durumunu belirtir. true / false değerlerini alır. XML yanıt gövdelerinde bu değer Int olur ve 0 / 1 değerlerini alır.
|data.gsm|Integer|Kara liste kaydının GSM numarasıdır.
|data.date|Date|GSM numarasının kara listeye eklenme tarihidir.
