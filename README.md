# API Test Otomasyonu

Bu proje, farklı API uç noktalarının test edilmesini sağlamak amacıyla oluşturulmuş Postman koleksiyonlarını içermektedir. Temel olarak, kullanıcı yönetimi ve e-ticaret işlevleriyle ilgili çeşitli API çağrılarının doğrulamasını gerçekleştirmek için tasarlanmıştır. Testler, GitHub Actions ile entegre edilerek uzaktan ve otomatik olarak çalıştırılmaktadır. Bu sayede manuel test süreci ortadan kaldırılarak daha verimli ve güvenilir bir test süreci oluşturulmuştur.

## Test Edilen API'ler ve Amaçları

### 1. **Api Collection**
Bu koleksiyon, `https://limitless-lake-55070.herokuapp.com` adresinde çalışan bir API'yi test etmek için hazırlanmıştır. İçerisinde beş farklı test isteği bulunmaktadır:

- **/user/signup (POST):** Yeni bir kullanıcı kaydetme işlemini test eder.
- **/user/signin (POST):** Sisteme giriş yapma işlemini test eder.
- **/user/all (GET):** Sistemde kayıtlı tüm kullanıcıları listeleme işlemini test eder.
- **/cart/update (PUT):** Sepetteki bir ürünün güncellenmesini test eder.
- **/cart/delete (DELETE):** Sepetten bir ürünün silinmesini test eder.

Tüm isteklerde, kimlik doğrulama amacıyla Bearer Token kullanılmaktadır. Bu token, hem yetkilendirme başlığında hem de URL içinde sorgu parametresi olarak iletilmektedir.

### 2. **Restful API Testleri**
Bu koleksiyon, `https://restful-booker.herokuapp.com/booking` adresindeki API'yi test etmek için oluşturulmuştur. Temel amacı, yeni bir rezervasyonun başarılı şekilde oluşturulup oluşturulmadığını kontrol etmektir.

Testler şunları kapsar:

- **Yeni bir rezervasyon isteği oluşturma:**
  - JSON formatında isim, soyisim, ödeme durumu, fiyat ve rezervasyon tarihleri gibi verilerle POST isteği gönderilir.
  - Sunucunun dönen yanıtında, oluşturulan rezervasyonun doğru bilgilerle kaydedildiği kontrol edilir.
  
- **Yanıt doğrulama:**
  - HTTP yanıt kodunun 200 OK olup olmadığı kontrol edilir.
  - JSON yanıtındaki `firstname` ve `lastname` değerlerinin gönderilen verilerle eşleşip eşleşmediği doğrulanır.
  - Yanıt içeriğinin doğru veri türlerine sahip olup olmadığı incelenir.

## GitHub Actions ile Otomasyon

Bu proje, GitHub Actions kullanılarak uzaktan ve otomatik testler çalıştıracak şekilde yapılandırılmıştır. Pipeline, Postman CLI komutlarını kullanarak belirlenen API uç noktalarına istek gönderir ve sonuçları değerlendirir. Başarısız olan testler detaylı hata mesajları ile raporlanarak geliştirme sürecinde hızlı aksiyon alınmasını sağlar.

Bu sayede, herhangi bir değişiklik yapıldığında testler otomatik olarak çalıştırılır ve API'nin doğru şekilde çalıştığı sürekli olarak kontrol edilir.
