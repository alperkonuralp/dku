# 23. Öğrenme Yol Haritası

Bu bölüm, kuantum bilgisayarları öğrenmek isteyen farklı profiller için ayrı öğrenme rotaları sunar. Çünkü kuantum bilgisayar konusu tek bir öğrenme çizgisine indirgenemez. Teknik olmayan bir kişinin ihtiyaç duyduğu kavramsal çerçeve ile yazılımcının, yazılım mimarının, siber güvenlik uzmanının veya yöneticinin ihtiyaç duyduğu bilgi seviyesi aynı değildir.

Bu nedenle bu bölümün amacı, “kuantum bilgisayarları öğrenmek için ne okumalıyım?” sorusuna tek bir cevap vermek değil; role, hedefe ve ihtiyaç duyulan derinliğe göre uygulanabilir öğrenme yolları oluşturmaktır.

Kuantum bilgisayar öğrenirken üç risk vardır:

1. **Aşırı popüler anlatımda kalmak:** “Aynı anda hem 0 hem 1”, “tüm olasılıkları aynı anda dener”, “her şeyi hızlandırır” gibi eksik anlatımlar konuyu cazip gösterir ama yanlış sezgi oluşturur.
2. **Aşırı matematiğe erken dalmak:** Lineer cebir, Hilbert uzayı, üniter dönüşüm ve tensör çarpımı gibi konular önemlidir; fakat en başta bunlara boğulmak öğrenmeyi zorlaştırabilir.
3. **Hype ile gerçekliği ayıramamak:** Kuantum bilgisayarlar önemlidir; ancak bugünkü cihazların sınırları, gürültü problemi, hata düzeltme ihtiyacı ve pratik olgunluk seviyesi bilinmeden sağlıklı strateji kurulamaz.

İyi bir öğrenme yolu bu üç riski dengeler: önce doğru sezgi, sonra temel matematik, ardından algoritmalar, donanım, hata düzeltme, programlama ve kullanım alanları.

---

## 23.1. Teknik olmayan kişiler için öğrenme yolu

Teknik olmayan kişiler için hedef, kuantum bilgisayarın matematiksel ayrıntılarına hâkim olmak değil; konunun ne olduğunu, ne olmadığını, neden önemli olduğunu ve hangi alanları etkileyebileceğini doğru anlayabilmektir.

Bu gruba şunlar dâhil olabilir:

- İş birimi temsilcileri
- Ürün yöneticileri
- Proje yöneticileri
- Teknoloji meraklıları
- Hukuk, uyum, risk ve denetim ekipleri
- Üniversite öğrencileri veya konuya yeni başlayanlar
- Teknik altyapısı sınırlı ama stratejik farkındalık kazanmak isteyen profesyoneller

Bu profil için öğrenme hedefleri şunlardır:

- Kuantum bilgisayarın klasik bilgisayardan farkını anlamak
- Qubit, süperpozisyon, dolaşıklık ve ölçüm kavramlarını temel düzeyde açıklayabilmek
- “Kuantum bilgisayar her şeyi hızlandırır” yanılgısından kaçınmak
- Kriptografi, kimya, malzeme bilimi ve optimizasyon gibi kullanım alanlarını ayırt edebilmek
- Bugünkü kuantum bilgisayarların sınırlarını bilmek
- Kurumsal karar vericilerle aynı dili konuşabilecek temel kavramlara sahip olmak

### Önerilen öğrenme sırası

Teknik olmayan bir kişi için ilk hedef kuantum mekaniğini matematiksel olarak öğrenmek olmamalıdır. Önce şu sorulara cevap aranmalıdır:

```text
Kuantum bilgisayar nedir?
Klasik bilgisayardan neden farklıdır?
Qubit neden bit değildir?
Süperpozisyon gerçekten ne anlama gelir?
Dolaşıklık neden önemlidir?
Kuantum bilgisayarlar bugün ne yapabilir, ne yapamaz?
```

Bu rota için önerilen sıra:

1. Kuantum bilgisayarın büyük resmini öğren
2. Bit ve qubit farkını kavra
3. Süperpozisyon ve ölçüm kavramlarını sezgisel düzeyde öğren
4. Dolaşıklığı “gizemli bağlantı” olarak değil, kuantum korelasyon olarak anla
5. Kuantum bilgisayarların bugün neden hata eğilimli olduğunu öğren
6. Kullanım alanlarını kısa/orta/uzun vade ayrımıyla değerlendir
7. Kriptografi etkisini ve post-quantum cryptography ihtiyacını temel düzeyde öğren
8. Hype ile gerçek ilerlemeyi ayırt etmeyi öğren

### Teknik olmayanlar için minimum kavram seti

Bu profildeki bir kişinin aşağıdaki kavramları kısa ve doğru biçimde açıklayabilmesi yeterli başlangıç seviyesidir:

| Kavram | Bilinmesi gereken seviye |
|---|---|
| Bit | Klasik 0/1 bilgi birimi |
| Qubit | Ölçümde 0/1 veren ama ölçümden önce kuantum durumuyla temsil edilen bilgi birimi |
| Süperpozisyon | Qubitin olası sonuçlara ait genliklerle temsil edilen durumu |
| Ölçüm | Kuantum durumundan klasik sonuç alma işlemi |
| Dolaşıklık | Birden fazla qubitin ayrı ayrı değil, ortak sistem olarak tanımlanması |
| Girişim | Doğru cevabın olasılığını artırma, yanlış cevapları bastırma mekanizması |
| NISQ | Gürültülü, orta ölçekli mevcut kuantum cihazlar dönemi |
| PQC | Kuantum saldırılarına dayanıklı olması hedeflenen klasik kriptografi |

### Teknik olmayanlar için kaçınılması gereken rota

Teknik olmayan bir kişi şu sırayla başlamamalıdır:

```text
Hilbert uzayları
Karmaşık sayılarla durum vektörleri
Matris çarpımları
Tensör çarpımı
Shor algoritmasının matematiksel ispatı
Quantum error correction kodlarının detayları
```

Bunlar değerli konulardır, fakat başlangıçta motivasyonu düşürebilir. Önce doğru kavramsal çerçeve kurulmalıdır.

### Teknik olmayanlar için başarı ölçütü

Bu rotanın sonunda kişi şunları yapabiliyorsa yeterli bir temel kazanmış demektir:

- Kuantum bilgisayarların klasik bilgisayarların yerine geçmeyeceğini açıklayabilir.
- Bugünkü kuantum bilgisayarların neden henüz sınırlı olduğunu anlatabilir.
- Kriptografi tarafındaki riskin neden bugünden konuşulduğunu açıklayabilir.
- Bir kuantum haberindeki “qubit sayısı”, “logical qubit”, “fault-tolerant”, “quantum advantage” gibi ifadeleri eleştirel okuyabilir.
- İş dünyasında kuantum stratejisinin neden PoC, yetkinlik ve risk yönetimiyle başlaması gerektiğini kavrar.

---

## 23.2. Yazılımcılar için öğrenme yolu

Yazılımcılar için kuantum bilgisayarları öğrenmek, yeni bir programlama dili öğrenmekten çok daha farklıdır. Burada asıl değişen şey syntax değil, hesaplama modelidir.

Klasik programlamada geliştirici çoğunlukla şu modelle düşünür:

```text
Veri bellekte tutulur.
İşlemci veriyi okur.
Koşullar ve döngüler çalışır.
Ara değerler gözlemlenebilir.
Sonuç deterministic veya kontrollü biçimde üretilir.
```

Kuantum programlamada ise düşünce modeli farklıdır:

```text
Qubitler başlangıç durumuna hazırlanır.
Kuantum kapıları uygulanır.
Süperpozisyon, dolaşıklık ve girişim kullanılır.
Ara ölçüm dikkatli yapılır.
Son ölçümden klasik sonuç alınır.
Sonuç çoğu zaman istatistiksel olarak yorumlanır.
```

Bu nedenle yazılımcı için ilk hedef, kuantum bilgisayarı “yeni bir işlemci türü” gibi değil, “farklı bir hesaplama modeli” gibi anlamaktır.

### Yazılımcı için ön koşullar

Yazılımcıların kuantum programlamaya başlamadan önce aşağıdaki temel konularda rahat olması faydalıdır:

- Temel lineer cebir: vektör, matris, matris çarpımı
- Karmaşık sayılar hakkında temel fikir
- Olasılık ve istatistik temeli
- Algoritma karmaşıklığına giriş
- Python ile temel programlama
- Jupyter Notebook kullanımı
- API/SDK mantığı

Bu konuların hepsinde uzman olmak gerekmez. Ancak kuantum programlama örneklerini anlamak için en azından vektör, matris ve olasılık kavramlarıyla barışık olmak gerekir.

### Yazılımcı için önerilen öğrenme sırası

Yazılımcılar için önerilen rota şöyledir:

1. Qubit, ölçüm, süperpozisyon ve dolaşıklık kavramlarını öğren
2. Tek qubit kapılarını ve CNOT gibi temel çok-qubit kapılarını tanı
3. Kuantum devresi okumayı öğren
4. Basit devreleri simülatörde çalıştır
5. Bell state, Deutsch-Jozsa, Bernstein-Vazirani gibi küçük algoritmaları uygula
6. Grover algoritmasının temel mantığını kod üzerinden incele
7. Qiskit veya Cirq ile devre yazmayı öğren
8. Simülatör ile gerçek donanım farkını deneyimle
9. Gürültü, shot, ölçüm sonucu dağılımı ve hata kavramlarını öğren
10. VQE/QAOA gibi hibrit algoritmaların yapısını incele
11. Gerçek bir problem seçmeden önce kuantum avantaj ihtimalini sorgula

### Yazılımcı için önerilen araç sırası

Başlangıç için en pratik yol genellikle Python tabanlı araçlardır.

| Aşama | Araç | Neden? |
|---|---|---|
| Kavramsal ve uygulamalı başlangıç | Qiskit | Eğitim içeriği güçlü, örnek çok, IBM Quantum ekosistemiyle bütünleşik |
| Devre modeli ve Google ekosistemi | Cirq | Devre, moment ve operation yapılarıyla düşük seviye kontrol sağlar |
| Hibrit QML ve optimizasyon | PennyLane | Otomatik türev, PyTorch/JAX/NumPy entegrasyonu ve QML odaklıdır |
| Microsoft ekosistemi | Q# / Azure Quantum | Q# dil modeli ve Azure Quantum servisleriyle kurumsal bağlam sağlar |
| Bulut ve cihaz çeşitliliği | Amazon Braket | Farklı donanım türlerine ve simülatörlere ortak servis modeli sunar |

Başlangıç için tek araç seçilecekse, çoğu yazılımcı için **Qiskit** iyi bir ilk tercihtir. IBM Quantum Learning ve Qiskit ekosistemi, temel kavramlardan algoritmalara kadar geniş bir eğitim yolu sunar. Daha sonra Cirq, PennyLane, Azure Quantum veya Braket ile ekosistem genişletilebilir.

### Yazılımcı için örnek mini rota

İlk iki hafta için yazılımcı rotası şöyle olabilir:

```text
1. gün: Qubit, ölçüm, süperpozisyon
2. gün: X, H, Z, CNOT kapıları
3. gün: Bell state devresi
4. gün: Ölçüm sonuçları ve shot kavramı
5. gün: Basit devreleri Qiskit ile yazma
6. gün: Simülatör kullanımı
7. gün: Gerçek donanım kavramı ve queue/job modeli
8. gün: Deutsch-Jozsa algoritması
9. gün: Bernstein-Vazirani algoritması
10. gün: Grover algoritmasına giriş
11. gün: Gürültülü simülasyon fikri
12. gün: VQE/QAOA kavramsal giriş
13. gün: Basit bir hibrit algoritma örneği
14. gün: Öğrenilenlerin kısa teknik özeti
```

### Yazılımcı için başarı ölçütü

Bir yazılımcı başlangıç seviyesini geçtiğini şu noktada anlayabilir:

- Basit bir kuantum devresini okuyabilir.
- Hadamard ve CNOT ile Bell state oluşturmayı açıklayabilir.
- Ölçüm sonuçlarının neden dağılım olarak geldiğini bilir.
- Simülatör ile gerçek donanım arasındaki farkı bilir.
- Grover algoritmasının “tüm cevapları deneme” değil, amplitude amplification olduğunu açıklayabilir.
- Qiskit veya benzeri bir araçla küçük devreleri çalıştırabilir.
- Kuantum bilgisayarın kurumsal uygulamaya nasıl hibrit bağlanabileceğini temel düzeyde anlayabilir.

---

## 23.3. Yazılım mimarları için öğrenme yolu

Yazılım mimarları için kuantum bilgisayar öğrenmenin amacı, kuantum devrelerini en derin matematiksel seviyede yazmak olmayabilir. Asıl amaç, kuantum teknolojilerinin mevcut kurumsal mimarilere nasıl bağlanabileceğini, hangi riskleri doğuracağını ve hangi koşullarda anlamlı PoC konusu olabileceğini değerlendirebilmektir.

Yazılım mimarı şu sorulara cevap arar:

```text
Kuantum bilgisayar mevcut mimarinin neresine oturur?
Bu bir servis midir, altyapı bileşeni midir, araştırma ortamı mıdır?
Hangi iş yükleri kuantum servislerine gönderilebilir?
Veri hazırlama nasıl yapılır?
Sonuçlar nasıl yorumlanır?
Güvenlik ve uyumluluk riskleri nelerdir?
PQC geçişi kurumsal mimaride nasıl yönetilir?
```

### Yazılım mimarının öğrenmesi gereken ana başlıklar

Yazılım mimarları için öğrenme başlıkları şunlardır:

1. Kuantum bilgisayarların temel çalışma modeli
2. Hibrit klasik-kuantum mimari
3. Quantum as a Service modeli
4. SDK/API tabanlı entegrasyon
5. Batch job, queue, shot, backend, simulator, QPU kavramları
6. Veri hazırlama ve encoding maliyeti
7. Sonuçların istatistiksel yorumlanması
8. NISQ kısıtları
9. Fault-tolerant döneme geçişin mimari etkileri
10. PQC migration ve crypto agility
11. Kurumsal güvenlik ve veri sınıflandırma
12. Vendor lock-in ve çoklu sağlayıcı stratejisi

### Yazılım mimarı için öğrenme sırası

Yazılım mimarları için önerilen rota:

1. Kuantum bilgisayarın klasik sistemin yerine geçmediğini öğren
2. Hibrit klasik-kuantum akışları incele
3. QaaS servis modellerini karşılaştır
4. Kuantum iş yükünün nasıl paketlenip gönderildiğini öğren
5. Simülatör ve gerçek QPU farkını anla
6. Veri encoding ve sonuç yorumlama maliyetlerini incele
7. PQC ve crypto inventory konularına ayrı odaklan
8. Basit bir kuantum PoC mimarisi tasarla
9. PoC başarı kriterlerini teknik ve iş açısından tanımla
10. Kurumsal yol haritası için kısa/orta/uzun vade ayrımı yap

### Mimari bakışla önemli ayrımlar

Yazılım mimarı için bazı ayrımlar kritiktir:

| Ayrım | Neden önemli? |
|---|---|
| Simülatör vs gerçek QPU | Test, maliyet, doğruluk ve performans beklentisini belirler |
| Fiziksel qubit vs mantıksal qubit | Donanım duyurularını doğru yorumlamayı sağlar |
| Quantum advantage vs PoC başarısı | Her PoC’nin kuantum avantaj göstermesi gerekmez |
| Quantum cryptography vs PQC | Kurumsal güvenlik stratejisinde karışıklığı önler |
| NISQ vs fault-tolerant dönem | Kullanım alanlarının zamanlamasını belirler |
| SDK bağımlılığı vs mimari soyutlama | Vendor lock-in riskini azaltır |

### Yazılım mimarı için örnek PoC soruları

Bir yazılım mimarı kuantum PoC seçerken şu soruları sormalıdır:

```text
Bu problem gerçekten kuantum hesaplama açısından anlamlı mı?
Klasik algoritmalarla mevcut en iyi çözüm nedir?
Kuantum yaklaşım hangi alt problemi hedefliyor?
Problem boyutu bugünkü cihazlar için uygun mu?
Simülatörde başlanabilir mi?
Gerçek QPU kullanımı gerekli mi?
Sonuç nasıl doğrulanacak?
Başarı kriteri ne olacak?
Bu PoC iş değerine mi, öğrenme değerine mi odaklı?
```

### Yazılım mimarı için başarı ölçütü

Bu rotanın sonunda yazılım mimarı:

- Kuantum servislerini mevcut sistem mimarisine kavramsal olarak yerleştirebilir.
- Kuantum PoC için gerçekçi kapsam belirleyebilir.
- Klasik/kuantum hibrit iş akışı tasarlayabilir.
- PQC migration için mimari sorumluluk alanlarını çıkarabilir.
- Yönetimle teknik ekip arasında köprü kurabilir.
- “Bu konu henüz araştırma seviyesinde” ile “bu konu kurumsal hazırlık gerektiriyor” ayrımını yapabilir.

---

## 23.4. Siber güvenlik ekipleri için öğrenme yolu

Siber güvenlik ekipleri için kuantum bilgisayar konusu iki farklı eksende ele alınmalıdır:

1. **Kuantum bilgisayarların mevcut kriptografiye etkisi**
2. **Post-Quantum Cryptography geçişi**

Güvenlik ekiplerinin kuantum algoritmaların tüm matematiksel ayrıntılarını öğrenmesi gerekmez; fakat Shor ve Grover algoritmalarının güvenlik etkisini doğru anlamaları gerekir.

### Güvenlik ekipleri için kritik kavramlar

| Kavram | Güvenlik açısından anlamı |
|---|---|
| Shor algoritması | RSA, Diffie-Hellman ve ECC gibi açık anahtarlı sistemler için teorik tehdit |
| Grover algoritması | Simetrik anahtar aramasında karekök hızlanma etkisi |
| PQC | Kuantum saldırılarına dayanıklı klasik kriptografi ailesi |
| Crypto inventory | Kurumda kullanılan kriptografik algoritma, protokol, sertifika, anahtar ve kütüphanelerin envanteri |
| Crypto agility | Kriptografik algoritmaları gerektiğinde hızlı değiştirebilme kabiliyeti |
| Store now, decrypt later | Bugün toplanan şifreli verinin gelecekte kuantum bilgisayarla çözülme riski |
| Hybrid key exchange | Klasik ve post-quantum yöntemleri geçiş döneminde birlikte kullanma yaklaşımı |

### Siber güvenlik ekipleri için öğrenme sırası

Güvenlik ekipleri için önerilen rota:

1. Kuantum bilgisayarların hangi kripto sistemlerini etkilediğini öğren
2. Shor algoritmasının RSA/DH/ECC üzerindeki etkisini kavra
3. Grover algoritmasının simetrik kriptografi üzerindeki etkisini öğren
4. NIST PQC standartlarını incele
5. FIPS 203, FIPS 204 ve FIPS 205 standartlarının neyi kapsadığını öğren
6. Crypto inventory yaklaşımını kurum içinde planla
7. Sertifika, TLS, VPN, HSM, PKI, kod imzalama ve veri saklama alanlarını incele
8. Crypto agility hedef mimarisini belirle
9. Tedarikçi ve ürün bağımlılıklarını değerlendir
10. PQC migration roadmap oluştur

### Güvenlik ekipleri için pratik başlangıç

Güvenlik ekibi için en pratik ilk çalışma bir **crypto inventory** çalışmasıdır.

Bu envanterde şu sorular cevaplanmalıdır:

```text
Kurumda hangi açık anahtarlı algoritmalar kullanılıyor?
RSA nerelerde var?
ECC nerelerde var?
Diffie-Hellman hangi protokollerde kullanılıyor?
TLS sertifikaları hangi algoritmalara dayanıyor?
VPN çözümleri hangi algoritmaları kullanıyor?
HSM ve KMS sistemleri hangi algoritmaları destekliyor?
Kod imzalama süreçlerinde hangi algoritmalar var?
Uzun süre saklanan hassas veriler hangi algoritmalarla korunuyor?
Üçüncü taraf ürünlerde kuantum-kırılgan kriptografi var mı?
```

### Güvenlik ekipleri için önceliklendirme

Tüm sistemleri aynı anda dönüştürmek gerçekçi değildir. Önceliklendirme şu şekilde yapılabilir:

1. Uzun süre gizli kalması gereken veriler
2. Kritik altyapı ve regülasyona tabi sistemler
3. İnternet açık yüzeyler
4. Kimlik doğrulama ve sertifika altyapısı
5. VPN ve ağ güvenliği bileşenleri
6. Kod imzalama ve yazılım tedarik zinciri
7. Üçüncü taraf bağımlılıklar
8. Arşiv/veri saklama sistemleri

### Güvenlik ekipleri için başarı ölçütü

Bu rotanın sonunda güvenlik ekibi:

- Kuantum tehdidini abartmadan ama küçümsemeden anlatabilir.
- RSA, DH ve ECC riskini açıklayabilir.
- Simetrik kriptografi tarafında anahtar boyu etkisini yorumlayabilir.
- NIST PQC standartlarının ne işe yaradığını bilir.
- Kurum için crypto inventory çalışması başlatabilir.
- PQC migration roadmap hazırlayabilir.
- “Bugün panik yok, ama bugünden hazırlık var” dengesini kurabilir.

---

## 23.5. Yöneticiler için öğrenme yolu

Yöneticiler için kuantum bilgisayar öğrenmenin amacı, teknik ayrıntıları uygulamak değil; doğru yatırım, risk ve yetkinlik kararlarını verebilmektir.

Yöneticinin öğrenmesi gereken ana fikir şudur:

> Kuantum bilgisayarlar bugün çoğu kurum için doğrudan üretim teknolojisi değil; stratejik izleme, yetkinlik geliştirme, risk azaltma ve seçilmiş PoC alanıdır.

### Yöneticiler için kritik sorular

Bir yönetici şu sorulara cevap verebilmelidir:

```text
Kuantum bilgisayarlar kurumumuzu hangi alanlarda etkileyebilir?
Bu etki kısa vadede mi, orta vadede mi, uzun vadede mi?
Kriptografi açısından hazırlık seviyemiz nedir?
Hangi ekiplerin farkındalık kazanması gerekir?
Kurum içinde kim bu konuyu sahiplenmeli?
PoC yapılacaksa amacı öğrenme mi, iş değeri mi?
Hangi tedarikçiler ve iş ortakları izlenmeli?
Bu konuda yatırım yapmamak hangi riski doğurur?
Aşırı erken yatırım yapmak hangi riski doğurur?
```

### Yöneticiler için öğrenme sırası

1. Kuantum bilgisayarların ne olduğunu ve ne olmadığını öğren
2. Kullanım alanlarını sektör bazlı değerlendir
3. Kriptografi etkisini ve PQC geçiş ihtiyacını anla
4. Kısa/orta/uzun vadeli beklentileri ayır
5. Kurumsal hazırlık seviyesini ölç
6. Yetkinlik geliştirme planı oluştur
7. PoC yaklaşımını belirle
8. Tedarikçi ve ekosistem izleme modeli kur
9. Yönetim raporlaması için sade metrikler belirle
10. Kuantum stratejisini teknoloji stratejisinin bir alt başlığı olarak konumlandır

### Yöneticiler için ana metrikler

Yöneticilerin takip edebileceği pratik metrikler şunlardır:

| Metrik | Ne anlatır? |
|---|---|
| Kuantum farkındalık seviyesi | Ekiplerin temel kavramları bilip bilmediği |
| Crypto inventory tamamlanma oranı | Kriptografik varlıkların ne kadarının envantere alındığı |
| PQC readiness seviyesi | PQC geçişine hazırlık düzeyi |
| PoC sayısı ve sonucu | Öğrenme ve keşif çalışmalarının çıktısı |
| Kritik veri sınıflandırması | Store now, decrypt later riskine maruz veri alanları |
| Tedarikçi PQC desteği | Ürün ve servis sağlayıcıların kuantum güvenli geçiş hazırlığı |
| Yetkinlik planı | Kurum içinde uzmanlık gelişimi |

### Yöneticiler için kaçınılması gereken hatalar

Yöneticiler açısından en sık hatalar şunlardır:

- Kuantum bilgisayarı kısa vadede tüm işleri değiştirecek bir teknoloji gibi görmek
- Konuyu tamamen akademik ve uzak gelecek diye görmezden gelmek
- Sadece donanım haberlerine bakarak strateji oluşturmak
- PQC geçişini yalnızca güvenlik ekibinin küçük bir işi gibi konumlandırmak
- PoC çalışmalarından doğrudan ticari geri dönüş beklemek
- Yetkinlik geliştirmeden tedarikçi bağımlı ilerlemek
- “Rakipler ne yapıyor?” sorusuna takılıp kurumun kendi risk profilini ihmal etmek

### Yöneticiler için başarı ölçütü

Bu rotanın sonunda yönetici:

- Kuantum bilgisayarların stratejik önemini doğru çerçeveleyebilir.
- Yönetim seviyesinde hype üretmeden farkındalık oluşturabilir.
- PQC geçişini kurumun risk yönetimi gündemine alabilir.
- PoC kararlarını gerçekçi hedeflerle değerlendirebilir.
- Teknik ekiplerden doğru raporlamayı isteyebilir.
- Kısa, orta ve uzun vadeli kuantum yol haritası isteyebilir.

---

## 23.6. 10 günlük hızlı başlangıç planı

Bu plan, kuantum bilgisayarlar hakkında hızlı ama doğru bir temel oluşturmak isteyen herkes için tasarlanmıştır. Teknik olmayan kişiler bazı uygulama adımlarını kavramsal düzeyde geçebilir; yazılımcılar ise basit kod örnekleriyle pekiştirebilir.

### Gün 1 — Büyük resmi öğren

**Hedef:** Kuantum bilgisayarın ne olduğunu ve ne olmadığını anlamak.

Okuma konuları:

- Kuantum bilgisayar nedir?
- Klasik bilgisayardan farkı nedir?
- Neden bugün gündemde?
- Hangi alanlarda potansiyel taşır?

Günün sonunda cevaplanması gereken soru:

```text
Kuantum bilgisayar neden “daha hızlı klasik bilgisayar” değildir?
```

### Gün 2 — Bit, qubit ve ölçüm

**Hedef:** Bit ile qubit farkını öğrenmek.

Okuma konuları:

- Bit nedir?
- Qubit nedir?
- Ölçüm neden önemlidir?
- Ölçüm sonucunda neden 0 veya 1 alırız?

Günün sonunda cevaplanması gereken soru:

```text
Bir qubit gerçekten neyi saklar?
```

### Gün 3 — Süperpozisyon

**Hedef:** Süperpozisyonu popüler klişelerin ötesinde anlamak.

Okuma konuları:

- Süperpozisyon nedir?
- “Aynı anda hem 0 hem 1” neden eksik bir anlatımdır?
- Olasılık genliği nedir?
- Ölçüm süperpozisyonu nasıl etkiler?

Günün sonunda cevaplanması gereken soru:

```text
Süperpozisyon neden tek başına kuantum avantaj anlamına gelmez?
```

### Gün 4 — Dolaşıklık

**Hedef:** Entanglement kavramını doğru anlamak.

Okuma konuları:

- Dolaşıklık nedir?
- Klasik korelasyon ile farkı nedir?
- Bell state nedir?
- Dolaşıklık ışıktan hızlı iletişim midir?

Günün sonunda cevaplanması gereken soru:

```text
Dolaşıklık neden güçlüdür ama mesaj göndermek için tek başına kullanılamaz?
```

### Gün 5 — Girişim

**Hedef:** Kuantum algoritmaların asıl mekanizmasını anlamak.

Okuma konuları:

- Kuantum girişim nedir?
- Olasılık genlikleri nasıl güçlenir veya söner?
- Doğru cevabı güçlendirmek ne demektir?
- Kuantum algoritmalar neden sadece paralellik değildir?

Günün sonunda cevaplanması gereken soru:

```text
Kuantum algoritmalar doğru cevabı nasıl daha olası hale getirir?
```

### Gün 6 — Kuantum kapıları ve devreler

**Hedef:** Basit kuantum devrelerini okuyabilmek.

Okuma konuları:

- X, H, Z kapıları
- CNOT kapısı
- Ölçüm sembolleri
- Bell state devresi

Yazılımcılar için uygulama:

```text
Qiskit veya Cirq ile iki qubitlik Bell state devresi kur.
Simülatörde çalıştır.
Ölçüm sonuçlarını yorumla.
```

Günün sonunda cevaplanması gereken soru:

```text
Hadamard + CNOT kombinasyonu neden temel bir örnektir?
```

### Gün 7 — Temel algoritma fikri

**Hedef:** Kuantum algoritmanın klasik algoritmadan farkını anlamak.

Okuma konuları:

- Oracle nedir?
- Amplitude amplification nedir?
- Phase estimation nedir?
- QFT ne işe yarar?

Günün sonunda cevaplanması gereken soru:

```text
Kuantum algoritma neden “bütün sonuçları okuyabilen” bir yapı değildir?
```

### Gün 8 — Grover ve Shor

**Hedef:** En bilinen iki algoritmanın etkisini öğrenmek.

Okuma konuları:

- Grover algoritması ve karekök hızlanma
- Shor algoritması ve çarpanlara ayırma / ayrık logaritma
- Kriptografi etkisi
- Teorik önem ile bugünkü pratik farkı

Günün sonunda cevaplanması gereken soru:

```text
Shor algoritması neden kriptografi açısından önemlidir ama bugün RSA kırıldı anlamına gelmez?
```

### Gün 9 — Donanım, gürültü ve hata düzeltme

**Hedef:** Bugünkü kuantum bilgisayarların sınırlarını anlamak.

Okuma konuları:

- Fiziksel qubit türleri
- Decoherence
- Gate hataları
- NISQ
- Mantıksal qubit
- Hata düzeltme
- Fault-tolerant quantum computing

Günün sonunda cevaplanması gereken soru:

```text
Neden yalnızca fiziksel qubit sayısına bakmak yanıltıcıdır?
```

### Gün 10 — Kullanım alanları ve stratejik sonuç

**Hedef:** Öğrenilenleri iş ve teknoloji stratejisine bağlamak.

Okuma konuları:

- Kuantum simülasyon
- Kimya ve malzeme bilimi
- Optimizasyon
- QML
- PQC
- Kurumsal hazırlık
- Hype ile gerçek ilerlemeyi ayırma

Günün sonunda cevaplanması gereken soru:

```text
Bugün bir kurum kuantum bilgisayarlar konusunda hangi somut adımları atabilir?
```

---

## 23.7. 30 günlük derinleşme planı

Bu plan, hızlı başlangıçtan sonra konuyu daha sistematik öğrenmek isteyenler içindir. Teknik olmayan kişiler bu planı kavramsal okuma olarak uygulayabilir; yazılımcılar ve mimarlar uygulama adımlarını da ekleyebilir.

### 1. hafta — Temelleri sağlamlaştırma

**1. gün:** Kuantum bilgisayarın büyük resmi  
**2. gün:** Bit, qubit ve ölçüm  
**3. gün:** Süperpozisyon  
**4. gün:** Dolaşıklık  
**5. gün:** Girişim  
**6. gün:** Klasik, olasılıksal ve kuantum hesaplama farkı  
**7. gün:** Haftalık tekrar ve kısa özet yazımı

Hafta sonunda üretilecek çıktı:

```text
Kuantum bilgisayarları 1 sayfada anlatan kişisel özet
```

### 2. hafta — Devre modeli ve algoritma sezgisi

**8. gün:** Kuantum kapıları: X, Y, Z, H  
**9. gün:** S, T, faz ve rotasyon kapıları  
**10. gün:** CNOT, CZ, SWAP  
**11. gün:** Kuantum devresi okuma  
**12. gün:** Bell state uygulaması  
**13. gün:** Deutsch-Jozsa ve Bernstein-Vazirani  
**14. gün:** Haftalık tekrar ve devre çizimi

Yazılımcılar için çıktı:

```text
Basit devreleri simülatörde çalıştıran küçük bir notebook
```

Mimarlar için çıktı:

```text
Kuantum job lifecycle diyagramı
```

### 3. hafta — Algoritmalar, kullanım alanları ve sınırlar

**15. gün:** Grover algoritması  
**16. gün:** Shor algoritması  
**17. gün:** Phase estimation ve QFT  
**18. gün:** VQE ve QAOA  
**19. gün:** Kuantum simülasyon ve kimya  
**20. gün:** Optimizasyon ve finansal kullanım alanları  
**21. gün:** Hype ve gerçek ilerleme analizi

Hafta sonunda üretilecek çıktı:

```text
Algoritma - kullanım alanı - pratik olgunluk karşılaştırma tablosu
```

### 4. hafta — Donanım, hata düzeltme, programlama ve strateji

**22. gün:** Donanım yaklaşımları  
**23. gün:** Gürültü ve decoherence  
**24. gün:** Kuantum hata düzeltme  
**25. gün:** NISQ ve fault-tolerant dönem  
**26. gün:** Qiskit / Cirq / Q# / PennyLane karşılaştırması  
**27. gün:** PQC ve crypto inventory  
**28. gün:** Yazılım mimarisi ve QaaS  
**29. gün:** Kurumsal strateji ve PoC yaklaşımı  
**30. gün:** Kişisel/kurumsal öğrenme raporu

30. gün sonunda üretilecek çıktı:

```text
Kuantum bilgisayarlar için kişisel veya kurumsal öğrenme yol haritası
```

### 30 günlük planın rol bazlı uyarlaması

| Rol | Ağırlık verilecek günler |
|---|---|
| Teknik olmayan kişi | 1-10, 19-21, 27-30 |
| Yazılımcı | 8-18, 22-26 |
| Yazılım mimarı | 11-14, 22-30 |
| Siber güvenlik ekibi | 8, 15-17, 23-24, 27-30 |
| Yönetici | 1-7, 19-21, 27-30 |

---

## 23.8. Önerilen kitaplar, kurslar ve kaynaklar

Bu bölümde önerilen kaynaklar farklı seviyelere göre ayrılmıştır. Tek bir kaynak bütün profiller için en iyi değildir. Başlangıçta sade ve güvenilir açıklamalar, yazılımcılar için uygulamalı platformlar, ileri seviye için ise akademik kitaplar tercih edilmelidir.

### Başlangıç için güvenilir açıklamalar

#### NIST — Quantum Computing Explained

NIST’in “Quantum Computing Explained” içeriği, kuantum bilgisayarları sade ve güvenilir biçimde anlamak için iyi bir başlangıçtır. Özellikle kuantum bilgisayarların bugün hâlâ erken, hata eğilimli ama belirli problem sınıfları için potansiyel taşıyan sistemler olduğunu anlamaya yardımcı olur.

Uygun olduğu kişiler:

- Teknik olmayan kişiler
- Yöneticiler
- Güvenlik ekipleri
- Konuya yeni başlayan yazılımcılar

Kullanım şekli:

```text
İlk gün okunmalı.
Not alınmalı.
“Ne yapar / ne yapmaz?” ayrımı çıkarılmalı.
```

#### IBM Quantum Learning

IBM Quantum Learning, kuantum bilgi, devre modeli, algoritmalar ve Qiskit ile uygulama tarafında güçlü bir öğrenme platformudur. Temel kurslar, modüller ve uygulamalı örneklerle yazılımcılar için özellikle faydalıdır.

Uygun olduğu kişiler:

- Yazılımcılar
- Yazılım mimarları
- Teknik liderler
- Kuantum algoritmalarına giriş yapmak isteyenler

Kullanım şekli:

```text
Önce temel quantum information kursları.
Sonra devreler ve algoritmalar.
Daha sonra Qiskit ile uygulama.
```

#### Microsoft Azure Quantum Documentation

Microsoft Azure Quantum ve Q# dokümantasyonu, özellikle Microsoft ekosisteminde çalışan ekipler için değerlidir. Q#, Azure Quantum, hibrit hesaplama ve kuantum servislerinin bulut üzerinden çalıştırılması hakkında düzenli bir çerçeve sunar.

Uygun olduğu kişiler:

- .NET / Azure ekosistemindeki yazılımcılar
- Yazılım mimarları
- Kurumsal teknoloji ekipleri
- Hibrit klasik-kuantum mimariyi anlamak isteyenler

Kullanım şekli:

```text
Qubit ve quantum circuit kavramları için temel sayfalar okunmalı.
Sonra Q# örnekleri incelenmeli.
Ardından Azure Quantum hibrit mimari dokümanları okunmalı.
```

#### Google Cirq Documentation

Cirq, Google tarafından geliştirilen açık kaynaklı bir Python framework’üdür. Devreler, moment’lar, operation’lar ve simülasyon konularında düşük seviyeli kontrol sunar.

Uygun olduğu kişiler:

- Python bilen yazılımcılar
- Kuantum devre modelini kod üzerinden öğrenmek isteyenler
- Google Quantum AI ekosistemini takip etmek isteyenler

Kullanım şekli:

```text
Cirq basics ile başlanmalı.
İlk devre oluşturulmalı.
Simülatörde çalıştırılmalı.
Daha sonra cihaz ve noise kavramları incelenmeli.
```

#### PennyLane Documentation ve QML kaynakları

PennyLane, quantum machine learning, quantum chemistry ve hibrit kuantum-klasik hesaplama için güçlü bir Python kütüphanesidir. Otomatik türev, PyTorch, JAX ve NumPy entegrasyonu gibi özellikleriyle QML ve VQE/QAOA benzeri hibrit algoritmalar için uygundur.

Uygun olduğu kişiler:

- Python bilen yazılımcılar
- Machine learning geçmişi olanlar
- Quantum machine learning ve quantum chemistry ile ilgilenenler
- Hibrit optimizasyon öğrenmek isteyenler

Kullanım şekli:

```text
Önce temel quantum circuit demosu.
Sonra gradient ve training kavramları.
Daha sonra QML veya quantum chemistry demoları.
```

#### Amazon Braket Documentation

Amazon Braket, farklı kuantum donanımlarına ve simülatörlere bulut üzerinden erişim sağlayan bir quantum computing servisidir. QaaS ve hibrit job yaklaşımını anlamak isteyen mimarlar için değerlidir.

Uygun olduğu kişiler:

- Yazılım mimarları
- Bulut mimarları
- Araştırma ekipleri
- Farklı donanım sağlayıcılarını tek platformdan denemek isteyenler

Kullanım şekli:

```text
Önce simulator üzerinde örnek görev çalıştırılmalı.
Sonra device seçimi, shots, job submission ve sonuç okuma akışı incelenmeli.
```

### Kitap önerileri

#### Michael A. Nielsen & Isaac L. Chuang — Quantum Computation and Quantum Information

Bu kitap alanın klasikleşmiş temel kaynaklarından biridir. Kuantum bilgi, kuantum devreleri, algoritmalar, teleportation, kuantum kriptografi ve hata düzeltme gibi konuları akademik derinlikte ele alır.

Uygun olduğu kişiler:

- İleri seviye yazılımcılar
- Araştırmacılar
- Akademik çalışma yapmak isteyenler
- Matematiksel temeli güçlendirmek isteyenler

Başlangıç seviyesi için doğrudan ilk kaynak olarak ağır olabilir. Önce kavramsal kaynaklarla temel oluşturup sonra bu kitaba geçmek daha sağlıklı olur.

#### Scott Aaronson — Quantum Computing Since Democritus

Bu kitap, kuantum bilgisayarları yalnızca teknik açıdan değil; matematik, bilgisayar bilimi, felsefe ve karmaşıklık teorisi bağlamında ele alır. Kavramsal derinliği yüksektir.

Uygun olduğu kişiler:

- Teorik bilgisayar bilimine ilgi duyanlar
- Karmaşıklık teorisini sevenler
- Kuantum bilgisayarların felsefi ve teorik sonuçlarını merak edenler
- Teknik arka planı olan okuyucular

Bu kitap bir “nasıl kod yazılır?” kitabı değildir. Daha çok derin düşünme, kavramları sorgulama ve teorik çerçeveyi genişletme kitabıdır.

### Kaynakları role göre seçme

| Profil | İlk kaynak | İkinci kaynak | İleri kaynak |
|---|---|---|---|
| Teknik olmayan kişi | NIST Quantum Computing Explained | IBM Quantum Learning temel içerikler | Popüler ama güvenilir makaleler |
| Yazılımcı | IBM Quantum Learning | Qiskit / Cirq dokümantasyonu | Nielsen & Chuang |
| Yazılım mimarı | Azure Quantum / Amazon Braket | IBM Quantum / NIST PQC | Kurumsal QaaS ve PQC rehberleri |
| Siber güvenlik ekibi | NIST PQC | NCCoE migration rehberleri | Kriptografi teknik standartları |
| Yönetici | NIST / IBM iş perspektifi | McKinsey / sektör raporları | Kurumsal strateji ve risk raporları |
| QML ilgilisi | PennyLane | Qiskit Machine Learning | Akademik QML makaleleri |

### Türkçe öğrenme için öneri

Türkçe kaynaklar giderek artsa da kuantum bilgisayar alanında en güncel ve en güvenilir kaynakların önemli kısmı İngilizcedir. Bu nedenle Türkçe öğrenenler için en iyi yöntem şu olabilir:

```text
Önce Türkçe kavramsal özet oku.
Sonra İngilizce resmi kaynaklardan doğrula.
Bilmediğin terimler için küçük bir sözlük oluştur.
Her bölüm sonunda kendi cümlelerinle Türkçe özet yaz.
```

Bu yöntem hem kavramları daha iyi yerleştirir hem de İngilizce teknik literatürü takip etmeyi kolaylaştırır.

---

## Bölüm Özeti

Bu bölümde kuantum bilgisayarları öğrenmek isteyen farklı profiller için ayrı öğrenme yolları tanımlandı. Teknik olmayan kişiler için kavramsal doğruluk, yazılımcılar için devre modeli ve uygulama, yazılım mimarları için hibrit entegrasyon ve QaaS, siber güvenlik ekipleri için PQC migration, yöneticiler için ise stratejik farkındalık ve karar desteği öne çıkarıldı.

Ana mesaj şudur:

> Kuantum bilgisayar öğrenmek tek bir çizgi değildir. Doğru öğrenme yolu, kişinin rolüne, hedeflediği derinliğe ve kurum içindeki sorumluluğuna göre değişir.

Başlangıç için en sağlıklı yaklaşım; önce sade ve doğru kavramlar, sonra temel matematik ve devre modeli, ardından algoritmalar, donanım, hata düzeltme, programlama ve strateji başlıklarıyla ilerlemektir.

---

## Kaynaklar ve İleri Okuma

- NIST — Quantum Computing Explained  
  https://www.nist.gov/quantum-information-science/quantum-computing-explained

- NIST — Quantum Information Science  
  https://www.nist.gov/quantum-information-science

- NIST — Post-Quantum Cryptography  
  https://www.nist.gov/pqc

- NIST NCCoE — Migration to Post-Quantum Cryptography  
  https://www.nccoe.nist.gov/applied-cryptography/migration-to-pqc

- IBM Quantum Learning  
  https://quantum.cloud.ibm.com/learning

- IBM Quantum Learning — Courses  
  https://quantum.cloud.ibm.com/learning/en/courses

- IBM Quantum / Qiskit  
  https://www.ibm.com/quantum/qiskit

- Microsoft Azure Quantum Documentation  
  https://learn.microsoft.com/en-us/azure/quantum/

- Microsoft Azure Quantum — Hybrid Computing  
  https://learn.microsoft.com/en-us/azure/quantum/hybrid-computing-overview

- Google Quantum AI — Cirq Basics  
  https://quantumai.google/cirq/start/basics

- PennyLane Documentation  
  https://docs.pennylane.ai/

- PennyLane QML  
  https://pennylane.ai/qml/

- Amazon Braket  
  https://aws.amazon.com/braket/

- Amazon Braket Developer Guide  
  https://docs.aws.amazon.com/braket/

- Michael A. Nielsen, Isaac L. Chuang — Quantum Computation and Quantum Information, Cambridge University Press  
  https://www.cambridge.org/highereducation/books/quantum-computation-and-quantum-information/01E10196D0A682A6AEFFEA52D53BE9AE

- Scott Aaronson — Quantum Computing Since Democritus, Cambridge University Press  
  https://www.cambridge.org/core/books/quantum-computing-since-democritus/197A4CD13738E10AAD787DBB78D8E92C
