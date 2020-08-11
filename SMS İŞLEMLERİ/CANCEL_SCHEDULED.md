# İleri Tarihli Gönderimlerin İptali

```
request_name = cancelscheduledtasks
```

### `POST` ile İleri Tarihli Gönderimi İptal Etme

`POST` URL Şablonu:
> /v2/`api_key`/**request_name**/`response_request_type`/**response_type**/
**POST** HTTP/1.1

Örnek `POST` URL'si:
> https://organikapi.com/v2/ce136df4c9c92d1428e828aba07d3b05/cancelscheduledtasks/

# Örnek İstek Gövdeleri:
## JSON
Request Headers:
```
Method: POST
Host:   organikapi.com
URL:    /v2/ce136df4c9c92d1428e828aba07d3b05/cancelscheduledtasks/json/
Accept: application/json
```
Form Data:
```
{
    "data": {
        "transaction_ids": [
            100,
            101,
            102
        ]
    }
}
```

## XML

Request Headers:
```
Method: POST
Host:   organikapi.com
URL:    /v2/ce136df4c9c92d1428e828aba07d3b05/cancelscheduledtasks/xml/
Accept: application/xml
```
Form Data:
```
<?xml version="1.0" encoding="UTF-8"?>
<document>
<data>
   <transaction_ids>100</transaction_ids>
   <transaction_ids>101</transaction_ids>
   <transaction_ids>102</transaction_ids>
</data>
</document>
```


|Değişken|Gereklilik|Tip|Açıklama|
|-|-|-|-|
|transaction_ids|Zorunlu|Array|İptal etmek istediğiniz ileri tarihli görevlerin, SMS gönderim sonucunda veya raporlarda aldığınız ID'leridir. Bu değişkeni göndererek ister tek ister birden fazla ileri tarihli gönderim görevini aynı anda iptal edebilirsiniz. Gönderim görevleri iptal edildikten sonra geri döndürülemez.|

# Başarılı Yanıt:
## JSON
Response Headers:
```
Method:       POST
Status:       200 OK
URL:          /v2/ce136df4c9c92d1428e828aba07d3b05/cancelscheduledtasks/json/
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
                "transaction_id": 100,
                "status": true
            },
            {
                "transaction_id": 101,
                "status": false
            },
            {
                "transaction_id": 102,
                "status": false
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
URL:          /v2/ce136df4c9c92d1428e828aba07d3b05/cancelscheduledtasks/xml/
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
	   <transaction_id>100</transaction_id>
	   <status>1</status>          
	</item>
	<item>
	   <transaction_id>101</transaction_id>
	   <status>0</status>           
	</item>
	<item>
	   <transaction_id>102</transaction_id>
	   <status>0</status>           
	</item> 	               
  </data>
</response>
```
|Node|Tip|Açıklama|
|-|-|-|
|result|Boolean / Int|Yanıt işleminin durumunu belirtir. true / false değerlerini alır. XML yanıt gövdelerinde bu değer Int olur ve 0 / 1 değerlerini alır.|
|data.transaction_id|Integer|İptal edilmesi istenen ileri tarihli gönderimin benzersiz ID'si.|
|data.status|Integer|İptal edilmesi istenen görevin işlem durumu. JSON yanıt gövdelerinde, true / false, XML yanıt gövdelerinde ise 1 - başarılı, 0 - başarısız değerlerini alır.|
# Dinamik Keliemer
Aşağıdaki tabloda API2nin desteklediği dinamik kelimeleri bulabilirsiniz. Bu kelimelerin içerikleri, gruplarınızdaki kişilerin bilgilerinden gelmektedir. Örneğin, `AD` dinamik kelimesinin değeri, gönderim yapılan numaranın AD alanından gelir. Bu alanları panelde `Rehber > Kayıtlı Gruplar` sekmesinden düzenlersiniz.
