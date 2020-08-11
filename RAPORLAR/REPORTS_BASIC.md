
# Basit Rapor Alma

```
request_name = basicreport
```

Organik API biri basit diğer detaylı olmak üzere 2 türlü rapor seçeneği içerir. Basit raporlamada döndürülen bilgiler ve raporun nasıl talep edileceği bilgisi aşağıda verilmiştir.

### `POST` ile Basit Rapor Alma

`POST` URL Şablonu:
> /v2/`api_key`/**request_name**/`response_request_type`/**response_type**/
**POST** HTTP/1.1

Örnek `POST` URL'si:
> https://organikapi.com/v2/ce136df4c9c92d1428e828aba07d3b05/basicreport/

# Örnek İstek Gövdeleri:
## JSON
Request Headers:
```
Method: POST
Host:   organikapi.com
URL:    /v2/ce136df4c9c92d1428e828aba07d3b05/basicreport/json/
Accept: application/json
```
Form Data:
```
{
    "data": {
        "transaction_ids": [id,id,id],
        "delivery_track_ids": [id,id,id],
        "gsm_track_ids": [id,id,id]
    }
}
```

## XML

Request Headers:
```
Method: POST
Host:   organikapi.com
URL:    /v2/ce136df4c9c92d1428e828aba07d3b05/basicreport/xml/
Accept: application/xml
```
Form Data:
```
<?xml version="1.0" encoding="UTF-8"?>
<document>
<data> 
   <transaction_ids> id </transaction_ids>
   <transaction_ids> id </transaction_ids>
   <transaction_ids> id </transaction_ids>
   <delivery_track_ids> id </delivery_track_ids>
   <delivery_track_ids> id </delivery_track_ids>
   <delivery_track_ids> id </delivery_track_ids>
   <gsm_track_ids> id </gsm_track_ids>
   <gsm_track_ids> id </gsm_track_ids>
   <gsm_track_ids> id </gsm_track_ids>   
</data>
</document>
```


|Değişken|Gereklilik|Tip|Açıklama|
|-|-|-|-|
|transaction_ids|Opsiyonel|Array|`sendsms` komutundan gelen yanıt gövdesinde yer alan transaction ID'leridir. Dizi şeklinde birden fazla ID gönderip, çoklu görev sorgulamaları yapabilirsiniz.|
|delivery_track_ids|Opsiyonel|Array|`sendsms` komutunda işlemleriniz için girdiğin benzersiz ID değeridir. Dizi şeklinde birden fazla ID gönderip, çoklu görev sorgulamaları yapabilirsiniz.|
|gsm_track_ids|Opsiyonel|Array|`sendsms` veya `detailedreport` komutundan gelen yanıt gövdesinde yer alan `gsm_track_id`'leridir. Dizi şeklinde birden fazla ID gönderip, çoklu görev sorgulamaları yapabilirsiniz.|

# Başarılı Yanıt:
## JSON
Response Headers:
```
Method:       POST
Status:       200 OK
URL:          /v2/ce136df4c9c92d1428e828aba07d3b05/basicreport/json/
Host:         organikapi.com
Content-Type: application/json
```
Reponse Body:
```
{
    "response": {
        "result": true,
        "data": {
            "gsm_count": 14,
            "credit_amount": 9,
            "tl_amount": 0.97,
            "sending_count": 0,
            "sended_count": 0,
            "deliveried_count": 4,
            "wrong_count": 6,
            "timeout_count": 4,
            "sms_count": 3,
        }
    }
}
```

## XML

Response Headers:
```
Method:       POST
Status:       200 OK
URL:          /v2/ce136df4c9c92d1428e828aba07d3b05/basicreport/xml/
Host:         organikapi.com
Content-Type: application/xml
```
Reponse Body:
```
<?xml version="1.0" encoding="UTF-8"?>
<response>
   <result>1</result>
   <data>
      <gsm_count>14</gsm_count>
      <credit_amount>9</credit_amount>
      <tl_amount>0.97</tl_amount>
      <sending_count>0</sending_count>
      <sended_count>0</sended_count>
      <deliveried_count>4</deliveried_count>
      <wrong_count>6</wrong_count>
      <timeout_count>4</timeout_count>
      <sms_count>3</sms_count>
   </data>
</response>
```

|Node|Tip|Açıklama|
|-|-|-|
|result|Boolean / Int|Yanıt işleminin durumunu belirtir.`true`/`false`değerlerini alır.`XML`yanıt gövdelerinde bu değer`Int`olur ve `0` / `1` değerlerini alır.|
|gsm_count|Integer|Talep ettiğiniz raporlardaki toplam gönderilen GSM saysını verir.|
|credit_amount|Integer|Talep ettiğiniz rapordaki tüm gönderimleriniz için hesaplanan toplam kredi miktarını verir. Bu miktar gönderiminiz için harcanan kredi miktarı`değildir`.|
|tl_amount|Decimal|Bu değer gönderimlerinizde yurtdışı numaralar varsa dolu gelir. Yurtdışı gönderimlerinizin dışındaki tüm gönderimler kredi ile yapılır.|
|sending_count|Integer|Henüz işlemen alınmamış ve gönderilmeyi bekleyen gönderim sayısıdır.|
|sended_count|Integer|İşlenmiş ve operatöre gönderilmiş gönderim sayısıdır.|
|deliveried_count|Integer|Talep ettiğiniz raporlardaki tüm gönderimlerinizde iletilen numaraların toplamıdır.|
|wrong_count|Integer|Talep ettiğiniz raporlardaki tüm gönderimlerinizdeki hatalı numara sayısıdır. Bu numaralar işleme alınmaz ve -eğer düşmüşse- kredileri iade edilir.|
|timeout_count|Integer|İşlenmesi için operatöre gönderilmiş ancak zaman aşımı süresince iletilmemiş gönderim sayısıdır. Eğer düşmüşse kredileri iade edilir.|
|sms_count|Integer|Gönderim metninizin kaç SMS uzunluğunda olduğu bilgisini verir.|
