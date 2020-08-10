# API URL

[![N|Solid](https://www.organikhaberlesme.com.tr/assets/images/organik-logo.png)](https://nodesource.com/products/nsolid)

API'ye gönderdiğiniz isteklerin ve aldığınız yanıtların tümü tek bir URL üzerinden çalışır. API farklı komutlar için farklı metodlarla çalışır. Genel olarak bu metodlar `GET` ve `POST`'tur. Hangi fonksiyonun, hangi metodla çalıştığı ilgili sayfalarda belirtilmiştir.

  - `API URL`: **https://organikapi.com/**

# İstek & Yanıt İçerik Tipleri

Organik API hem istek hem de yanıt gövdelerinde `JSON`, `XML` ve `SOAP` (yakında) formatlarını desteklemektedir. Ayrıca API isteklerinin ve yanıtlarının formatlarını her sorgu için ayrı ayrı belirleyebilirsiniz. Örneğin isteğinizi `JSON` olarak gönderip API yanıtını `XML` olarak isteyebilirsiniz.

### Desteklenen istek içerik tipleri: (Content-Type)
Content-Type: `application/json`, `application/xml`. Bu içerik tipleri sadece POST ile yapılan isteklerde beklenir. `GET` ile yaptığınız isteklerde içerik tipi aranmaz.

### Desteklenen yanıt içerik tipleri: (Content-Type)
Content-Type: application/json, application/xml.

Not: `GET` ile yapılan isteklerde yanıt varsayılan olarak `JSON` döner.

# API Kullanıcıları

Organik API istek almak ve yanıt vermek için panel üzerinden açtığınız ve kullanıcı adı-şifreden oluşan API kullanıcılarına ihtiyaç duyar. **Panelde Üyelik Ayarları > API Kullanıcıları** sekmesinden dilediğiniz kadar API kullanıcısı oluşturabilirsiniz. Bu kullanıcılar API'ye istek göndermek için bir API anahtarına ihtiyaç duyar. Bu konuyla ilgili bilgiler **API Kullanıcıları** sayfasında verilmiştir.

# API Erişimleri & IP/Alan Adı Kısıtlama

Verilerinizin güvenliğini sağlamak için API erişimini IP veya alan adı bazlı kısıtlayabilirsiniz. Panelde **Üyelik Ayarları** bölümünde **İzinli IP**'ler sekmesinde izin verilen IP'leri veya alan adlarını ayarlayarak API'ye ve verilerinize kimin erişebileceğini belirleyebilirsiniz.

Bir kere IP veya alan adı tanımlaması yapıldığı zaman, tanımlanan IP/alan adı dışında API'ye gelen tüm istekler reddedilir ve yanıt alamaz. Bu yüzden API yanıtlarında sıkıntı yaşarsanız panelden izinli IP ve alan adı ayarlarını kontrol etmenizi öneririz.

# API Kullanıcıları

Organik API aldığı isteklere yanıt vermek için API kullanıcılarına ihtiyaç duyar. bu kullanıcıları panelde **Üyelik Ayarları > API Kullanıcıları** kısmından oluşturabilirsiniz. API kullanıcıları için bir kullanıcı adı ve şifre belirtmeniz yeterlidir.

# Yetkilendirmeler
Oluşturduğunuz API kullanıcılarının hangi API özelliğini kullanabileceğini belirterek spesifik olarak yetkilendirebilirsiniz. Yetkilendirmeye bağlı olarak çalışan API fonksiyonları şu şekildedir:
- Bakiye sorgulama = `balance`,
- Başlıkları getirme = `headers`,
- (GET) Basit SMS gönderme = `smsviaget`,
- (POST) Basit SMS gönderme = `sendsms`,
- Gelişmiş SMS gönderme = `sendsms`,
- Detaylı rapor alma = `detailedreport`,
- Basit rapor alma = `basicreport`,
- Grupları getirme = `groups`,
- Grup kişilerini getirme = `groupcontent`,
- İleri tarihli gönderimleri iptal etme = `cancelscheduledtasks`,
- Kara listeyi okuma = `blacklist`,
- Kara listeye ekleme = `blacklistadd`,
- Kara listeden çıkarma = `blacklistremove`

Yukarıda belirtilen özelliklerden bir veya birden fazlasını oluşturduğunuz kullanıcılara atayarak kullanıcı bazlı yetkilendirme yapabilirsiniz.
# API Anahtarı

Organik API aldığı gönderdiğiniz istekleri kabul edip işlemek için API anahtarına ihtiyaç duyar. Bu anahtarı `POST` ya da `GET` yaptığınız tüm isteklerde URL kısmında göndermeniz gerekir. API anahtarını oluşturabilmek için API kullanıcısına ihtiyacınız vardır. Oluşturulan her anahtar tek bir API kullanıcısına bağlıdır. Birden fazla API kullanıcınız var ve bunların tümüyle işlem yapıyorsanız, tüm API kullanıcıları için ayrı ayrı anahtar oluşturmanız gerekir.
# API Anahtarı Oluşturma

API anahtarları bağlı oldukları API kullanıcılarının oturum açma bilgileri ile üretilir. Anahtar oluşturmak için API kullanıcınızın kullanıcı adı ve şifresini MD5 ile şifreleyerek oluşturursunuz. API anahtarı oluşturma örnekleri aşağıdadır:

API Kullanıcısı Bilgileri:
Kullanıcı Adı: `OrganikHaberlesme`
Şifre: `mn_0g4R!`
```bash
API Anahtarı = MD5(Kullanıcı Adı + Şifre)
API Anahtarı = MD5(OrganikHaberlesmemn_0g4R!)
API Anahtarı = ce136df4c9c92d1428e828aba07d3b05
```
Not: Kullanıcı adı ve şifre arasında boşluk olmamalı, birleşik şekilde encrypt edilmelidir.

# İstek Yapısı
**POST/GET HOST**
  - `API URL`: **https://organikapi.com/**
  
**POST/GET HOST**

 - **/v**`api_version`/`api_key`/`request_name`/`request_response_type`/`response_type`/
 
**Örnek POST/GET URL'si**

 - **https://organikapi.com/v**`2`/`ce136df4c9c92d1428e828aba07d3b05`/`balance`/
 - **https://organikapi.com/v**`2`/`ce136df4c9c92d1428e828aba07d3b05`/`sendsms`/`json`/`xml`/
 
API'ye gönderdiğiniz istek yapısı yukarıdaki gibi olmalıdır. İstek yolundaki değişkenlerin değerleri aşağıdaki tabloda verilmiştir.

| **Değişken** | **Gereklilik** | **Varsayılan Değer** | **Açıklama** |
| ------ | ------ | ------ | ------ | 
| api_version | Zorunlu | N/A | Kullandığınız API'nin versiyonunu belirtir. Bu dokümantasyonun hazırlandığı son sürüm v2.0'dır. Bu yüzden bu değer **2** olmalıdır. |
| api_key | Zorunlu | N/A | API'nin size yanıt verebilmesi için gerekli API anahtarı değeridir. "**API Anahtarı Oluşturma**" başlığında nasıl belirleneceği anlatılmıştır. |
| request_name | Zorunlu | N/A | API'ye hangi görevi yapmasını istediğiniz belirttiğiniz değişkendir. Bu değişkenin değerine göre API farklı görevleri yapar ve yanıt verir. API'nin görevleri bu değişkenin alabileceği değerler bir sonraki tabloda anlatılmıştır. |
| request_response_type | Opsiyonel | N/A | API'ye `POST` ettiğiniz istek gövdesinin formatını belirttiğiniz değişkendir. `POST` ettiğiniz verinin formatına göre değer almalıdır. Gönderdiğiniz istek gövdesi `XML` ise, `XML`, `JSON` ise, `JSON` olmalıdır. Bu değişken opsiyonel olup, hiçbir şey yazılmaması durumunda varsayılan olarak JSON formatında veri bekler. Bu değişkenin çalışma prensibi ve koşulları aşağıda anlatılmıştır. |
| response_type | Opsiyonel | N/A | Organik API farklı format tipleriyle istek alıp yanıt verebilir. API'nin döndürdüğü yanıtın hangi formatta olmasını istediğinizi bu değişkenle belirtirsiniz. Yanıtı `XML` olarak almak istiyorsanız, bu değişkene XML değeri vermelisiniz. Eğer bu değişkeni kullanmazsanız hem beklenen istek tipi hem de verilecek tipi `request_response_type` değerine verdiğiniz formatta olur. |

`POST`/`GET` **Alabileceği Yanıt, İstek ve Fonskiyon Değerleri**

Bu bölümde URL'de yer alan `request_name`, `request_response_type` ve `response_type` değişkenlerinin alabileceği değerler ve anlamları anlatılmıştır. API fonksiyonlarının detaylı anlatımları, ilgili başlıklar altında verilmiştir.

| | | |
|-|-|-|
|Metod|Alabileceği Değer|Açıklama|
|GET|balance|Kredi sorgulama metodudur. API'ye bu değer gönderildiğinde size sonuç olarak hesabınızdaki TL ve SMS kredi bakiyenizi döndürür.|
|GET|headers|Kayıtlı gönderen kimliklerinizi (başlıklarınızı) sorgulama metodudur. Yanıt olarak başlık ID ve başlık isimlerini döndürür.|
|GET|smsviaget|GET ile tekli SMS gönderme metodudur. Detaylı anlatımı SMS Gönderme başlığında verilmiştir.|
|POST|sendsms|Toplu ve hitaplı SMS gönderme metodudur. Detaylı anlatımı SMS Gönderme başlığında verilmiştir.|
|POST|detailedreport|Detaylı rapor alma metodudur. Detaylı anlatımı Detaylı Rapor Alma başlığında verilmiştir.|
|POST|basicreport|Basit rapor alma metodudur. Detaylı anlatımı Basit Rapor Alma başlığında verilmiştir.|
|GET|groups|Kayıtlı grupları sorgulama metodudur. Grup ID'leri, isimleri ve gruplardaki kayıtlı kişi sayılarını döndürür.|
|POST|groupcontent|Belirli grup veya grupların kişi bilgilerini sorgulama metodudur. Kişilerin ID, ad, soyad, doğum tarihi gibi bilgilerini döndürür.|
|POST|cancelscheduledtasks|İleri tarihli gönderimleri iptal etme metodudur.|
|GET|blacklist|Kara listenizdeki numaraları listeleme metodudur. GSM numaralarını ve kara listeye eklenme tarihlerini döndürür.|
|POST|blacklistadd|Kara listeye numara ekleme metodudur.|
|POST|blacklistremove|Kara listeden numara çıkarma metodudur.|
