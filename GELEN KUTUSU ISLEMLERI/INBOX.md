
# Gelen Mesajları Listeleme

```
request_name = inbox
```

Bu API, tanımlı anahtar kelimeleriniz ile gelen mesajları listelemenizi sağlar.

### `POST` ile Gelen Mesajları Listeleme

`POST` URL Şablonu:
> /v2/`api_key`/**inbox**/

Örnek `POST` URL'si:
> https://organikapi.com/v2/ce136df4c9c92d1428e828aba07d3b05/inbox/

# Örnek İstek Gövdeleri:
## JSON
Request Headers:
```
Method: POST
Host:   organikapi.com
URL:    /v2/ce136df4c9c92d1428e828aba07d3b05/inbox/json/
Accept: application/json
```
Form Data:
```
{
    "data": {
      "rootKeyword": "ANAHTARKELIME",
      "date": {
          "begin": "2020-01-30",
          "end": "2020-03-01"
      }
    }
}
```



|Değişken|Gereklilik|Tip|Açıklama|
|-|-|-|-|
|rootKeyword|Opsiyonel|String|Mesajları anahtar kelime içeriğine göre listelemek için kullanılır.|
|date.begin|Opsiyonel|Datetime|Listelenecek mesajların tarih başlangıcını seçmek için kullanılır. `date_end` ile aynı anda kullanılabilir, fakat maksimum zaman aralığı 30 gün olmalıdır.Tarih bilgisi, `YYYY-MM-DD` formatında gönderilmelidir.|
|date.end|Opsiyonel|Datetime|Listelenecek mesajların tarih aralığını seçmek için kullanılır. `date_begin` ile aynı anda kullanılabilir, fakat maksimum zaman aralığı 30 gün olmalıdır.Tarih bilgisi, `YYYY-MM-DD` formatında gönderilmelidir.|


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
          "0": {
              "id": 123456,
              "recipient": 1010,
              "message": "",
              "sender": 905000000000,
              "received": "2020-01-01 10:10:10",
              "rootKeyword": "ANAHTARKELIME",
              "receiveKeyword": "RED"
          }
        }
    }
}
```



|Node|Tip|Açıklama|
|-|-|-|
|result|Boolean|Yanıt işleminin durumunu belirtir.`true`/`false`değerlerini alır.|
|id|Integer|Gelen mesajın benzersiz sıra numarasıdır.|
|recipient|Integer|Mesajın gönderildiği numaradır.|
|message|String|Gelen mesaj içeriği|
|sender|Integer|Mesajın gönderildiği numara|
|received|Datetime|Mesajın alınma tarihi|
|rootKeyword|String|Mesaj içeriğindeki temel anahtar kelime|
|receiveKeyword|String|Mesaj içeriğindeki alt anahtar kelime. Boş ise`NULL`değerini alır.|
