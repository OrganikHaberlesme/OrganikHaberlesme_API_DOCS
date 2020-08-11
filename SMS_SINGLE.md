# GET ile SMS Gönderme

```
request_name = smsviaget
```

> /v2/`api_key`/**smsviaget**/`request_response_type`/?**header=ID** ya da `Başlık Adı`&**gsms**=`GSM1, GSM2, GSM3,`...&**groupids**=`Grup ID'leri`&**timeout**=`Zaman Aşımı Değeri`&**message**=`Mesaj Metni (Base64)`&**deliverytime**=`Gönderilme Tarihi`&**gsm_isunique**=`Tekrarlanan numaralara gönderim`&**track_id**=`Gönderimin benzersiz izleme ID`'si&**report_url**=`Gönderim raporunun post edileceği adres`

Örnek `GET` URL'si:
> **https://organikapi.com/v2/ce136df4c9c92d1428e828aba07d3b05/smsviaget/?header=ORGANIKHBR&gsms=905001234567,905001234568,905001234569&message=QnUgYmlyIGRlbmVtZSBtZXNhasSxZMSxcg==**
