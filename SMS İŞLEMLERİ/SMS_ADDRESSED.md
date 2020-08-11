# Hitaplı Toplu SMS Gönderme

```
request_name = sendsms
```

Hitaplı Toplu SMS gönderme işlemi `POST` metodu ile yapılır. Tek bir işlemde aynı anda birden fazla gönderim görevi oluşturabilir, bu görevlerin her birinde sınırsız gruba gönderim yapabilirsiniz.

Hitaplı Toplu SMS gönderimi için grup kullanımı şarttır. Ayrıca hitap kelimelerini ve mesaja eklemek istediğiniz dinamik kelimeleri mesaj metninde ayarlarsınız. Dinamik kelimeleriniz gruplarınızdaki kişilerin bilgilerinden gelir.

Organik API oluşturduğunuz gönderim görevlerindeki her bir numara için ayrı ayrı takip kodu oluşturur ve tüm gönderileri tek tek denetlemenize imkan sağlar. Aşağıda sıklıkla kullanabileceğiniz hitaplı toplu SMS gönderme işlemlerine örnekleri bulabilirsiniz.

# Dinamik Keliemer
Aşağıdaki tabloda API2nin desteklediği dinamik kelimeleri bulabilirsiniz. Bu kelimelerin içerikleri, gruplarınızdaki kişilerin bilgilerinden gelmektedir. Örneğin, `AD` dinamik kelimesinin değeri, gönderim yapılan numaranın AD alanından gelir. Bu alanları panelde `Rehber > Kayıtlı Gruplar` sekmesinden düzenlersiniz.

|Dinamik Kelime|Karşılık Alanı|
|-|-|
|`#AD#`|Ad|
|`#SOYAD#`|Soyad|
|`#GSM#`|GSM Numarası|
|`#OZEL1#`|Özel alan 1|
|`#OZEL2#`|Özel alan 2|
|`#OZEL3#`|Özel alan 3|
|`#OZEL4#`|Özel alan 4|
|`#OZEL5#`|Özel alan 5|


> Sayın `#AD#` `#SOYAD#`, `#GSM#` numaralı hattınızın `#OZEL1#` dönemi borcu `#OZEL2#` TL'dir.

Bu mesaj metni işlenirken çıktısı veritabanındaki bilgilere göre değişecek şekilde şöyle olur:

> Sayın `ORGANİK` `HABERLEŞME`, `05001234567` numaralı hattınızın `Kasım` dönemi borcu `121.25` TL'dir.

### `POST` ile Hitaplı Toplu SMS Gönderme

`POST` URL Şablonu:
> /v2/`api_key`/**request_name**/`response_request_type`/**response_type**/
**POST** HTTP/1.1

Örnek `POST` URL'si:
> https://organikapi.com/v2/ce136df4c9c92d1428e828aba07d3b05/sendsms/

### İstekte Bulunma:
Organik API tek bir istek gövdesinde birden fazla ileti oluşturarak, bu iletilerde ayrı ayrı binlerce numaraya SMS göndermenize imkan verir. Yanıt gövdesinin içinde bulunan `global_options` nesnesinin değerleri ile gövde içinde bulunan bütün iletilere ortak ayarlar tanımlayabileceğiniz gibi, oluşturduğunuz tüm iletilerin içinde yer alan `options` nesnesi ile ayrı ayrı ayarlar da tanımlayabilirsiniz.

API iletilerinize özellik atamalarını yaparken varsayılan olarak önce `global_options` nesnesini kontrol eder. Bu nesnenin içinde yer alan bilgilerin tümünü, tüm iletilere atar. `global_option`s nesnesinin içinde yer almayan özellikleri ise iletilerin `options` nesnesinde arar.

Aşağıda örnek istek gövdeleri ve içindeki değişken ve nesnelerin anlamlarını anlatan tabloları bulabilirsiniz.



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
      "global_options": {
         "track_id": "1234",
         "header": "ORGANIKHBR",
         "delivery_time": "",
         "timeout": 48,
         "message_format": 0,
         "report_url": "",
         "gsm_isUnique": 0
      },
      "deliveries": [
         {
            "options": {
               "track_id": "1235",
               "header": "OHT",
               "delivery_time": "",
               "timeout": 12,
               "message_format": "",
               "report_url": ""
            },
            "recipients": {
               "groups": [
                  1,
                  2,
                  3
               ]
            },
            "message": "QnUgYmlyIGRlbmVtZSBtZXNhasSxZMSxcg=="
         },
         {
            "options": {
               "track_id": 1236,
               "header": "OHT3"
            },
            "recipients": {
               "gsms": [
                   905301234567
               ]
            },
            "message": "T3JnYW5payBIYWJlcmxlxZ9tZSBkZW5lbWUgbWV0bmlkaXIu=="
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
  <global_options>
     <delivery_time />
     <header>ORGANIKHBR</header>
     <message_format>normal</message_format>
     <report_url />
     <timeout>48</timeout>
     <track_id>897as6d8ygas07ad75a</track_id>
     <gsm_isUnique />
  </global_options>  
  <deliveries>
     <options>
        <delivery_time />
        <header />
        <message_format />
        <report_url />
        <gsm_isUnique />
        <timeout>24</timeout>
        <track_id />
     </options>
     <recipients>
        <groups>1</groups>
        <groups>2</groups>
        <groups>3</groups>
        <gsms>905301234567</gsms>
        <gsms>905301234568</gsms>
        <gsms>905301234569</gsms>
     </recipients>
     <message>QnUgYmlyIGRlbmVtZSBtZXNhasSxZMSxcg==</message>
  </deliveries>
  <deliveries>
     <options>
        <track_id>1223</track_id>
     </options>
     <recipients>
        <gsms>905301234569</gsms>
     </recipients>
     <message>T3JnYW5payBIYWJlcmxlxZ9tZSBkZW5lbWUgbWV0bmlkaXIu==</message>
  </deliveries>     
</data>
</document>
```



|Değişken|Gereklilik|Tip|Açıklama|
|-|-|-|-|
|global_options|Zorunlu|-|`global_options`içine tanımladığınız değerler, istek gövdesinde yer alan tüm iletilere uygulanır. İçindeki değişkenlerin bazıları zorunludur.`options`içindeki değişkenlerle belirlenmemiş ayarlar, iletilerin`global_options`nesnesinde aranır.|
|global_options.track_id|Opsiyonel|Integer|İletinizin takibi için sizin belirleyeceğiniz ve benzersiz olması gereken parametredir. Bu takip numarası ile daha sonra kendi tarafınızda sorgulama yapabilir ya da rapor taleplerinizde görevin durumunu bu takip ID'si ile bulabilirsiniz. İletilerin`options`değerinin içinde yer alan`track_id`parametresine değer atanırsa,`global_options`içindeki parametre`işleme alınmaz`ve iletilerin içindeki değer okunur.|
|global_options.header|Opsiyonel|Değişken|Oluşturduğunuz gönderim görevindeki tüm iletilere atanacak "Gönderen Başlığı" parametresidir. Başlık ID'si ya da direkt başlığın adı olmalıdır.|
|global_options.delivery_time|Opsiyonel|Datetime|Gönderiminizin ileri bir tarihte yapılmasını istiyorsanız, istediğiniz tarihi bu parametreyle gönderebilirsiniz. Gönderdiğiniz tarih`yyyy-aa-gg SS:dd`formatında olmalıdır (Örn: 2017-01-04 15:46). Eğer gönderiminizin hemen yapılmasını istiyorsanız bu parametreyi göndermenize gerek yoktur. Gönderilen saat değeri +3 İstanbul UTC değerinde olmalıdır.|
|global_options.timeout|Opsiyonel|Integer|İlgili SMS operatöre iletildikten sonra mesajın operatörden alıcıya iletilmek için en fazla ne kadar süre ile bekletileceğini belirlediğiniz değişkendir.`timeout`değerinde belirtilen süre boyunca SMS alıcıya ulaştırılamazsa ilgili SMS iptal olur ve yurtiçi SMS'lerde krediniz otomatik iade edilir. Girdiğiniz değerler saat cinsindendir ve`int`olmalıdır. Bu değişken opsiyoneldir. Varsayılan değeri`48`saattir.|
|global_options.message_format|Opsiyonel|Integer|Gönderiminizin hangi karakter setleriyle yapılacağını belirler.`0`,`1`ve`2`değerlerini alır. 0 -`normal`, 1 -`turkish`, 2 -`unicode`değeridir.`normal`olarak ayarlandığında sadece İngilizce karakterlerle gönderim yapılır.`turkish`olarak ayarlandığında Türkçe karakterle atış yapılır.`unicode`değeri ise yurtdışı gönderimlerde farklı alfabelerle atış yapmak için kullanılır.|
|global_options.report_url|Opsiyonel|String|Gönderim görevinizin durumunda bir değişiklik olduğunda gönderim yaptığınız numarayla ilgili raporun gönderileceği`URL`'dir. Görevin raporu`JSON`formatında buraya gireceğiniz adrese`POST`edilir. Gönderilen raporun detaylarını`Raporlar`bölümünden bulabilirsiniz.|
|global_options.gsm_isunique|Zorunlu|1|Gönderim yaptığınız numaraların içinde tekrarlanan numaralar varsa bu numaralara da gönderim yapılıp yapılmayacağını belirleyen parametredir. 1 - olduğunda tekrarlanan numaraların sadece 1 tanesine gönderim yapılır, 0 - olduğunda ise tekrarlanan numaraların tümüne gönderim yapılır. Alacağı değer`int`olmalıdır.|
|deliveries|Zorunlu|-|İletilerinizi tanımladığınız bölümdür.`Array`formatındadır ve dilediğiniz kadar iletiyi bu bölümde tanımlayabilirsiniz. bu bölümde oluşturduğunuz iletilerin raporlarını tek tek veya toplu olarak alabilirsiniz.|
|deliveries.options|Zorunlu|-|İçeriği yukarıda anlatılan`global_options`nesnesi ile aynıdır. Ancak geçerliliği sadece ait olduğu iletiyi kapsar.`global_options`içine tanımlanmayan özellikler bu bölümde aranır ve bulunursa işlenir. Aynı anda hem`global_options`hem de`options`içine atama yapılırsa, API`options`değerlerini baz alır ve işler.|
|deliveries.recipients|Zorunlu|-|Gönderim yapmak istediğiniz numara ve/veya grupları belirlediğiniz bölümdür.|
|deliveries.recipients.groups|Değişken|Array|Kayıtlı gruplarınıza gönderim yapmak istiyorsanız, bir veya birden fazla grup ID değerini bu değişkene yazarak gönderim yapabilirsiniz (Örn: 1,2,3,4,...). Birden fazla grup ID'si yazdığınız durumlarda, ID değerlerinden geçersiz olanlar varsa gönderiminiz sadece geçerli ID'lere yapılır.`recipients.gsms`değişkenine geçerli bir değer verildiğinde bu değişken opsiyonel hale gelir, gönderilmesi zorunlu değildir. Bunun dışındaki tüm koşullarda gönderilmesi zorunludur.|
|deliveries.recipients.gsms|Değişken|Array|Mesajınızın atılacağı numaraları belirlediğiniz değişkendir.`,`ile ayırarak birden fazla numara yazabilirsiniz (Örn: 905301234567,901234566,901234555,...). Bu değişkende belirttiğiniz virgül ile ayrılmış numaraların sınırlaması yoktur, n tane olabilir.`recipients.groups`değişkenine geçerli bir değer verildiğinde bu değişken opsiyonel hale gelir, gönderilmesi zorunlu değildir. Bunun dışındaki tüm koşullarda gönderilmesi zorunludur.|
|deliveries.message|Zorunlu|String|Gönderiminizin metnidir.`base64`formatında gönderilmelidir.`base64`formatına çevrilmemiş halinin uzunluğu en fazla gönderilecek mesaj metinin tipine (`message_format`değerine) göre değişiklik göstermektedir. Mesaj karakterlerinin tamamının doğru iletilebilmesi için mesaj metnini base64 formatına dönüştürerek yollamak zorunludur.|


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
               "track_id": "",
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
            },
            {
               "track_id": 2525,
               "transaction_id": null,
               "error": {
                  "number": 101,
                  "message": "The SMS title is incorrect."
               },
               "valid": [],
               "invalid": []
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
               <item>
                  <track_id>2525</track_id>
                  <error>
                     <number>101</number>
                     <message>The SMS title is incorrect.</message>
                  </error>
                  <valid />
                  <invalid />
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
         <item>
            <track_id>2526</track_id>
            <transaction_id />
            <error>
               <number>101</number>
               <message>The SMS title is incorrect.</message>
            </error>
            <valid />
            <invalid />
         </item>         
      </deliveries>
   </data>
</response>
```



|Node|Tip|Açıklama|
|-|-|-|
|result|Boolean / Int|Yanıt işleminin durumunu belirtir.`true`/`false`değerlerini alır.`XML`yanıt gövdelerinde bu değer`Int`olur ve 0 / 1 değerlerini alır.|
|data.valid|Array|Gönderim görevinizdeki işleme alınan bütün GSM numaralarının detayları burada gönderilir.|
|data.valid.gsm|Integer|Gönderim yapılan GSM numarasıdır.|
|data.valid.transaction_id|Integer|Gönderim işleminin sistem tarafından otomatik oluşturulan benzersiz ID'sidir. Gönderim görevindeki her ileti (deliveries) için ayrı bir ID üretilir.|
|data.valid.gsm_track_id|String|Gönderim yapılan her numara için benzersiz olarak üretilen ID'dir. Bu veriyi raporlamalarınızda kullanabilirsiniz.|
|data.valid.sms_count|Integer|Gönderilen SMS'in kaç boy olduğu bilgisini verir.|
|data.valid.sms_count|Integer|Gönderilen SMS'in TL tutarı bilgisini verir. Yurtdışı numaralar TL bakiye ile gönderilir.|
|data.invalid|Array|Gönderim görevinizdeki işleme alınamayan bütün GSM numaralarının detayları burada gönderilir. İçeriği`valid`parametreleri ile aynıdır.|
