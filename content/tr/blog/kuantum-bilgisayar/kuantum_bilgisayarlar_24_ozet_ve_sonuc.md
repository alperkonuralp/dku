---
draft: true
---
# 24. Özet ve Sonuç

Bu dokümanın önceki bölümlerinde kuantum bilgisayarları; fiziksel temellerinden qubit kavramına, süperpozisyondan dolaşıklığa, kuantum kapılarından algoritmalara, donanım yaklaşımlarından hata düzeltmeye, kriptografiden kurumsal stratejiye kadar geniş bir çerçevede ele aldık. Bu son bölümün amacı, bütün bu anlatıyı tek bir yerde toparlamak ve okuyucunun zihninde net bir sonuç bırakmaktır.

Kuantum bilgisayarlar üzerine konuşurken iki uç yaklaşım sık görülür. Birinci yaklaşım, kuantum bilgisayarları neredeyse her problemi çözecek sihirli makineler gibi sunar. İkinci yaklaşım ise bugünkü sınırlara bakarak alanın önemini küçümser. Sağlıklı bakış bu ikisinin arasında, fakat teknik gerçeklere daha yakın bir noktadadır: kuantum bilgisayarlar henüz genel amaçlı, yaygın, hataya dayanıklı üretim sistemleri değildir; buna rağmen belirli problem sınıflarında uzun vadeli etkisi çok büyük olabilecek yeni bir hesaplama modelini temsil eder.

Bu nedenle kuantum bilgisayarları anlamak için yalnızca “ne kadar hızlı?” sorusunu sormak yeterli değildir. Daha doğru sorular şunlardır:

- Hangi problem sınıflarında klasik bilgisayarlardan farklı bir avantaj sağlayabilir?
- Bu avantajın ortaya çıkması için kaç mantıksal qubit, ne kadar düşük hata oranı ve ne kadar uzun devre derinliği gerekir?
- Bugünkü donanım, algoritma ve hata düzeltme seviyesi bu hedefe ne kadar yakındır?
- Kurumlar bugün hangi riskler ve fırsatlar için hazırlık yapmalıdır?
- Yazılımcılar ve mimarlar kuantum bilgisayarı mevcut sistemler içinde nasıl konumlandırmalıdır?

Bu bölüm bu sorulara kısa ama bütünlüklü bir cevap vermeyi hedefler.

---

## 24.1. Kuantum bilgisayarları tek cümlede anlatmak

Kuantum bilgisayarları tek cümlede şöyle anlatabiliriz:

> Kuantum bilgisayar, kuantum mekaniğinin süperpozisyon, dolaşıklık ve girişim gibi özelliklerini kullanarak bazı özel problem türlerinde klasik bilgisayarlardan farklı ve potansiyel olarak çok daha güçlü hesaplama yapmayı hedefleyen bir hesaplama sistemidir.

Bu cümlede özellikle üç nokta önemlidir.

Birincisi, kuantum bilgisayar **klasik bilgisayarın daha hızlı versiyonu değildir**. Daha yüksek saat hızına sahip bir işlemci, daha fazla çekirdekli bir CPU veya daha güçlü bir GPU gibi düşünülmemelidir. Kuantum bilgisayar, bilgiyi farklı şekilde temsil eder ve hesaplamayı farklı fiziksel-matematiksel kurallar üzerinden yapar.

İkincisi, kuantum bilgisayar **her problem için avantaj vaat etmez**. Web uygulaması çalıştırmak, klasik veritabanı sorgusu yapmak, e-posta göndermek, ERP süreci yönetmek, çoğu backend servisini işletmek veya standart raporlama yapmak için kuantum bilgisayar beklenen çözüm değildir. Kuantum bilgisayarların potansiyel gücü; kuantum simülasyon, belirli optimizasyon problemleri, bazı cebirsel yapılar, kriptografiyle ilişkili problemler ve belirli bilimsel hesaplama alanlarında ortaya çıkar.

Üçüncüsü, kuantum bilgisayarın hesaplama gücü yalnızca “çok sayıda ihtimali aynı anda denemesi”nden gelmez. Bu popüler ama eksik bir anlatımdır. Asıl mesele, kuantum durumlarının olasılık genlikleri üzerinde işlem yapılabilmesi ve girişim yoluyla doğru ya da yararlı sonuçların ölçümde ortaya çıkma olasılığının artırılabilmesidir.

Bu nedenle kuantum bilgisayarı anlamanın en sağlıklı yolu şudur:

```text
Klasik bilgisayar:
Bitler üzerinde deterministik veya olasılıksal işlemler yapar.

Kuantum bilgisayar:
Qubitlerin kuantum durumları üzerinde dönüşümler yapar,
olasılık genliklerini girişimle şekillendirir,
sonunda ölçümle klasik bilgi üretir.
```

Kuantum bilgisayarın çıktısı yine klasik dünyaya döner. Sonuçta kullanıcıya, sisteme veya uygulamaya gelen bilgi klasik bittir. Fakat bu sonucun üretilme yolu klasik hesaplamadan farklıdır.

---

## 24.2. Bugün neredeyiz?

2026 itibarıyla kuantum bilgisayarlar ciddi bir mühendislik ve bilimsel ilerleme göstermiş durumdadır; ancak hâlâ yaygın, genel amaçlı, hataya dayanıklı üretim sistemleri değildir. Bugünkü sistemlerin çoğu hâlâ NISQ olarak anılan gürültülü, orta ölçekli kuantum cihazlar kategorisine girer.

Bu tabloyu doğru anlamak için birkaç ayrımı net tutmak gerekir.

### Fiziksel qubit sayısı tek başına yeterli değildir

Kuantum bilgisayar haberlerinde çoğu zaman qubit sayısı öne çıkar. Ancak yalnızca fiziksel qubit sayısına bakmak yanıltıcı olabilir. Önemli olan yalnızca kaç qubit olduğu değil; bu qubitlerin ne kadar düşük hata oranıyla çalıştığı, ne kadar süre tutarlı kalabildiği, hangi bağlantı yapısına sahip olduğu, kapı işlemlerinin ne kadar güvenilir olduğu ve hata düzeltmeye ne kadar uygun olduğudur.

Büyük ölçekli pratik kuantum hesaplama için asıl kritik kavram **mantıksal qubit**tir. Mantıksal qubit, birçok fiziksel qubitin hata düzeltme kodlarıyla birlikte daha güvenilir tek bir kuantum bilgi birimi gibi davranmasıdır. Bu nedenle kuantum bilgisayarların olgunluk değerlendirmesinde artık “kaç fiziksel qubit var?” sorusu tek başına yeterli değildir.

Daha doğru metrikler şunlardır:

- Mantıksal qubit sayısı
- Mantıksal hata oranı
- Fiziksel hata oranı
- Gate fidelity
- Devre derinliği
- Coherence süresi
- Hata düzeltme overhead’i
- Gerçek problem üzerinde klasik yöntemlere göre avantaj gösterimi

### Hata düzeltme hâlâ merkezi problemdir

Kuantum sistemler kırılgandır. Qubitler çevreleriyle etkileşime girdiklerinde decoherence oluşur. Kapılar hatalı çalışabilir, ölçümler yanlış sonuç verebilir, qubitler arasında istenmeyen crosstalk görülebilir. Bu yüzden hata düzeltme, kuantum bilgisayarlar için opsiyonel bir iyileştirme değil, büyük ölçekli kullanımın temel şartıdır.

Google Willow gibi çalışmaların önemi burada ortaya çıkar. Willow ile ilgili yayınlanan sonuçlar, hata düzeltme ölçeği büyüdükçe mantıksal hata oranının bastırılabileceğini gösterme açısından önemli bir adım olarak değerlendirildi. Ancak bu tür ilerlemeler, hemen yarın pratik üretim sistemleri hazır anlamına gelmez. Bunlar, fault-tolerant kuantum bilgisayara giden uzun yolun kritik mühendislik basamaklarıdır.

### Büyük oyuncular yol haritası açıklıyor ama yol hâlâ zorlu

IBM, fault-tolerant kuantum bilgisayar hedefini açık bir yol haritasıyla ortaya koyuyor. IBM’in 2029 için Starling hedefi, 200 mantıksal qubit üzerinde 100 milyon quantum gate çalıştırabilecek büyük ölçekli fault-tolerant sistem vizyonunu içeriyor. Bu tür hedefler, alanın fiziksel qubit sayısından mantıksal qubit ve hata düzeltmeli hesaplama yönüne kaydığını gösteriyor.

Microsoft topolojik qubit yaklaşımıyla Majorana tabanlı daha kararlı qubitler üretmeyi hedefliyor. Ancak topolojik qubitler ve Majorana tabanlı iddialar bilim dünyasında hâlâ dikkatli değerlendirilmesi gereken konular arasında. Bu alan büyük potansiyel taşısa da, iddialar ile bağımsız doğrulama arasındaki farkı korumak gerekir.

IonQ, Quantinuum, Rigetti, D-Wave, Google, IBM, Microsoft, PsiQuantum, Xanadu ve diğer oyuncular farklı donanım yolları deniyor. Süperiletken qubitler, hapsedilmiş iyonlar, nötr atomlar, fotonik sistemler, spin qubitler, topolojik qubitler ve quantum annealing birbirinden farklı avantajlara ve zorluklara sahip.

Bugün için en doğru özet şudur:

```text
Kuantum bilgisayarlar bilimsel ve mühendislik olarak hızla ilerliyor.
Fakat pratik, geniş ölçekli, hataya dayanıklı ve genel kullanıma açık kuantum bilgisayarlar henüz olgunlaşmış değil.
Gerçek değer, hata düzeltme ve mantıksal qubit ölçeği büyüdükçe daha netleşecek.
```

---

## 24.3. Yakın gelecekte ne beklemeliyiz?

Yakın geleceği üç ayrı zaman ufkunda düşünmek daha sağlıklıdır: kısa vade, orta vade ve uzun vade.

### Kısa vadede: farkındalık, deney, kriptografik hazırlık

Kısa vadede çoğu kurum için kuantum bilgisayarların doğrudan üretim iş yüklerini devralması beklenmemelidir. Ancak bu, kurumların beklemesi gerektiği anlamına gelmez.

Kısa vadede yapılması gerekenler şunlardır:

- Kuantum bilgisayarların temel kavramlarını öğrenmek
- Kurum içinde farkındalık oluşturmak
- Yazılım, güvenlik ve mimari ekiplerinde temel yetkinlik geliştirmek
- Kuantum kullanım alanlarını gerçekçi biçimde değerlendirmek
- PQC geçiş hazırlığına başlamak
- Kriptografik envanter çıkarmak
- Crypto agility yaklaşımını kurumsal mimariye dahil etmek
- Küçük ölçekli PoC çalışmalarıyla ekosistemi tanımak

Bu dönemde en somut ve acil başlıklardan biri post-quantum cryptography’dir. Çünkü kuantum bilgisayarlar bugün RSA’yı veya ECC’yi pratik ölçekte kırmıyor olsa bile, kriptografik geçişler uzun sürer. Ayrıca “store now, decrypt later” riski bugünden başlayan bir risktir.

NIST’in 2024’te FIPS 203, FIPS 204 ve FIPS 205 standartlarını yayımlaması bu nedenle önemlidir. Bu standartlar, kuantum bilgisayar saldırılarına dayanıklı olması hedeflenen algoritmalar için kurumsal geçişin somut temelini oluşturur.

### Orta vadede: hibrit kullanım, özel problem sınıfları, daha güçlü deneyler

Orta vadede kuantum bilgisayarlar, klasik sistemlerle birlikte çalışan uzmanlaşmış hızlandırıcılar gibi konumlanabilir. Bu modelde kuantum bilgisayar tek başına tüm sistemi çalıştırmaz; klasik bilgisayar veri hazırlama, orkestrasyon, optimizasyon döngüsü, hata yönetimi ve sonuç yorumlama görevlerini üstlenir.

Bu dönemde daha fazla deney şu alanlarda görülebilir:

- Kuantum simülasyon
- Kimya ve moleküler modelleme
- Malzeme bilimi
- Optimizasyon problemleri
- Finansal modelleme
- Tedarik zinciri ve lojistik deneyleri
- Hibrit kuantum-klasik algoritmalar
- Quantum machine learning araştırmaları

Ancak burada dikkatli olmak gerekir. Bir problemin kuantum bilgisayarda modellenebilmesi, otomatik olarak üretim değerine dönüşeceği anlamına gelmez. Gerçek değer için klasik en iyi yöntemlerle karşılaştırma, maliyet/fayda analizi, veri hazırlama maliyeti ve operasyonel karmaşıklık hesaba katılmalıdır.

### Uzun vadede: fault-tolerant kuantum bilgisayarlar ve gerçek uygulama kırılımları

Uzun vadede asıl kırılım, fault-tolerant kuantum bilgisayarların yeterli mantıksal qubit sayısına ve yeterince düşük logical error rate değerlerine ulaşmasıyla beklenir.

Bu gerçekleştiğinde kuantum bilgisayarların etkisi özellikle şu alanlarda güçlenebilir:

- Karmaşık kuantum sistemlerinin simülasyonu
- Yeni ilaç adaylarının ve moleküllerin modellenmesi
- Yeni malzemeler ve katalizörler
- Batarya teknolojileri
- Belirli optimizasyon problemleri
- Kriptografik risklerin fiilen daha kritik hale gelmesi
- Yeni algoritmik yaklaşımlar

Ancak uzun vadeli potansiyel, bugünkü sistemlerin abartılı pazarlanmasını haklı çıkarmaz. Kuantum bilgisayarlar için en sağlıklı strateji, ne erken ve kontrolsüz yatırım heyecanına kapılmak ne de alanı tamamen görmezden gelmektir.

---

## 24.4. Kurumlar ve yazılımcılar için ana mesajlar

Kuantum bilgisayarlar farklı roller için farklı anlamlar taşır. Bir yönetici, bir yazılım mimarı, bir güvenlik uzmanı ve bir yazılımcı aynı konuya aynı derinlikte bakmak zorunda değildir. Ancak her rolün bilmesi gereken temel mesajlar vardır.

### Kurumlar için ana mesajlar

Kurumlar açısından kuantum bilgisayarların ilk etkisi çoğu zaman doğrudan kuantum algoritma çalıştırmak değil, **stratejik hazırlık** olacaktır.

Kurumların bugün sorması gereken sorular şunlardır:

- Hangi sistemlerimizde RSA, Diffie-Hellman veya ECC kullanıyoruz?
- Sertifikalarımız, TLS yapılandırmalarımız, HSM kullanımlarımız, VPN çözümlerimiz ve imza altyapılarımız kuantum tehdidine karşı nasıl konumlanıyor?
- Uzun süre gizli kalması gereken verilerimiz var mı?
- Tedarikçilerimizin PQC yol haritası nedir?
- Crypto inventory çıkarabiliyor muyuz?
- Crypto agility seviyemiz nedir?
- Kuantum bilgisayarları hangi iş problemleri için izlemeliyiz?
- Kurum içinde kuantum farkındalığı nasıl artırılmalı?

Kurumlar için önerilen yaklaşım şu şekilde özetlenebilir:

```text
Önce farkındalık.
Sonra envanter.
Sonra risk sınıflandırması.
Sonra küçük PoC'ler.
Sonra kontrollü geçiş planı.
```

Kuantum stratejisi, bugün devasa kuantum projeleri başlatmak anlamına gelmez. Daha çok, kurumun gelecekteki riske ve fırsata hazırlık seviyesini artırmak anlamına gelir.

### Yazılımcılar için ana mesajlar

Yazılımcılar açısından kuantum programlama yeni bir syntax öğrenmekten ibaret değildir. Asıl zorluk, hesaplama sezgisinin değişmesidir.

Klasik programlamada geliştirici genellikle şu şekilde düşünür:

```text
Veriyi al.
Koşulu değerlendir.
Döngü kur.
Değişkeni güncelle.
Sonucu döndür.
```

Kuantum programlamada ise düşünce biçimi farklıdır:

```text
Qubitleri hazırla.
Süperpozisyon oluştur.
Dolaşıklık kur.
Faz ve genlikleri dönüştür.
Girişimle yararlı sonuçları güçlendir.
Ölçüm yap.
Klasik post-processing uygula.
```

Bu nedenle yazılımcılar için ilk hedef, Qiskit, Q#, Cirq veya PennyLane gibi araçlarda küçük devreler yazmak olabilir; fakat daha önemli hedef, kuantum algoritmaların neden farklı çalıştığını anlamaktır.

Yazılımcılar için pratik rota:

1. Qubit, ölçüm, süperpozisyon, dolaşıklık ve girişim kavramlarını öğren.
2. Basit kuantum devrelerini oku ve simülatörde çalıştır.
3. Bell state, Deutsch-Jozsa, Grover gibi temel örnekleri incele.
4. Hibrit klasik-kuantum akış mantığını öğren.
5. Gerçek donanım ile simülatör farkını deneyimle.
6. Kendi alanındaki olası kullanım senaryolarını gerçekçi biçimde değerlendir.

### Yazılım mimarları için ana mesajlar

Yazılım mimarları için kuantum bilgisayarlar, mevcut mimariye yeni bir işlemci takmak gibi düşünülmemelidir. Daha doğru model şudur:

```text
Kuantum bilgisayar = uzak, özel amaçlı, sınırlı erişimli, gürültülü veya gelecekte fault-tolerant hale gelecek bir hesaplama servisi.
```

Bu bakışla mimarın dikkat etmesi gereken başlıklar şunlardır:

- Quantum as a Service entegrasyonu
- API ve SDK bağımlılıkları
- Veri hazırlama maliyeti
- Kuyruklama ve job yönetimi
- Sonuçların olasılıksal doğası
- Klasik post-processing
- Gözlemlenebilirlik
- Güvenlik ve uyumluluk
- Vendor lock-in riski
- PQC ve crypto agility

Yazılım mimarı için en önemli nokta, kuantum bilgisayarı bir “yerine koyma teknolojisi” değil, belirli iş akışlarında kullanılabilecek uzmanlaşmış bir hesaplama bileşeni olarak düşünmektir.

### Siber güvenlik ekipleri için ana mesajlar

Siber güvenlik ekipleri açısından en somut konu post-quantum cryptography hazırlığıdır. Kuantum bilgisayarların bugün tüm kriptografiyi kırdığı söylenemez. Ancak kriptografik sistemlerin dönüşümü uzun sürdüğü için hazırlığa geç başlamak ciddi risk yaratabilir.

Güvenlik ekiplerinin bugün atabileceği adımlar:

- Kriptografik varlık envanteri çıkarmak
- RSA, DH ve ECC kullanılan noktaları belirlemek
- Uzun süre gizli kalması gereken veri sınıflarını işaretlemek
- Tedarikçi ve ürün bağımlılıklarını değerlendirmek
- PQC destek planlarını izlemek
- Hibrit sertifika ve protokol geçişlerini araştırmak
- Crypto agility ilkelerini mimari standartlara eklemek

Bu alanda “bekleyelim, kuantum bilgisayar çıkınca bakarız” yaklaşımı risklidir. Çünkü geçiş yalnızca algoritma değiştirmekten ibaret değildir; protokoller, sertifikalar, donanımlar, yazılımlar, tedarikçiler ve regülasyonlar birlikte ele alınmalıdır.

### Yöneticiler için ana mesajlar

Yönetim seviyesinde kuantum bilgisayarlar anlatılırken teknik detaylar yerine şu çerçeve daha etkilidir:

- Kuantum bilgisayarlar bugün her şeyi değiştirmedi.
- Ancak belirli alanlarda uzun vadeli stratejik etki potansiyeli yüksek.
- Kriptografi tarafında hazırlık şimdiden başlamalı.
- Kurumun bugün yapması gereken şey büyük yatırım değil, kontrollü farkındalık ve hazırlık.
- Hype’a kapılmadan, ama geç de kalmadan ilerlemek gerekir.

Yönetim diliyle özet:

```text
Kuantum bilgisayarlar bugün operasyonel bir zorunluluk değil,
ama stratejik hazırlık gerektiren bir teknoloji alanıdır.
En acil başlık kriptografik hazırlıktır.
En değerli yaklaşım ölçülü PoC, yetkinlik geliştirme ve crypto agility'dir.
```

---

## 24.5. Son söz: Hype’ın ötesinde gerçek değer

Kuantum bilgisayarlar hakkında sağlıklı düşünmek için önce abartıyı temizlemek gerekir.

Kuantum bilgisayarlar:

- Her şeyi hızlandırmayacak.
- Klasik bilgisayarların yerini tamamen almayacak.
- Bugün RSA’yı pratik ölçekte kırmıyor.
- Her optimizasyon problemini otomatik olarak çözmeyecek.
- AI alanındaki tüm problemleri sihirli biçimde ortadan kaldırmayacak.
- Sadece daha fazla qubit ekleyerek olgunlaşmayacak.

Ama aynı zamanda kuantum bilgisayarlar:

- Yeni bir hesaplama modelidir.
- Bazı problem türlerinde çok güçlü avantajlar sunabilir.
- Kuantum simülasyon ve malzeme bilimi gibi alanlarda uzun vadeli değer yaratabilir.
- Kriptografi dünyasını bugünden dönüştürmeye başlamıştır.
- Hata düzeltme ve mantıksal qubit ilerledikçe daha ciddi uygulama alanlarına yaklaşabilir.
- Yazılım mimarisi, güvenlik ve teknoloji stratejisi açısından şimdiden izlenmesi gereken bir alandır.

Bu dokümanın ana mesajı şu şekilde özetlenebilir:

```text
Kuantum bilgisayarları ne mucize olarak görmek gerekir,
ne de bugünkü sınırlılıkları nedeniyle önemsiz saymak.
Doğru yaklaşım; teknik gerçekleri anlamak,
stratejik etkileri ayırt etmek,
kurumsal hazırlığı zamanında başlatmak
ve hype'ın ötesindeki gerçek değere odaklanmaktır.
```

Kuantum bilgisayarların gerçek değeri, yalnızca daha hızlı hesaplama yapmalarında değil; bazı problemleri klasik düşünme biçiminin dışına çıkararak yeniden formüle etmelerinde yatıyor. Bu, yazılımcılar, mimarlar, güvenlik ekipleri, akademisyenler ve yöneticiler için önemli bir zihinsel dönüşüm anlamına gelir.

Bugün yapılması gereken şey, kuantum bilgisayarların yarın sabah bütün sistemleri değiştireceğini varsaymak değildir. Aynı şekilde, “henüz hazır değil” diyerek tamamen görmezden gelmek de doğru değildir. En sağlıklı yol, bu alanı düzenli takip etmek, temel yetkinlikleri geliştirmek, kriptografik hazırlığı başlatmak ve gerçekçi kullanım alanlarını disiplinli biçimde değerlendirmektir.

Kuantum bilgisayarların geleceği hâlâ yazılıyor. Fakat bu geleceği anlamak için bugünden doğru kavramlara, doğru beklentilere ve doğru stratejik çerçeveye sahip olmak gerekiyor.

---

## Bölüm Özeti

Bu bölümde dokümanın ana mesajları toparlandı:

- Kuantum bilgisayarlar klasik bilgisayarların daha hızlı versiyonu değil, farklı bir hesaplama modelidir.
- 2026 itibarıyla alan hızla ilerlemekte, fakat genel amaçlı fault-tolerant kuantum bilgisayarlar hâlâ olgunlaşma sürecindedir.
- Gerçek ilerleme fiziksel qubit sayısından çok mantıksal qubit, logical error rate, hata düzeltme ve pratik uygulama gösterimleri üzerinden okunmalıdır.
- Yakın vadede en somut kurumsal başlık post-quantum cryptography hazırlığıdır.
- Yazılımcılar için asıl öğrenme konusu syntax değil, kuantum hesaplama sezgisidir.
- Yazılım mimarları kuantum bilgisayarları uzmanlaşmış, hibrit, servis tabanlı hesaplama kaynakları olarak düşünmelidir.
- Kurumlar için en sağlıklı strateji; farkındalık, envanter, risk değerlendirmesi, yetkinlik geliştirme ve kontrollü PoC yaklaşımıdır.
- Kuantum bilgisayarların gerçek değeri hype’ın ötesinde, belirli problem sınıflarında ve uzun vadeli stratejik etkilerde aranmalıdır.

---

## Kaynaklar ve İleri Okuma

Bu bölüm, dokümanın önceki bölümlerinde kullanılan ana kaynakların sonuç perspektifiyle tekrar değerlendirilmesiyle hazırlanmıştır. Özellikle aşağıdaki kaynaklar temel alınmıştır:

- NIST — Quantum Computing Explained  
  https://www.nist.gov/quantum-information-science/quantum-computing-explained

- NIST — Post-Quantum Cryptography  
  https://www.nist.gov/pqc

- NIST — First Three Finalized Post-Quantum Encryption Standards  
  https://www.nist.gov/news-events/news/2024/08/nist-releases-first-3-finalized-post-quantum-encryption-standards

- NIST CSRC — FIPS 203, FIPS 204, FIPS 205 Approval  
  https://csrc.nist.gov/news/2024/postquantum-cryptography-fips-approved

- IBM Quantum Roadmap  
  https://www.ibm.com/roadmaps/quantum/

- IBM — Large-scale Fault-Tolerant Quantum Computing Roadmap  
  https://www.ibm.com/quantum/blog/large-scale-ftqc

- IBM Quantum Learning  
  https://quantum.cloud.ibm.com/learning

- Microsoft Azure Quantum Documentation  
  https://learn.microsoft.com/en-us/azure/quantum/

- Google Quantum AI — Willow and Quantum Error Correction  
  https://research.google/blog/making-quantum-error-correction-work/
