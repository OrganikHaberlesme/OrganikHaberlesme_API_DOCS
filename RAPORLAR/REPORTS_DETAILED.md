# Detaylı Rapor Alma

```
request_name = detailedreport
```

Organik API biri basit diğer detaylı olmak üzere 2 türlü rapor seçeneği içerir. Detaylı raporlamada döndürülen bilgiler ve raporun nasıl talep edileceği bilgisi aşağıda verilmiştir.

### `POST` ile Basit Rapor Alma

`POST` URL Şablonu:
> /v2/`api_key`/**request_name**/`response_request_type`/**response_type**/
**POST** HTTP/1.1

Örnek `POST` URL'si:
> https://organikapi.com/v2/ce136df4c9c92d1428e828aba07d3b05/detailedreport/

# Örnek İstek Gövdeleri:
## JSON
Request Headers:
```
Method: POST
Host:   organikapi.com
URL:    /v2/ce136df4c9c92d1428e828aba07d3b05/detailedreport/json/
Accept: application/json
```
Form Data:
```
{
    "data": {
        "transaction_ids": [id, id, id],
        "delivery_track_ids": [id, id, id],
        "gsm_track_ids": [id, id, id]
    }
}
```

## XML

Request Headers:
```
Method: POST
Host:   organikapi.com
URL:    /v2/ce136df4c9c92d1428e828aba07d3b05/detailedreport/xml/
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
URL:          /v2/ce136df4c9c92d1428e828aba07d3b05/detailedreport/json/
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
                "gsm" : 905445359675,
                "transaction_id" : 14094857,
                "gsm_track_id" : 410471976,
                "delivery_track_id" : "b627ffe79fc148e8ea7425222c4ed8",
                "create_date" : "2016-11-02 11:47:38",
                "start_date" : "2016-11-02 11:47:38",
                "finish_date" : "2016-11-02 12:47:42",
                "status" : 2,
                "sms_count" : 1,
                "credit_amount" : 1,
                "is_foreign_gsm" : 0
            }, 
            {
                "gsm" : 61491570156,
                "transaction_id" : 14094857,
                "gsm_track_id" : 410471979,
                "delivery_track_id" : "b627ffe79fc148e8ea7425222c4ed8",
                "create_date" : "2016-11-02 11:47:38",
                "start_date" : "2016-11-02 11:47:38",
                "finish_date" : "2016-11-02 13:47:45",
                "status" : 4,
                "sms_count" : 1,
                "credit_amount" : 0,
                "is_foreign_gsm" : 1
            },             
            {
                "gsm" : 905445359675,
                "transaction_id" : 16334701,
                "gsm_track_id" : 474057742,
                "delivery_track_id" : "6959792d54f3c7510bcbb6303a67a4",
                "create_date" : "2017-02-02 11:36:09",
                "start_date" : "2017-02-28 00:00:00",
                "finish_date" : null,
                "status" : 0,
                "sms_count" : 0,
                "credit_amount" : 0,
                "is_foreign_gsm" : 0
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
URL:          /v2/ce136df4c9c92d1428e828aba07d3b05/basicreport/xml/
Host:         organikapi.com
Content-Type: application/xml
```
Reponse Body:
```
<?xml version="1.0" encoding="UTF-8" ?>
<item>
   <gsm>905445359675</gsm>
   <transaction_id>14094857</transaction_id>
   <gsm_track_id>410471976</gsm_track_id>
   <delivery_track_id>b627ffe79fc148e8ea7425222c4ed8</delivery_track_id>
   <create_date>2016-11-02 11:47:38</create_date>
   <start_date>2016-11-02 11:47:38</start_date>
   <finish_date>2016-11-02 12:47:42</finish_date>
   <status>2</status>
   <sms_count>1</sms_count>
   <credit_amount>1</credit_amount>
   <is_foreign_gsm>0</is_foreign_gsm>
</item>
<item>
   <gsm>61491570156</gsm>
   <transaction_id>14094857</transaction_id>
   <gsm_track_id>410471979</gsm_track_id>
   <delivery_track_id>b627ffe79fc148e8ea7425222c4ed8</delivery_track_id>
   <create_date>2016-11-02 11:47:38</create_date>
   <start_date>2016-11-02 11:47:38</start_date>
   <finish_date>2016-11-02 13:47:45</finish_date>
   <status>4</status>
   <sms_count>1</sms_count>
   <credit_amount>0</credit_amount>
   <is_foreign_gsm>1</is_foreign_gsm>
</item>
<item>
   <gsm>905445359675</gsm>
   <transaction_id>16334701</transaction_id>
   <gsm_track_id>474057742</gsm_track_id>
   <delivery_track_id>6959792d54f3c7510bcbb6303a67a4</delivery_track_id>
   <create_date>2017-02-02 11:36:09</create_date>
   <start_date>2017-02-28 00:00:00</start_date>
   <finish_date />
   <status>0</status>
   <sms_count>0</sms_count>
   <credit_amount>0</credit_amount>
   <is_foreign_gsm>0</is_foreign_gsm>
</item>
```

|Node|Tip|Açıklama|
|-|-|-|
|result|Boolean / Int|Yanıt işleminin durumunu belirtir.`true`/`false`değerlerini alır.`XML`yanıt gövdelerinde bu değer`Int`olur ve 0 / 1 değerlerini alır.|
|gsm|Int|Mesaj gönderilen GSM numarası|
|transaction_id|Integer|Atışın ait olduğu gönderim görevi ID'sidir.|
|gsm_track_id|Integer|`sendsms`komutundan gelen yanıt gövdesinde yer alan`gsm_track_id`'sidir.|
|delivery_track_id|String|`sendsms`komutunda işlemleriniz için girdiğin benzersiz ID değeridir.|
|create_date|datetime|Gönderim görevinin oluşturulma tarihidir.|`
|start_date|datetime|Görevin gönderime başlandığı tarihtir.|
|finish_date|datetime|Bu numara gönderiminin sonuçlandığı tarih. Eğer gönderim henüz sonuçlanmamışsa bu değer`null`gelir.|
|status|Integer|Bu numara gönderiminin durum bilgisini verir. 0 - henüz gönderilmedi, 1 - operatöre iletildi, 2 - alıcıya iletildi, 3 - hatalı numara, 4 - zaman aşımı anlamına gelir.|
|sms_count|Integer|Gönderim metninizin kaç SMS uzunluğunda olduğu bilgisini verir. Eğer bu numaraya gönderim işlemi henüz başlamamışsa değeri`0`olur.|
|credit_amount|Integer|Gönderiminiz için hesaplanan toplam kredi miktarını verir. Bu miktar gönderiminiz için harcanan kredi miktarı`değildir`. Yurtdışı numaralar ve henüz başlamamışlar işlemler için değeri`0`olur.|
|is_foreign_gsm|Integer|Gönderim yaptığınız GSM numarasının yurtdışına ait bir numara olup olmadığı bilgisini verir. 1 - yurtdışı numara, 0 - yurtiçi numara anlamına gelir.|
