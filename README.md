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
