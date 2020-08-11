# Hata Kodları

|Kod|Mesaj|Açıklama|
|-|-|-|
|1|An unknown error has occurred.|Bilinmeyen bir hata oluştuğunda bu hata alınır.|
|99|Authorization error.|Geçersiz API anahtarı gönderildiğinde alınır.|
|98|Unauthorize IP address.|Panelden IP kısıtlaması yapılıp, izin verilen IP'lerden başka bir IP ile giriş yapıldığında bu hata alınır.|
|97|Invalid request body format.|API'ye gönderdiğiniz istek gövdesi istenilen biçimden farklı olduğunda bu hata alınır.|
|96|Invalid request parameters.|API'ye gönderdiğiniz istek gövdesi değişkenlerinde bir veya daha fazlasında geçersiz değer olduğunda bu hata alınır.|
|95|Server fault.|Sunucu hatası oluştuğunda bu hata alınır.|
|94|Server temporary unavailable.|İstek yaptığınız sırada sunucudan yanıt gelmezse bu hata alınır.|
|93|Too much request.|API'ye aynı anda izin verilenden çok talep olduğunda bu hata alınır.|
|92|Unsupported request type.|Gönderdiğiniz`request_response_type`değişkeninde geçersiz değer olduğunda bu hata alınır.|
|91|Unsupported response type.|Gönderdiğiniz`response_type`değişkeninde geçersiz değer olduğunda bu hata alınır.|
|90|API KEY must be 32 characters.|API anahtarınız yanlış formatta gönderildiğinde bu hata alınır.|
|89|User not found.|Gönderilen API anahtarına bağlı bir kullanıcı bulunamaz ya da bulunan kullanıcı aktive edilmemişse bu hata alınır.|
|88|Unsupported`request_name`|İstek prosedürü değişkenine geçersiz bir değer verildiğinde bu hata alınır.|
|87|No records were found.`request_name`|Herhangi bir veri bulunamadığında bu hata alınır.|
|86|No valid registration data was found.`request_name`|Arama yapılan kriterlere uygun kayıt bulunamadığında bu hata alınır.|
|85|The database could not be registered.`request_name`|Kayıt işlemi başarısız olduğunda bu hata alınır.|
|84|Database operation failed.request_name|Veritabanına erişim hatası oluştuğunda bu hata alınır.|
|112|Message text is not in BASE64 format.|Gönderilen mesaj metni base64 formatında değilse bu hata alınır.|
|111|The GSM number is too short or too long.|Gönderilen GSM numarası olması gerekenden uzun ya da kısa olduğunda bu hata alınır.|
|110|The number is incorrect.|Gönderim yapılan GSM numarası yanlış ise bu hata alınır.|
|109|The GSM number is on the black list.|Gönderim yapılan GSM numarası kara listede ise bu hata alınır.|
|108|Insufficient TL balance|Gönderim için gerekli tutarı kadar TL bakiyesi yoksa bu hata alınır.|
|107|This SMS title is disabled.|Gönderim yapılmak istenen başlık kullanıma kapalı ise bu hata alınır.|
|106|Message text is too long.|SMS mesaj metni olması gerekenden uzun ise bu hata alınır.|
|105|Message text was not found.|Gönderim isteğinde mesaj metni bulunmazsa bu hata alınır.|
|104|There is no customer contract for sending SMS.|SMS gönderimi için gerekli sözleşme yoksa bu hata alınır.|
|103|Insufficient balance|Gönderim için gerekli kontör yoksa bu hata alınır.|
|102|Couldn't found any valid GSM number|Gönderimde GSM numarası veya grup ID'si belirtilmediği veya belirtilen GSM numaralarının geçersiz olduğu durumlarda bu hata alınır.|
|101|The SMS title is incorrect.|Gödnerimde belirttiğiniz başlık sistemde bulunamazsa bu hata alınır.|


