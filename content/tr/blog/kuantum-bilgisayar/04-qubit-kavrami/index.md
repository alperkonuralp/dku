+++
title = "4. Qubit Kavramı"
description = "Qubit'i olasılık genlikleri, Bloch küresi ve fiziksel/mantıksal qubit ayrımıyla derinlemesine anlamak."
date = "2026-05-18T00:00:00+03:00"
weight = 4
type = "guide"
draft = false
+++

> Bu bölümün amacı, kuantum bilgisayarların temel bilgi birimi olan **qubit** kavramını hem sezgisel hem de teknik açıdan açıklamaktır. Burada hedef, okuyucunun qubit'i "aynı anda hem 0 hem 1 olan sihirli bit" gibi eksik bir cümleyle değil; ölçüm, olasılık genliği, kuantum durum vektörü, Bloch küresi, fiziksel qubit ve mantıksal qubit gibi temel kavramlarla birlikte anlamasıdır.

---

## 4.1. Qubit nedir?

**Qubit**, yani *quantum bit*, kuantum bilgisayarların temel bilgi birimidir. Klasik bilgisayarda bilginin en küçük birimi **bit**tir. Bit, pratik olarak iki değerden birini temsil eder:

```text
0 veya 1
```

Qubit de ölçüldüğünde yine klasik bir sonuç üretir:

```text
0 veya 1
```

Fakat qubit'i klasik bitten ayıran şey, **ölçümden önceki durumunun** klasik bir 0 veya 1 değeriyle sınırlı olmamasıdır. Bir qubit, matematiksel olarak 0 ve 1 durumlarının belirli katsayılarla birleşimi olan bir **kuantum durumunda** bulunabilir.

Bu durum genellikle şöyle yazılır:

```text
|ψ⟩ = α|0⟩ + β|1⟩
```

Burada:

- `|ψ⟩` qubit'in genel kuantum durumudur.
- `|0⟩` klasik 0 sonucuna karşılık gelen temel kuantum durumudur.
- `|1⟩` klasik 1 sonucuna karşılık gelen temel kuantum durumudur.
- `α` ve `β` ise **olasılık genlikleri**dir.

Bu ifade ilk bakışta karmaşık görünebilir. Fakat ana fikir şudur:

> Qubit, ölçüldüğünde 0 veya 1 veren; ölçülmeden önce ise bu sonuçlara ait olasılık genlikleriyle tanımlanan kuantum bilgi birimidir.

Bu yüzden qubit için "0 ve 1'i aynı anda tutar" demek popüler ama eksik bir anlatımdır. Daha doğru ifade şudur:

> Qubit, ölçüm yapılana kadar 0 ve 1 sonuçlarına ait olasılık genliklerinin birleşimiyle tanımlanan bir kuantum durumunda bulunur.

Kuantum bilgisayarın gücü de bu durumların kontrollü biçimde dönüştürülmesinden gelir. Qubitler üzerinde yapılan işlemler, doğrudan "değer değiştirme" gibi değil, **kuantum durumunu dönüştürme** gibi düşünülmelidir.

---

## 4.2. Bit ile qubit arasındaki fark

Klasik bit ile qubit arasındaki farkı anlamadan kuantum bilgisayarı anlamak zordur. Çünkü çoğu yanlış anlatım, qubit'i bitin "daha gelişmiş" veya "daha hızlı" hali gibi göstermeye çalışır. Oysa qubit, bitin hızlı versiyonu değildir; farklı fiziksel ve matematiksel kurallara bağlı bir bilgi birimidir.

### 4.2.1. Bit nasıl davranır?

Bir klasik bitin değeri belirgindir:

```text
bit = 0
```

veya

```text
bit = 1
```

Bir bit üzerinde işlem yaptığınızda, örneğin NOT kapısı uyguladığınızda:

```text
0 → 1
1 → 0
```

şeklinde net bir dönüşüm elde edersiniz.

Klasik bilgisayarın tüm dünyası, bu tür belirli değerlerin mantıksal kapılarla işlenmesine dayanır. İşlemci, bellek, disk, ağ protokolü, dosya sistemi, veritabanı motoru, programlama dili çalışma zamanı gibi sistemlerin tamamı en altta bu klasik bilgi modelinin üzerine kuruludur.

### 4.2.2. Qubit nasıl davranır?

Qubit'in durumu ise yalnızca `0` veya `1` diye ifade edilmez. Ölçümden önce qubit'in durumu şu biçimdedir:

```text
|ψ⟩ = α|0⟩ + β|1⟩
```

Bu, qubit'in ölçüm sonucunda 0 veya 1 verebileceği anlamına gelir; fakat hangi sonucu vereceği deterministik olarak değil, olasılıksal olarak belirlenir.

Örneğin bir qubit şu durumda olabilir:

```text
|ψ⟩ = 1/√2 |0⟩ + 1/√2 |1⟩
```

Bu durumda ölçüm yapıldığında 0 gelme olasılığı %50, 1 gelme olasılığı %50'dir.

Ama dikkat: Bu cümle, qubit'in klasik anlamda "bazen 0, bazen 1" olduğu anlamına gelmez. Qubit ölçülmeden önce gerçekten klasik bir değer taşımaz. Onun durumu, ölçüm sonuçlarına ait olasılık genlikleriyle tanımlanır.

### 4.2.3. Temel farkların özeti

| Özellik | Bit | Qubit |
| --- | --- | --- |
| Temel değer | 0 veya 1 | Ölçümde 0 veya 1 |
| Ölçümden önceki durum | Belirli klasik değer | Kuantum durum vektörü |
| Durum gösterimi | `0`, `1` | `α\|0⟩ + β\|1⟩` |
| Ölçüm etkisi | Genellikle değeri bozmaz | Kuantum durumu etkiler |
| Kopyalanabilirlik | Kopyalanabilir | Bilinmeyen kuantum durum genel olarak kopyalanamaz |
| İşlem modeli | Mantık kapıları | Üniter dönüşümler ve ölçüm |
| Sezgisel model | Anahtar açık/kapalı | Dönüştürülebilen olasılık genliği durumu |

### 4.2.4. Kopyalama farkı neden önemlidir?

Klasik bilgisayarda bir biti kopyalamak son derece basittir:

```text
a = 1
b = a
```

Artık hem `a` hem `b` aynı değeri taşır.

Kuantum dünyasında ise bilinmeyen bir qubit durumunu genel olarak birebir kopyalamak mümkün değildir. Bu ilke **no-cloning theorem** olarak bilinir. Bu durum, kuantum hata düzeltmeyi de klasik hata düzeltmeden çok daha zor hale getirir. Çünkü klasik dünyada hata düzeltme çoğu zaman bilgiyi kopyalayıp çoğunluk oylaması yapmakla açıklanabilirken, kuantum dünyasında bilinmeyen kuantum durumunu basitçe kopyalayamazsınız.

---

## 4.3. Qubit durumu nasıl temsil edilir?

Bir qubit'in durumu, iki boyutlu karmaşık bir vektörle temsil edilir. En temel iki durum şöyle gösterilir:

```text
|0⟩ = [1]
      [0]

|1⟩ = [0]
      [1]
```

Bu iki durum, klasik bitin 0 ve 1 değerlerine karşılık gelen temel kuantum durumlarıdır. Ancak qubit'in durumu yalnızca bu iki vektörden biri olmak zorunda değildir. Genel durum şudur:

```text
|ψ⟩ = α|0⟩ + β|1⟩
```

Vektör biçimiyle:

```text
|ψ⟩ = [α]
      [β]
```

Burada `α` ve `β` karmaşık sayılar olabilir. Yani yalnızca reel sayılarla sınırlı değillerdir. Örneğin:

```text
α = 1/√2
β = i/√2
```

gibi bir durum mümkündür.

### 4.3.1. Normalizasyon şartı

Bir qubit durumunun geçerli olabilmesi için şu koşul sağlanmalıdır:

```text
|α|² + |β|² = 1
```

Bu koşul, ölçüm sonucunda tüm olasılıkların toplamının 1 olması gerektiğini ifade eder.

Örneğin:

```text
|ψ⟩ = 1/√2 |0⟩ + 1/√2 |1⟩
```

için:

```text
|1/√2|² + |1/√2|² = 1/2 + 1/2 = 1
```

Bu geçerli bir qubit durumudur.

Ama şu ifade geçerli değildir:

```text
|ψ⟩ = 1|0⟩ + 1|1⟩
```

Çünkü:

```text
|1|² + |1|² = 2
```

Bu durumda olasılıkların toplamı 1 değil 2 olur. Böyle bir durum fiziksel olarak geçerli bir normalize kuantum durumu değildir.

### 4.3.2. Dirac notasyonu

Kuantum hesaplamada sık kullanılan `|0⟩`, `|1⟩`, `|ψ⟩` gibi gösterimler **Dirac notasyonu** veya **bra-ket notasyonu** olarak bilinir.

Bu notasyonda:

```text
|ψ⟩
```

bir kuantum durumunu ifade eder. Buna "ket psi" denir.

Bu dokümanda çok ağır matematiğe girilmeyecek; ancak qubit kavramını doğru anlamak için bu notasyonu en azından okuyabilir hale gelmek önemlidir.

### 4.3.3. Qubit durumunu klasik bir değişken gibi düşünmemek

Bir yazılımcı için qubit'i şöyle düşünmek cazip olabilir:

```csharp
var qubit = new Qubit();
qubit.Value = 0.5 * Zero + 0.5 * One;
```

Fakat bu yanıltıcıdır. Qubit, klasik bellekte tuttuğumuz sıradan bir veri yapısı değildir. Bir kuantum bilgisayarda qubit, fiziksel bir kuantum sisteminin durumudur. Biz bu durumu matematiksel olarak vektörlerle temsil ederiz; fakat gerçek donanımda bu durum bir iyonun enerji seviyesi, süperiletken devredeki enerji durumu, bir fotonun polarizasyonu veya başka bir fiziksel özellik olabilir.

---

## 4.4. Olasılık ile olasılık genliği arasındaki fark

Qubit'i anlamanın en kritik noktalarından biri, **olasılık** ile **olasılık genliği** arasındaki farkı kavramaktır.

Klasik olasılıkta doğrudan şöyle konuşuruz:

```text
0 gelme olasılığı = %50
1 gelme olasılığı = %50
```

Kuantum durumunda ise önce olasılık genlikleri vardır:

```text
|ψ⟩ = α|0⟩ + β|1⟩
```

Ölçüm olasılıkları bu genliklerin mutlak değerlerinin karesinden elde edilir:

```text
P(0) = |α|²
P(1) = |β|²
```

Burada `P(0)`, ölçümde 0 sonucunu alma olasılığıdır. `P(1)` ise ölçümde 1 sonucunu alma olasılığıdır.

### 4.4.1. Basit örnek

Şu qubit durumunu düşünelim:

```text
|ψ⟩ = 1/√2 |0⟩ + 1/√2 |1⟩
```

Bu durumda:

```text
α = 1/√2
β = 1/√2
```

Olasılıklar:

```text
P(0) = |1/√2|² = 1/2
P(1) = |1/√2|² = 1/2
```

Yani ölçüm sonucu %50 olasılıkla 0, %50 olasılıkla 1 olur.

### 4.4.2. Genlikler negatif veya karmaşık olabilir

Klasik olasılıklar negatif olamaz. Örneğin "-0.3 olasılık" anlamsızdır. Fakat kuantum genlikleri negatif veya karmaşık olabilir:

```text
|ψ⟩ = 1/√2 |0⟩ - 1/√2 |1⟩
```

Bu durumda da:

```text
P(0) = 1/2
P(1) = 1/2
```

Yani ölçüm olasılıkları önceki örnekle aynıdır. Ancak iki durum aynı değildir:

```text
1/√2 |0⟩ + 1/√2 |1⟩
```

ile

```text
1/√2 |0⟩ - 1/√2 |1⟩
```

arasında faz farkı vardır. Bu fark, sonraki kuantum işlemlerinde çok önemli sonuçlar doğurabilir.

İşte kuantum algoritmalardaki **girişim** kavramı buradan güç alır. Genlikler yalnızca olasılık üretmez; aynı zamanda birbirini güçlendirebilir veya söndürebilir. Bu yüzden kuantum hesaplamayı klasik olasılıksal hesaplamadan ayıran en temel farklardan biri genliklerin işaret ve faz bilgisi taşımasıdır.

### 4.4.3. Global faz ve göreli faz

Bazı faz farkları fiziksel olarak gözlemlenebilir sonuç üretmez. Örneğin bir kuantum durumunun tamamını aynı faz katsayısıyla çarpmak, ölçüm olasılıklarını değiştirmez. Buna **global faz** denir.

Örneğin:

```text
|ψ⟩
```

ile

```text
-|ψ⟩
```

ölçüm olasılıkları açısından aynı sonucu verir.

Ancak `|0⟩` ve `|1⟩` bileşenleri arasındaki faz farkı, yani **göreli faz**, kuantum işlemlerde önemlidir. Çünkü sonraki kapılar bu faz farkını ölçülebilir olasılık farklarına dönüştürebilir.

Bu nedenle qubit'in durumu yalnızca "0 gelme olasılığı kaç, 1 gelme olasılığı kaç?" sorusundan ibaret değildir. Aynı olasılıklara sahip farklı kuantum durumları, sonraki işlemlerde farklı davranabilir.

---

## 4.5. Bloch küresi ile sezgisel anlatım

Tek qubit durumunu görselleştirmenin en yaygın yollarından biri **Bloch küresi**dir. Bloch küresi, tek qubit'in olası saf durumlarını üç boyutlu bir kürenin yüzeyi üzerinde temsil etmeye yarar.

Bu anlatım özellikle sezgisel olarak faydalıdır; çünkü qubit durumunu soyut bir vektör yerine, küre üzerinde yön gösteren bir ok gibi düşünmemizi sağlar.

### 4.5.1. Bloch küresinin temel noktaları

Bloch küresinde genellikle:

```text
Kuzey kutbu  → |0⟩
Güney kutbu → |1⟩
```

olarak gösterilir.

Kürenin yüzeyindeki diğer noktalar ise farklı süperpozisyon durumlarını temsil eder.

Örneğin ekvator üzerindeki bazı noktalar, 0 ve 1 sonuçlarının eşit olasılıkla geldiği ama farklı fazlara sahip durumları ifade eder.

### 4.5.2. Basit sezgi

Bir qubit'i Bloch küresinde bir ok gibi düşünebiliriz:

```text
Ok kuzeye bakıyorsa  → ölçümde kesin 0
Ok güneye bakıyorsa → ölçümde kesin 1
Ok ekvatordaysa     → 0 ve 1 olasılıkları eşit olabilir
```

Fakat okun ekvator üzerinde hangi yöne baktığı da önemlidir. Çünkü bu yön, faz bilgisini temsil eder.

Yani iki qubit durumu ölçümde aynı 0/1 olasılıklarını verebilir; ama Bloch küresinde farklı yönlere bakıyor olabilir. Bu fark, daha sonra uygulanacak kuantum kapılarıyla görünür hale gelebilir.

### 4.5.3. Kuantum kapıları Bloch küresinde nasıl görünür?

Tek qubit kapıları, Bloch küresi üzerinde qubit okunu döndüren işlemler gibi düşünülebilir.

Örneğin:

- `X` kapısı, `|0⟩` ile `|1⟩` durumlarını değiştirir.
- `Z` kapısı, faz bilgisini değiştirir.
- `H`, yani Hadamard kapısı, temel durumlar ile süperpozisyon durumları arasında dönüşüm yapar.

Bu nedenle Bloch küresi, özellikle tek qubit işlemlerini anlamak için güçlü bir görsel araçtır.

### 4.5.4. Bloch küresinin sınırı

Bloch küresi çok faydalıdır ama her şeyi açıklamaz. En önemli sınırı şudur:

> Bloch küresi tek qubit için sezgisel bir gösterimdir; çok qubitli sistemlerin tamamını aynı basitlikle görselleştiremez.

İki qubit, üç qubit veya daha fazla qubit olduğunda durum uzayı çok hızlı büyür. Ayrıca dolaşıklık gibi çok-qubitli özellikler Bloch küresiyle tam olarak temsil edilemez. Bu nedenle Bloch küresi öğrenme açısından çok değerlidir; ama kuantum hesaplamanın tamamını görselleştiren evrensel bir araç değildir.

---

## 4.6. Fiziksel qubit ve mantıksal qubit ayrımı

Kuantum bilgisayar haberlerinde sıkça "şu kadar qubitlik işlemci", "bin qubit", "milyon qubit hedefi" gibi ifadeler duyulur. Ancak burada kritik bir ayrım vardır:

```text
Fiziksel qubit ≠ Mantıksal qubit
```

Bu ayrımı anlamadan kuantum donanım haberlerini doğru yorumlamak mümkün değildir.

### 4.6.1. Fiziksel qubit nedir?

**Fiziksel qubit**, gerçek donanımda kontrol edilen kuantum sistemidir.

Bu, farklı teknolojilerle gerçekleştirilebilir:

- Süperiletken devre
- Hapsedilmiş iyon
- Nötr atom
- Foton
- Spin qubit
- Topolojik qubit adayı

Örneğin süperiletken qubitlerde, çok düşük sıcaklıklara soğutulan küçük devrelerdeki enerji seviyeleri kuantum bilgi taşımak için kullanılır. Hapsedilmiş iyonlarda ise elektrik yüklü atomlar elektromanyetik alanlarla tuzaklanır ve lazerlerle kontrol edilir.

Fiziksel qubitler son derece hassastır. Çevreyle etkileşim, sıcaklık, elektromanyetik gürültü, kontrol hataları ve ölçüm hataları qubit durumunu bozabilir.

Bu yüzden fiziksel qubit sayısı tek başına yeterli bir kalite göstergesi değildir. Önemli olan yalnızca kaç qubit olduğu değil, bu qubitlerin ne kadar güvenilir çalıştığıdır.

### 4.6.2. Mantıksal qubit nedir?

**Mantıksal qubit**, birden fazla fiziksel qubit kullanılarak hata düzeltme protokolleriyle daha güvenilir hale getirilen qubit'tir.

Basit sezgi şudur:

```text
Birçok kırılgan fiziksel qubit
        ↓
Hata düzeltme kodu
        ↓
Daha güvenilir bir mantıksal qubit
```

Bu, klasik bilgisayarlardaki yedeklilik fikrine biraz benzer; ancak doğrudan aynı değildir. Çünkü kuantum durumda bilgiyi kopyalayamazsınız. Bu nedenle kuantum hata düzeltme, klasik çoğunluk oylamasından çok daha karmaşık teknikler gerektirir.

Mantıksal qubitler, **fault-tolerant quantum computing** hedefinin temelidir. Pratikte uzun ve güvenilir kuantum algoritmalar çalıştırmak için yalnızca fiziksel qubitlere değil, yeterince düşük hata oranına sahip mantıksal qubitlere ihtiyaç vardır.

### 4.6.3. Neden fiziksel qubit sayısı tek başına yetmez?

İki kuantum işlemci düşünelim:

```text
A işlemcisi:
10.000 fiziksel qubit
yüksek hata oranı
zayıf bağlantı yapısı
kısa coherence süresi

B işlemcisi:
1.000 fiziksel qubit
daha düşük hata oranı
daha iyi kontrol
daha iyi hata düzeltme kabiliyeti
```

Yalnızca qubit sayısına bakarsak A işlemcisi daha güçlü görünür. Ancak gerçek hesaplama kapasitesi açısından B işlemcisi daha anlamlı olabilir.

Bu nedenle kuantum bilgisayarları değerlendirirken şu metriklere birlikte bakmak gerekir:

- Fiziksel qubit sayısı
- Gate fidelity
- Ölçüm doğruluğu
- Coherence süresi
- Bağlantı yapısı
- Hata düzeltme kapasitesi
- Mantıksal qubit sayısı
- Mantıksal hata oranı
- Çalıştırılabilen devre derinliği
- Gerçek uygulama performansı

### 4.6.4. Haberleri okurken dikkat edilmesi gereken soru

Bir şirket "1 milyon qubit hedefliyoruz" dediğinde hemen şu sorular sorulmalıdır:

```text
Bunlar fiziksel qubit mi, mantıksal qubit mi?
Hata oranları nedir?
Bu qubitlerle ne kadar derin devre çalıştırılabiliyor?
Hata düzeltme var mı?
Mantıksal qubit başına kaç fiziksel qubit gerekiyor?
Gerçek bir algoritmada klasik bilgisayara göre avantaj gösterildi mi?
```

Bu sorular, hype ile gerçek teknik ilerlemeyi ayırmak için önemlidir.

---

## 4.7. Bir qubit gerçekten neyi "saklar"?

Bu soru çok önemlidir, çünkü qubit hakkında en yaygın yanlışlardan biri "bir qubit sonsuz bilgi saklar" yanılgısıdır.

Matematiksel olarak bir qubit durumu iki karmaşık sayı ile ifade edilir:

```text
|ψ⟩ = α|0⟩ + β|1⟩
```

İlk bakışta bu, "bir qubit içinde iki karmaşık sayı var; o halde çok fazla bilgi saklıyor" gibi görünebilir. Fakat bu doğru bir sonuç değildir.

Çünkü qubit'i ölçtüğünüzde yalnızca klasik bir bitlik sonuç elde edersiniz:

```text
0 veya 1
```

Yani tek bir qubit'i ölçerek `α` ve `β` değerlerini doğrudan okuyamazsınız. Qubit'in kuantum durumu hesaplama sırasında etki eder, fakat ölçümde sınırlı klasik bilgi verir.

### 4.7.1. Qubit klasik veri deposu değildir

Bir qubit'i klasik bellek hücresi gibi düşünmek yanlıştır. Klasik bellekte bir hücreye veri yazarsınız, sonra onu okursunuz:

```text
write x
read x
```

Qubit dünyasında ise durum farklıdır. Bir qubit'i belirli bir kuantum durumuna hazırlarsınız, üzerinde kapılar uygularsınız, başka qubitlerle dolaştırırsınız ve sonunda ölçersiniz.

Ölçüm sonucu size yalnızca klasik bir sonuç verir. Bu nedenle qubit, "çok büyük veri sıkıştırma aracı" değildir.

### 4.7.2. Peki kuantum bilgisayar gücünü nereden alır?

Qubit'in gücü, sakladığı bilgiyi doğrudan okumamızdan değil; durumların hesaplama boyunca birbirleriyle etkileşmesinden, girişim oluşturmasından ve doğru cevabın olasılığını artırabilmesinden gelir.

Özellikle çok qubitli sistemlerde durum uzayı çok hızlı büyür. `n` qubitlik bir sistemin genel durumu, `2^n` temel durumun genlikleriyle ifade edilir:

```text
1 qubit  → 2 temel durum
2 qubit  → 4 temel durum
3 qubit  → 8 temel durum
n qubit  → 2^n temel durum
```

Fakat bu, `2^n` klasik bilgiyi serbestçe okuyabileceğimiz anlamına gelmez. Ölçüm sonucunda yine `n` bitlik klasik sonuç elde ederiz.

Kuantum algoritmanın başarısı, bu büyük durum uzayını doğrudan okumakta değil; onu doğru sonucun öne çıkacağı şekilde dönüştürmektedir.

### 4.7.3. "Qubit neyi saklar?" sorusuna kısa cevap

Kısa cevap şudur:

> Bir qubit, klasik anlamda doğrudan okunabilir bir veri değeri değil; ölçüm sonuçlarına ait olasılık genlikleriyle tanımlanan bir kuantum durumu taşır.

Daha sade ifade:

> Qubit, sonucu değil; sonuca giden kuantum olasılık yapısını taşır.

Bu cümle kuantum bilgisayarı anlamak için çok değerlidir. Çünkü kuantum programlamada amaç, qubitlerin içindeki "gizli cevabı" okumak değildir. Amaç, qubitlerin durumlarını öyle dönüştürmektir ki ölçüm yapıldığında doğru cevabın gelme olasılığı yüksek olsun.

---

## 4.8. Bölüm özeti

Bu bölümde kuantum bilgisayarların temel bilgi birimi olan qubit kavramı ele alındı.

Öne çıkan noktalar şunlardır:

- Qubit, klasik bitin hızlı veya gelişmiş versiyonu değildir; farklı fiziksel ve matematiksel kurallara bağlı bir bilgi birimidir.
- Bir qubit ölçüldüğünde 0 veya 1 sonucu verir; fakat ölçümden önce `α|0⟩ + β|1⟩` biçiminde bir kuantum durumuyla temsil edilir.
- `α` ve `β` doğrudan olasılık değil, olasılık genlikleridir.
- Ölçüm olasılıkları `|α|²` ve `|β|²` ile hesaplanır.
- Olasılık genlikleri negatif veya karmaşık olabilir; bu da girişim etkisinin temelini oluşturur.
- Bloch küresi, tek qubit durumlarını görselleştirmek için yararlı bir araçtır.
- Fiziksel qubit, donanımda gerçekten kontrol edilen kuantum sistemidir.
- Mantıksal qubit, birçok fiziksel qubitin hata düzeltme ile daha güvenilir tek bir qubit gibi davranmasıdır.
- Qubit klasik anlamda "sonsuz bilgi saklayan" bir yapı değildir; ölçümde sınırlı klasik bilgi verir.
- Kuantum bilgisayarın gücü, qubit durumlarını doğru cevabı güçlendirecek biçimde dönüştürebilmesinden gelir.

Bu bölümden çıkarılacak en kısa ana fikir şudur:

> Qubit, klasik bir veri hücresi değil; kuantum durumunu taşıyan, ölçümde klasik sonuç veren ve hesaplama boyunca olasılık genlikleri üzerinden dönüştürülen temel bilgi birimidir.

---

## Kaynaklar ve İleri Okuma

- Microsoft Learn — *The Qubit in Quantum Computing*  
  <https://learn.microsoft.com/en-us/azure/quantum/concepts-the-qubit>

- NIST — *Quantum Computing Explained*  
  <https://www.nist.gov/quantum-information-science/quantum-computing-explained>

- NIST — *Logical Qubit Illustration*  
  <https://www.nist.gov/image/logical-qubit-illustration>

- NIST — *Quantum Logic Gates*  
  <https://www.nist.gov/physics/introduction-new-quantum-revolution/quantum-logic-gates>

- Microsoft Learn — *Explore Quantum Superposition with Q#*  
  <https://learn.microsoft.com/en-us/training/modules/explore-superposition/>
