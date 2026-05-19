+++
title = "2. Klasik Bilgisayardan Kuantum Bilgisayara"
description = "Klasik bilgisayarın nasıl çalıştığı, sınırları ve kuantum hesaplamanın neden farklı bir model sunduğu."
date = "2026-05-18T00:00:00+03:00"
weight = 2
type = "guide"
draft = false
+++

> Bu bölümün amacı, kuantum bilgisayarları doğrudan "gizemli fizik" kavramlarıyla değil, önce bildiğimiz klasik bilgisayar modeliyle karşılaştırarak anlamaktır. Kuantum bilgisayarları doğru konumlandırabilmek için önce klasik bilgisayarların nasıl çalıştığını, nerelerde çok güçlü olduklarını, nerelerde zorlandıklarını ve kuantum hesaplama modelinin bu tabloya nasıl farklı bir yaklaşım getirdiğini görmek gerekir.

---

## 2.1. Klasik bilgisayar nasıl düşünür?

Klasik bilgisayarlar temelde **kesin, ayrık ve denetlenebilir durumlar** üzerinde çalışır. Bellekte saklanan bilgi bitlerden oluşur. Bir bit, belirli bir anda 0 ya da 1 değerindedir. Bu değerler fiziksel dünyada elektriksel gerilim seviyeleri, manyetik durumlar, yük varlığı/yokluğu veya başka kararlı fiziksel durumlarla temsil edilebilir.

Bir klasik bilgisayarı çok basitleştirerek şöyle düşünebiliriz:

```text
Girdi alır.
Girdiyi bellekte bitler halinde temsil eder.
İşlemci, bu bitler üzerinde mantıksal ve aritmetik işlemler yapar.
Ara sonuçları yine bitler halinde saklar.
Sonucu çıktı olarak üretir.
```

Bu modelin en önemli özelliği, bilgisayarın iç durumunun prensipte okunabilir, kopyalanabilir ve tekrar üretilebilir olmasıdır. Elinizde aynı program, aynı girdi ve aynı çalışma koşulları varsa, klasik bir bilgisayardan aynı sonucu beklemek doğaldır. Elbette modern sistemlerde paralellik, önbellek, işletim sistemi zamanlaması, dağıtık çalışma ve donanım hataları gibi birçok karmaşıklık vardır; ama temel hesaplama modeli hâlâ klasik bitler ve bu bitler üzerinde çalışan mantıksal işlemler üzerine kuruludur.

Klasik bilgisayarın "düşünme" biçimi çoğunlukla şu kalıplara dayanır:

- Durumu sakla.
- Durumu oku.
- Koşula göre karar ver.
- Döngüyle tekrar et.
- Değeri değiştir.
- Sonucu üret.

Bir yazılımcı açısından bu model çok tanıdıktır:

```csharp
if (amount > limit)
{
    ApproveManually();
}
else
{
    ApproveAutomatically();
}
```

Burada `amount` ve `limit` değerleri okunur, karşılaştırılır ve sonuca göre bir dal seçilir. Bu basit örneğin arkasında işlemci seviyesinde bitler, register'lar, mantık kapıları ve makine komutları vardır.

Klasik bilgisayarlar bu tarz sembolik, deterministik ve adım adım yürütülen işlemlerde son derece başarılıdır. Muhasebe sistemleri, web uygulamaları, veritabanları, işletim sistemleri, derleyiciler, oyun motorları, grafik işlemciler ve yapay zekâ modellerinin büyük kısmı bu klasik hesaplama modeli üzerine inşa edilmiştir.

Kuantum bilgisayarları anlamaya çalışırken ilk önemli nokta şudur: Kuantum bilgisayarlar klasik bilgisayarların yaptığı bu genel işleri daha hızlı yapmak için tasarlanmış doğrudan bir ikame değildir. Onlar farklı bir hesaplama modeli kullanır.

---

## 2.2. Bit, transistor ve mantık kapıları

Klasik bilgisayarların en küçük bilgi birimi **bit**tir. Bit, iki olası değerden birini temsil eder:

```text
0 veya 1
```

Bu iki değer, soyut matematiksel değerlerdir. Fiziksel donanımda ise bu değerleri temsil etmek için kararlı durumlara ihtiyaç vardır. Modern bilgisayarlarda bu işin temel yapı taşlarından biri **transistor**dür.

Transistor, çok basitleştirilmiş haliyle elektronik bir anahtar gibi düşünülebilir. Akımın geçmesine izin verebilir ya da engelleyebilir. Bu iki durum, sayısal devrelerde 0 ve 1 değerlerini temsil etmek için kullanılır.

```text
Transistor kapalı  -> 0
Transistor açık    -> 1
```

Gerçek donanım seviyesinde durum bu kadar basit değildir; gerilim eşikleri, sızıntı akımları, ısı, üretim teknolojisi, saat frekansı, güç tüketimi ve sinyal bütünlüğü gibi birçok mühendislik detayı vardır. Ancak soyutlama açısından transistorlar, bitleri işleyen mantık kapılarının fiziksel temelini oluşturur.

Mantık kapıları, bitler üzerinde temel işlemler yapar:

| Kapı | Anlamı | Örnek |
|---|---|---|
| NOT | Değeri tersine çevirir | 0 → 1, 1 → 0 |
| AND | İki değer de 1 ise 1 üretir | 1 AND 1 = 1 |
| OR | En az bir değer 1 ise 1 üretir | 1 OR 0 = 1 |
| XOR | Değerler farklıysa 1 üretir | 1 XOR 0 = 1 |
| NAND | AND sonucunun tersidir | 1 NAND 1 = 0 |

Bu kapılar tek başlarına basit görünür; fakat milyarlarca transistor ve çok büyük sayıda mantık kapısı bir araya geldiğinde modern işlemciler ortaya çıkar. İşlemciler aritmetik işlemler, karşılaştırmalar, bellek erişimleri, dallanmalar ve vektör işlemleri gibi daha karmaşık davranışları bu temel yapı taşları üzerinden gerçekleştirir.

Bir klasik işlemcideki komutlar da nihayetinde bitler üzerinde yapılan kontrollü dönüşümlerdir:

```text
Topla
Çıkar
Karşılaştır
Bellekten oku
Belleğe yaz
Koşullu dallan
```

Klasik bilgisayarın gücü, bu basit işlemleri inanılmaz hızda, yüksek güvenilirlikle ve büyük ölçekli mühendislik altyapısıyla gerçekleştirebilmesinden gelir.

Bugünkü klasik bilgisayarlar sadece CPU'lardan ibaret değildir. GPU'lar, TPU'lar, FPGA'ler, ASIC'ler, ağ hızlandırıcıları ve özel yapay zekâ çipleri de klasik hesaplama ailesinin parçasıdır. Bunlar farklı mimarilere sahip olabilir; ama yine de bilgiyi klasik bitler halinde temsil eder ve klasik hesaplama kurallarıyla işler.

---

## 2.3. Klasik hesaplamanın güçlü ve zayıf yönleri

Klasik bilgisayarlar, modern teknolojinin temel taşıdır. Bugünkü yazılım dünyasının neredeyse tamamı klasik hesaplama modeli üzerine kuruludur. Bu nedenle kuantum bilgisayarları anlatırken klasik bilgisayarları küçümsemek ciddi bir hata olur.

Klasik hesaplamanın en güçlü olduğu alanlar şunlardır:

### 2.3.1. Genel amaçlı işlem gücü

Klasik bilgisayarlar çok geniş bir problem yelpazesinde kullanılabilir. Web uygulaması çalıştırmak, dosya sistemi yönetmek, video oynatmak, derleme yapmak, veritabanı sorgusu çalıştırmak, e-posta göndermek, oyun çalıştırmak, görsel işlemek veya makine öğrenmesi modeli eğitmek klasik bilgisayarların güçlü olduğu alanlardır.

### 2.3.2. Güvenilirlik ve hata yönetimi

Klasik bilgisayarlarda bitler oldukça kararlı biçimde saklanabilir. Bellek hataları, disk bozulmaları veya ağ paket kayıpları gibi sorunlar elbette vardır; ancak bunlar için gelişmiş hata tespit ve hata düzeltme yöntemleri uzun süredir kullanılmaktadır.

Örneğin:

- ECC bellek,
- checksum,
- RAID,
- transaction log,
- retry mekanizmaları,
- distributed consensus protokolleri,
- hata toleranslı veri merkezleri,
- yedekleme ve felaket kurtarma stratejileri.

Kuantum bilgisayarlarda ise hata problemi çok daha temel ve zordur. Qubitler çevreyle etkileşime karşı hassastır; ölçüm kuantum durumunu etkiler; ayrıca bilinmeyen bir kuantum durumunu klasik bit gibi kopyalamak mümkün değildir. Bu konu ileride kuantum hata düzeltme bölümünde detaylandırılacaktır.

### 2.3.3. Ölçeklenmiş üretim ekosistemi

Klasik bilgisayar endüstrisi onlarca yıllık mühendislik birikimine sahiptir. Yarı iletken üretimi, işlemci tasarımı, işletim sistemleri, derleyiciler, programlama dilleri, bulut altyapıları ve yazılım geliştirme araçları son derece olgunlaşmıştır.

Bir geliştirici bugün birkaç dakika içinde bir bulut sunucu açabilir, container çalıştırabilir, veritabanı oluşturabilir, API yayınlayabilir ve global ölçekte servis verebilir. Kuantum bilgisayarlar henüz bu olgunluk seviyesinde değildir.

### 2.3.4. Deterministik iş yükleri

Birçok iş problemi deterministik ve klasik yapıdadır. Örneğin:

- Bir siparişin toplam tutarını hesaplamak,
- Bir kullanıcının yetkisini kontrol etmek,
- Bir SQL sorgusunu çalıştırmak,
- Bir REST API isteğini işlemek,
- Bir dosyayı sıkıştırmak,
- Bir form validasyonu yapmak.

Bu işler için kuantum bilgisayar beklemek anlamsızdır. Klasik bilgisayarlar bu görevlerde zaten hızlı, ucuz, güvenilir ve yeterlidir.

### 2.3.5. Klasik hesaplamanın zayıf olduğu alanlar

Buna rağmen klasik bilgisayarların zorlandığı problem sınıfları vardır. Bunların başında bazı kombinatoryal optimizasyon problemleri, büyük ölçekli arama problemleri, kuantum sistemlerin simülasyonu ve bazı kriptografik problemlerin matematiksel yapıları gelir.

Örneğin bir molekülün kuantum davranışını klasik bilgisayarda tam doğrulukla simüle etmek çok zor olabilir. Çünkü molekülün kuantum durumu büyüdükçe temsil edilmesi gereken durum uzayı çok hızlı büyür. Benzer şekilde bazı optimizasyon problemlerinde olası çözüm sayısı problem boyutuyla birlikte patlayıcı şekilde artabilir.

Bu tür problemler için klasik bilgisayarlar çeşitli yöntemler kullanır:

- Yaklaşık algoritmalar,
- sezgisel yöntemler,
- metaheuristic yaklaşımlar,
- paralel hesaplama,
- GPU hızlandırma,
- süper bilgisayarlar,
- problem özelinde matematiksel sadeleştirmeler.

Kuantum bilgisayarların potansiyel değeri, klasik bilgisayarların tamamen başarısız olduğu her yerde değil, **belirli matematiksel yapılara sahip bazı problemler için farklı ve daha avantajlı bir hesaplama yolu sunabilme ihtimalinde** yatar.

---

## 2.4. Kuantum bilgisayar neden "daha hızlı klasik bilgisayar" değildir?

Kuantum bilgisayarlar hakkında en yaygın yanlışlardan biri şudur:

> Kuantum bilgisayar, klasik bilgisayarın çok daha hızlı çalışan yeni neslidir.

Bu ifade teknik olarak yanlıştır. Kuantum bilgisayar, klasik bilgisayarın saat frekansı daha yüksek, çekirdek sayısı daha fazla veya belleği daha geniş bir sürümü değildir. Kuantum bilgisayar, bilgiyi farklı biçimde temsil eden ve işleyen farklı bir hesaplama modelidir.

NIST'in kuantum bilgisayar açıklamasında da vurgulandığı gibi kuantum bilgisayarlar klasik bitler yerine qubit kullanır; bu qubitler süperpozisyon ve dolaşıklık gibi kuantum özelliklerinden yararlanabilir. Bu, klasik bilgisayarlardan sadece hız bakımından değil, hesaplama biçimi bakımından da ayrıldıkları anlamına gelir.

Klasik bilgisayarda bir bit belirli anda 0 veya 1'dir. Kuantum bilgisayarda qubit ölçüldüğünde 0 veya 1 sonucu verir; ancak ölçümden önce kuantum durumu olasılık genlikleriyle temsil edilir. Birden fazla qubit birlikte ele alındığında sistemin durum uzayı klasik sezgilerden çok daha farklı davranır. IBM'in kuantum eğitim içeriklerinde de belirtildiği gibi, kuantum bilgisayarlar süperpozisyon, dolaşıklık ve girişim sayesinde problemlere klasik bilgisayarlardan farklı biçimde yaklaşır.

Ancak bu fark "her problemde hız" anlamına gelmez.

Bir kuantum bilgisayarın avantaj sağlayabilmesi için problem yapısının kuantum algoritmaya uygun olması gerekir. Kuantum algoritmanın, doğru cevapların olasılık genliklerini güçlendirip yanlış cevapların genliklerini bastıracak şekilde tasarlanması gerekir. Aksi halde süperpozisyon tek başına fayda üretmez.

Bunu şu şekilde düşünebiliriz:

```text
Klasik hızlandırma:
Aynı hesaplama modelini daha hızlı, daha paralel veya daha özel donanımla çalıştırmak.

Kuantum hesaplama:
Problemi farklı bir matematiksel temsil ve farklı fiziksel kurallarla çözmeye çalışmak.
```

Bu nedenle kuantum bilgisayar, klasik bilgisayarların yerine geçmesi beklenen genel amaçlı bir cihaz değildir. Daha gerçekçi beklenti, kuantum bilgisayarların klasik sistemlerle birlikte çalışan özel hızlandırıcılar veya yardımcı hesaplama kaynakları olarak konumlanmasıdır. Microsoft Azure Quantum dokümantasyonu da hibrit kuantum hesaplamayı, klasik bilgisayar ve kuantum bilgisayarın birlikte problem çözmesi olarak tanımlar. IBM de quantum-centric supercomputing yaklaşımında kuantum bilgisayarların klasik sistemlerin yerine geçmesinden çok, klasik süper bilgisayarlarla birlikte çalışmasını vurgular.

Bu noktada önemli bir ayrım daha vardır:

```text
Kuantum bilgisayar ≠ Daha hızlı CPU
Kuantum bilgisayar ≠ Daha büyük GPU
Kuantum bilgisayar ≠ Her problemi çözen sihirli makine
Kuantum bilgisayar = Belirli problem sınıfları için farklı hesaplama paradigması
```

Örneğin bir web uygulamasında kullanıcı login işlemini kuantum bilgisayarla yapmak anlamlı değildir. Bir SQL veritabanının günlük transaction işlerini kuantum bilgisayara taşımak anlamlı değildir. Bir mikroservisin JSON parse etmesini kuantum bilgisayarla hızlandırmaya çalışmak anlamlı değildir.

Buna karşılık aşağıdaki alanlarda kuantum bilgisayarlar teorik veya araştırma düzeyinde ilgi çekicidir:

- Kuantum sistemlerin simülasyonu,
- bazı kimya ve malzeme bilimi problemleri,
- bazı optimizasyon problemleri,
- bazı lineer cebir tabanlı algoritmalar,
- bazı arama problemleri,
- açık anahtarlı kriptografiyi etkileyen sayı teorisi problemleri.

Dolayısıyla kuantum bilgisayarları anlamanın ilk adımı, onları "daha hızlı bilgisayar" olarak değil, "farklı hesaplama modeli" olarak görmektir.

---

## 2.5. Farklı hesaplama modelleri: klasik, olasılıksal ve kuantum

Kuantum bilgisayarları daha doğru anlamak için üç hesaplama modelini karşılaştırmak faydalıdır:

1. Klasik deterministik hesaplama,
2. klasik olasılıksal hesaplama,
3. kuantum hesaplama.

### 2.5.1. Klasik deterministik hesaplama

Deterministik hesaplamada aynı girdi aynı programla işlendiğinde aynı çıktı üretilir.

```text
Girdi:  5, 7
İşlem:  Topla
Çıktı:  12
```

Bu modelde programın her adımı belirli bir kurala göre ilerler. Koşullar, döngüler ve fonksiyon çağrıları deterministik biçimde yürütülür.

Örnek:

```csharp
int Add(int a, int b)
{
    return a + b;
}
```

Bu fonksiyon aynı girdiler için her zaman aynı sonucu üretir.

Deterministik hesaplama şu alanlarda çok uygundur:

- İş kuralları,
- finansal hesaplamalar,
- veri tabanı işlemleri,
- derleyiciler,
- işletim sistemleri,
- çoğu backend servisi,
- veri dönüştürme işlemleri.

### 2.5.2. Klasik olasılıksal hesaplama

Olasılıksal hesaplamada algoritma rastgelelik kullanabilir. Aynı girdiyle farklı çalıştırmalarda farklı ara yollar izlenebilir veya farklı sonuçlar üretilebilir. Ancak bu rastgelelik klasik anlamdadır.

Örnekler:

- Monte Carlo simülasyonları,
- rastgele örnekleme,
- genetik algoritmalar,
- randomize veri yapıları,
- bazı makine öğrenmesi yöntemleri,
- probabilistic primality testing.

Basit örnek:

```text
Bir noktayı rastgele seç.
Dairenin içinde mi kontrol et.
Bunu çok kez tekrarla.
Sonuçlardan π değerini yaklaşık hesapla.
```

Burada rastgelelik hesaplama stratejisinin parçasıdır. Ancak sistemin durumu hâlâ klasik bitlerle temsil edilir. Rastgele sayı üreticisi kullanılsa bile program klasik bilgisayarda çalışır ve ara değerler klasik olarak okunabilir, kopyalanabilir ve saklanabilir.

### 2.5.3. Kuantum hesaplama

Kuantum hesaplama, klasik olasılıksal hesaplamadan farklıdır. Çünkü burada olasılık yalnızca "rastgele seçim" anlamına gelmez. Qubit durumları olasılık genlikleriyle temsil edilir. Bu genlikler karmaşık sayılar olabilir ve birbirleriyle girişim yapabilir.

Bu fark çok önemlidir:

```text
Klasik olasılıksal hesaplama:
Olasılıklar kullanılır.
Olasılıklar negatif olamaz.
Olasılıklar doğrudan toplanır.

Kuantum hesaplama:
Olasılık genlikleri kullanılır.
Genlikler pozitif, negatif veya karmaşık fazlı olabilir.
Genlikler birbirini güçlendirebilir veya söndürebilir.
Ölçüm sonunda klasik olasılıklar elde edilir.
```

Kuantum algoritmaların gücü, bu olasılık genliklerini bilinçli biçimde yönlendirebilmesinden gelir. Yanlış cevaplara giden yolların genlikleri birbirini söndürebilir; doğru cevaplara giden yolların genlikleri birbirini güçlendirebilir. Bu kavram ileride "Girişim: Interference" bölümünde detaylandırılacaktır.

### 2.5.4. Üç modelin kısa karşılaştırması

| Özellik | Klasik deterministik | Klasik olasılıksal | Kuantum |
|---|---|---|---|
| Temel bilgi birimi | Bit | Bit + rastgelelik | Qubit |
| Aynı girdi aynı çıktı mı? | Evet | Her zaman değil | Ölçüm sonucu olasılıksaldır |
| Ara durum okunabilir mi? | Evet | Evet | Ölçüm durumu etkiler |
| Kopyalama mümkün mü? | Evet | Evet | Bilinmeyen kuantum durum kopyalanamaz |
| Ana güç | Kesinlik ve kontrol | Örnekleme ve yaklaşık çözüm | Süperpozisyon, dolaşıklık, girişim |
| Tipik kullanım | Genel yazılım sistemleri | Simülasyon, optimizasyon, ML | Özel problem sınıfları |

### 2.5.5. Neden bu ayrım önemli?

Bu ayrım, kuantum bilgisayarlarla ilgili beklentiyi doğru kurmak için kritiktir. Kuantum bilgisayarlar klasik deterministik hesaplamanın yerine geçmez. Klasik olasılıksal algoritmaların doğrudan daha hızlı hali de değildir. Kuantum hesaplama, kendine özgü matematiksel kuralları olan farklı bir modeldir.

Bu nedenle bir problem için şu soruları sormak gerekir:

```text
Bu problem klasik bilgisayarda zaten verimli çözülebiliyor mu?
Problem kuantum algoritmaya uygun bir matematiksel yapıya sahip mi?
Kuantum çözüm, veri hazırlama ve ölçüm maliyetleri dahil edildiğinde avantaj sağlıyor mu?
Mevcut kuantum donanımı bu problemi çalıştırabilecek kadar güvenilir mi?
Klasik alternatiflerle karşılaştırıldığında gerçek bir fayda var mı?
```

Bu sorulara net cevap vermeden "kuantum bilgisayar bunu hızlandırır" demek doğru değildir.

---

## Bölüm Özeti

Bu bölümde klasik bilgisayardan kuantum bilgisayara geçiş için temel zemini kurduk.

Klasik bilgisayarlar bitler, transistorlar ve mantık kapıları üzerine inşa edilir. Bu model son derece güçlü, güvenilir ve olgunlaşmıştır. Günlük yazılım sistemlerinin, bulut servislerinin, veritabanlarının, işletim sistemlerinin ve yapay zekâ altyapılarının büyük kısmı klasik hesaplama modeliyle çalışır.

Kuantum bilgisayarlar ise klasik bilgisayarların daha hızlı sürümü değildir. Qubitler, süperpozisyon, dolaşıklık ve girişim gibi kuantum özellikleri sayesinde belirli problem sınıflarına farklı bir hesaplama yaklaşımı sunar. Ancak bu, her problemde avantaj anlamına gelmez.

Klasik deterministik, klasik olasılıksal ve kuantum hesaplama modelleri arasındaki farkı anlamak, kuantum bilgisayarlar hakkında sağlıklı bir bakış açısı geliştirmenin ilk adımıdır. Bundan sonraki bölümde bu farklılığın fiziksel ve kavramsal temeline, yani kuantum mekaniğine yalın bir giriş yapılacaktır.

---

## Kaynaklar ve İleri Okuma

- NIST — Quantum Computing Explained  
  <https://www.nist.gov/quantum-information-science/quantum-computing-explained>

- IBM Quantum Learning — Quantum Computing Fundamentals  
  <https://quantum.cloud.ibm.com/learning/en/courses/quantum-business-foundations/quantum-computing-fundamentals>

- IBM Think — What Is Quantum Computing?  
  <https://www.ibm.com/think/topics/quantum-computing>

- Microsoft Azure Quantum — What Is Quantum Computing?  
  <https://learn.microsoft.com/en-us/azure/quantum/overview-understanding-quantum-computing>

- Microsoft Azure Quantum — Hybrid Quantum Computing  
  <https://learn.microsoft.com/en-us/azure/quantum/hybrid-computing-overview>

- IBM Think — Quantum-Centric Supercomputing  
  <https://www.ibm.com/think/topics/quantum-centric-supercomputing>
