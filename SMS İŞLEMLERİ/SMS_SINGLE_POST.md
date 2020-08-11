# POST ile SMS Gönderme

```
request_name = sendsms
```

`POST` ile SMS göndermeyle ilgili örnekler aşağıda verilmiştir.

`POST` ile yaptığınız tüm isteklerin yanıt tipini request_response_type veya response_type parametresi ile ayarlayabilirsiniz.

`POST` URL Şablonu:
> /v2/`api_key`/**request_name**/`response_request_type`/**response_type**/
**POST** HTTP/1.1

Örnek `POST`` URL'si:
> https://organikapi.com/v2/ce136df4c9c92d1428e828aba07d3b05/sendsms/

# Örnek İstek Gövdeleri:
## JSON
Request Headers:
```
Method: POST
Host:   organikapi.com
URL:    /v2/ce136df4c9c92d1428e828aba07d3b05/sendsms/json/
Accept: application/json
```
Form Data:
```
{
   "data": {
      "deliveries": [
         {
            "options": {
               "header": "OHT",
               "delivery_time": "2020-08-11 07:11",
               "timeout": 24,
               "message_format": 1,
               "gsm_isUnique": 0,
               "track_id": 1234,
               "report_url": "http://www.domain.com/rapor_al/"
            },
            "recipients": {
               "groups": [
                  1,
                  2,
                  3
               ],
               "gsms": [
                   905301234567,
                   905301234568,
                   905301234569
               ]
            },
            "message": "QnUgYmlyIGRlbmVtZSBtZXNhasSxZMSxcg=="
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
URL:    /v2/ce136df4c9c92d1428e828aba07d3b05/sendsms/xml/
Accept: application/xml
```
Form Data:
```
<?xml version="1.0" encoding="UTF-8"?>
<document>
<data>
   <deliveries>
      <options>
         <delivery_time />
         <header />
         <message_format />
         <timeout />
      </options>
      <recipients>
         <groups>1</groups>
         <groups>2</groups>
         <groups>3</groups>
         <gsms>905301234567</gsms>
         <gsms>905301234568</gsms>
         <gsms>905301234569</gsms>
      </recipients>
      <message>QnUgYmlyIGRlbmVtZSBtZXNhasSxZMSxci4=</message>
   </deliveries>
</data>
</document>
```


|Değişken|Gereklilik|Tip|Açıklama|
|-|-|-|-|
|deliveries|Zorunlu|-|İstek gövdenizin ana elemanıdır. Tüm istekleriniz`data`etiketinin içinde olmalıdır.|
|options|Zorunlu|-|Gönderiminizin seçeneklerini belirlediğiniz bölümdür. Gönderilmesi zorunlu değildir. Gönderilmediği taktirde API varsayılan değerlerle işleminizi gerçekleştirir.|
|options.header|Zorunlu|String / Integer|Gönderdiğiniz SMS'in kim tarafından atıldığı bilgisidir. Kayıtlı başlıklarınızdan birinin ID'si veya direkt adını alabilir. Başlık adı yazılırken kayıtlı başlık adıyla aynı ve büyük harflerle yazıldığından emin olunuz. Başlık adlarının tutmaması durumunda gönderiminiz gerçekleşmeyecektir.|
|options.delivery_time|Opsiyonel|Datetime|Gönderiminizin ileri bir tarihte yapılmasını istiyorsanız, istediğiniz tarihi bu parametreyle gönderebilirsiniz. Gönderdiğiniz tarih`yyyy-aa-gg SS:dd`formatında olmalıdır (Örn: 2017-01-04 15:46). Eğer gönderiminizin hemen yapılmasını istiyorsanız bu parametreyi göndermenize gerek yoktur. Gönderilen saat değeri +3 İstanbul UTC değerinde olmalıdır.|
|options.timeout|Opsiyonel|Integer|İlgili SMS operatöre iletildikten sonra mesajın operatörden alıcıya iletilmek için en fazla ne kadar süre ile bekletileceğini belirlediğiniz değişkendir.`timeout`değerinde belirtilen süre boyunca SMS alıcıya ulaştırılamazsa ilgili SMS iptal olur ve yurtiçi SMS'lerde krediniz otomatik iade edilir. Girdiğiniz değerler saat cinsindendir ve`int`olmalıdır. Bu değişken opsiyoneldir. Varsayılan değeri`48`saattir.|
|options.message_format|Opsiyonel|Integer|Gönderiminizin hangi karakter setleriyle yapılacağını belirler.`0`,`1`ve`2`değerlerini alır. 0 -`normal`, 1 -`turkish`, 2 -`unicode`değeridir.`normal`olarak ayarlandığında sadece İngilizce karakterlerle gönderim yapılır.`turkish`olarak ayarlandığında Türkçe karakterle atış yapılır.`unicode`değeri ise yurtdışı gönderimlerde farklı alfabelerle atış yapmak için kullanılır. Varsayılan değeri`0`'dır.|
|options.gsm_isunique|Zorunlu|1|Gönderim yaptığınız numaraların içinde tekrarlanan numaralar varsa bu numaralara da gönderim yapılıp yapılmayacağını belirleyen parametredir. 1 - olduğunda tekrarlanan numaraların sadece 1 tanesine gönderim yapılır, 0 - olduğunda ise tekrarlanan numaraların tümüne gönderim yapılır. Alacağı değer`int`olmalıdır.|
|options.track_id|Opsiyonel|N/A|Gönderiminizi kendi sisteminizde takip edebilmek için üreteceğiniz benzersiz`integer`değerdir.|
|options.report_url|Opsiyonel|N/A|Gönderiminiz tamamlandıktan sonra gönderim raporunun`POST`edileceği adrestir.`POST`edilen rapor formatı`JSON`'dır. Girdiğiniz değer`http://< domain >.com/`şeklinde olmalıdır.|
|recipients|Zorunlu|-|Gönderim yapmak istediğiniz numara ve/veya grupları belirlediğiniz bölümdür.|
|recipients.groups|Değişken|Array|Kayıtlı gruplarınıza gönderim yapmak istiyorsanız, bir veya birden fazla grup ID değerini bu değişkene yazarak gönderim yapabilirsiniz (Örn: 1,2,3,4,...). Birden fazla grup ID'si yazdığınız durumlarda, ID değerlerinden geçersiz olanlar varsa gönderiminiz sadece geçerli ID'lere yapılır.`recipients.gsms`değişkenine geçerli bir değer verildiğinde bu değişken opsiyonel hale gelir, gönderilmesi zorunlu değildir. Bunun dışındaki tüm koşullarda gönderilmesi zorunludur.|
|recipients.gsms|Değişken|Array|Mesajınızın atılacağı numaraları belirlediğiniz değişkendir.`,`ile ayırarak birden fazla numara yazabilirsiniz (Örn: 905301234567,901234566,901234555,...). Bu değişkende belirttiğiniz virgül ile ayrılmış numaraların sınırlaması yoktur, n tane olabilir.`recipients.groups`değişkenine geçerli bir değer verildiğinde bu değişken opsiyonel hale gelir, gönderilmesi zorunlu değildir. Bunun dışındaki tüm koşullarda gönderilmesi zorunludur.|
|message|Zorunlu|String|Gönderiminizin metnidir.`base64`formatında gönderilmelidir.`base64`formatına çevrilmemiş halinin uzunluğu en fazla gönderilecek mesaj metinin tipine (`message_format`değerine) göre değişiklik göstermektedir. Mesaj karakterlerinin tamamının doğru iletilebilmesi için mesaj metnini `base64` formatına dönüştürerek yollamak zorunludur.|

# Başarılı Yanıt:
## JSON
Response Headers:
```
Method:       POST
Status:       200 OK
URL:          /v2/ce136df4c9c92d1428e828aba07d3b05/sendsms/json/
Host:         organikapi.com
Content-Type: application/json
```
Reponse Body:
```
{
   "response": {
      "result": true,
         "data": {
            "deliveries": [{
               "track_id": 1234,
               "transaction_id": 16502030,
               "valid": [
                  {
                     "request_gsm": 5444444444,
                     "gsm": 905445359675,
                     "gsm_track_id": "16502030-4730-63032793",
                     "tl_amount": 0,
                     "sms_count": 1,
                     "credit_amount": 1
                  }, {
                     "request_gsm": 5444444445,
                     "gsm": 905445359675,
                     "gsm_track_id": "16502030-4730-70484559",
                     "tl_amount": 0,
                     "sms_count": 1,
                     "credit_amount": 1
                  }
               ],
               "invalid": [
                  {
                     "request_gsm": 5444444446,
                     "gsm": 905444444446,
                     "error": {
                        "number": 110,
                        "message": "The number is incorrect."
                     }
                  }
               ]
            }            
         ]
      }
   }
}
```

## XML

Response Headers:
```
Method:       POST
Status:       200 OK
URL:          /v2/ce136df4c9c92d1428e828aba07d3b05/sendsms/xml/
Host:         organikapi.com
Content-Type: application/xml
```
Reponse Body:
```
<?xml version="1.0" encoding="UTF-8"?>
<response>
   <data>
   <result>1</result>
      <deliveries>
         <item>
            <track_id>2567</track_id>
            <transaction_id>16502030</transaction_id>
            <valid>
               <item>
                  <request_gsm>5444444444</request_gsm>
                  <gsm>905444444444</gsm>
                  <gsm_track_id>16502030-4730-63032793</gsm_track_id>
                  <tl_amount>0</tl_amount>
                  <sms_count>1</sms_count>
                  <credit_amount>1</credit_amount>
               </item>
               <item>
                  <request_gsm>5444444445</request_gsm>
                  <gsm>905444444445</gsm>
                  <gsm_track_id>16587001-4730-70484559</gsm_track_id>
                  <tl_amount>0</tl_amount>
                  <sms_count>1</sms_count>
                  <credit_amount>1</credit_amount>
               </item>                  
            </valid>
            <invalid>
               <item>
                  <request_gsm>5444444446</request_gsm>
                  <gsm>4444</gsm>
                  <error>
                     <number>110</number>
                     <message>The number is incorrect.</message>
                  </error>
               </item>
            </invalid>
         </item>       
      </deliveries>
   </data>
</response>
```


|Node|Tip|Açıklama|
|-|-|-|
|result|Boolean / Int|Yanıt işleminin durumunu belirtir.`true`/`false`değerlerini alır.`XML`yanıt gövdelerinde bu değer`Int`olur ve `0 / 1` değerlerini alır.|
|data.deliveries|Array|Gönderim görevinizdeki işlemlerin detayları burada gönderilir.|
|data.deliveries.track_id|String|Yapılan her gönderim işlemi için sizin tarafınızdan üretilen ID'dir. Bu veriyi raporlamalarınızda kullanabilirsiniz.|
|data.deliveries.transaction_id|Integer|Gönderim işleminin sistem tarafından otomatik oluşturulan benzersiz ID'sidir. Gönderim görevindeki her ileti (`deliveries`) için ayrı bir ID üretilir.|
|data.valid|Array|Gönderim görevinizdeki işleme alınan bütün GSM numaralarının detayları burada gönderilir.|
|data.valid.request_gsm|Integer|İşlem sırasında API'ye gönderdiğiniz GSM numarasıdır.|
|data.valid.gsm|Integer|`request_gsm`uluslararası geçerli telefon formatına dönüştürülerek API tarafından kullanılan GSM numarasıdır. Raporlamalarda bu GSM numarası kullanılır.|
|data.valid.gsm_track_id|String|Gönderim yapılan her numara için benzersiz olarak üretilen ID'dir. Bu veriyi raporlamalarınızda kullanabilirsiniz.|
|data.valid.tl_amount|Integer|Gönderilen SMS'in TL tutarı bilgisini verir. Yurtdışı numaralar TL bakiye ile gönderilir. TL tutarı raporlamalarda gönderilmez.|
|data.valid.sms_count|Integer|Gönderim metninizin kaç SMS uzunluğunda olduğu bilgisini verir.|
|data.valid.credit_amount|Integer|Gönderiminiz için hesaplanan toplam kredi miktarını verir. Bu miktar gönderiminiz için harcanan kredi miktarı`değildir`. Yurtdışı numaralar ve henüz başlamamışlar işlemler için değeri`0`olur.|
|data.invalid|Array|Gönderim görevinizdeki işleme alınamayan bütün GSM numaralarının detayları burada gönderilir. İçeriği`valid`parametreleri ile aynıdır.|
|data.invalid.request_gsm|Integer|İşlem sırasında API'ye gönderdiğiniz GSM numarasıdır.|
|data.invalid.gsm|Integer|`request_gsm`uluslararası geçerli telefon formatına dönüştürülerek API tarafından kullanılan GSM numarasıdır. Raporlamalarda bu GSM numarası kullanılır.|
|data.invalid.error.number|Integer|İşlemin ürettiği hata kodudur. Anlamları için hata kodları sayfasına bakabilirsiniz.|
|data.invalid.error.message|Integer|İşlemin ürettiği hata mesajıdır|
