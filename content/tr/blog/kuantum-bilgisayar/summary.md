Açık konuşayım: “dünyadaki tek en iyi içerik budur” diyebileceğim kusursuz bir kaynak bulamadım. En sağlam kombinasyon şu görünüyor: **NIST’in sade açıklamaları**, **IBM Quantum Learning / Qiskit tarafındaki eğitim içerikleri** ve **Microsoft Azure Quantum dokümantasyonu**. Aşağıdaki dokümanı bu kaynakları doğrulayarak, yalın ama deep-dive olacak şekilde hazırladım. Güncel durum için özellikle Google Willow, IBM fault-tolerant roadmap, Microsoft Majorana 1 iddiası ve NIST PQC standartlarını da kontrol ettim. ([NIST][1])

---

# Kuantum Bilgisayarlar: Yalın ama Derinlemesine Bir Rehber

## 1. Kuantum bilgisayar nedir?

Kuantum bilgisayar, klasik bilgisayarın yaptığı işi “daha hızlı işlemci” mantığıyla yapan bir makine değildir. Daha doğru tanım şudur: **Kuantum mekaniğinin süperpozisyon, dolaşıklık ve girişim gibi özelliklerini kullanarak bazı özel problem sınıflarını klasik bilgisayarlardan farklı bir hesaplama modeliyle çözmeye çalışan bilgisayardır.** NIST de kuantum bilgisayarları; atomlar, ışık parçacıkları veya süperiletken devreler gibi kuantum sistemleri kullanarak bilgi işleyen makineler olarak açıklar. ([NIST][1])

Klasik bilgisayarların temel birimi **bit**tir. Bit, pratikte 0 veya 1 değerini temsil eder. Kuantum bilgisayarların temel birimi ise **qubit**tir. Qubit ölçüldüğünde yine 0 veya 1 sonucu verir; fakat ölçülmeden önce matematiksel olarak 0 ve 1 durumlarının bir kombinasyonu halinde bulunabilir. Microsoft’un Azure Quantum dokümantasyonu bunu, qubit durumlarının olasılık genlikleriyle tanımlanması ve ölçüm sonucunda 0 veya 1 elde edilmesi şeklinde açıklar. ([Microsoft Learn][2])

Buradaki kritik nokta şudur: Qubit “aynı anda hem 0 hem 1’dir” cümlesi popüler ama eksik bir ifadedir. Daha doğru anlatım: **Qubit, ölçüm yapılana kadar 0 ve 1 sonuçlarına ait olasılık genliklerinin birleşimiyle temsil edilen bir kuantum durumundadır.** Ölçüm yaptığınız anda sistemden klasik bir sonuç alırsınız: 0 ya da 1. ([Microsoft Learn][2])

---

## 2. Klasik bilgisayar ile kuantum bilgisayar arasındaki temel fark

Klasik bilgisayarlar deterministik veya olasılıksal algoritmalarla çalışır. Bellekteki bitler 0/1 değerleridir; işlemcideki kapılar bu bitleri işler; sonuç yine bitlerden oluşur. Kuantum bilgisayarda ise işlem, qubitlerin kuantum durumları üzerinde yapılır. Bu işlem çoğunlukla **kuantum kapıları** ve **kuantum devreleri** ile modellenir. Microsoft dokümantasyonu, kuantum bilgisayarların veriyi kuantum durum vektörünü döndüren kapılarla işlediğini ve bu kapıların klasik mantık kapılarına benzer şekilde devreler halinde birleştirildiğini anlatır. ([Microsoft Learn][3])

Kuantum bilgisayarların gücü “çok sayıda ihtimali aynı anda deneyip cevabı hemen bulması” değildir. Bu, popüler ama yanıltıcı bir anlatımdır. Asıl güç, kuantum durumlarının **girişim** yoluyla doğru cevapların olasılığını artıracak, yanlış cevapların olasılığını azaltacak şekilde tasarlanabilmesidir. IBM, kuantum hesaplamayı anlamak için süperpozisyon, dolaşıklık, decoherence ve interference kavramlarını temel kavramlar olarak verir. ([IBM][4])

Kısaca:

| Klasik bilgisayar                       | Kuantum bilgisayar                            |
| --------------------------------------- | --------------------------------------------- |
| Bit kullanır                            | Qubit kullanır                                |
| Bit değeri 0 veya 1’dir                 | Qubit ölçülmeden önce kuantum durumundadır    |
| Klasik mantık kapıları kullanır         | Kuantum kapıları kullanır                     |
| Çoğu günlük iş için idealdir            | Bazı özel problem türlerinde avantaj hedefler |
| Hata düzeltme olgun ve çok güvenilirdir | Hata düzeltme hâlâ ana araştırma konusudur    |

---

## 3. “Quantum” ne demek?

“Quantum” kelimesi fizikte, bir fiziksel büyüklüğün alabileceği en küçük ayrık miktar fikrine dayanır. Kuantum mekaniği, atomik ve atom altı ölçekte enerjinin, momentumun, spin’in ve benzeri özelliklerin klasik sezgilerimizden farklı davrandığını gösterir. Kuantum bilgi bilimi ise bu fiziksel davranışları bilgi saklama, taşıma ve işleme amacıyla kullanır. NIST, kuantum bilgi bilimini elektronlar, atomlar, ışık parçacıkları ve küçük devreler gibi sistemlerle bilgi işleme alanı olarak açıklar. ([NIST][5])

Bu yüzden kuantum bilgisayar, “çok küçük transistörlü bilgisayar” değildir. Zaten klasik işlemcilerdeki transistörler de çok küçüktür. Kuantum bilgisayarı farklı yapan şey, hesaplama modelinin kuantum durumları üzerine kurulmasıdır.

---

## 4. Qubit nedir?

Qubit, kuantum bilgisayarın temel bilgi birimidir. Klasik bitin 0 veya 1 olmasına karşılık, qubitin durumu genellikle şu şekilde yazılır:

```text
|ψ⟩ = α|0⟩ + β|1⟩
```

Burada `α` ve `β`, olasılık değil, **olasılık genliği**dir. Ölçüm yaptığınızda 0 gelme olasılığı `|α|²`, 1 gelme olasılığı ise `|β|²` ile ilişkilidir. Bu nedenle kuantum programlama doğrudan “değerleri okumak” üzerine değil, durumları kontrollü biçimde dönüştürmek ve sonunda ölçmek üzerine kuruludur. ([arXiv][6])

Qubit fiziksel olarak farklı teknolojilerle üretilebilir. Örneğin süperiletken devreler, hapsedilmiş iyonlar, nötr atomlar, fotonik sistemler ve topolojik qubit yaklaşımları farklı donanım yollarıdır. NIST’in açıklamasına göre kuantum bilgi bilimi, elektronlardan atomlara ve fotonlara kadar farklı fiziksel sistemleri bilgi işleme için kullanır. ([NIST][5])

---

## 5. Süperpozisyon nedir?

Süperpozisyon, bir kuantum sisteminin birden fazla olası durumun lineer kombinasyonu halinde temsil edilebilmesidir. Microsoft’un açıklamasına göre klasik bit 0 veya 1 olabilirken, qubit 0 ve 1’in lineer kombinasyonu olan bir durumda bulunabilir. ([quantum.microsoft.com][7])

Basit sezgi:

```text
Klasik bit:
0 veya 1

Qubit:
ölçümden önce 0 ve 1 sonuçlarına ait genliklerin birleşimi
ölçümden sonra 0 veya 1
```

Ama süperpozisyon “bedava paralel evren hesaplaması” değildir. Çünkü siz ölçüm yaptığınızda tüm ara kuantum durumunu okuyamazsınız; sadece tek bir klasik sonuç alırsınız. Bu nedenle kuantum algoritmanın başarısı, ölçüm öncesi işlemlerin doğru cevabın olasılığını büyütmesine bağlıdır.

---

## 6. Ölçüm neden bu kadar önemli?

Kuantum dünyasında ölçüm pasif bir okuma işlemi gibi düşünülemez. Qubit ölçüldüğünde sistemden klasik bir sonuç elde edilir ve kuantum durumuna dair bilgi büyük ölçüde “çöker”. Microsoft’un eğitim içeriği, qubit ölçüldüğünde her zaman 0 veya 1 sonucu alındığını ve bu sonucun olasılıklarının ölçüm anındaki genliklerle belirlendiğini açıklar. ([Microsoft Learn][2])

Bu yüzden klasik programlamadaki gibi “değişkenin değerini arada bir okuyayım” yaklaşımı kuantum programlamada geçerli değildir. Qubit durumunu ölçtüğünüz anda hesaplamanın kuantum doğasını bozabilirsiniz. Bu, kuantum algoritma tasarımını klasik algoritma tasarımından ciddi biçimde ayırır.

---

## 7. Dolaşıklık / entanglement nedir?

Dolaşıklık, iki veya daha fazla qubitin durumlarının ayrı ayrı değil, tek bir bütün sistem olarak tanımlanmasıdır. Microsoft dokümantasyonu, dolaşık iki qubitin birbirinden bağımsız olarak tanımlanamayacağını ve bir qubitin durumunun diğer qubit ile kuantum korelasyon içinde olduğunu belirtir. ([Microsoft Learn][8])

En meşhur örneklerden biri şu durumdur:

```text
(|00⟩ + |11⟩) / √2
```

Bu durumda iki qubit ölçüldüğünde sonuçlar korelasyon gösterir: ya 00 ya da 11 görürsünüz. Önemli olan, bu korelasyonun klasik “önceden belirlenmiş iki kart” benzetmesinden daha güçlü bir kuantum korelasyon olmasıdır. Ancak bu, ışıktan hızlı haberleşme anlamına gelmez.

Dolaşıklık, kuantum hesaplamanın tek başına garantili hızlandırıcısı değildir; ama kuantum algoritmalar, kuantum teleportation, kuantum iletişim ve kuantum hata düzeltme gibi alanlarda temel bir kaynaktır. Microsoft bunu kuantum bilgi işleme görevleri için kilit kaynaklardan biri olarak açıklar. ([Microsoft Learn][8])

---

## 8. Girişim / interference nedir?

Girişim, kuantum algoritmaların kalbidir. Kuantum durumlarında olasılık genlikleri birbirini güçlendirebilir veya zayıflatabilir. İyi tasarlanmış bir kuantum algoritma, doğru cevaplara giden yolların genliklerini güçlendirmeye, yanlış cevaplara giden yolları ise bastırmaya çalışır. IBM, interference kavramını kuantum hesaplamanın temel ilkelerinden biri olarak sayar. ([IBM][4])

Yalın benzetme:

```text
Yanlış cevapların dalgaları birbirini söndürsün.
Doğru cevabın dalgaları birbirini güçlendirsin.
Son ölçümde doğru cevap daha yüksek olasılıkla gelsin.
```

Bu nedenle kuantum bilgisayarlar “tüm cevapları aynı anda deneyip hepsini bize göstermez”. Bize sadece ölçüm sonucu verir. Algoritmanın mahareti, ölçüm sonucunda doğru cevabın gelme olasılığını yükseltmektir.

---

## 9. Kuantum kapıları ve devre modeli

Kuantum kapıları, qubitlerin kuantum durumlarını dönüştüren işlemlerdir. Hadamard kapısı, Pauli kapıları, faz kapıları, CNOT gibi kontrollü kapılar temel örneklerdir. Microsoft dokümantasyonu, kuantum kapılarını durum vektörü üzerinde dönüşümler olarak açıklar ve çok-qubitli sistemlerde kontrollü kapıların önemini anlatır. ([Microsoft Learn][3])

Basit bir kuantum devresi şu mantıkla düşünülebilir:

```text
1. Qubitleri başlangıç durumuna getir.
2. Süperpozisyon oluştur.
3. Qubitleri dolaşık hale getir.
4. Kuantum kapılarıyla girişim etkisi oluştur.
5. Ölçüm yap.
6. Gerekirse klasik post-processing uygula.
```

Kuantum programlama genellikle hibrit ilerler: kuantum işlemci belirli alt problemi çözer, klasik bilgisayar ise hazırlık, parametre optimizasyonu, hata yönetimi ve sonuç yorumlama gibi işleri yapar.

---

## 10. Kuantum bilgisayarlar neden zor?

Çünkü qubitler son derece hassastır. Çevreyle en küçük etkileşim bile kuantum durumunu bozabilir. Bu bozulmaya genel olarak **decoherence** denir. IBM, decoherence kavramını kuantum hesaplamayı anlamak için temel kavramlar arasında verir. ([IBM][4])

Klasik bilgisayarlarda bitler çok kararlıdır. Bir transistörün 0 mı 1 mi olduğunu güvenilir şekilde okuyabilirsiniz. Kuantum bilgisayarda ise qubit hem hassastır hem de doğrudan kopyalanamaz; ayrıca ölçüm kuantum durumunu etkiler. Bu yüzden kuantum hata düzeltme, alanın en büyük teknik problemlerinden biridir.

Nature’ın kuantum hata düzeltme özetlerinde de vurgulandığı gibi, pratik öneme sahip problemleri çözmek için kuantum bilgisayarların büyük olasılıkla quantum error correction kullanması gerekir; bu da bir mantıksal qubit’i çok sayıda fiziksel qubit üzerine yedekli olarak kodlamayı gerektirir. ([Nature][9])

---

## 11. Fiziksel qubit ve mantıksal qubit farkı

Bu ayrım çok önemlidir:

**Fiziksel qubit**, laboratuvarda gerçekten kontrol edilen qubit’tir. Süperiletken devre, iyon, atom veya foton olabilir.

**Mantıksal qubit**, hata düzeltme sayesinde birçok fiziksel qubitin birlikte daha güvenilir tek bir qubit gibi davranmasıdır.

Bugünkü kuantum bilgisayar haberlerinde genellikle fiziksel qubit sayısı duyurulur. Ama pratik, büyük ölçekli, hataya dayanıklı kuantum hesaplama için asıl önemli olan mantıksal qubit sayısı, hata oranı, gate kalitesi ve hesaplama süresidir. IBM’in 2025 yol haritası, 2029 için 200 mantıksal qubit ve 100 milyon quantum gate çalıştırabilecek fault-tolerant sistem hedefinden bahseder; bu, alanın fiziksel qubit sayısından mantıksal ve güvenilir hesaplamaya doğru kaydığını gösterir. ([IBM][10])

---

## 12. NISQ dönemi nedir?

NISQ, “Noisy Intermediate-Scale Quantum” anlamına gelir. Bugünkü kuantum cihazların çoğu bu döneme aittir: belirli sayıda qubit vardır, fakat qubitler gürültülüdür ve hata düzeltme tam anlamıyla olgunlaşmamıştır. Bu nedenle bugün kuantum bilgisayarlar çok önemli araştırma araçlarıdır, ama genel amaçlı klasik bilgisayarların yerini alabilecek üretim makineleri değildir.

Bu dönem, deney yapmak, algoritma geliştirmek, hata düzeltme tekniklerini test etmek ve donanım mimarilerini olgunlaştırmak açısından kritiktir. Google Willow çalışması gibi gelişmelerin önemi de burada ortaya çıkar: Willow, hata düzeltme ölçeği büyüdükçe mantıksal hata oranının düşürülebildiğini gösteren önemli bir adım olarak sunuldu. Google’ın kendi araştırma blogu bunu, error-corrected qubitlerin büyüdükçe daha iyi hale geldiği ilk işlemci olarak duyurdu; Nature makalesi de Willow üzerinde surface code threshold altında hata düzeltme sonuçlarını raporladı. ([Google Research][11])

---

## 13. Başlıca kuantum bilgisayar donanım yaklaşımları

### 13.1 Süperiletken qubitler

Google ve IBM gibi kurumların önemli çalışmalarında süperiletken qubitler kullanılır. Bu sistemler çok düşük sıcaklıklarda çalışır. IBM’in donanım sayfası, kuantum işlemcilerin mutlak sıfırın çok az üzerinde sıcaklıklara soğutulması gerektiğini ve bunun için karmaşık cryostat sistemleri kullanıldığını açıklar. ([IBM][12])

Avantajları: hızlı kapılar, güçlü endüstri yatırımı, gelişmiş üretim altyapısı.
Zorlukları: decoherence, kablolama, soğutma, hata düzeltme overhead’i.

### 13.2 Hapsedilmiş iyonlar

Hapsedilmiş iyon sistemlerinde qubitler elektrik alanlarıyla hapsedilen iyonlar üzerinde temsil edilir. Bu mimari yüksek doğruluklu işlemlerle bilinir, ancak ölçekleme ve işlem hızı gibi farklı zorlukları vardır. Son yıllarda iyon tabanlı sistemlerde çok düşük tek-qubit hata oranları gibi önemli deneysel sonuçlar bildirilmiştir, fakat çok-qubitli işlemler hâlâ daha zorlu bir alandır. ([Live Science][13])

### 13.3 Nötr atomlar

Nötr atom sistemleri, lazerlerle tutulan ve düzenlenen atomları kullanır. 2025’te Nature’da yayımlanan çalışmalar, nötr atom mimarilerinde fault-tolerant quantum computation için önemli ilerlemeler olduğunu gösterdi. ([Nature][14])

Nötr atomların cazibesi, çok sayıda atomu düzenleyebilme ve esnek bağlantı yapıları kurabilme potansiyelidir. Ancak kapı doğruluğu, kontrol kararlılığı ve hata düzeltme entegrasyonu hâlâ aktif araştırma alanlarıdır.

### 13.4 Fotonik kuantum bilgisayarlar

Fotonik yaklaşımda bilgi ışık parçacıklarıyla taşınır. Oda sıcaklığına daha yakın çalışma ve iletişimle doğal uyum gibi avantajları olabilir. Buna karşılık yüksek kaliteli kaynaklar, kayıp yönetimi ve ölçeklenebilir gate uygulamaları önemli zorluklardır.

### 13.5 Topolojik qubitler

Topolojik qubitler, teorik olarak hatalara daha dayanıklı qubitler üretmeyi hedefler. Microsoft, Majorana 1 işlemcisini topolojik qubit mimarisi ve “topoconductor” malzeme yaklaşımıyla duyurdu. Ancak Nature’da yayımlanan analizler ve bilimsel tartışmalar, Microsoft’un iddiasının bazı yönlerinde ihtiyatlı olunması gerektiğini belirtiyor; özellikle Majorana kanıtlarının yorumu konusunda akademik tartışma devam ediyor. ([Source][15])

### 13.6 Quantum annealing

D-Wave’in bilinen yaklaşımı gate-based evrensel kuantum bilgisayardan farklı olan **quantum annealing** modelidir. Bu model özellikle optimizasyon problemlerine odaklanır. D-Wave, annealing yaklaşımını optimizasyon ölçeği ve hibrit çözümler açısından konumlandırır; ancak bu modeli genel amaçlı gate-based kuantum bilgisayarlarla birebir aynı kategoriye koymak doğru değildir. ([dwavequantum.com][16])

---

## 14. Kuantum algoritmalar ne işe yarar?

Kuantum bilgisayarların her işi hızlandıracağı doğru değildir. Kuantum avantaj, belirli matematiksel yapılara sahip problem sınıflarında beklenir.

### 14.1 Shor algoritması

Shor algoritması, büyük sayıların çarpanlara ayrılması ve ayrık logaritma gibi problemler için teorik olarak çok önemlidir. Bu yüzden RSA ve eliptik eğri kriptografisi gibi yaygın açık anahtarlı kripto sistemleri açısından kritik kabul edilir. NIST, gelecekte yeterince güçlü kuantum bilgisayarların bugünkü bazı kriptografik savunmaları kırabileceğini ve bu nedenle post-quantum cryptography standartlarına ihtiyaç duyulduğunu açıklar. ([NIST][17])

Fakat bugünkü kuantum bilgisayarlar RSA’yı pratik ölçekte kıracak seviyede değildir. Örneğin Google Willow gibi duyurular kriptografiyi bugün kırma anlamına gelmez; bu makineler hâlâ çok daha büyük, hataya dayanıklı sistemlere ihtiyaç duyar. ([The Verge][18])

### 14.2 Grover algoritması

Grover algoritması, yapılandırılmamış arama problemlerinde karekök düzeyinde hızlanma sağlar. Yani N elemanlı bir aramada klasik kaba kuvvet yaklaşımı O(N) iken, Grover yaklaşımı ideal koşullarda O(√N) sorgu düzeyine iner. Qiskit’in Grover eğitim içeriği, oracle ve amplitude amplification kavramları üzerinden algoritmanın iyi çözüm olasılığını artırma mantığını açıklar. ([IBM Quantum][19])

Bu çok değerlidir, fakat “her şeyi üstel hızlandırır” anlamına gelmez. Grover önemli ama sınırlı bir hızlanma sağlar.

### 14.3 Kuantum simülasyon

Kuantum bilgisayarların en doğal kullanım alanlarından biri kuantum sistemlerini simüle etmektir. Richard Feynman’ın meşhur sezgisi de buradan gelir: Doğanın kendisi kuantum ise, kuantum sistemleri klasik bilgisayarla simüle etmek çok zor olabilir; kuantum sistemleri kuantum cihazlarla simüle etmek daha doğal olabilir. Microsoft’un Azure Quantum dokümantasyonu da Feynman ve Manin’in kuantum sistemleri simüle etmek için kuantum temelli donanım fikrine işaret ettiğini anlatır. ([Microsoft Learn][20])

Potansiyel uygulamalar: yeni malzemeler, katalizörler, batarya kimyası, ilaç keşfi, moleküler simülasyon.

### 14.4 VQE, QAOA ve hibrit algoritmalar

NISQ döneminde VQE ve QAOA gibi hibrit algoritmalar öne çıkar. Bunlarda kuantum bilgisayar bir parçayı hesaplar; klasik bilgisayar parametreleri optimize eder. Bu yaklaşım, mevcut gürültülü cihazlarla deney yapmayı mümkün kılar. Ancak bu algoritmaların geniş ölçekte klasik yöntemleri net biçimde yendiği uygulamalar hâlâ sınırlıdır.

### 14.5 Quantum Machine Learning

Quantum Machine Learning çok ilgi çekici ama çok erken aşamadadır. Literatürde potansiyel hızlanmalar, kuantum kernel yöntemleri ve hibrit modeller tartışılsa da güncel çalışmalar donanım gürültüsü, qubit sayısı, veri yükleme maliyeti ve ölçeklenebilirlik gibi ciddi sınırlamalara dikkat çeker. 2026 tarihli bir inceleme de QML’nin henüz olgunlaşmadığını ve donanım sınırlamalarıyla kısıtlandığını vurgular. ([Springer][21])

---

## 15. Kuantum bilgisayarlar bugün ne durumda? — Mayıs 2026 resmi

2026 itibarıyla kuantum bilgisayarlar ciddi bir araştırma ve mühendislik ivmesine sahip, ancak hâlâ genel amaçlı, hataya dayanıklı, geniş üretim kullanımı olan makineler değildir. En büyük teknik darboğazlar qubit kalitesi, hata oranları, decoherence, hata düzeltme overhead’i, ölçeklenebilir kontrol sistemleri ve ekonomik faydanın gösterilmesidir. Nature ve büyük teknoloji şirketlerinin yayımladığı güncel çalışmalar, alanın odağının artık sadece “daha çok fiziksel qubit” değil, “daha güvenilir mantıksal qubit ve hata düzeltmeli hesaplama” olduğunu gösteriyor. ([Nature][9])

Google’ın Willow duyurusu önemlidir çünkü hata düzeltme ölçeği büyüdükçe mantıksal hata oranının düşürülebildiğine dair güçlü bir deneysel gösterim sundu. IBM, 2029 için Starling adlı fault-tolerant kuantum bilgisayar hedefini ve 2033+ için daha büyük Blue Jay hedefini açıkladı. Microsoft ise Majorana 1 ile topolojik qubit yolunda iddialı bir yaklaşım sundu, ancak bu konuda bilimsel ihtiyat devam ediyor. ([Google Research][11])

---

## 16. Kriptografi açısından neden önemli?

Kuantum bilgisayarların en somut stratejik etkilerinden biri kriptografidir. Yeterince büyük ve hataya dayanıklı bir kuantum bilgisayar, bugün yaygın kullanılan bazı açık anahtarlı kripto sistemlerini kırabilecek algoritmaları çalıştırabilir. Bu nedenle NIST, 2024’te ilk üç post-quantum cryptography standardını yayımladı ve kurumların kuantuma dayanıklı kriptografiye geçiş yapabilmesi için standartlaşma sürecini yürütüyor. ([NIST][22])

Burada önemli ayrım:

```text
Quantum cryptography:
Kuantum fiziğini kullanarak güvenli iletişim teknikleri geliştirme alanı.

Post-quantum cryptography:
Klasik bilgisayarlarda çalışan ama kuantum saldırılarına dayanıklı olması hedeflenen kriptografik algoritmalar.
```

Bugün kurumların pratikte ilgilenmesi gereken konu çoğunlukla **post-quantum cryptography migration**dır. Özellikle uzun süre gizli kalması gereken veriler için “store now, decrypt later” riski önemlidir: saldırgan bugün şifreli veriyi saklayıp gelecekte güçlü kuantum bilgisayarlar ortaya çıktığında çözmeyi hedefleyebilir. NIST’in PQC çalışmaları bu nedenle bugünden geçiş planı yapılmasını teşvik eder. ([NIST Publications][23])

---

## 17. Kuantum bilgisayarlar hangi alanlarda faydalı olabilir?

### 17.1 Kimya ve malzeme bilimi

Kuantum bilgisayarların en doğal aday kullanım alanı molekül ve malzeme simülasyonudur. Çünkü moleküllerin davranışı zaten kuantum mekaniğiyle açıklanır. Klasik bilgisayarlar büyük kuantum sistemlerini simüle ederken hızla zorlanır. Azure Quantum dokümantasyonu da kuantum sistemlerinin klasik bilgisayarlarla zor veya imkânsız simüle edilebileceğini ve bu nedenle kuantum donanım fikrinin ortaya çıktığını anlatır. ([Microsoft Learn][20])

### 17.2 Optimizasyon

Rota planlama, portföy optimizasyonu, tedarik zinciri, çizelgeleme ve kaynak atama gibi problemler kuantum optimizasyon çalışmalarında sık geçer. Ancak burada beklenti dikkatli kurulmalıdır: Her optimizasyon problemi kuantum bilgisayarda otomatik olarak daha hızlı çözülmez. Problem formülasyonu, donanım, hata oranı ve klasik alternatiflerin gücü belirleyicidir.

### 17.3 Kriptografi ve güvenlik

Kuantum bilgisayarlar bazı mevcut kripto sistemleri için tehdit oluştururken, PQC de bu tehdide karşı yeni standartlar getirir. NIST’in 2024’te yayımladığı standartlar bu alanın artık akademik tartışmadan çıkıp gerçek geçiş planlamasına dönüştüğünü gösterir. ([NIST][22])

### 17.4 Finans

Risk analizi, portföy optimizasyonu, Monte Carlo benzeri hesaplamalar ve dolandırıcılık tespiti gibi alanlarda deneysel çalışmalar vardır. Ancak bunların çoğu hâlâ araştırma, prototip veya uzun vadeli potansiyel aşamasındadır. Örneğin Lloyds ve IBM’in finansal dolandırıcılık alanındaki deneysel çalışması, kuantum tekniklerin mevcut AI/ML yaklaşımlarını hemen değiştirmekten çok gelecekte tamamlayıcı özellik üretme potansiyelini araştırmıştır. ([IT Pro][24])

### 17.5 Yapay zekâ

Kuantum makine öğrenmesi potansiyel taşır, fakat bugünkü AI iş yükleri için GPU’ların yerine kuantum bilgisayarların geçeceğini söylemek doğru değildir. QML hâlâ donanım gürültüsü, veri kodlama ve ölçeklenebilirlik sorunlarıyla boğuşan erken aşama bir alandır. ([Springer][21])

---

## 18. Yanlış bilinenler

### Yanlış 1: “Kuantum bilgisayar her şeyi hızlandırır.”

Hayır. Kuantum bilgisayarlar özel problem sınıflarında avantaj sağlayabilir. Web gezme, e-posta, ERP, klasik veritabanı sorguları, video render veya standart backend servisleri gibi işlerde kuantum bilgisayar beklenen genel çözüm değildir.

### Yanlış 2: “Qubit aynı anda hem 0 hem 1 olduğu için tüm cevaplar hesaplanır.”

Eksik ve yanıltıcı. Süperpozisyon vardır, ama ölçümde tek sonuç alınır. Algoritmanın gücü, girişim yoluyla doğru sonucun olasılığını artırmaktır. ([IBM Quantum][25])

### Yanlış 3: “Kuantum bilgisayarlar bugün RSA’yı kırıyor.”

Hayır. Bugünkü cihazlar bunun için yeterli ölçek ve hata dayanıklılığında değildir. Yine de PQC’ye geçiş bugünden planlanmalıdır, çünkü standartların uygulanması ve ekosistem geçişi uzun sürebilir. ([The Verge][18])

### Yanlış 4: “Daha çok qubit = daha iyi kuantum bilgisayar.”

Tek başına hayır. Qubit kalitesi, hata oranı, bağlantı yapısı, gate süresi, coherence süresi, hata düzeltme kapasitesi ve mantıksal qubit sayısı daha anlamlı metriklerdir. IBM’in roadmap anlatısı da fiziksel qubit sayısından fault-tolerant ve mantıksal qubit hedeflerine geçişi vurgular. ([IBM][10])

---

## 19. Bir yazılımcı nasıl düşünmeli?

Kuantum programlamayı klasik programlamanın devamı gibi değil, yeni bir hesaplama modeli gibi düşünmek gerekir.

Klasik programlama refleksi:

```text
Veriyi oku.
Koşula bak.
Döngü kur.
Değişkeni güncelle.
Sonucu yaz.
```

Kuantum programlama refleksi:

```text
Qubitleri hazırla.
Süperpozisyon oluştur.
Dolaşıklık kur.
Kapılarla genlikleri dönüştür.
Girişimi doğru cevabı güçlendirecek şekilde tasarla.
Ölç.
Klasik bilgisayarda sonucu yorumla.
```

Bu yüzden bir .NET, Python veya JavaScript geliştiricisi için kuantum programlama öğrenirken en zor kısım syntax değil, **hesaplama sezgisinin değişmesidir**.

---

## 20. Öğrenmek için en iyi kaynak seti

Benim doğruladığım kaynaklara göre en iyi yol şu:

### 1. En yalın başlangıç: NIST Quantum Computing Explained

NIST’in açıklaması sade, güvenilir ve kavramları abartmadan anlatıyor. Özellikle qubit, entanglement, quantum operation ve quantum computer’ın neden farklı olduğu konusunda iyi bir giriş sağlar. ([NIST][1])

### 2. En iyi uygulamalı öğrenme: IBM Quantum Learning / Qiskit

IBM Quantum Learning, qubit, süperpozisyon, dolaşıklık ve interference kavramlarını eğitim modülleriyle anlatır. Qiskit tarafı ise gerçek devreler kurarak öğrenmek için iyi bir ekosistemdir. ([IBM Quantum][25])

### 3. Microsoft ekosistemi için: Azure Quantum ve Q#

Microsoft dokümantasyonu, Q#, Azure Quantum, qubit kavramı, entanglement ve quantum circuit mantığını düzenli biçimde açıklar. Özellikle yazılımcı bakışıyla ilerlemek isteyenler için faydalıdır. ([Microsoft Learn][26])

### 4. Güncel alan takibi için: Google Quantum AI, IBM Roadmap, Nature

Google Willow, IBM fault-tolerant roadmap ve Nature’daki hata düzeltme çalışmaları alanın teknik yönünü takip etmek için önemlidir. Ancak bunlar başlangıç kaynağı değil, daha çok alanın “nereye gidiyor?” sorusuna cevap veren kaynaklardır. ([Google Research][11])

---

## 21. 10 günlük öğrenme planı

### Gün 1 — Büyük resim

Amaç: Kuantum bilgisayar klasik bilgisayardan neden farklı?
Okuma: NIST Quantum Computing Explained.
Çıktı: Bit, qubit, ölçüm, süperpozisyon kavramlarını 5 cümleyle açıklayabilmek.

### Gün 2 — Qubit matematiği

Amaç: `α|0⟩ + β|1⟩` ifadesinden korkmamak.
Çıktı: Olasılık genliği ile olasılık arasındaki farkı anlamak.

### Gün 3 — Süperpozisyon ve ölçüm

Amaç: “Aynı anda 0 ve 1” klişesinin neden eksik olduğunu anlamak.
Çıktı: Ölçümün neden hesaplamayı etkilediğini açıklayabilmek.

### Gün 4 — Entanglement

Amaç: Dolaşıklığın klasik korelasyondan farkını öğrenmek.
Çıktı: Bell state mantığını basitçe anlatabilmek.

### Gün 5 — Quantum gates

Amaç: Hadamard, X, Z, CNOT gibi temel kapıları tanımak.
Çıktı: Basit bir devrede Hadamard + CNOT ile dolaşıklık oluşturmayı anlamak.

### Gün 6 — Interference

Amaç: Kuantum algoritmaların neden sadece paralellik olmadığını görmek.
Çıktı: Doğru cevabın olasılığını artırma fikrini açıklayabilmek.

### Gün 7 — Grover algoritması

Amaç: Oracle ve amplitude amplification kavramlarını öğrenmek.
Çıktı: Grover’ın neden karekök hızlanma sağladığını sezgisel açıklayabilmek.

### Gün 8 — Shor ve kriptografi

Amaç: Kuantum bilgisayarların kriptografi açısından önemini anlamak.
Çıktı: PQC ile quantum cryptography farkını açıklayabilmek.

### Gün 9 — Donanım yaklaşımları

Amaç: Süperiletken, iyon, nötr atom, fotonik, topolojik ve annealing yaklaşımlarını ayırmak.
Çıktı: “Qubit sayısı tek başına yeterli metrik değildir” diyebilmek.

### Gün 10 — Güncel durum

Amaç: Alanın gerçekçi olgunluk seviyesini anlamak.
Çıktı: NISQ, logical qubit, error correction ve fault tolerance kavramlarını bağlamak.

---

## 22. Kısa sözlük

**Bit:** Klasik bilgisayarın 0/1 bilgi birimi.

**Qubit:** Kuantum bilgisayarın temel bilgi birimi.

**Süperpozisyon:** Qubitin ölçümden önce 0 ve 1 sonuçlarına ait genliklerin birleşimiyle temsil edilmesi.

**Ölçüm:** Kuantum durumundan klasik sonuç alma işlemi.

**Entanglement / dolaşıklık:** Birden fazla qubitin ayrı ayrı değil, bütün sistem olarak tanımlanması.

**Interference / girişim:** Olasılık genliklerinin birbirini güçlendirmesi veya zayıflatması.

**Quantum gate:** Qubit durumunu dönüştüren işlem.

**Quantum circuit:** Kuantum kapılarının sıralı gösterimi.

**Decoherence:** Qubitin çevreyle etkileşerek kuantum özelliğini kaybetmesi.

**Physical qubit:** Donanımda gerçekten kontrol edilen qubit.

**Logical qubit:** Hata düzeltme ile birçok fiziksel qubitin birlikte oluşturduğu daha güvenilir qubit.

**Quantum error correction:** Qubit hatalarını tespit edip düzeltmeye yönelik yöntemler.

**NISQ:** Gürültülü, orta ölçekli mevcut kuantum cihazlar dönemi.

**Fault-tolerant quantum computer:** Hatalara rağmen uzun ve güvenilir kuantum hesaplama yapabilen sistem.

**PQC / Post-Quantum Cryptography:** Klasik bilgisayarlarda çalışan ama kuantum saldırılarına dayanıklı olması hedeflenen kriptografi.

---

## 23. En kısa özet

Kuantum bilgisayarlar, klasik bilgisayarların yerini alacak “daha hızlı bilgisayarlar” değildir. Onlar, kuantum mekaniğinin kurallarını kullanarak belirli problem türlerinde klasik bilgisayarlardan farklı ve potansiyel olarak çok daha güçlü hesaplama yapmayı hedefleyen özel makinelerdir. Bugün alan çok hızlı ilerliyor; özellikle hata düzeltme, mantıksal qubitler ve fault-tolerant mimariler kritik eşik olarak görülüyor. Fakat hâlâ pratik, genel amaçlı ve geniş üretim kullanımına hazır değiller. En somut kısa-orta vadeli etki alanlarından biri kriptografi geçişidir; bu yüzden NIST’in PQC standartları ve kurumların kripto envanteri / geçiş planları şimdiden önemlidir. ([NIST][22])

[1]: https://www.nist.gov/quantum-information-science/quantum-computing-explained?utm_source=chatgpt.com "Quantum Computing Explained | NIST"
[2]: https://learn.microsoft.com/en-us/azure/quantum/tutorial-qdk-explore-entanglement?utm_source=chatgpt.com "Tutorial: Quantum Entanglement with Q - Azure"
[3]: https://learn.microsoft.com/en-us/azure/quantum/concepts-the-qubit?utm_source=chatgpt.com "The Qubit in Quantum Computing"
[4]: https://www.ibm.com/think/topics/quantum-computing?utm_source=chatgpt.com "What Is Quantum Computing?"
[5]: https://www.nist.gov/quantum-information-science?utm_source=chatgpt.com "Quantum information science | NIST"
[6]: https://arxiv.org/pdf/1804.03719?utm_source=chatgpt.com "Quantum Algorithm Implementations for Beginners"
[7]: https://quantum.microsoft.com/en-us/insights/education/concepts/superposition?utm_source=chatgpt.com "Microsoft Quantum | Superposition"
[8]: https://learn.microsoft.com/en-us/azure/quantum/concepts-entanglement?utm_source=chatgpt.com "Entanglement & Correlations - Azure Quantum"
[9]: https://www.nature.com/nature-index/topics/l4/quantum-error-correction-in-quantum-computing-systems?utm_source=chatgpt.com "Quantum Error Correction in Quantum Computing Systems"
[10]: https://www.ibm.com/quantum/blog/large-scale-ftqc?utm_source=chatgpt.com "IBM lays out clear path to fault-tolerant quantum computing"
[11]: https://research.google/blog/making-quantum-error-correction-work/?utm_source=chatgpt.com "Making quantum error correction work"
[12]: https://www.ibm.com/quantum/hardware?utm_source=chatgpt.com "IBM Quantum Computing | Hardware and roadmap"
[13]: https://www.livescience.com/technology/computing/scientists-hit-quantum-computer-error-rate-of-0-000015-percent-a-world-record-achievement-that-could-lead-to-smaller-and-faster-machines?utm_source=chatgpt.com "Scientists hit quantum computer error rate of 0.000015% - a world record achievement that could lead to smaller and faster machines"
[14]: https://www.nature.com/articles/s41586-025-09848-5?utm_source=chatgpt.com "A fault-tolerant neutral-atom architecture for universal ..."
[15]: https://news.microsoft.com/source/features/innovation/microsofts-majorana-1-chip-carves-new-path-for-quantum-computing/?utm_source=chatgpt.com "Microsoft's Majorana 1 chip carves new path for quantum ..."
[16]: https://www.dwavequantum.com/learn/d-wave-s-approach/?utm_source=chatgpt.com "D-Wave's Approach to Quantum Computing"
[17]: https://www.nist.gov/cybersecurity-and-privacy/what-post-quantum-cryptography?utm_source=chatgpt.com "What Is Post-Quantum Cryptography? | NIST"
[18]: https://www.theverge.com/2024/12/12/24319879/google-willow-cant-break-rsa-cryptography?utm_source=chatgpt.com "Google says its breakthrough quantum chip can't break modern cryptography"
[19]: https://quantum.cloud.ibm.com/learning/modules/computer-science/grovers?utm_source=chatgpt.com "Grover's algorithm | IBM Quantum Learning"
[20]: https://learn.microsoft.com/en-us/azure/quantum/overview-understanding-quantum-computing?utm_source=chatgpt.com "What Is Quantum Computing? - Azure Quantum"
[21]: https://link.springer.com/article/10.1007/s10791-026-10085-1?utm_source=chatgpt.com "A review of quantum machine learning algorithms ..."
[22]: https://www.nist.gov/news-events/news/2024/08/nist-releases-first-3-finalized-post-quantum-encryption-standards?utm_source=chatgpt.com "NIST Releases First 3 Finalized Post-Quantum Encryption ..."
[23]: https://nvlpubs.nist.gov/nistpubs/ir/2024/NIST.IR.8547.ipd.pdf?utm_source=chatgpt.com "NIST IR 8547 initial public draft, Transition to Post-Quantum ..."
[24]: https://www.itpro.com/technology/lloyds-bank-touts-quantum-potential-in-anti-fraud-activities?utm_source=chatgpt.com "Lloyds Bank touts quantum potential in anti-fraud activities"
[25]: https://quantum.cloud.ibm.com/learning/en/courses/quantum-business-foundations/quantum-computing-fundamentals?utm_source=chatgpt.com "quantum Computing fundamentals | IBM Quantum Learning"
[26]: https://learn.microsoft.com/en-us/azure/quantum/?utm_source=chatgpt.com "Microsoft Quantum documentation - Azure"
