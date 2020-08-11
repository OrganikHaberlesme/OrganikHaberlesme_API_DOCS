# GET ile SMS Gönderme

```
request_name = smsviaget
```

> /v2/`api_key`/**smsviaget**/`request_response_type`/?**header=ID** ya da `Başlık Adı`&**gsms**=`GSM1, GSM2, GSM3,`...&**groupids**=`Grup ID'leri`&**timeout**=`Zaman Aşımı Değeri`&**message**=`Mesaj Metni (Base64)`&**deliverytime**=`Gönderilme Tarihi`&**gsm_isunique**=`Tekrarlanan numaralara gönderim`&**track_id**=`Gönderimin benzersiz izleme ID`'si&**report_url**=`Gönderim raporunun post edileceği adres`

Örnek `GET` URL'si:
> **https://organikapi.com/v2/ce136df4c9c92d1428e828aba07d3b05/smsviaget/?header=ORGANIKHBR&gsms=905001234567,905001234568,905001234569&message=QnUgYmlyIGRlbmVtZSBtZXNhasSxZMSxcg==**




|Değişken|Gereklilik|Varsayılan Değer|Açıklama|
|-|-|-|-|
|header|Zorunlu|N/A|Gönderdiğiniz SMS'in kim tarafından atıldığı bilgisidir. Kayıtlı başlıklarınızdan birinin ID'si veya direkt adını alabilir. Başlık adı yazılırken kayıtlı başlık adıyla aynı şekilde ve büyük-küçük harf djuyarlılığıyla yazıldığından emin olunuz. Başlık adlarının tutmaması durumunda gönderiminiz gerçekleşmeyecektir.|
|gsms|Değişken|N/A|Mesajınızın atılacağı numaraları belirlediğiniz değişkendir.`,`ile ayırarak birden fazla numara yazabilirsiniz (Örn: 905301234567,901234566,901234555,...). Bu değişkende belirttiğiniz virgül ile ayrılmış numaraların sınırlaması yoktur, n tane olabilir.`groupids` değişkenine geçerli bir değer verildiğinde bu değişken opsiyonel hale gelir, gönderilmesi zorunlu değildir. Bunun dışındaki tüm koşullarda gönderilmesi zorunludur.|
|groupids|Değişken|N/A|Kayıtlı gruplarınıza gönderim yapmak istiyorsanız, bir veya birden fazla grup ID değerini bu değişkene yazarak gönderim yapabilirsiniz (Örn: 1,2,3,4,...). Birden fazla grup ID'si yazdığınız durumlarda, ID değerlerinden geçersiz olanlar varsa gönderiminiz sadece geçerli ID'lere yapılır.`gsms`değişkenine geçerli bir değer verildiğinde bu değişken opsiyonel hale gelir, gönderilmesi zorunlu değildir. Bunun dışındaki tüm koşullarda gönderilmesi zorunludur.|
|timeout|Opsiyonel|48|İlgili SMS operatöre iletildikten sonra mesajın operatörden alıcıya iletilmek için en fazla ne kadar süre ile bekletileceğini belirlediğiniz değişkendir.`timeout` değerinde belirtilen süre boyunca SMS alıcıya ulaştırılamazsa ilgili SMS iptal olur ve yurtiçi SMS'lerde krediniz otomatik iade edilir. Girdiğiniz değerler saat cinsindendir ve `int` olmalıdır. Bu değişken opsiyoneldir ve gönderilmek zorunda değildir.|
|message|Zorunlu|N/A|Gönderiminizin metnidir.`base64` formatında gönderilmelidir.`base64` formatına çevrilmemiş halinin uzunluğu en fazla gönderilecek mesaj metinin tipine (`message_format` değerine) göre değişiklik göstermektedir. Mesaj karakterlerinin tamamının doğru iletilebilmesi için mesaj metnini base64 formatına dönüştürerek yollamak zorunludur.|
|deliverytime|Opsiyonel|N/A|Gönderiminizin ileri bir tarihte yapılmasını istiyorsanız, istediğiniz tarihi bu parametreyle gönderebilirsiniz. Gönderdiğiniz tarih `yyyy-aa-gg SS:dd` formatında olmalıdır (Örn: 2017-01-04 15:46). Eğer gönderiminizin hemen yapılmasını istiyorsanız bu parametreyi göndermenize gerek yoktur.|
|gsm_isunique|Zorunlu|1|Gönderim yaptığınız numaraların içinde tekrarlanan numaralar varsa bu numaralara da gönderim yapılıp yapılmayacağını belirleyen parametredir. 1 - olduğunda tekrarlanan numaraların sadece 1 tanesine gönderim yapılır, 0 - olduğunda ise tekrarlanan numaraların tümüne gönderim yapılır. Alacağı değer `int` olmalıdır.|
|track_id|Opsiyonel|N/A|Gönderiminizi kendi sisteminizde takip edebilmek için üreteceğiniz benzersiz `integer` değerdir.|
|report_url|Opsiyonel|N/A|Gönderiminiz tamamlandıktan sonra gönderim raporunun `POST` edileceği adrestir.`POST` edilen rapor formatı `JSON`'dır. Girdiğiniz değer `http://< domain >.com/`şeklinde olmalıdır.|
