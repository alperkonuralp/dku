---
draft: true
---
# 19. Kuantum Bilgisayarlar ve Yazılım Mimarisi

Kuantum bilgisayarları yalnızca fiziksel donanım, qubit sayısı veya laboratuvar başarısı üzerinden anlamak eksik kalır. Kurumsal yazılım mimarisi açısından asıl soru şudur:

> Bir kuantum bilgisayar, mevcut yazılım sistemlerinin içine nasıl girer?

Bugünkü gerçekçi cevap şudur: Kuantum bilgisayarlar, klasik sistemlerin yerini alan bağımsız makineler olarak değil; çoğunlukla **bulut üzerinden erişilen, belirli hesaplama adımlarında kullanılan, klasik sistemlerle birlikte çalışan uzmanlaşmış hızlandırıcılar** olarak düşünülmelidir.

Bu bakış açısı, GPU kullanımına kısmen benzetilebilir. Bir kurum, yapay zekâ modeli eğitirken tüm sistemi GPU üzerinde çalıştırmaz. Veri hazırlama, orkestrasyon, servis entegrasyonu, güvenlik, izleme, kullanıcı arayüzü ve iş süreçleri çoğunlukla klasik altyapıda kalır; GPU yalnızca yoğun matris hesaplamaları için devreye girer. Kuantum bilgisayarlar için de benzer ama daha sınırlı ve daha deneysel bir modelden söz edilebilir. Klasik sistem problemi hazırlar, kuantum sistem belirli bir alt hesaplamayı yürütür, sonuç klasik sisteme döner ve iş kararı yine klasik yazılım mimarisi içinde verilir.

Bu nedenle kuantum bilgisayarları yazılım mimarisi açısından değerlendirirken şu üç ilke akılda tutulmalıdır:

1. **Kuantum bilgisayarlar mevcut kurumsal sistemlerin yerine geçmez.**
2. **Yakın ve orta vadede kullanım modeli büyük ölçüde hibrit klasik-kuantum mimaridir.**
3. **Kuantum servislerinin kurumsal mimariye girmesi teknik olduğu kadar güvenlik, yönetişim, maliyet ve yetkinlik meselesidir.**

---

## 19.1. Kuantum bilgisayarlar mevcut sistemlere nasıl entegre olur?

Bir kuantum bilgisayarın mevcut bir yazılım sistemine entegrasyonu, çoğu durumda doğrudan donanım seviyesinde gerçekleşmez. Kurumların veri merkezlerine kuantum işlemci koyması yakın vadede yaygın bir senaryo değildir. Bunun yerine kuantum işlemciler genellikle özel laboratuvar koşullarında, çok düşük sıcaklıklarda veya karmaşık fiziksel kontrol sistemleriyle çalıştırılır. Kullanıcılar bu donanımlara çoğunlukla **bulut servisleri, SDK’lar, API’ler ve yönetilen platformlar** üzerinden erişir.

Bu entegrasyon kabaca şu akışla düşünülebilir:

```text
Kurumsal uygulama
      |
      v
Klasik hesaplama / iş akışı servisi
      |
      v
Problem hazırlama ve kuantum devresi oluşturma
      |
      v
Kuantum SDK / API
      |
      v
Bulut tabanlı kuantum servis sağlayıcısı
      |
      v
Gerçek kuantum donanımı veya kuantum simülatörü
      |
      v
Ölçüm sonuçları
      |
      v
Klasik post-processing
      |
      v
Kurumsal uygulamaya sonuç dönüşü
```

Bu akışta kuantum bilgisayar, sistemin tamamını çalıştıran ana platform değildir. Daha çok belirli bir matematiksel alt problemin çözümünde veya deneysel bir algoritmanın denenmesinde kullanılan harici bir hesaplama kaynağıdır.

Örneğin bir lojistik optimizasyon uygulamasını düşünelim. Bu uygulamada siparişler, araçlar, lokasyonlar, zaman pencereleri, kapasite sınırları, yakıt maliyeti ve müşteri öncelikleri klasik veritabanlarında tutulur. Uygulamanın kullanıcı arayüzü, API katmanı, yetkilendirme modeli, raporlama sistemi ve operasyonel süreçleri klasik yazılım mimarisi üzerinde çalışır. Kuantum tarafına gönderilebilecek kısım, bu verilerden türetilmiş belirli bir optimizasyon modelidir. Kuantum veya hibrit algoritma bir aday çözüm üretir. Son karar, iş kuralları ve operasyonel kontrollerle birlikte yine klasik sistemde değerlendirilir.

Bu nedenle mimari açıdan kuantum entegrasyonu şu soruyla başlamalıdır:

> Sistemimin tamamını kuantum bilgisayarda nasıl çalıştırırım?

değil,

> Mevcut sistemimde hangi dar, matematiksel, hesaplama yoğun ve kuantum yaklaşıma uygun alt problem izole edilebilir?

olmalıdır.

---

## 19.2. Quantum as a Service modeli

**Quantum as a Service (QaaS)**, kuantum hesaplama kaynaklarına bulut üzerinden erişilmesini ifade eder. Bu modelde kurum, kuantum donanımını kendi veri merkezinde işletmez. Bunun yerine IBM Quantum, Azure Quantum, Amazon Braket veya benzeri platformlar üzerinden kuantum işlemcilere, simülatörlere ve yazılım araçlarına erişir.

QaaS modeli birkaç nedenle önemlidir:

- Kuantum donanımını fiziksel olarak işletmek çok zordur.
- Donanım teknolojileri hızla değişmektedir.
- Farklı sağlayıcılar farklı qubit mimarileri sunmaktadır.
- Deneysel çalışma için simülatör ve gerçek donanım arasında geçiş yapabilmek gerekir.
- Kurumlar erken dönemde büyük donanım yatırımı yapmadan PoC geliştirebilir.

QaaS modelinde mimari bağımlılık iki seviyede ortaya çıkar.

İlk seviye **programlama ve SDK bağımlılığıdır**. Örneğin Qiskit, Q#, Cirq, PennyLane veya Braket SDK gibi araçlar kullanılarak kuantum devreleri ve hibrit algoritmalar tanımlanır. Bu seviye geliştirici deneyimini, öğrenme eğrisini ve kod taşınabilirliğini etkiler.

İkinci seviye **çalıştırma ortamı bağımlılığıdır**. Gerçek kuantum donanımına erişim, kuyruk mekanizması, fiyatlandırma, hedef cihaz seçimi, simülatör kapasitesi, kimlik doğrulama, veri saklama ve bölgesel uyumluluk gibi konular platforma bağlıdır.

QaaS modeli pratikte şu avantajları sağlar:

```text
Donanım yatırımı yapmadan deneme
Farklı kuantum teknolojilerini karşılaştırma
Gerçek donanım ve simülatör arasında geçiş
Eğitim ve PoC geliştirme imkânı
Klasik bulut kaynaklarıyla hibrit çalışma
```

Ancak bazı riskleri de vardır:

```text
Sağlayıcı bağımlılığı
Donanım erişim kısıtları
Kuyruk süreleri
Maliyet belirsizliği
Veri güvenliği ve uyumluluk sorunları
SDK/API değişiklikleri
Deneysel sonuçların üretim kalitesine taşınamaması
```

Bu nedenle QaaS, kurumsal mimaride doğrudan “yeni bir üretim altyapısı” olarak değil, önce **araştırma, PoC, eğitim, algoritma keşfi ve stratejik hazırlık platformu** olarak konumlandırılmalıdır.

---

## 19.3. API, SDK ve bulut servisleri

Kuantum bilgisayarlara erişim çoğunlukla SDK ve API katmanları üzerinden gerçekleşir. Yazılım mimarisi açısından bu katmanlar, kuantum donanımın karmaşıklığını soyutlar.

Tipik bir kuantum SDK şu işlevleri sağlar:

- Kuantum devresi oluşturma
- Qubit ve gate tanımlama
- Ölçüm ekleme
- Simülatörde çalışma
- Gerçek donanıma job gönderme
- Job durumunu izleme
- Ölçüm sonuçlarını alma
- Klasik post-processing için veri üretme
- Bazı durumlarda hata azaltma veya optimizasyon ayarları sağlama

Örneğin IBM tarafında Qiskit ve IBM Quantum Platform, kuantum devreleri oluşturma, simülatörlerde çalışma ve gerçek kuantum donanımlarına erişme akışları sunar. Microsoft Azure Quantum, Q# ve Python ile kuantum programları oluşturma, farklı sağlayıcı hedeflerine gönderme ve bulut tabanlı kuantum servisleri kullanma yaklaşımı sunar. Amazon Braket ise farklı kuantum donanım sağlayıcılarına, simülatörlere ve hibrit işler için klasik AWS kaynaklarıyla birlikte çalışma modeline odaklanır.

Mimari açıdan bu servisler genellikle şu bileşenlerle çevrelenir:

```text
Application Layer
    - İş uygulaması
    - Kullanıcı arayüzü
    - API Gateway
    - Yetkilendirme

Classical Compute Layer
    - Problem hazırlama
    - Veri dönüştürme
    - Algoritma orkestrasyonu
    - Parametre optimizasyonu
    - Post-processing

Quantum Access Layer
    - SDK
    - Provider API
    - Job submission
    - Target selection
    - Result retrieval

Quantum Execution Layer
    - Simülatör
    - Gerçek QPU
    - Hybrid job runtime

Governance Layer
    - Kimlik ve erişim
    - Loglama
    - Maliyet kontrolü
    - Güvenlik
    - Uyumluluk
```

Bu yapıda doğrudan kuantum servis sağlayıcısına bağımlı kodun sistemin her yerine yayılması istenmez. Daha doğru yaklaşım, kuantum servislerine erişimi bir **adapter**, **facade** veya **anti-corruption layer** arkasına almaktır.

Örnek soyutlama:

```text
IRouteOptimizationQuantumSolver
IQuantumChemistryEstimator
IQuantumExperimentRunner
IQuantumJobClient
IQuantumResultInterpreter
```

Böylece uygulama katmanı belirli bir sağlayıcının SDK’sına doğrudan bağımlı olmaz. Sağlayıcı değiştiğinde veya simülatörden gerçek donanıma geçildiğinde etki alanı daha sınırlı kalır.

---

## 19.4. Hibrit iş akışları

Kuantum bilgisayarların yakın ve orta vadeli kullanımında en önemli mimari model **hibrit klasik-kuantum iş akışı**dır.

Hibrit modelde klasik bilgisayar ve kuantum bilgisayar birlikte çalışır. Microsoft’un Azure Quantum dokümantasyonu hibrit kuantum hesaplamayı, klasik bilgisayar ve kuantum bilgisayarın bir problemi çözmek için birlikte çalıştığı süreç ve mimari olarak tanımlar. Amazon Braket Hybrid Jobs da klasik AWS kaynakları ile kuantum işlem birimlerini birlikte kullanan hibrit kuantum-klasik algoritmalar için yönetilen bir çalışma modeli sunar.

Hibrit iş akışı özellikle VQE, QAOA ve bazı quantum machine learning yaklaşımlarında görülür. Genel akış şöyledir:

```text
1. Klasik sistem problemi hazırlar.
2. Parametreli kuantum devresi oluşturulur.
3. Devre kuantum simülatörde veya QPU üzerinde çalıştırılır.
4. Ölçüm sonuçları klasik sisteme döner.
5. Klasik optimizer parametreleri günceller.
6. Yeni parametrelerle kuantum devresi tekrar çalıştırılır.
7. Döngü yakınsama ölçütüne kadar devam eder.
8. Sonuç klasik sistemde yorumlanır.
```

Bu modelde kuantum bilgisayar tek başına çözüm üreten bağımsız bir karar motoru değildir. Daha çok klasik optimizasyon döngüsünün içinde kullanılan özel bir hesaplama bileşenidir.

Hibrit mimari aşağıdaki sorunları beraberinde getirir:

### Gecikme

Gerçek kuantum donanımına job göndermek, klasik bir fonksiyon çağrısı gibi düşük gecikmeli olmayabilir. Kuyruk süreleri, donanım erişimi, job scheduling ve ölçüm tekrarları gecikmeyi artırabilir. Bu nedenle kullanıcı etkileşimli, milisaniye seviyesinde cevap bekleyen senaryolarda doğrudan gerçek QPU çağrısı yapmak genellikle uygun değildir.

### Orkestrasyon

Hibrit algoritmalar tekrar eden çağrılar içerir. Bu nedenle workflow engine, job scheduler, retry mekanizması, checkpointing ve izleme önemlidir.

### Maliyet

Her job çalıştırması, simülatör kullanımı veya QPU erişimi maliyet doğurabilir. Özellikle deneysel algoritmalarda yüzlerce veya binlerce tekrar gerekebilir.

### Gözlemlenebilirlik

Kuantum job’ların durumu, hata oranları, ölçüm sayıları, parametre setleri, kullanılan backend ve sonuç dağılımları izlenmelidir. Aksi halde deneyler tekrar üretilemez ve kurumsal öğrenme oluşmaz.

### Sonuçların yorumlanması

Kuantum ölçüm sonuçları çoğunlukla tek bir deterministik cevap değil, örnekleme sonucu oluşan olasılık dağılımlarıdır. Bu nedenle sonuç yorumlama katmanı klasik mimaride açıkça tasarlanmalıdır.

---

## 19.5. Kurumsal mimaride kuantum servislerinin yeri

Kurumlar için kuantum servisleri ilk aşamada çekirdek üretim sistemlerinin merkezine yerleştirilmemelidir. Daha doğru konumlandırma şu aşamalı modeldir:

```text
Aşama 1: Farkındalık ve eğitim
Aşama 2: Problem keşfi
Aşama 3: Simülatör tabanlı deneyler
Aşama 4: Bulut QPU üzerinde PoC
Aşama 5: Hibrit algoritma prototipi
Aşama 6: İş değeri ve maliyet değerlendirmesi
Aşama 7: Sınırlı üretim entegrasyonu veya stratejik bekleme
```

Kurumsal mimaride kuantum servisleri için uygun ilk yerler şunlardır:

- Ar-Ge ortamları
- İnovasyon laboratuvarları
- Veri bilimi ve optimizasyon ekipleri
- Siber güvenlik / kriptografi dönüşüm ekipleri
- Akademik ve teknoloji iş birlikleri
- Simülasyon ve modelleme takımları
- Strateji ve teknoloji yaygınlaştırma ekipleri

Buna karşılık şu alanlarda dikkatli olunmalıdır:

- Kritik üretim iş akışları
- Gerçek zamanlı karar sistemleri
- Müşteri önündeki düşük gecikmeli servisler
- Regülasyona tabi hassas veri işleyen sistemler
- Denetlenebilirliği yüksek finansal karar motorları
- Henüz klasik yöntemlerle yeterince optimize edilmemiş süreçler

Bir kurumsal mimari diyagramında kuantum servisleri genellikle “external specialized compute provider” veya “experimental advanced compute capability” olarak yer almalıdır. Yani klasik mikroservisler, veri platformu, API gateway, IAM, observability ve governance katmanları korunur; kuantum servisleri bu mimariye kontrollü bir entegrasyon noktası olarak eklenir.

Önerilen mimari görünüm:

```text
[Business Applications]
        |
        v
[Domain Services / APIs]
        |
        v
[Optimization / Simulation Service]
        |
        +--------------------+
        | Classical Solver   |
        | Heuristic Solver   |
        | ML-based Solver    |
        | Quantum Adapter    |
        +--------------------+
                  |
                  v
        [Quantum Provider Abstraction]
                  |
        +---------+---------+---------+
        | IBM Quantum       | Azure Quantum |
        | Amazon Braket     | Other Provider|
        +-------------------+--------------+
```

Bu yapıda kuantum çözüm bir alternatif çözüm motoru olarak konumlanır. Aynı problem için klasik solver, heuristic solver ve quantum/hybrid solver sonuçları karşılaştırılabilir. Bu, kurumsal karar alma açısından çok daha sağlıklı bir yaklaşımdır.

---

## 19.6. Veri hazırlama ve sonuç yorumlama

Kuantum bilgisayarlara problem göndermeden önce verinin uygun matematiksel forma dönüştürülmesi gerekir. Bu adım çoğu zaman kuantum hesaplamanın kendisinden daha zordur.

Bir iş problemi doğrudan kuantum devresi değildir. Örneğin:

```text
“En iyi teslimat rotasını bul”
```

ifadesi bir kuantum algoritmanın doğrudan anlayacağı bir girdi değildir. Bu problemin önce matematiksel modele dönüştürülmesi gerekir:

```text
Amaç fonksiyonu
Kısıtlar
Değişkenler
Ceza terimleri
Graf gösterimi
Maliyet matrisi
Optimizasyon formülasyonu
```

Daha sonra bu model kuantum algoritmaya uygun bir forma çevrilir. Örneğin QAOA için problem Hamiltonian’ı veya Ising/QUBO formu gerekebilir. Quantum annealing için problem çoğunlukla QUBO veya Ising modeli olarak ifade edilir. Kuantum kimya için moleküler Hamiltonian, baz seti, elektron konfigürasyonu ve ölçülecek enerji beklenti değerleri gibi özel hazırlık adımları vardır.

Bu nedenle kurumsal mimaride kuantum entegrasyonu yalnızca SDK bilen geliştiricilerle değil, şu rollerin birlikte çalışmasıyla olgunlaşır:

- Domain uzmanı
- Yazılım mimarı
- Veri bilimci
- Optimizasyon uzmanı
- Kuantum algoritma uzmanı
- Güvenlik uzmanı
- Platform / DevOps ekibi
- İş birimi temsilcisi

Sonuç yorumlama da en az veri hazırlama kadar önemlidir. Kuantum algoritma çoğu zaman tek bir kesin sonuç döndürmez. Ölçümlerden oluşan bir dağılım döndürür. Bu dağılımın yorumlanması gerekir:

```text
En sık görülen sonuç nedir?
Sonuçların varyansı nedir?
Çözüm iş kısıtlarını sağlıyor mu?
Klasik baseline’a göre daha iyi mi?
Maliyet / süre / doğruluk dengesi kabul edilebilir mi?
Sonuç tekrar üretilebilir mi?
Gürültüden etkilenmiş olabilir mi?
```

Bu nedenle kuantum sonuçları doğrudan üretim kararına bağlamak yerine, önce klasik doğrulama katmanından geçirmek gerekir.

Önerilen sonuç işleme akışı:

```text
Quantum result
      |
      v
Statistical interpretation
      |
      v
Constraint validation
      |
      v
Comparison with classical baseline
      |
      v
Business rule validation
      |
      v
Human review or automated decision
```

---

## 19.7. Güvenlik, uyumluluk ve operasyonel riskler

Kuantum bilgisayarlar yazılım mimarisine girdiğinde yalnızca algoritmik bir yenilik getirmez; güvenlik ve uyumluluk açısından da yeni sorular doğurur.

### Veri güvenliği

QaaS modelinde problem verisi veya ondan türetilmiş matematiksel model bulut sağlayıcısına gönderilebilir. Bu model ham müşteri verisi içermese bile hassas iş bilgisini temsil edebilir. Örneğin rota optimizasyon modeli, lojistik ağ yapısını; finansal optimizasyon modeli, portföy stratejisini; kimya simülasyonu, Ar-Ge fikri mülkiyetini açığa çıkarabilir.

Bu nedenle şu sorular sorulmalıdır:

```text
Kuantum servisine hangi veri gönderiliyor?
Veri anonimleştirildi mi?
Model hassas iş bilgisini açığa çıkarıyor mu?
Veri hangi bölgede işleniyor?
Sonuçlar ve job metadata nerede saklanıyor?
Sağlayıcı loglarında ne kalıyor?
Kimler erişebiliyor?
```

### Kimlik ve erişim yönetimi

Kuantum servislerine erişim kurumsal IAM yapısıyla uyumlu olmalıdır. API anahtarlarının geliştirici makinelerinde kontrolsüz saklanması, deneysel PoC ortamlarında sık görülen bir risktir. Erişimler rol bazlı, sınırlı ve izlenebilir olmalıdır.

### Maliyet kontrolü

Kuantum ve simülatör job’ları plansız çalıştırıldığında maliyet oluşturabilir. Bu nedenle quota, budget alert, job limit, environment separation ve approval mekanizmaları düşünülmelidir.

### Deney tekrarlanabilirliği

Kuantum donanımlar gürültülü olduğu için aynı devre farklı zamanlarda farklı dağılımlar üretebilir. Donanım kalibrasyonu, backend sürümü, shot sayısı, hata azaltma ayarları ve parametreler kaydedilmezse deneyler tekrar üretilemez.

Kayıt altına alınması gereken bilgiler:

```text
Algoritma versiyonu
Kod commit id
SDK versiyonu
Backend / target adı
Çalıştırma zamanı
Shot sayısı
Parametre seti
Seed bilgisi, varsa
Noise model, varsa
Calibration metadata, varsa
Raw measurement counts
Post-processing versiyonu
```

### Uyumluluk

Finans, sağlık, savunma, telekom ve kamu gibi sektörlerde dış sağlayıcıya veri gönderimi regülasyonlara tabi olabilir. Kuantum servisleri henüz yaygın kurumsal denetim kalıplarına tam oturmadığı için mimari kararlar hukuk, risk ve uyum ekipleriyle birlikte değerlendirilmelidir.

### Kriptografik risk

Kuantum bilgisayarların yazılım mimarisindeki güvenlik etkisi yalnızca kuantum servis kullanımıyla sınırlı değildir. Daha büyük stratejik konu, mevcut kurum sistemlerinde kuantum-kırılgan kriptografik algoritmaların kullanımıdır. NIST’in PQC migration çalışmaları bu nedenle crypto inventory, crypto agility ve migration roadmap konularını öne çıkarır.

Bu bölümün odağı kuantum servis entegrasyonu olsa da, kurumsal mimari açısından kuantum gündemi iki paralel hatta ilerlemelidir:

```text
1. Kuantum hesaplama servisleri nasıl kullanılabilir?
2. Mevcut kriptografik altyapı kuantum tehdidine nasıl hazırlanır?
```

İkinci hat, çoğu kurum için birinci hattan daha acil ve daha somut olabilir.

---

## 19.8. Yazılım ekipleri bugün ne yapmalı?

Kuantum bilgisayarlar henüz çoğu kurum için üretim sistemlerine doğrudan değer katan olgun bir teknoloji değildir. Ancak bu, yazılım ekiplerinin hiçbir şey yapmaması gerektiği anlamına gelmez. Doğru yaklaşım, abartılı beklentiye kapılmadan kontrollü hazırlık yapmaktır.

### 1. Temel farkındalık oluşturun

Ekipler önce kuantum bilgisayarların ne olduğunu, ne olmadığını ve hangi problem sınıflarında anlamlı olabileceğini öğrenmelidir. Özellikle şu yanlışlardan kaçınılmalıdır:

```text
Kuantum bilgisayar her şeyi hızlandırır.
Yakında tüm klasik sistemler kuantuma taşınacak.
Daha çok qubit her zaman daha iyi sistem demektir.
Bugün RSA tamamen kırıldı.
QML tüm yapay zekâ problemlerini çözecek.
```

### 2. Problem envanteri çıkarın

Kurumsal sistemlerde kuantum yaklaşıma aday olabilecek problemler belirlenmelidir. Bunlar genellikle optimizasyon, simülasyon, örnekleme, kimya/malzeme, risk analizi veya kriptografi geçişi ile ilişkili olur.

Değerlendirme soruları:

```text
Problem matematiksel olarak net tanımlanabiliyor mu?
Klasik yöntemlerle çözüm maliyeti yüksek mi?
Yaklaşık çözüm kabul edilebilir mi?
Problem boyutu büyüdükçe klasik çözüm zorlaşıyor mu?
Kuantum algoritma literatüründe benzer problem var mı?
Veri hassasiyeti QaaS kullanımına uygun mu?
Klasik baseline mevcut mu?
```

### 3. Klasik baseline oluşturmadan kuantum PoC yapmayın

Bir kuantum PoC’nin anlamlı olabilmesi için karşılaştırılacak güçlü bir klasik çözüm olmalıdır. Aksi halde kuantum yaklaşımın gerçekten değer üretip üretmediği anlaşılamaz.

Baseline şunları içermelidir:

```text
Çözüm kalitesi
Çalışma süresi
Maliyet
Ölçeklenebilirlik
Operasyonel karmaşıklık
Bakım maliyeti
Tekrarlanabilirlik
```

### 4. Simülatörlerle başlayın

İlk öğrenme ve deneyler gerçek kuantum donanım yerine simülatörlerle yapılmalıdır. Simülatörler daha kontrollü, daha hızlı ve daha öğreticidir. Gerçek donanıma geçiş, algoritmanın temel doğruluğu anlaşıldıktan sonra yapılmalıdır.

### 5. Sağlayıcı bağımlılığını erken yönetin

Kuantum SDK ve platformları hızlı değişebilir. Bu nedenle PoC kodu bile mümkünse temiz soyutlamalarla yazılmalıdır. Quantum provider adapter yaklaşımı ileride platform değiştirme veya çoklu sağlayıcı denemesi için faydalıdır.

### 6. PQC hazırlığını ayrı bir iş akışı olarak başlatın

Yazılım ekipleri için en somut yakın dönem kuantum görevi çoğu zaman kuantum algoritma yazmak değil, kurumun kriptografik varlıklarını anlamaktır.

Başlangıç adımları:

```text
Kriptografik algoritma envanteri çıkarın.
TLS, SSH, VPN, PKI, HSM, sertifika, imza, anahtar değişimi kullanımlarını belirleyin.
RSA, Diffie-Hellman, ECC kullanımlarını sınıflandırın.
Uzun süre gizli kalması gereken veri akışlarını tespit edin.
Crypto agility kabiliyetini değerlendirin.
PQC migration roadmap hazırlayın.
```

### 7. Yetkinlik geliştirme planı yapın

Her yazılım geliştiricinin kuantum algoritma uzmanı olması gerekmez. Ancak kurum içinde farklı seviyelerde yetkinlik oluşmalıdır:

```text
Farkındalık seviyesi:
Temel kavramları ve iş etkilerini anlar.

Geliştirici seviyesi:
Basit kuantum devreleri yazabilir, SDK kullanabilir, simülatörde deney yapabilir.

Mimari seviye:
QaaS, hibrit iş akışı, güvenlik, veri yönetimi ve entegrasyon risklerini değerlendirebilir.

Uzman seviye:
Algoritma seçimi, problem formülasyonu, hata/gürültü analizi ve sonuç yorumlama yapabilir.
```

### 8. Küçük, ölçülebilir PoC’ler seçin

İlk PoC’ler büyük iş dönüşümü hedeflememelidir. Daha doğru hedefler şunlardır:

```text
Qiskit veya Q# ile Bell state devresi yazmak
Basit Grover örneğini simülatörde çalıştırmak
Küçük QAOA optimizasyon problemi denemek
Kuantum kimya için küçük molekül enerji tahmini örneği incelemek
Quantum annealing ile küçük QUBO problemi modellemek
Klasik baseline ile sonuç karşılaştırmak
```

PoC’nin başarı kriteri “kuantum klasik yöntemi yendi” olmak zorunda değildir. Erken aşamada başarı kriteri şu olabilir:

```text
Ekip kavramları öğrendi.
Problem formülasyonu anlaşıldı.
Araç zinciri denendi.
Maliyet ve operasyonel karmaşıklık görüldü.
Kurum için gerçekçi yol haritası oluştu.
```

---

## Bölüm Özeti

Kuantum bilgisayarlar yazılım mimarisi açısından mevcut sistemlerin yerine geçen yeni genel amaçlı bilgisayarlar değildir. Daha gerçekçi model, kuantum bilgisayarları bulut üzerinden erişilen, belirli problem sınıflarında kullanılan, klasik sistemlerle birlikte çalışan uzmanlaşmış hesaplama kaynakları olarak görmektir.

Bu bölümde öne çıkan ana noktalar şunlardır:

- Kuantum bilgisayar entegrasyonu çoğunlukla SDK, API ve bulut servisleri üzerinden yapılır.
- Yakın ve orta vadede en gerçekçi mimari model hibrit klasik-kuantum iş akışıdır.
- QaaS modeli donanım yatırımı yapmadan deneme imkânı sağlar, fakat sağlayıcı bağımlılığı, maliyet ve veri güvenliği riskleri doğurur.
- Kuantum servisleri kurumsal mimaride önce Ar-Ge, PoC ve stratejik hazırlık alanlarına yerleştirilmelidir.
- Veri hazırlama ve sonuç yorumlama, kuantum hesaplamanın en kritik mimari parçalarıdır.
- Kuantum sonuçları çoğu zaman olasılık dağılımı şeklindedir; klasik doğrulama ve iş kuralı katmanlarından geçirilmelidir.
- Güvenlik, uyumluluk, gözlemlenebilirlik, maliyet kontrolü ve deney tekrarlanabilirliği baştan tasarlanmalıdır.
- Yazılım ekipleri bugün temel farkındalık, problem envanteri, klasik baseline, simülatör deneyleri, sağlayıcı soyutlaması ve PQC hazırlığına odaklanmalıdır.

Kısaca, kuantum bilgisayarları kurumsal yazılım mimarisine taşımak bir “donanım bağlantısı” problemi değildir. Bu, problem modelleme, veri hazırlama, hibrit orkestrasyon, güvenlik, yönetişim, maliyet ve yetkinlik geliştirme problemidir.

---

## Kaynaklar ve İleri Okuma

1. Microsoft Learn — *Microsoft Quantum and Azure Quantum documentation*  
   https://learn.microsoft.com/en-us/azure/quantum/

2. Microsoft Learn — *Introduction to Hybrid Quantum Computing*  
   https://learn.microsoft.com/en-us/azure/quantum/hybrid-computing-overview

3. Microsoft Learn — *Hybrid Quantum Computing Concepts*  
   https://learn.microsoft.com/en-us/azure/quantum/hybrid-computing-concepts

4. IBM Quantum — *Qiskit and IBM Quantum Platform*  
   https://www.ibm.com/quantum/qiskit

5. Amazon Braket Developer Guide — *Working with Amazon Braket Hybrid Jobs*  
   https://docs.aws.amazon.com/braket/latest/developerguide/braket-jobs.html

6. Amazon Braket Developer Guide — *Run your local code as a hybrid job*  
   https://docs.aws.amazon.com/braket/latest/developerguide/braket-hybrid-job-decorator.html

7. NIST NCCoE — *Migration to Post-Quantum Cryptography*  
   https://www.nccoe.nist.gov/applied-cryptography/migration-to-pqc

8. NIST — *Considerations for Achieving Crypto Agility*  
   https://nvlpubs.nist.gov/nistpubs/CSWP/NIST.CSWP.39.pdf

9. NIST — *Transition to Post-Quantum Cryptography Standards*  
   https://nvlpubs.nist.gov/nistpubs/ir/2024/NIST.IR.8547.ipd.pdf
