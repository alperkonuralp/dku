---
draft: true
---
# 17. Kriptografi ve Post-Quantum Cryptography

Kuantum bilgisayarların iş dünyası, kamu kurumları ve yazılım mimarisi üzerindeki en somut etkilerinden biri kriptografi alanında ortaya çıkar. Çünkü bugünkü dijital dünyanın önemli bir bölümü; kimlik doğrulama, güvenli iletişim, dijital imza, sertifika altyapısı, VPN bağlantıları, yazılım güncellemeleri, finansal işlemler ve kurumlar arası veri alışverişi gibi kritik süreçlerde açık anahtarlı kriptografiye dayanır.

Bu bölümün amacı, kuantum bilgisayarların kriptografiyi neden etkilediğini sade ama teknik olarak doğru şekilde açıklamak; hangi algoritma ailelerinin risk altında olduğunu göstermek; Post-Quantum Cryptography kavramını Quantum Cryptography ile karıştırmadan konumlandırmak ve kurumlar için gerçekçi bir geçiş stratejisi önermektir.

Bu konu iki uç yaklaşım arasında sıkışmaya çok uygundur. Bir tarafta “kuantum bilgisayarlar bugün bütün şifreleri kırdı” şeklinde abartılı ve yanlış bir panik dili vardır. Diğer tarafta ise “nasıl olsa henüz büyük kuantum bilgisayar yok, o yüzden bugün yapılacak bir şey yok” şeklinde tehlikeli bir rehavet vardır. Doğru yaklaşım bu ikisinin ortasındadır: Bugün genel amaçlı, kriptografik açıdan anlamlı, büyük ölçekli ve hataya dayanıklı kuantum bilgisayarlar henüz yaygın kullanımda değildir; ancak kriptografik geçişler yıllar sürdüğü için kurumların bugünden hazırlık yapması gerekir.

---

## 17.1. Kuantum bilgisayarlar kriptografiyi neden etkiler?

Modern kriptografi kabaca iki büyük aile üzerinden düşünülebilir:

1. **Simetrik kriptografi**
2. **Asimetrik / açık anahtarlı kriptografi**

Simetrik kriptografide aynı gizli anahtar hem şifreleme hem de çözme için kullanılır. AES gibi algoritmalar bu gruba girer. Açık anahtarlı kriptografide ise bir açık anahtar ve bir özel anahtar vardır. RSA, Diffie-Hellman, DSA ve eliptik eğri tabanlı algoritmalar bu gruba girer.

Bugünkü internet güvenliğinde açık anahtarlı kriptografi çok merkezi bir rol oynar. Örneğin TLS bağlantılarında tarafların güvenli şekilde anahtar anlaşması yapması, sertifika zincirlerinin doğrulanması, yazılım paketlerinin imzalanması, kod imzalama süreçleri, elektronik imzalar ve birçok kimlik doğrulama mekanizması açık anahtarlı kriptografiye dayanır.

Kuantum bilgisayarların kriptografiyi etkilemesinin temel nedeni şudur:

> Bazı kuantum algoritmaları, bugün yaygın kullanılan bazı açık anahtarlı kriptografik problemlerin altında yatan matematiksel zorlukları klasik bilgisayarlara göre çok daha verimli çözebilir.

Bu ifade dikkatli okunmalıdır. Kuantum bilgisayarlar “bütün şifreleri kırar” demek doğru değildir. Asıl risk, belirli matematiksel varsayımlara dayanan açık anahtarlı kriptografik sistemler üzerindedir. Özellikle RSA, klasik Diffie-Hellman, DSA ve eliptik eğri tabanlı kriptografi, yeterince güçlü bir kuantum bilgisayar ortaya çıktığında ciddi risk altına girer.

Kuantum bilgisayarların kriptografik etkisini anlamak için iki algoritma özellikle önemlidir:

- **Shor algoritması**
- **Grover algoritması**

Shor algoritması açık anahtarlı kriptografi açısından yıkıcı etkiye sahip olabilir. Çünkü büyük sayıların çarpanlarına ayrılması ve ayrık logaritma problemini verimli biçimde çözebilir. RSA ve Diffie-Hellman/ECC gibi sistemlerin güvenliği bu problemlerin klasik bilgisayarlar için zor olmasına dayanır.

Grover algoritması ise simetrik anahtar arama problemlerinde karekök düzeyinde hızlanma sağlar. Bu, simetrik kriptografiyi tamamen geçersiz kılmaz; ancak güvenlik seviyesini etkiler ve anahtar uzunlukları açısından dikkatli değerlendirme gerektirir.

---

## 17.2. RSA, Diffie-Hellman ve ECC açısından risk

Açık anahtarlı kriptografi bugün dijital güvenliğin taşıyıcı kolonlarından biridir. Ancak yaygın kullanılan birçok açık anahtarlı algoritma, kuantum bilgisayarlara karşı dayanıklı olacak şekilde tasarlanmamıştır.

### RSA açısından risk

RSA’nın güvenliği, çok büyük iki asal sayının çarpımından oluşan bir sayıyı tekrar asal çarpanlarına ayırmanın klasik bilgisayarlar için pratikte çok zor olmasına dayanır. Basitleştirirsek:

```text
p ve q iki büyük asal sayı olsun.

n = p × q

Açık anahtar n üzerinden kurulur.
Özel anahtar ise p ve q bilgisine bağlıdır.
```

Klasik bilgisayarlar için yeterince büyük `n` değerini çarpanlarına ayırmak pratikte çok zordur. Fakat Shor algoritması, yeterince büyük ve hataya dayanıklı bir kuantum bilgisayar üzerinde bu problemi verimli biçimde çözebilir. Bu nedenle RSA, kriptografik açıdan anlamlı bir kuantum bilgisayar ortaya çıktığında kırılabilir kabul edilir.

Burada önemli nokta şudur: RSA’nın bugün yaygın kullanılan anahtar uzunlukları, klasik saldırganlara karşı güvenli kabul edilebilir; ancak bu güvenlik varsayımı büyük ölçekli kuantum bilgisayarlar için geçerli değildir.

### Diffie-Hellman açısından risk

Diffie-Hellman anahtar değişimi, iki tarafın güvensiz bir kanal üzerinden ortak bir gizli anahtar türetmesini sağlar. Klasik Diffie-Hellman’ın güvenliği ayrık logaritma probleminin zorluğuna dayanır.

Shor algoritması ayrık logaritma problemini de verimli çözebildiği için klasik Diffie-Hellman da kuantum tehdidi altındadır. Bu özellikle TLS, VPN ve benzeri protokollerde anahtar anlaşması mekanizmaları açısından önemlidir.

### ECC açısından risk

Eliptik eğri kriptografisi, RSA’ya kıyasla daha kısa anahtarlarla benzer klasik güvenlik seviyeleri sunabildiği için modern sistemlerde çok yaygındır. ECDH, ECDSA ve EdDSA gibi algoritmalar birçok uygulamada kullanılır.

Ancak ECC’nin güvenliği de eliptik eğri ayrık logaritma probleminin zorluğuna dayanır. Shor algoritması bu problemi de hedefleyebilir. Bu nedenle ECC, kuantum sonrası dünyada güvenli varsayılamaz.

### Riskin pratik anlamı

Bu risk yalnızca “şifreli verinin çözülmesi” ile sınırlı değildir. Açık anahtarlı kriptografi birçok farklı amaca hizmet eder:

- TLS bağlantılarında anahtar anlaşması
- Sunucu sertifikalarının doğrulanması
- Kod imzalama
- Yazılım güncelleme güvenliği
- Belge imzalama
- E-posta güvenliği
- VPN bağlantıları
- Kimlik doğrulama altyapıları
- IoT cihaz kimlikleri
- Donanım güven kökleri
- Blockchain ve dijital varlık sistemleri

Dolayısıyla kuantum tehdidi yalnızca “bir dosya şifresi kırılır mı?” sorusu değildir. Asıl mesele, dijital güvenlik altyapısının önemli bir kısmının yeniden değerlendirilmesidir.

---

## 17.3. Shor algoritmasının kriptografik etkisi

Shor algoritması, kuantum hesaplama tarihindeki en önemli algoritmalardan biridir. Önemi, teorik bir hızlanma örneği olmasının ötesindedir; doğrudan modern açık anahtarlı kriptografinin temel varsayımlarını hedefler.

Shor algoritması iki temel problem açısından kritiktir:

1. **Integer factorization**
2. **Discrete logarithm**

RSA, integer factorization problemine dayanır. Diffie-Hellman ve ECC ise ayrık logaritma problemlerinin farklı biçimlerine dayanır. Shor algoritması bu problem sınıflarına karşı kuantum bilgisayarlar için verimli bir yol sunar.

### Shor algoritması nasıl düşünülmeli?

Shor algoritmasının teknik detayları oldukça derindir; Quantum Fourier Transform ve period finding gibi konular içerir. Ancak kriptografik etki açısından sade açıklama şudur:

> Shor algoritması, bazı matematiksel problemlerde gizli periyodik yapıyı kuantum bilgisayar yardımıyla ortaya çıkarır. Bu periyot bilgisi daha sonra klasik işlemle çarpanlara ayırma veya ayrık logaritma çözümüne dönüştürülebilir.

Yani Shor algoritması tamamen “kuantum bilgisayar her şeyi tek başına çözer” şeklinde çalışmaz. Algoritma hibrit karakter taşır:

```text
1. Problem klasik olarak hazırlanır.
2. Kuantum devre, periyot bulma gibi zor kısmı hedefler.
3. Ölçüm sonucu alınır.
4. Klasik bilgisayar sonucu işler.
5. Gerekirse süreç tekrarlanır.
```

Bu, kuantum algoritmaların genel doğasıyla uyumludur. Kuantum bilgisayar doğru sonucun olasılığını artıran özel bir hesaplama yapar; klasik bilgisayar ise sonucu yorumlar, doğrular ve sonuca dönüştürür.

### Shor algoritması bugün RSA’yı kırıyor mu?

Hayır. Bugünkü kuantum bilgisayarlar, gerçek dünyada kullanılan RSA anahtarlarını kıracak ölçek, hata düzeltme kapasitesi ve güvenilirlik seviyesinde değildir. RSA-2048 gibi anahtarları kırmak için çok sayıda yüksek kaliteli mantıksal qubit ve uzun süre hataya dayanıklı hesaplama gerekir.

Ancak bu, Shor algoritmasının önemsiz olduğu anlamına gelmez. Tam tersine, kriptografi açısından stratejik riskin temelidir. Çünkü kurumlar bugünkü sistemlerini birkaç ayda değiştiremez. Kripto geçişleri; ürünleri, protokolleri, sertifika altyapılarını, donanımları, gömülü sistemleri, uyumluluk süreçlerini ve tedarikçileri etkiler. Bu nedenle “henüz kırılmadı” cümlesi, “hazırlık yapmaya gerek yok” anlamına gelmez.

---

## 17.4. Grover algoritması ve simetrik kriptografi

Grover algoritması, yapılandırılmamış arama problemlerinde karekök düzeyinde hızlanma sağlayan bir kuantum algoritmadır. Kriptografi açısından bu, kaba kuvvet anahtar arama saldırıları için önemlidir.

Klasik bir saldırganın `N` olası anahtar içinde doğru anahtarı bulmak için ortalama çok büyük sayıda deneme yapması gerekir. Grover algoritması ideal koşullarda bu arama maliyetini yaklaşık `√N` seviyesine indirebilir.

Örneğin sezgisel olarak:

```text
Klasik kaba kuvvet maliyeti:
2^k

Grover ile ideal kuantum arama maliyeti:
yaklaşık 2^(k/2)
```

Bu, simetrik kriptografiyi açık anahtarlı kriptografi kadar dramatik biçimde kırmaz. Çünkü çözüm genellikle anahtar uzunluğunu artırmaktır.

Örneğin:

```text
AES-128 klasik güvenlik seviyesi açısından güçlüdür.
Grover etkisi düşünülürse güvenlik marjı azalır.
AES-256, kuantum sonrası güvenlik marjı açısından daha rahat bir tercih olarak görülür.
```

Ancak burada da dikkatli olmak gerekir. Grover algoritmasını gerçek bir saldırıda etkili kullanmak için büyük, hataya dayanıklı kuantum bilgisayarlar gerekir. Ayrıca simetrik kriptografiye saldırı sadece teorik sorgu sayısı meselesi değildir; devre derinliği, oracle maliyeti, hata düzeltme overhead’i ve paralelleştirme gibi mühendislik faktörleri de önemlidir.

### Hash fonksiyonları açısından etki

Grover algoritması hash fonksiyonları için de güvenlik değerlendirmelerini etkileyebilir. Preimage resistance gibi özelliklerde karekök düzeyinde hızlanma söz konusu olabilir. Bu yüzden uzun çıktı boyutları ve yeterli güvenlik marjı önemlidir.

Örneğin 256-bit hash çıktıları, kuantum sonrası değerlendirmelerde 128-bit civarı güvenlik marjı sağlayacak şekilde düşünülebilir. Bu tür değerlendirmeler sistemin güvenlik hedeflerine göre yapılmalıdır.

---

## 17.5. Store now, decrypt later riski

Kuantum tehdidinin bugünden önemli olmasının en pratik sebebi **store now, decrypt later** veya **harvest now, decrypt later** riskidir.

Bu risk şu anlama gelir:

> Saldırgan bugün şifreli trafiği veya şifreli veriyi toplar, saklar ve gelecekte yeterince güçlü kuantum bilgisayarlar ortaya çıktığında bu veriyi çözmeye çalışır.

Bu senaryoda saldırganın bugün veriyi okuyabilmesi gerekmez. Sadece veriyi ele geçirip saklaması yeterlidir. Eğer verinin gizlilik süresi uzunsa, gelecek yıllarda ortaya çıkacak kuantum kapasitesi bugünkü veriler için tehdit oluşturabilir.

Bu risk özellikle şu veri türleri için önemlidir:

- Devlet sırları
- Savunma ve güvenlik verileri
- Finansal kayıtlar
- Sağlık verileri
- Kişisel veriler
- Fikri mülkiyet
- Ar-Ge dokümanları
- Uzun vadeli sözleşmeler
- Kritik altyapı verileri
- Kurumlar arası gizli yazışmalar
- Müşteri sırları
- Hukuki belgeler

Basit bir risk sorusu şudur:

```text
Bu veri kaç yıl gizli kalmalı?

Eğer cevap 5, 10, 20 yıl veya daha fazlaysa,
kuantum tehdidi bugünden dikkate alınmalıdır.
```

Örneğin bugün TLS ile korunan bir bağlantı üzerinden gönderilen hassas bir veri, saldırgan tarafından kaydedilirse ve gelecekte o TLS oturumunun anahtar anlaşması kuantum bilgisayarlarla çözülebilirse, geçmiş trafiğin gizliliği tehlikeye girebilir. Bu yüzden PQC geçişi sadece gelecekteki iletişimleri değil, bugünkü uzun ömürlü sırları da ilgilendirir.

---

## 17.6. Post-Quantum Cryptography nedir?

Post-Quantum Cryptography, klasik bilgisayarlarda çalışan ancak bilinen kuantum saldırılarına karşı dayanıklı olması hedeflenen kriptografik algoritmalar alanıdır.

Bu tanım özellikle önemlidir:

```text
PQC = Kuantum bilgisayarda çalışan kriptografi değildir.
PQC = Kuantum saldırılarına dayanıklı olması hedeflenen klasik kriptografidir.
```

PQC algoritmaları klasik işlemcilerde, klasik ağ protokollerinde, klasik yazılım kütüphanelerinde ve klasik donanımlarda çalıştırılır. Ama matematiksel dayanakları, Shor algoritmasının kolayca çözebildiği çarpanlara ayırma veya ayrık logaritma problemlerine dayanmaz.

PQC algoritma aileleri arasında şunlar bulunur:

- Kafes tabanlı kriptografi
- Hash tabanlı imzalar
- Kod tabanlı kriptografi
- Çok değişkenli polinom tabanlı yaklaşımlar
- İzogeni tabanlı yaklaşımlar

Ancak standartlaşma sürecinde her algoritma ailesi aynı seviyede başarı göstermemiştir. Bazı adaylar kırılmış, bazıları elenmiş, bazıları yedek veya alternatif olarak değerlendirilmiştir. Bu yüzden kurumların “herhangi bir kuantuma dayanıklı algoritma” seçmesi doğru değildir. Standartlaşmış ve güvenilirliği daha geniş topluluk tarafından incelenmiş algoritmalara yönelmek gerekir.

### PQC’nin hedefi nedir?

PQC’nin hedefi şudur:

- Bugünkü dijital sistemlerde kullanılan açık anahtarlı kriptografiyi kuantum saldırılarına dayanıklı hale getirmek
- TLS, VPN, sertifika, kod imzalama ve kimlik doğrulama altyapılarını dönüştürmek
- Uzun ömürlü verileri gelecekteki kuantum saldırılarına karşı korumak
- Kriptografik çevikliği artırmak
- Tedarikçi ve ürün ekosistemini kuantum sonrası döneme hazırlamak

### PQC klasik bilgisayarları ortadan kaldırmaz

PQC geçişi, kuantum bilgisayar satın almak veya kuantum donanımı kullanmak anlamına gelmez. Bir kurum PQC’ye geçerken genellikle klasik sunucular, uygulamalar, istemciler, network cihazları, HSM’ler, sertifika otoriteleri ve yazılım kütüphaneleri üzerinde değişiklik yapar.

Bu nedenle PQC, kuantum teknolojilerinin en erken kurumsal etkilerinden biridir. Çünkü uygulanması kuantum bilgisayarların kurum içinde kullanılmasını gerektirmez.

---

## 17.7. NIST PQC standartları

NIST, 2024 yılında ilk üç post-quantum cryptography standardını yayımladı. Bu standartlar, kuantum sonrası kriptografiye geçiş açısından önemli bir kilometre taşıdır.

İlk yayımlanan standartlar şunlardır:

| Standart | Algoritma adı | Amaç | Temel yaklaşım |
|---|---|---|---|
| FIPS 203 | ML-KEM | Anahtar kapsülleme / anahtar anlaşması | Module-LWE / kafes tabanlı |
| FIPS 204 | ML-DSA | Dijital imza | Module-LWE / kafes tabanlı |
| FIPS 205 | SLH-DSA | Dijital imza | Hash tabanlı |

### FIPS 203 — ML-KEM

ML-KEM, “Module-Lattice-Based Key-Encapsulation Mechanism” anlamına gelir. Eski adıyla CRYSTALS-Kyber ailesinden gelir. Anahtar kapsülleme mekanizmasıdır ve özellikle TLS gibi protokollerde güvenli anahtar anlaşması için önemlidir.

ML-KEM, RSA veya ECDH’nin birebir aynı çalışma semantiğine sahip değildir. ECDH tarafların ortak sır türetmesi üzerinden ilerlerken, KEM modelinde bir taraf bir ortak sır kapsüller, diğer taraf özel anahtarıyla bu kapsülü açar. Bu fark uygulama ve protokol entegrasyonunda önemlidir.

ML-KEM’in parametre setleri güvenlik seviyesi ve performans dengesi açısından farklı seçenekler sunar:

- ML-KEM-512
- ML-KEM-768
- ML-KEM-1024

Genel kurumsal kullanımda hangi seviyenin tercih edileceği güvenlik politikası, uyumluluk gereklilikleri, protokol desteği ve performans beklentisine göre değerlendirilmelidir.

### FIPS 204 — ML-DSA

ML-DSA, “Module-Lattice-Based Digital Signature Algorithm” anlamına gelir. Eski adıyla CRYSTALS-Dilithium ailesinden gelir. Dijital imza için kullanılır.

ML-DSA şu alanlarda önemlidir:

- Sertifika imzalama
- Kod imzalama
- Yazılım güncelleme imzaları
- Belge imzalama
- Kimlik doğrulama protokolleri
- Cihaz kimliği
- Firmware doğrulama

Dijital imzalar, yalnızca iletişim gizliliği için değil, güven zinciri için de kritiktir. Bu nedenle PQC geçişinde imza algoritmaları anahtar anlaşması kadar önemlidir.

### FIPS 205 — SLH-DSA

SLH-DSA, “Stateless Hash-Based Digital Signature Algorithm” anlamına gelir. Eski adıyla SPHINCS+ ailesinden gelir. Hash tabanlı bir imza yaklaşımıdır.

SLH-DSA’nın önemi, ML-DSA’dan farklı bir matematiksel varsayıma dayanmasıdır. Bu nedenle kriptografik çeşitlilik ve yedek yaklaşım açısından önemlidir. Ancak imza boyutu ve performans gibi pratik konularda ML-DSA’ya göre farklı maliyetleri olabilir.

### Henüz tüm geçiş tamamlandı mı?

Hayır. Standartların yayımlanması, ekosistemin tamamen hazır olduğu anlamına gelmez. Protokoller, kütüphaneler, HSM’ler, işletim sistemleri, tarayıcılar, network cihazları, sertifika otoriteleri, gömülü cihazlar ve uygulama platformları zaman içinde destek kazanır.

Bu nedenle kurumsal geçiş bir ürün güncellemesinden ibaret değildir. Bir program olarak yönetilmelidir.

---

## 17.8. Quantum cryptography ile PQC farkı

Bu iki kavram sık karıştırılır.

### Post-Quantum Cryptography

PQC, klasik bilgisayarlarda çalışan ve kuantum saldırılarına dayanıklı olması hedeflenen algoritmalardır.

Örnekler:

- ML-KEM
- ML-DSA
- SLH-DSA

PQC için kuantum bilgisayar, kuantum ağ veya özel kuantum donanımı gerekmez. Yazılım, protokol ve donanım destekleriyle klasik altyapılara entegre edilir.

### Quantum Cryptography

Quantum cryptography ise kuantum fiziğinin kendisini güvenlik mekanizması olarak kullanan yaklaşımları ifade eder. En bilinen örnek Quantum Key Distribution, yani QKD’dir.

QKD’nin amacı, kuantum fiziksel ilkeleri kullanarak anahtar paylaşımı yapmaktır. Teorik olarak dinleme girişiminin tespit edilebilmesi gibi avantajları vardır. Ancak pratikte özel donanım, özel iletişim altyapısı, mesafe kısıtları, maliyet ve operasyonel karmaşıklık gibi faktörler vardır.

### Temel fark

| Konu | PQC | Quantum Cryptography |
|---|---|---|
| Çalıştığı ortam | Klasik bilgisayarlar | Kuantum fiziksel sistemler |
| Amaç | Kuantum saldırılarına dayanıklı klasik kriptografi | Kuantum fizik kullanarak güvenli iletişim |
| Özel kuantum donanım gerekir mi? | Hayır | Genellikle evet |
| Kurumsal geçişte kısa/orta vadede daha yaygın mı? | Evet | Daha sınırlı |
| Örnek | ML-KEM, ML-DSA, SLH-DSA | QKD |

Kurumlar açısından kısa ve orta vadede daha yaygın gündem PQC’dir. QKD ise belirli yüksek güvenlik senaryolarında değerlendirilebilir, ancak genel kurumsal kriptografi geçişinin ana yolu olarak görülmemelidir.

---

## 17.9. Kurumlar için PQC geçiş stratejisi

PQC geçişi teknik, operasyonel ve yönetişim boyutları olan uzun soluklu bir programdır. Başarılı bir geçiş için yalnızca algoritma seçmek yetmez. Kurumun kriptografik bağımlılıklarını bilmesi, riskleri önceliklendirmesi, tedarikçilerini değerlendirmesi, protokolleri test etmesi ve kripto çeviklik kazanması gerekir.

Aşağıdaki yaklaşım kurumsal ölçekte uygulanabilir bir çerçeve sunar.

### 1. Yönetim sahipliği oluştur

PQC geçişi yalnızca güvenlik ekibinin teknik işi olarak bırakılmamalıdır. CISO, CIO, mimari ekipler, uygulama ekipleri, altyapı ekipleri, hukuk, risk, uyumluluk ve satın alma süreçleri bu programın parçası olmalıdır.

Programın sahibi net olmalıdır:

```text
PQC Program Sahibi
├─ Siber Güvenlik
├─ Kurumsal Mimari
├─ Uygulama Ekipleri
├─ Altyapı / Network
├─ PKI / Sertifika Yönetimi
├─ Tedarikçi Yönetimi
├─ Risk ve Uyum
└─ İş Birimleri
```

### 2. Quantum-readiness roadmap hazırla

Kurumun kuantum tehdidine hazırlık yol haritası olmalıdır. Bu yol haritası yalnızca teknik değişiklik listesi değil, aynı zamanda önceliklendirme ve zamanlama dokümanı olmalıdır.

Yol haritası şu sorulara yanıt vermelidir:

- Hangi sistemler kuantum açısından hassas?
- Hangi verilerin gizlilik ömrü uzun?
- Hangi protokoller açık anahtarlı kriptografiye dayanıyor?
- Hangi tedarikçiler PQC desteği sunuyor veya ne zaman sunacak?
- Hangi sistemler önce dönüştürülmeli?
- Hangi sistemlerde hibrit yaklaşım kullanılmalı?
- Hangi regülasyonlar ve sektör standartları dikkate alınmalı?

### 3. Kriptografik envanter çıkar

PQC geçişinin en kritik adımı kriptografik envanterdir. Kurumlar çoğu zaman nerede hangi algoritmanın kullanıldığını tam olarak bilmez.

Envanter şu başlıkları içermelidir:

| Envanter alanı | Açıklama |
|---|---|
| Sistem adı | Uygulama, servis, cihaz veya platform |
| İş sahibi | Sistemden sorumlu iş birimi |
| Teknik sahip | Uygulama veya altyapı ekibi |
| Kullanılan algoritmalar | RSA, ECDH, ECDSA, AES, SHA vb. |
| Anahtar uzunlukları | RSA-2048, RSA-4096, P-256, AES-256 vb. |
| Kullanım amacı | Şifreleme, imza, anahtar değişimi, kimlik doğrulama |
| Protokol | TLS, SSH, IPsec, S/MIME, JWT, XML Signature vb. |
| Sertifika bilgisi | CA, geçerlilik süresi, algoritma |
| Kütüphane / ürün | OpenSSL, BouncyCastle, Windows CNG, HSM, appliance vb. |
| Veri hassasiyeti | Düşük, orta, yüksek, kritik |
| Gizlilik ömrü | 1 yıl, 5 yıl, 10+ yıl |
| PQC destek durumu | Destekli, yol haritasında, bilinmiyor |
| Tedarikçi bağımlılığı | Var/yok |
| Öncelik | Düşük, orta, yüksek, kritik |

### 4. Veriyi gizlilik ömrüne göre sınıflandır

PQC geçişinde her sistemi aynı anda dönüştürmek gerçekçi değildir. Önceliklendirme için en iyi göstergelerden biri verinin gizlilik ömrüdür.

Örnek sınıflandırma:

| Gizlilik ömrü | Risk seviyesi | Yaklaşım |
|---|---|---|
| 0-1 yıl | Düşük/orta | İzle, planla |
| 1-5 yıl | Orta | Roadmap’e al |
| 5-10 yıl | Yüksek | Önceliklendir |
| 10+ yıl | Kritik | Erken geçiş / hibrit koruma değerlendir |

### 5. Açık anahtar kullanım noktalarını önceliklendir

Kuantum tehdidi en çok açık anahtarlı kriptografiyi etkilediği için öncelik bu alanlarda olmalıdır:

- TLS anahtar değişimi
- VPN/IPsec
- SSH
- PKI ve sertifika altyapısı
- Kod imzalama
- Firmware imzalama
- E-posta güvenliği
- API gateway ve mTLS
- Kimlik sağlayıcılar
- IoT cihaz sertifikaları
- HSM entegrasyonları
- Donanım güven kökleri
- Uzun ömürlü arşiv şifreleme

### 6. Kripto çeviklik kazan

Kripto çeviklik, bir sistemin kullanılan kriptografik algoritmaları ve parametreleri büyük mimari kırılmalar yaşamadan değiştirebilme yeteneğidir.

Kripto çeviklik yoksa PQC geçişi çok zorlaşır. Örneğin algoritma isimleri kod içine gömülmüşse, sertifika formatları sabit varsayılmışsa, anahtar boyutları veritabanı kolonlarında dar alanlara yazılmışsa veya protokol implementasyonu esnek değilse geçiş maliyeti artar.

Kripto çeviklik için yapılabilecekler:

- Algoritma ve anahtar boyutlarını konfigürasyona almak
- Kriptografik kütüphane kullanımını merkezi hale getirmek
- Sertifika ve imza boyutlarındaki artışa hazırlıklı olmak
- Protokol sürümlerini güncel tutmak
- Eski algoritma bağımlılıklarını azaltmak
- Test ortamlarında hibrit algoritmaları denemek
- Tedarikçi ürünlerinde PQC roadmap istemek
- Kripto kullanımını CI/CD ve güvenlik taramalarına dahil etmek

### 7. Hibrit geçiş yaklaşımını değerlendir

PQC algoritmaları yeni olduğu için birçok kurum bir süre hibrit yaklaşım kullanmayı tercih edebilir. Hibrit yaklaşımda klasik ve PQC algoritmalar birlikte kullanılır. Amaç, hem mevcut klasik güvenliği korumak hem de kuantum sonrası koruma katmanı eklemektir.

Örneğin TLS anahtar anlaşmasında klasik ECDHE ile ML-KEM tabanlı bir mekanizma birlikte kullanılabilir. Böylece güvenlik, iki yaklaşımın birlikte değerlendirilmesiyle sağlanır.

Hibrit yaklaşımın avantajları:

- Yeni algoritmalara geçişte daha kontrollü risk yönetimi
- Mevcut klasik güvenlik özelliklerinin korunması
- Geriye dönük uyumluluğun daha iyi yönetilmesi
- Ekosistem geçişi sırasında ara çözüm sağlaması

Zorlukları:

- Performans maliyeti
- Paket boyutlarının artması
- Protokol karmaşıklığı
- Sertifika ve imza boyutu etkileri
- Kütüphane ve tedarikçi uyumluluğu

### 8. Tedarikçi ve ürün değerlendirmesi yap

Kurumların kriptografik altyapısının önemli kısmı üçüncü parti ürünlerde bulunur. Bu nedenle PQC geçişi yalnızca iç geliştirme ekiplerinin yapacağı bir refactoring değildir.

Tedarikçilere sorulması gereken sorular:

- Ürün hangi kriptografik algoritmaları kullanıyor?
- RSA, ECDH, ECDSA kullanımı nerelerde var?
- PQC desteği var mı?
- ML-KEM, ML-DSA veya SLH-DSA desteklenecek mi?
- Destek hangi sürümde gelecek?
- Hibrit TLS desteklenecek mi?
- HSM veya sertifika altyapısı PQC destekliyor mu?
- Sertifika ve imza boyutu artışı ürün tarafından destekleniyor mu?
- Ürün FIPS uyumluluğunu nasıl yönetecek?
- Firmware ve kod imzalama süreçleri nasıl güncellenecek?

### 9. Pilot uygulamalar yap

PQC geçişi doğrudan üretim ortamında başlatılmamalıdır. Önce kontrollü pilotlar yapılmalıdır.

Uygun pilot alanları:

- İç servisler arası mTLS
- Laboratuvar ortamında TLS testleri
- Kod imzalama test ortamları
- API gateway testleri
- VPN test segmentleri
- HSM entegrasyon testleri
- Sertifika yaşam döngüsü testleri
- Performans benchmark’ları

Pilotlardan ölçülmesi gerekenler:

- Bağlantı kurma süresi
- CPU maliyeti
- Bellek kullanımı
- Paket boyutu
- Sertifika boyutu
- Loglama ve izleme etkisi
- Eski istemcilerle uyumluluk
- Hata senaryoları
- Operasyonel karmaşıklık

### 10. Regülasyon ve uyumluluk takibi yap

PQC geçişi yalnızca teknik bir tercih değildir; zaman içinde regülasyonlar, sektör standartları ve müşteri beklentileriyle zorunlu hale gelebilir. Finans, telekom, savunma, kamu, sağlık ve kritik altyapı sektörlerinde bu konu özellikle önemlidir.

Kurumsal ekiplerin NIST, CISA, NSA, ENISA, NCSC ve yerel düzenleyici otoritelerin rehberlerini düzenli takip etmesi gerekir.

---

## 17.10. Crypto inventory ve migration roadmap

Bu bölümde kurumsal uygulama açısından daha somut bir geçiş modeli sunalım. PQC geçişini yönetilebilir hale getirmek için iki ana çıktı gerekir:

1. **Crypto inventory**
2. **Migration roadmap**

### Crypto inventory nedir?

Crypto inventory, kurumun sistemlerinde kullanılan kriptografik varlıkların, algoritmaların, protokollerin, sertifikaların, anahtarların ve tedarikçi bağımlılıklarının sistematik envanteridir.

İyi bir crypto inventory şu sorulara cevap verir:

```text
Nerede kriptografi kullanıyoruz?
Hangi algoritmaları kullanıyoruz?
Hangi algoritmalar kuantum açısından riskli?
Hangi veriler uzun süre gizli kalmalı?
Hangi sistemler üçüncü parti ürünlere bağlı?
Hangi sistemler hızlıca değiştirilebilir?
Hangi sistemler gömülü, eski veya kırılgan?
```

### Crypto inventory kaynakları

Envanter çıkarmak için farklı kaynaklardan veri toplanabilir:

- Uygulama kodu taramaları
- Bağımlılık analizleri
- TLS endpoint taramaları
- Sertifika yönetim sistemleri
- HSM kayıtları
- API gateway konfigürasyonları
- Load balancer konfigürasyonları
- VPN ve firewall ayarları
- SSH anahtar yönetimi
- CI/CD pipeline’ları
- Kod imzalama süreçleri
- SBOM çıktıları
- CMDB kayıtları
- Tedarikçi anketleri
- Penetrasyon testi bulguları
- Log ve trafik analizleri

### Örnek crypto inventory tablosu

| Sistem | Kullanım | Algoritma | Protokol | Veri ömrü | Risk | PQC aksiyonu |
|---|---|---|---|---|---|---|
| Müşteri Portalı | TLS | ECDHE + ECDSA | TLS 1.2/1.3 | 5 yıl | Yüksek | TLS/PQC pilotu |
| Mobil API Gateway | mTLS | RSA-2048 | TLS | 3 yıl | Orta | Sertifika dönüşümü planla |
| Kod İmzalama | Dijital imza | RSA-4096 | Code signing | 10+ yıl | Kritik | ML-DSA test et |
| VPN | Anahtar değişimi | ECDH | IPsec | 5 yıl | Yüksek | Tedarikçi roadmap iste |
| IoT Cihazları | Cihaz kimliği | ECDSA P-256 | Özel protokol | 10+ yıl | Kritik | Donanım/firmware planı |
| Arşiv Sistemi | Veri şifreleme | AES-256 + RSA wrapping | Özel | 20 yıl | Kritik | Anahtar yönetimini incele |

### Migration roadmap nasıl hazırlanır?

Migration roadmap, crypto inventory’den çıkan riskleri zaman çizelgesine bağlar. İyi bir roadmap, yalnızca “şu algoritmaya geçilecek” demez; hangi sistemde, hangi sırayla, hangi bağımlılıklarla, hangi testlerle ve hangi geri dönüş planıyla geçileceğini tanımlar.

Örnek roadmap yapısı:

```text
Faz 0 — Program Başlatma
- Sponsorluk ve sahiplik oluştur
- PQC çalışma grubu kur
- Kapsam ve öncelik kriterlerini belirle

Faz 1 — Envanter
- Kriptografik kullanım noktalarını keşfet
- Sertifika, protokol, algoritma ve tedarikçi verilerini topla
- Uzun ömürlü veri varlıklarını belirle

Faz 2 — Risk Analizi
- Kuantum kırılgan algoritmaları sınıflandır
- Store now, decrypt later riskini değerlendir
- Kritik sistemleri önceliklendir

Faz 3 — Mimari Hazırlık
- Kripto çeviklik eksiklerini gider
- Kütüphane ve protokol bağımlılıklarını güncelle
- Tedarikçi PQC roadmap’lerini doğrula

Faz 4 — Pilotlar
- TLS/mTLS pilotu
- Kod imzalama pilotu
- HSM/PKI pilotu
- Performans ve uyumluluk testleri

Faz 5 — Kademeli Geçiş
- Kritik sistemlerden başla
- Hibrit modları değerlendir
- Sertifika ve anahtar yaşam döngüsünü güncelle

Faz 6 — Operasyonel Olgunluk
- İzleme ve raporlama ekle
- Eski algoritmaları devreden çıkar
- Periyodik kripto envanter güncellemesi yap
- Yeni sistemlerde PQC-ready mimariyi standartlaştır
```

### Önceliklendirme matrisi

Her sistem aynı öncelikte değildir. Aşağıdaki matris pratik bir başlangıç sağlar:

| Kriter | Düşük öncelik | Orta öncelik | Yüksek öncelik | Kritik öncelik |
|---|---|---|---|---|
| Veri gizlilik ömrü | <1 yıl | 1-5 yıl | 5-10 yıl | 10+ yıl |
| Açık anahtar kullanımı | Yok | Sınırlı | Yoğun | Kritik güven kökü |
| İnternete açıklık | Kapalı | İç ağ | Partner ağı | İnternet / kritik altyapı |
| Tedarikçi bağımlılığı | Yok | Az | Orta | Yüksek / belirsiz |
| Değişim zorluğu | Kolay | Orta | Zor | Çok zor / gömülü |
| Regülasyon etkisi | Yok | Az | Yüksek | Kritik |

### Başarı kriterleri

PQC migration programı için ölçülebilir başarı kriterleri belirlenmelidir:

- Kriptografik envanter kapsam oranı
- Kuantum kırılgan algoritma kullanım sayısı
- Kritik sistemlerde PQC-ready durumu
- Tedarikçi PQC destek oranı
- Uzun ömürlü veri koruma planı
- Hibrit TLS pilot başarısı
- Kod imzalama PQC pilot başarısı
- HSM/PKI uyumluluk durumu
- Kripto çeviklik skoru
- Eski algoritmaların devreden çıkarılma oranı

### Kurumlar için pratik ilk adım

Bir kurum PQC konusunda nereden başlayacağını bilmiyorsa, en mantıklı ilk adım şudur:

```text
1. Kritik veri varlıklarını belirle.
2. Bu verilerin kaç yıl gizli kalması gerektiğini yaz.
3. Bu verilerin hangi sistemlerden geçtiğini çıkar.
4. Bu sistemlerde hangi açık anahtarlı kriptografi kullanıldığını bul.
5. Tedarikçilere PQC destek planlarını sor.
6. En az bir kontrollü TLS/mTLS veya kod imzalama pilotu başlat.
```

Bu yaklaşım, teorik tartışmayı somut aksiyonlara dönüştürür.

---

## Bölüm Özeti

Bu bölümde kuantum bilgisayarların kriptografi üzerindeki etkisini ele aldık. Ana sonuçlar şunlardır:

- Kuantum bilgisayarlar özellikle açık anahtarlı kriptografiyi etkiler.
- RSA, klasik Diffie-Hellman, DSA ve ECC gibi algoritmalar Shor algoritması nedeniyle uzun vadede risk altındadır.
- Grover algoritması simetrik kriptografi üzerinde karekök düzeyinde hızlanma sağlar; bu genellikle anahtar uzunluklarıyla yönetilebilir.
- Bugün RSA’nın pratikte kırıldığı söylenemez; ancak kurumsal geçişler uzun sürdüğü için hazırlık bugünden başlamalıdır.
- Store now, decrypt later riski, uzun ömürlü gizli veriler için bugünden gerçek bir planlama konusudur.
- PQC, kuantum bilgisayarda çalışan kriptografi değil; klasik bilgisayarlarda çalışan ve kuantum saldırılarına dayanıklı olması hedeflenen kriptografidir.
- NIST’in FIPS 203, FIPS 204 ve FIPS 205 standartları PQC geçişi için temel referanslardır.
- Quantum cryptography ile Post-Quantum Cryptography aynı şey değildir.
- Kurumlar için en kritik adımlar crypto inventory, risk önceliklendirme, kripto çeviklik, tedarikçi değerlendirmesi ve kademeli migration roadmap’tir.

Kuantum bilgisayarların kriptografiye etkisi, kuantum teknolojilerinin en erken ve en somut kurumsal etkilerinden biridir. Bu nedenle PQC konusu yalnızca geleceğin teknolojisi değil, bugünün güvenlik ve mimari planlama gündemidir.

---

## Kaynaklar ve İleri Okuma

- NIST — What Is Post-Quantum Cryptography?  
  https://www.nist.gov/cybersecurity-and-privacy/what-post-quantum-cryptography

- NIST — First 3 Finalized Post-Quantum Encryption Standards  
  https://www.nist.gov/news-events/news/2024/08/nist-releases-first-3-finalized-post-quantum-encryption-standards

- NIST FIPS 203 — Module-Lattice-Based Key-Encapsulation Mechanism Standard  
  https://csrc.nist.gov/pubs/fips/203/final

- NIST FIPS 204 — Module-Lattice-Based Digital Signature Standard  
  https://csrc.nist.gov/pubs/fips/204/final

- NIST FIPS 205 — Stateless Hash-Based Digital Signature Standard  
  https://csrc.nist.gov/pubs/fips/205/final

- NIST NCCoE — Migration to Post-Quantum Cryptography  
  https://www.nccoe.nist.gov/applied-cryptography/migration-to-pqc

- CISA / NSA / NIST — Quantum-Readiness: Migration to Post-Quantum Cryptography  
  https://www.nsa.gov/Press-Room/Press-Releases-Statements/Press-Release-View/article/3498776/post-quantum-cryptography-cisa-nist-and-nsa-recommend-how-to-prepare-now/

- CISA — Product Categories for Technologies That Use Post-Quantum Cryptography Standards  
  https://www.cisa.gov/resources-tools/resources/product-categories-technologies-use-post-quantum-cryptography-standards

- NIST SP 1800-38B Preliminary Draft — Migration to Post-Quantum Cryptography  
  https://www.nccoe.nist.gov/sites/default/files/2023-12/pqc-migration-nist-sp-1800-38b-preliminary-draft.pdf
