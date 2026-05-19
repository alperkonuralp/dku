---
draft: true
---
# 11. Önemli Kuantum Algoritmaları

Bu bölümde kuantum algoritmaların tarihsel ve kavramsal olarak en çok referans verilen örnekleri ele alınır. Amaç, algoritmaları yalnızca isimleriyle tanıtmak değildir. Her algoritma için şu sorulara cevap aranır:

- Hangi problemi çözmeye çalışır?
- Kuantum yaklaşımın temel fikri nedir?
- Neden kuantum hesaplama tarihinde önemlidir?
- Bugün pratik kullanım açısından ne kadar olgundur?

Önceki bölümde kuantum algoritmaların temel mantığını, oracle kavramını, amplitude amplification yaklaşımını, phase estimation mekanizmasını, Quantum Fourier Transform kavramını ve klasik post-processing ihtiyacını ele almıştık. Bu bölümde bu yapı taşlarının gerçek algoritmalarda nasıl kullanıldığını göreceğiz.

Kuantum algoritmaları değerlendirirken iki ayrı ekseni ayırmak gerekir:

1. **Teorik önem:** Algoritma kuantum bilgisayarların klasik bilgisayarlara göre hangi tür avantajları sağlayabileceğini gösteriyor mu?
2. **Pratik olgunluk:** Algoritma bugünkü veya yakın gelecekteki donanımlarla gerçek problem ölçeklerinde uygulanabilir mi?

Bu ayrım önemlidir. Bazı algoritmalar kuantum hesaplama teorisi açısından çok önemlidir ama doğrudan iş dünyasında kullanılabilir durumda değildir. Bazıları ise bugünkü gürültülü kuantum cihazlarla denenebilir, fakat henüz klasik yöntemlere karşı genel ve net bir üstünlük sağlamamıştır.

---

## 11.1. Deutsch-Jozsa algoritması

Deutsch-Jozsa algoritması, kuantum hesaplama tarihindeki ilk önemli algoritma örneklerinden biridir. Pratikte büyük iş problemlerini çözmek için kullanılmaz; ancak kuantum algoritmaların klasik algoritmalardan yapısal olarak nasıl farklı çalıştığını göstermek için çok değerlidir.

### Problem nedir?

Elimizde bir kara kutu fonksiyon olduğunu düşünelim:

```text
f: {0,1}^n -> {0,1}
```

Bu fonksiyon için bize önceden şu söz verilir:

- Fonksiyon ya **sabit**tir: Tüm girdiler için aynı sonucu verir.
- Ya da **dengeli**dir: Girdilerin yarısı için 0, diğer yarısı için 1 verir.

Soru şudur:

```text
Fonksiyon sabit mi, dengeli mi?
```

Klasik deterministik yaklaşımda en kötü durumda fonksiyonu çok sayıda girdide test etmek gerekir. Çünkü ilk birkaç sonuç aynı gelse bile fonksiyonun sabit olduğundan emin olmak için yeterli olmayabilir.

Kuantum yaklaşımda ise Deutsch-Jozsa algoritması, ideal oracle modeli altında bu ayrımı tek sorguda yapabilir.

### Temel fikir

Algoritma, girdileri tek tek denemek yerine, girdilerin süperpozisyonunu oluşturur. Fonksiyon oracle üzerinden çalıştırıldığında sonuç bilgisi doğrudan ölçülebilir bir değer olarak değil, kuantum durumunun fazına işlenir. Daha sonra Hadamard kapıları ile girişim oluşturulur.

Eğer fonksiyon sabitse genlikler belirli bir durumda yapıcı girişim yapar. Eğer fonksiyon dengeliyse bu durumun genliği söner. Böylece ölçüm sonucunda fonksiyonun sabit mi dengeli mi olduğu anlaşılır.

Bu algoritmadaki asıl ders şudur:

```text
Kuantum algoritma, tüm cevapları okuyarak değil,
fonksiyonun küresel yapısını faz ve girişim üzerinden ortaya çıkararak çalışır.
```

### Neden önemlidir?

Deutsch-Jozsa algoritması, kuantum bilgisayarların belirli oracle problemlerinde klasik deterministik algoritmalara göre daha az sorguyla sonuca ulaşabileceğini gösterir. IBM Quantum Learning bu algoritmayı, kuantum paralellik ve girişim kombinasyonunun klasik yaklaşımdan daha hızlı cevap verebildiğini gösteren temel örneklerden biri olarak ele alır.

### Pratik olgunluk

Deutsch-Jozsa algoritması pratik iş problemleri için doğrudan kullanılan bir algoritma değildir. Daha çok eğitim, kavramsal gösterim ve kuantum algoritma tasarımının temel prensiplerini öğretmek için kullanılır.

**Kısa değerlendirme:**

| Boyut | Değerlendirme |
|---|---|
| Teorik önem | Yüksek |
| Pratik kullanım | Düşük |
| Öğretici değer | Çok yüksek |
| Ana kavram | Süperpozisyon + oracle + girişim |

---

## 11.2. Bernstein-Vazirani algoritması

Bernstein-Vazirani algoritması, Deutsch-Jozsa ailesine yakın bir başka temel oracle algoritmasıdır. Bu algoritma da pratik uygulamadan çok kuantum sorgu karmaşıklığı açısından önemlidir.

### Problem nedir?

Gizli bir bit dizisi olduğunu düşünelim:

```text
s = s1s2s3...sn
```

Oracle bize şu fonksiyonu verir:

```text
f(x) = s · x mod 2
```

Burada `s · x`, bit düzeyinde iç çarpımdır. Soru şudur:

```text
Gizli s bit dizisi nedir?
```

Klasik olarak `s` dizisinin her bitini öğrenmek için oracle’a birden fazla sorgu yapmak gerekir. Örneğin `n` bitlik bir gizli dizi için klasik deterministik yaklaşımda genellikle `n` sorgu gerekir.

Kuantum algoritma ise ideal oracle modeli altında gizli diziyi tek oracle sorgusuyla bulabilir.

### Temel fikir

Bernstein-Vazirani algoritması, faz geri tepmesi olarak çevrilebilecek **phase kickback** mekanizmasını kullanır. Oracle fonksiyon sonucu ayrı bir çıktı bitinde okunmak yerine, giriş register’ının fazına işlenir.

Hadamard kapıları ile başlanan süperpozisyon, oracle uygulandıktan sonra gizli bit dizisinin faz imzasını taşır. Son bir Hadamard katmanı bu faz bilgisini ölçülebilir klasik bit dizisine dönüştürür.

Sonuçta ölçüm doğrudan `s` dizisini verir.

### Neden önemlidir?

Bernstein-Vazirani algoritması, kuantum bilgisayarın tek bir oracle sorgusunda fonksiyonun gizli lineer yapısını çıkarabileceğini gösterir. Bu, kuantum algoritmaların yalnızca “çok sayıda girdiyi paralel denemesi” değil, fonksiyonun matematiksel yapısını faz ve girişim üzerinden yakalaması açısından önemlidir.

### Pratik olgunluk

Bu algoritma da doğrudan ticari problem çözmek için kullanılan bir algoritma değildir. Ancak kuantum algoritma eğitiminde çok kullanışlıdır. Çünkü Deutsch-Jozsa’ya göre daha somut bir çıktı verir: gizli bit dizisi.

**Kısa değerlendirme:**

| Boyut | Değerlendirme |
|---|---|
| Teorik önem | Orta-yüksek |
| Pratik kullanım | Düşük |
| Öğretici değer | Çok yüksek |
| Ana kavram | Phase kickback |

---

## 11.3. Simon algoritması

Simon algoritması, kuantum algoritmalar tarihinde çok özel bir yere sahiptir. Çünkü Shor algoritmasına giden fikrî yolda önemli bir basamaktır.

### Problem nedir?

Bir fonksiyon olduğunu düşünelim:

```text
f: {0,1}^n -> {0,1}^n
```

Bu fonksiyon için gizli bir `s` bit dizisi vardır ve şu özellik geçerlidir:

```text
f(x) = f(y) ancak ve ancak y = x ⊕ s
```

Burada `⊕`, bit düzeyinde XOR işlemidir.

Soru şudur:

```text
Gizli s dizisi nedir?
```

Bu problem klasik bilgisayarlar için oracle sorgu sayısı bakımından zorlaşırken, kuantum algoritma çok daha az sorguyla `s` hakkında doğrusal denklemler üretir.

### Temel fikir

Simon algoritması, fonksiyonun periyodik benzeri gizli yapısını ortaya çıkarmaya çalışır. Oracle’a süperpozisyon halinde sorgu yapılır. Ölçüm ve Hadamard işlemleri sonucunda `s` ile ilişkili doğrusal denklemler elde edilir.

Her çalıştırma şu türden bir bilgi verir:

```text
y · s = 0 mod 2
```

Algoritma birkaç kez tekrarlandığında yeterli sayıda bağımsız denklem toplanır. Sonra klasik bilgisayar bu denklemleri çözerek `s` değerini bulur.

Burada önemli nokta şudur:

```text
Kuantum kısım gizli yapıya dair denklemler üretir.
Klasik kısım bu denklemleri çözer.
```

Bu, kuantum algoritmaların çoğunda görülen hibrit yapının erken bir örneğidir.

### Neden önemlidir?

Simon algoritması, oracle problemlerinde kuantum bilgisayarların üstel hızlanma sağlayabileceğini gösteren erken örneklerden biridir. Daha da önemlisi, periyodiklik ve gizli yapı bulma fikri daha sonra Shor algoritmasında merkezi hale gelir.

Simon algoritması şu açıdan tarihsel olarak kritiktir:

```text
Gizli yapı problemleri → Simon algoritması → Shor algoritmasının sezgisel temeli
```

### Pratik olgunluk

Simon algoritması doğrudan iş uygulaması için kullanılan bir algoritma değildir. Fakat kuantum algoritma teorisinde çok önemlidir. Shor algoritmasını anlamak isteyen biri için Simon algoritması güçlü bir hazırlık adımıdır.

**Kısa değerlendirme:**

| Boyut | Değerlendirme |
|---|---|
| Teorik önem | Çok yüksek |
| Pratik kullanım | Düşük |
| Öğretici değer | Yüksek |
| Ana kavram | Gizli periyot / gizli yapı bulma |

---

## 11.4. Grover algoritması

Grover algoritması, kuantum algoritmalar arasında en bilinenlerden biridir. Bunun nedeni, çok genel bir problem sınıfına uygulanabilmesidir: yapılandırılmamış arama.

### Problem nedir?

Elimizde `N` elemanlı bir arama uzayı olduğunu düşünelim. Bu elemanlardan biri veya birkaçı “aranan” özelliğe sahiptir. Ama elimizde arama uzayını düzenli biçimde daraltmamızı sağlayacak bir yapı yoktur.

Klasik kaba kuvvet yaklaşımında ortalama olarak yaklaşık `N/2`, en kötü durumda `N` deneme gerekir.

Grover algoritması ideal koşullarda bu aramayı yaklaşık şu sorgu karmaşıklığına indirir:

```text
O(√N)
```

Bu, üstel değil ama çok önemli bir ikinci dereceden hızlanmadır.

### Temel fikir

Grover algoritmasının merkezinde iki bileşen vardır:

1. **Oracle:** Aranan çözüm durumlarını işaretler.
2. **Diffusion / amplitude amplification:** İşaretlenen durumların genliğini artırır.

Algoritma tüm durumların eşit süperpozisyonuyla başlar. Oracle doğru cevabın fazını değiştirir. Ardından diffusion işlemi, bu faz bilgisini genlik artışına dönüştürür. Bu süreç birkaç kez tekrarlandığında doğru cevabın ölçülme olasılığı artar.

Yalın anlatımla:

```text
Oracle doğru cevabı işaretler.
Girişim doğru cevabın genliğini büyütür.
Ölçüm doğru cevabı daha yüksek olasılıkla verir.
```

IBM Quantum kaynakları Grover algoritmasını amplitude amplification ile ilişkilendirir; algoritma doğru cevap durumunun olasılık genliğini artırarak ölçümde daha yüksek olasılıkla elde edilmesini sağlar.

### Neden önemlidir?

Grover algoritması şu yüzden önemlidir:

- Genel arama problemleri için kuantum hızlanma sağlar.
- Amplitude amplification tekniğini görünür hale getirir.
- Simetrik kriptografi açısından güvenlik parametrelerinin değerlendirilmesinde dikkate alınır.
- Çok sayıda kuantum algoritmada alt yordam veya fikirsel araç olarak kullanılır.

Grover algoritması “kuantum bilgisayar her şeyi üstel hızlandırır” iddiasını desteklemez. Aksine, bazı önemli problemlerde hızlanmanın sınırlı ama değerli olabileceğini gösterir.

### Kriptografi açısından etkisi

Grover algoritması, kaba kuvvet arama maliyetini karekök düzeyinde azaltabilir. Bu nedenle simetrik anahtar uzunlukları değerlendirilirken dikkate alınır.

Örneğin sezgisel olarak:

```text
128-bit güvenlik düzeyi, Grover etkisi altında yaklaşık 64-bit kaba kuvvet arama maliyeti gibi düşünülebilir.
```

Bu cümle dikkatli yorumlanmalıdır. Gerçek sistemlerde algoritmanın fiziksel maliyeti, hata düzeltme ihtiyacı, oracle uygulama maliyeti ve donanım ölçeği belirleyicidir. Ancak güvenlik tasarımında daha uzun anahtar boylarına yönelme fikrinin arkasında bu tür değerlendirmeler vardır.

### Pratik olgunluk

Grover algoritması teorik olarak güçlü ve genel bir algoritmadır. Fakat gerçek dünyada büyük ölçekli fayda üretmesi için güvenilir, derin devre çalıştırabilen, hata düzeltmeli kuantum bilgisayarlar gerekir. Bugünkü NISQ cihazlarda küçük gösterimler yapılabilir ama büyük pratik avantaj henüz beklenen olgunlukta değildir.

**Kısa değerlendirme:**

| Boyut | Değerlendirme |
|---|---|
| Teorik önem | Çok yüksek |
| Pratik kullanım | Orta-uzun vadeli |
| Öğretici değer | Çok yüksek |
| Ana kavram | Amplitude amplification |

---

## 11.5. Shor algoritması

Shor algoritması, kuantum bilgisayarların dünya çapında bu kadar stratejik önem kazanmasının ana nedenlerinden biridir. Çünkü büyük sayıların çarpanlara ayrılması ve ayrık logaritma gibi kriptografi açısından kritik problemlerle ilişkilidir.

### Problem nedir?

Shor algoritmasının en bilinen uygulaması şudur:

```text
Büyük bir N tam sayısını asal çarpanlarına ayırmak.
```

Klasik bilgisayarlar için büyük sayıların çarpanlara ayrılması çok zor kabul edilir. RSA gibi açık anahtarlı kriptografi sistemleri bu zorluğa dayanır.

Shor algoritması, yeterince büyük ve hataya dayanıklı bir kuantum bilgisayarda çarpanlara ayırma problemini polinom zamanda çözebilir.

### Temel fikir

Shor algoritması doğrudan “çarpanları aramak” şeklinde çalışmaz. Problem, matematiksel olarak bir **periyot bulma** problemine dönüştürülür.

Basitleştirilmiş akış şöyledir:

1. `N` ile aralarında asal bir `a` sayısı seçilir.
2. Şu fonksiyonun periyodu bulunmaya çalışılır:

```text
f(x) = a^x mod N
```

3. Kuantum bilgisayar, bu periyodu bulmak için Quantum Phase Estimation ve Quantum Fourier Transform benzeri yapıları kullanır.
4. Elde edilen periyot klasik post-processing ile çarpanlara dönüştürülür.

IBM Quantum Learning, Shor algoritmasını klasik-kuantum hibrit bir iş akışı olarak açıklar: klasik taraf bir taban seçer, kuantum taraf order finding işlemini yapar, klasik taraf da sonuçtan çarpanları hesaplar.

### Neden önemlidir?

Shor algoritması şu açıdan benzersizdir:

- Kriptografik etkisi çok büyüktür.
- Kuantum bilgisayarların yalnızca teorik oyuncaklar olmadığını, çok önemli bir problem sınıfında dramatik hızlanma potansiyeli taşıdığını gösterir.
- Phase estimation ve QFT gibi yapı taşlarının pratik önemini görünür hale getirir.
- Post-Quantum Cryptography çalışmalarının temel motivasyonlarından biridir.

### Bugün RSA kırıyor mu?

Hayır. Shor algoritmasının varlığı, bugünkü kuantum bilgisayarların büyük RSA anahtarlarını kırabildiği anlamına gelmez. Bunun için çok sayıda güvenilir mantıksal qubit, düşük hata oranı ve büyük ölçekli fault-tolerant kuantum hesaplama gerekir.

Bugünkü cihazlarda Shor algoritmasının küçük sayılar üzerinde gösterimleri yapılabilir. Ancak bunlar kriptografik ölçekte saldırı anlamına gelmez.

### Pratik olgunluk

Shor algoritması teorik olarak çok güçlüdür ama pratikte büyük ölçekli uygulanabilirliği henüz fault-tolerant kuantum bilgisayarların olgunlaşmasına bağlıdır.

**Kısa değerlendirme:**

| Boyut | Değerlendirme |
|---|---|
| Teorik önem | Çok yüksek |
| Pratik kullanım | Uzun vadeli / fault-tolerant donanım gerektirir |
| Kriptografik etki | Çok yüksek |
| Ana kavram | Periyot bulma + phase estimation + QFT |

---

## 11.6. Quantum Phase Estimation

Quantum Phase Estimation, tek başına bir algoritma gibi anlatılsa da aslında birçok önemli kuantum algoritmanın merkezinde yer alan temel bir alt yordamdır.

### Problem nedir?

Bir üniter işlem `U` ve bu işlemin özvektörü olan bir durum `|ψ⟩` olduğunu düşünelim:

```text
U|ψ⟩ = e^{2πiθ}|ψ⟩
```

Buradaki amaç, `θ` fazını tahmin etmektir.

### Temel fikir

Quantum Phase Estimation, kontrollü üniter işlemler, süperpozisyon ve inverse Quantum Fourier Transform kullanarak faz bilgisini ölçülebilir bit dizisine dönüştürür.

Basitleştirilmiş akış:

1. Yardımcı register süperpozisyona alınır.
2. Kontrollü `U`, `U²`, `U⁴`, `U⁸` gibi işlemler uygulanır.
3. Faz bilgisi yardımcı register’a kodlanır.
4. Inverse QFT ile bu faz bilgisi ölçülebilir hale getirilir.
5. Ölçüm sonucu `θ` için yaklaşık bir değer verir.

### Neden önemlidir?

Quantum Phase Estimation şu algoritmaların temel yapı taşlarından biridir:

- Shor algoritması
- HHL algoritması
- Kuantum kimya ve enerji tahmini algoritmaları
- Amplitude estimation türevleri

IBM Quantum dokümantasyonu Phase Estimation devresini Shor algoritması ve Quantum Amplitude Estimation gibi iyi bilinen algoritmalar için merkezi bir rutin olarak tanımlar.

### Pratik olgunluk

Phase Estimation çok güçlüdür, fakat yüksek doğruluk için derin devreler ve kontrollü üniter işlemler gerekir. Bu nedenle tam ölçekli kullanımı çoğunlukla hata düzeltmeli kuantum bilgisayar gerektirir.

NISQ döneminde daha sığ, varyasyonel veya iteratif alternatifler araştırılır; ancak klasik anlamda yüksek hassasiyetli phase estimation hâlâ donanım açısından zorludur.

**Kısa değerlendirme:**

| Boyut | Değerlendirme |
|---|---|
| Teorik önem | Çok yüksek |
| Pratik kullanım | Fault-tolerant döneme daha uygun |
| Öğretici değer | Yüksek |
| Ana kavram | Faz bilgisini ölçülebilir klasik bilgiye dönüştürme |

---

## 11.7. HHL algoritması

HHL algoritması, adını Aram Harrow, Avinatan Hassidim ve Seth Lloyd’dan alır. Lineer denklem sistemleri için geliştirilmiş en meşhur kuantum algoritmalardan biridir.

### Problem nedir?

Klasik lineer cebirde sık karşılaşılan problem şudur:

```text
A x = b
```

Burada `A` bir matris, `b` bilinen vektör, `x` ise bulunmak istenen çözümdür.

HHL algoritması, belirli şartlar altında `x` çözüm vektörünün tamamını klasik olarak üretmek yerine, bu çözüme karşılık gelen kuantum durumu hazırlar:

```text
|x⟩ ∝ A^{-1}|b⟩
```

### Temel fikir

HHL algoritması kabaca şu adımları içerir:

1. `b` vektörü kuantum durumuna hazırlanır.
2. `A` matrisinin özellikleri kuantum sistemde simüle edilir.
3. Quantum Phase Estimation ile özdeğer bilgisi çıkarılır.
4. Özdeğerlerin tersleriyle ilişkili kontrollü işlemler uygulanır.
5. Sonuçta `A^{-1}|b⟩` ile orantılı bir kuantum durum elde edilir.

### Kritik şartlar

HHL algoritmasının teorik hızlanması yalnızca bazı koşullar altında anlamlıdır:

- `A` matrisi seyrek olmalıdır.
- Matrisin koşul sayısı uygun olmalıdır.
- `|b⟩` durumunu verimli hazırlayabilmek gerekir.
- Kullanıcı çözüm vektörünün tüm elemanlarını klasik olarak okumak istememelidir.
- Çözümün belirli özellikleri kuantum durumda ölçülerek elde edilebilmelidir.

Bu son madde çok önemlidir. Eğer `x` vektörünün tüm elemanlarını klasik olarak okumak gerekiyorsa, okuma maliyeti kuantum avantajı azaltabilir veya ortadan kaldırabilir.

### Neden önemlidir?

Lineer sistemler bilim, mühendislik, optimizasyon, makine öğrenmesi ve simülasyon alanlarında çok yaygındır. Bu nedenle HHL algoritması büyük heyecan yaratmıştır. Teorik olarak bazı durumlarda klasik yöntemlere göre üstel hızlanma potansiyeli taşır.

Ancak bu potansiyel, problem yapısına ve veri erişim modeline çok bağımlıdır.

### Pratik olgunluk

HHL algoritması bugün daha çok teorik ve araştırma odaklıdır. Gerçek dünya problemlerinde avantaj göstermek için yüksek kaliteli, derin devre çalıştırabilen, hata düzeltmeli kuantum bilgisayarlar gerekir. Ayrıca veri yükleme ve sonuç okuma maliyetleri dikkatle analiz edilmelidir.

**Kısa değerlendirme:**

| Boyut | Değerlendirme |
|---|---|
| Teorik önem | Çok yüksek |
| Pratik kullanım | Henüz sınırlı |
| Ana risk | Veri hazırlama ve çıktı okuma maliyeti |
| Ana kavram | Kuantum lineer sistem çözümü |

---

## 11.8. VQE: Variational Quantum Eigensolver

VQE, NISQ dönemi için öne çıkan hibrit kuantum-klasik algoritmalardan biridir. Özellikle kuantum kimya ve malzeme simülasyonu bağlamında sık anılır.

### Problem nedir?

VQE’nin temel amacı, bir kuantum sistemin en düşük enerji durumunu yaklaşık olarak bulmaktır. Bu problem kuantum kimyada çok önemlidir.

Matematiksel olarak hedef, bir Hamiltonian için en düşük özdeğeri tahmin etmektir:

```text
H |ψ⟩ = E |ψ⟩
```

Burada en küçük `E` değeri, sistemin ground state enerjisini ifade eder.

### Temel fikir

VQE hibrit çalışır:

1. Klasik bilgisayar parametreli bir kuantum devresi seçer.
2. Kuantum bilgisayar bu devreyi çalıştırır ve ölçümler yapar.
3. Ölçümlerden enerji beklenti değeri hesaplanır.
4. Klasik optimizasyon algoritması parametreleri günceller.
5. Süreç daha düşük enerji bulunana kadar tekrar eder.

Bu akış şöyle özetlenebilir:

```text
Klasik optimizasyon → Parametreli kuantum devresi → Ölçüm → Enerji tahmini → Parametre güncelleme
```

Microsoft Azure Quantum dokümantasyonu VQE’yi, klasik bilgisayarın parametreli devreleri tanımladığı, kuantum durum ölçüldükten sonra klasik bilgisayarın parametreleri iyileştirdiği hibrit bir algoritma olarak açıklar.

### Neden önemlidir?

VQE’nin önemi şuradan gelir:

- Kimya ve malzeme bilimi kuantum bilgisayarların en doğal uygulama alanlarındandır.
- VQE, tam hata düzeltmeli sistemler beklenmeden NISQ cihazlarla denenebilir.
- Hibrit kuantum-klasik modelin en bilinen örneklerinden biridir.

### Sınırlamalar

VQE’nin de ciddi sınırlamaları vardır:

- Ölçüm sayısı çok yüksek olabilir.
- Klasik optimizasyon zorlaşabilir.
- Parametreli devre seçimi sonucu çok etkiler.
- Barren plateau adı verilen optimizasyon problemleri ortaya çıkabilir.
- Gürültülü donanım sonuç kalitesini bozabilir.

### Pratik olgunluk

VQE, bugünkü cihazlarla küçük ölçekli deneyler için uygundur. Ancak büyük moleküllerde klasik yöntemlere karşı genel ve net bir üstünlük henüz olgunlaşmış değildir. Buna rağmen NISQ döneminin en önemli algoritma ailelerinden biridir.

**Kısa değerlendirme:**

| Boyut | Değerlendirme |
|---|---|
| Teorik önem | Yüksek |
| NISQ uyumluluğu | Yüksek |
| Pratik avantaj | Henüz araştırma aşamasında |
| Ana kavram | Hibrit optimizasyon + enerji minimizasyonu |

---

## 11.9. QAOA: Quantum Approximate Optimization Algorithm

QAOA, kombinatoryal optimizasyon problemleri için geliştirilmiş hibrit bir kuantum algoritmadır. VQE gibi NISQ döneminde çok ilgi görmüştür.

### Problem nedir?

QAOA, MaxCut gibi kombinatoryal optimizasyon problemlerine yaklaşık çözümler üretmeyi hedefler.

Örneğin MaxCut probleminde bir grafın düğümleri iki kümeye ayrılır ve farklı kümelere düşen kenar sayısı maksimize edilmeye çalışılır.

### Temel fikir

QAOA’da problem bir maliyet Hamiltonian’ı olarak ifade edilir. Sonra iki tür işlem dönüşümlü uygulanır:

1. **Cost unitary:** Problemin maliyet fonksiyonuyla ilişkili dönüşüm.
2. **Mixer unitary:** Arama uzayında durumları karıştıran dönüşüm.

Bu işlemler `p` katman boyunca tekrar edilir:

```text
Cost → Mixer → Cost → Mixer → ...
```

Her katmanda ayarlanabilir parametreler vardır. Klasik optimizasyon algoritması bu parametreleri günceller.

QAOA’nın orijinal Farhi, Goldstone ve Gutmann çalışmasında algoritmanın yaklaşık kombinatoryal optimizasyon çözümleri üretmek için tasarlandığı ve `p` parametresi arttıkça yaklaşım kalitesinin iyileşebileceği anlatılır.

### Neden önemlidir?

QAOA şu açılardan önemlidir:

- Optimizasyon problemleri iş dünyasında çok yaygındır.
- NISQ cihazlara uygun sığ devrelerle denenebilir.
- Hibrit klasik-kuantum iş akışını temsil eder.
- Problemin yapısına göre özelleştirilebilir.

### Sınırlamalar

QAOA için de dikkatli olmak gerekir:

- Her optimizasyon problemi kuantum avantaj sağlamaz.
- Parametre optimizasyonu zor olabilir.
- Derinlik arttıkça gürültü etkisi büyür.
- Klasik sezgisel algoritmalar çoğu pratik problemde çok güçlüdür.
- Avantaj iddiası problem sınıfı, donanım ve ölçekle birlikte değerlendirilmelidir.

### Pratik olgunluk

QAOA bugün aktif araştırma alanıdır. Küçük ve orta ölçekli deneyler yapılabilir, fakat genel iş problemlerinde klasik optimizasyon yöntemlerini sistematik olarak geride bıraktığı söylenemez.

**Kısa değerlendirme:**

| Boyut | Değerlendirme |
|---|---|
| Teorik önem | Yüksek |
| NISQ uyumluluğu | Yüksek |
| Pratik avantaj | Henüz belirsiz / problem bağımlı |
| Ana kavram | Hibrit yaklaşık optimizasyon |

---

## 11.10. Algoritmaların pratik olgunluk karşılaştırması

Kuantum algoritmaları değerlendirirken yalnızca “ne kadar etkileyici hızlanma vaat ediyor?” sorusu yeterli değildir. Şu sorular birlikte sorulmalıdır:

- Algoritmanın teorik hızlanması hangi varsayımlara dayanıyor?
- Problem girdisi kuantum bilgisayara nasıl yüklenecek?
- Çıktının tamamı mı gerekiyor, yoksa sadece belirli bir özelliği mi?
- Devre derinliği bugünkü donanımla uygulanabilir mi?
- Hata düzeltme gerekiyor mu?
- Klasik algoritmalar aynı problemde ne kadar güçlü?
- Gerçek dünya problemi algoritmanın varsayımlarına uyuyor mu?

Aşağıdaki tablo, bu bölümde ele alınan algoritmaları yüksek seviyede karşılaştırır.

| Algoritma | Ana problem | Temel kuantum fikir | Teorik önem | Bugünkü pratik olgunluk | Tipik donanım ihtiyacı |
|---|---|---|---|---|---|
| Deutsch-Jozsa | Sabit/dengeli fonksiyon ayrımı | Süperpozisyon, oracle, girişim | Yüksek | Eğitim amaçlı | Küçük devreler |
| Bernstein-Vazirani | Gizli bit dizisini bulma | Phase kickback | Orta-yüksek | Eğitim amaçlı | Küçük devreler |
| Simon | Gizli periyot/yapı bulma | Süperpozisyon, ölçüm, lineer denklem | Çok yüksek | Teorik/eğitim | Küçük-orta devreler |
| Grover | Yapılandırılmamış arama | Amplitude amplification | Çok yüksek | Büyük avantaj için erken | Hata düzeltmeli sistemler tercih edilir |
| Shor | Çarpanlara ayırma, ayrık logaritma | Period finding, QPE, QFT | Çok yüksek | Kriptografik ölçekte henüz yok | Büyük fault-tolerant sistem |
| Quantum Phase Estimation | Faz/özdeğer tahmini | Kontrollü üniterler, inverse QFT | Çok yüksek | Derin devre ihtiyacı nedeniyle sınırlı | Hata düzeltmeli sistem |
| HHL | Lineer sistemler | QPE, matris tersleme, kuantum durum çıktısı | Çok yüksek | Şartlı ve araştırma odaklı | Hata düzeltmeli sistem |
| VQE | Ground state enerji tahmini | Hibrit optimizasyon | Yüksek | NISQ deneyleri için uygun | NISQ + klasik optimizasyon |
| QAOA | Kombinatoryal optimizasyon | Cost/mixer katmanları, hibrit optimizasyon | Yüksek | Araştırma ve PoC düzeyi | NISQ + klasik optimizasyon |

### Kavramsal sınıflandırma

Bu algoritmaları birkaç ana aileye ayırabiliriz.

#### 1. Oracle ve sorgu modeli algoritmaları

- Deutsch-Jozsa
- Bernstein-Vazirani
- Simon
- Grover

Bu algoritmalar, kuantum bilgisayarların oracle’a daha az sorgu yaparak bilgi çıkarabileceğini gösterir. Eğitim açısından çok değerlidirler.

#### 2. Periyot, faz ve spektral bilgi algoritmaları

- Shor
- Quantum Phase Estimation
- HHL

Bu algoritmalar matematiksel yapıdan yararlanır. Genellikle derin devreler ve yüksek doğruluk gerektirir. Uzun vadede fault-tolerant kuantum bilgisayarlarla daha anlamlı hale gelirler.

#### 3. Hibrit varyasyonel algoritmalar

- VQE
- QAOA

Bu algoritmalar NISQ döneminde öne çıkmıştır. Klasik bilgisayar ve kuantum bilgisayar birlikte çalışır. Bugün denenebilir olmaları avantajdır, ancak pratik üstünlükleri problem ve donanım koşullarına bağlıdır.

### Pratik beklenti açısından sıralama

Aşağıdaki değerlendirme kesin bir gelecek tahmini değil, bugünkü olgunluk ve beklenti düzeyine göre yaklaşık bir çerçevedir.

#### Eğitim ve kavram öğretimi için en uygunlar

1. Deutsch-Jozsa
2. Bernstein-Vazirani
3. Grover
4. Bell state ve teleportation gibi protokollerle birlikte Simon öncesi hazırlık örnekleri

#### Teorik kuantum avantajı anlamak için en önemliler

1. Simon
2. Shor
3. Grover
4. HHL
5. Quantum Phase Estimation

#### Kurumsal PoC için daha sık gündeme gelenler

1. VQE
2. QAOA
3. Grover türevi arama/amplitude amplification senaryoları
4. Kuantum simülasyon yaklaşımları

#### Kriptografi açısından en kritik olanlar

1. Shor
2. Grover

Shor açık anahtarlı kriptografi için, Grover ise simetrik anahtar güvenliği değerlendirmeleri için önemlidir.

---

## Bölüm özeti

Bu bölümde kuantum algoritmaların en önemli örneklerini inceledik. Gördüğümüz ana fikirler şunlardır:

- Kuantum algoritmalar, klasik algoritmaların sadece daha hızlı çalışan sürümleri değildir.
- Deutsch-Jozsa ve Bernstein-Vazirani algoritmaları, kuantum sorgu modelinin gücünü öğretici biçimde gösterir.
- Simon algoritması, Shor algoritmasına giden yolda gizli yapı ve periyot bulma fikrini öne çıkarır.
- Grover algoritması, yapılandırılmamış arama problemlerinde karekök düzeyinde hızlanma sağlar.
- Shor algoritması, kriptografi açısından en stratejik kuantum algoritmalardan biridir.
- Quantum Phase Estimation, birçok büyük algoritmanın temel alt yordamıdır.
- HHL algoritması lineer sistemlerde teorik olarak güçlüdür, ancak veri yükleme ve çıktı okuma şartları nedeniyle dikkatle değerlendirilmelidir.
- VQE ve QAOA, NISQ döneminin en bilinen hibrit algoritmalarıdır; bugün deney yapılabilir ama genel pratik üstünlük iddiası için hâlâ temkinli olunmalıdır.

Bu bölümün en önemli mesajı şudur:

```text
Kuantum algoritmanın değeri yalnızca teorik hızlanmasına bakılarak anlaşılmaz.
Problem yapısı, veri erişimi, çıktı ihtiyacı, devre derinliği, hata oranı ve klasik alternatifler birlikte değerlendirilmelidir.
```

---

## Kaynaklar ve ileri okuma

- IBM Quantum Learning — The Deutsch-Jozsa algorithm  
  https://quantum.cloud.ibm.com/learning/en/courses/fundamentals-of-quantum-algorithms/quantum-query-algorithms/deutsch-jozsa-algorithm

- IBM Quantum Learning — Quantum query algorithms introduction  
  https://quantum.cloud.ibm.com/learning/en/courses/fundamentals-of-quantum-algorithms/quantum-query-algorithms/introduction

- IBM Quantum Documentation — Grover's algorithm  
  https://quantum.cloud.ibm.com/docs/tutorials/grovers-algorithm

- IBM Quantum Learning — Grover algorithm  
  https://quantum.cloud.ibm.com/learning/en/courses/utility-scale-quantum-computing/grovers-algorithm

- IBM Quantum Learning — Shor's algorithm  
  https://quantum.cloud.ibm.com/learning/courses/fundamentals-of-quantum-algorithms/phase-estimation-and-factoring/shor-algorithm

- IBM Quantum Documentation — PhaseEstimation  
  https://quantum.cloud.ibm.com/docs/api/qiskit/qiskit.circuit.library.PhaseEstimation

- Microsoft Learn — Hybrid quantum computing concepts  
  https://learn.microsoft.com/en-us/azure/quantum/hybrid-computing-concepts

- Harrow, Hassidim, Lloyd — Quantum algorithm for solving linear systems of equations  
  https://arxiv.org/abs/0811.3171

- Farhi, Goldstone, Gutmann — A Quantum Approximate Optimization Algorithm  
  https://arxiv.org/abs/1411.4028

- Adedoyin et al. — Quantum Algorithm Implementations for Beginners  
  https://www.osti.gov/pages/servlets/purl/1993220
