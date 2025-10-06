# kart-bakiye-aktarim-case
Kart Bakiye Aktarım Süreci için hazırladığım iş analizi, diagramı ve test senaryoları

**Kullanılmayan akıllı kartlarda ki bakiyerin farklı kartlara aktarımı**

**AMAÇ / FAYDA:**

Bu uygulama ile kullanılmayan akıllı kartlardaki bakiyelerin yeni kartlara aktarılması hedeflenmektedir.
Böylelikle müşteri memnuniyeti artar ve kullanılmayan kartlardaki bakiye kaybı önlenir. 

**KULLANILAN EKRANLAR VE VERİ AKIŞI:**

**Ekranlar:**

- Kart okuma ekranı
- Bakiye görüntüleme ekranı
- Yeni kartı okuma ekranı
- Kullanıcı onay ekranı
- İşlem sonuç / mesaj ekranı

**Veri Akışı:**

- Kullanıcı kartı okutur.
- Sistem kartın ID bilgisini alır.
- Kartın geçerli olup olmadığı kontrol edilir.
- Geçersiz kartlar için işlem sonlandırılır.
- Geçerli kartlar için bakiye okunur.
- Bakiye kullanıcıya gösterilir.
- Kullanıcı bakiye aktarımını onaylar. 
- Kartın kara listede olup olmadığı kontrol edilir.
- Kara listede ise işlem sonlandırılır.
- Kara listede değilse yeni kart okutulur.
- Yeni kartın geçerli olup olmadığı kontrol edilir.
- Geçersiz kartlar için işlem sonlandırılır.
- Geçerli yeni kartın kara listede olup olmadığı kontrol edilir.
- Kara listede ise işlem sonlandırılır.
- Kara listede değilse kullanıcıdan bakiye aktarım onayı alınır.
- Onay verilmezse işlem sonlandırılır.
- Onay verilirse yeni karta bakiye aktarımı yapılır.
- Kullanıcıya işlem başarı mesajı verilir.
- Eski kart iptal edilir.

**AKILLI KART VERİLERİNİN (BAKİYE) İŞLENMESİ**

- Eski kart okutulur.
- Kartın çipinde saklı olan bakiye bilgisi okunur.
- Sistem kartın kara listede bulunup bulunmadığını kontrol eder.
- Geçerli kartlar için bakiye bilgisi sistemin geçici belleğine kaydedilir.
- Kullanıcı yeni kartı okutur ve geçici bellekte tutulan bakiye yeni kartın çipine yazılır.
- Eski kart iptal edilir.
- İşlem detayları sistem loglarına kaydedilir. 

**TEST SENARYOLARI:**


1) Kategori: Pozitif

Test Senaryosu: Eski geçerli karttan yeni geçerli karta bakiye aktarımı

Girdi: 
- Eski kart: Geçerli
- Bakiye: 100 TL
- Yeni kart: Geçerli

Beklenen Çıktı: Yeni karta 50 TL aktarılır, eski kart iptal edilir.

**2) Kategori: Negatif**

**Test Senaryosu:** Eski kara listedeki karttan yeni geçerli karta bakiye aktarımı

**Girdi:** 
- Eski kart: Kara listede
- Bakiye: 100 TL
- Yeni kart: Geçerli

**Beklenen Çıktı:** Kullanıcıya “Kart geçersizdir” bilgisi verilir. İşlem yapılmaz.

**3) Kategori: Negatif**

**Test Senaryosu:** Eski geçerli karttan yeni kara listedeki karta bakiye aktarımı

**Girdi:**
- Eski kart: Geçerli
- Bakiye: 100 TL
- Yeni kart: Kara listede

**Beklenen Çıktı:** Kullanıcıya “Kart geçersizdir” bilgisi verilir. İşlem yapılmaz.

**4) Kategori: Negatif**

**Test Senaryosu:** Eski geçerli karttan yeni geçersiz karta bakiye aktarımı

**Girdi:**
- Eski kart: Geçerli
- Bakiye: 100 TL
- Yeni kart: Geçersiz

**Beklenen Çıktı:** Kullanıcıya “Kart geçersizdir” bilgisi verilir. İşlem yapılmaz.

