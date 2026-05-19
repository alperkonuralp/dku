+++
title = "25. Ekler"
description = "Terimler sözlüğü, kaynak listesi ve ek referans materyalleri."
date = "2026-05-18T00:00:00+03:00"
weight = 25
type = "guide"
draft = false
+++

Bu bölüm, dokümanın önceki bölümlerinde kullanılan kavramları hızlıca hatırlamak, temel matematiksel notasyonu görmek, kuantum kapıları ve algoritmaları karşılaştırmak, donanım yaklaşımlarını yan yana değerlendirmek ve Post-Quantum Cryptography tarafındaki temel standartları özetlemek için hazırlanmıştır.

Ekler bölümü, dokümanın ana gövdesindeki anlatımın yerine geçmez. Daha çok **hızlı başvuru**, **tekrar**, **eğitim hazırlığı**, **sunum çıkarımı** ve **kurumsal değerlendirme** sırasında kullanılabilecek bir referans alanı olarak düşünülmelidir.

---

## 25.1. Temel kavramlar sözlüğü

### Bit

Klasik bilgisayarın temel bilgi birimidir. Bir bit, ideal düzeyde iki değerden birini temsil eder:

```text
0 veya 1
```

Klasik işlemcilerde bu değerler fiziksel olarak elektriksel gerilim seviyeleri, transistor durumları veya manyetik/fiziksel durumlar üzerinden temsil edilir. Yazılım açısından bitler, daha büyük veri yapılarını oluşturmak için bir araya gelir.

---

### Qubit

Kuantum bilgisayarın temel bilgi birimidir. Qubit ölçüldüğünde klasik bir bit gibi 0 veya 1 sonucu verir; fakat ölçümden önce kuantum mekaniksel bir durumla temsil edilir.

Genel tek qubit durumu şöyle yazılabilir:

```text
|ψ⟩ = α|0⟩ + β|1⟩
```

Burada `α` ve `β` olasılık değil, **olasılık genliği**dir. Ölçüm sonucunda 0 veya 1 elde etme olasılığı bu genliklerin mutlak değerlerinin karesiyle ilişkilidir.

---

### Süperpozisyon

Bir kuantum sisteminin birden fazla temel durumun lineer birleşimi halinde temsil edilmesidir.

Tek qubit için örnek:

```text
|ψ⟩ = 1/√2 |0⟩ + 1/√2 |1⟩
```

Bu durum ölçüldüğünde yaklaşık %50 olasılıkla 0, %50 olasılıkla 1 sonucu verir. Ancak süperpozisyonu yalnızca "aynı anda hem 0 hem 1" diye anlatmak eksiktir. Asıl önemli olan, durumun olasılık genlikleri ve faz bilgisiyle tanımlanmasıdır.

---

### Olasılık genliği

Kuantum durumunu tanımlayan karmaşık sayıdır. Klasik olasılıktan farklıdır. Olasılık genlikleri toplanabilir, birbirini güçlendirebilir veya birbirini sönümleyebilir.

Bir sonucun ölçüm olasılığı, ilgili genliğin mutlak değerinin karesiyle hesaplanır:

```text
P(0) = |α|²
P(1) = |β|²
```

---

### Faz

Olasılık genliğinin yalnızca büyüklüğü değil, yönü/fazı da vardır. Faz bilgisi ölçüm olasılığında doğrudan görünmeyebilir; fakat kuantum kapıları ve girişim yoluyla hesaplamanın sonucunu etkileyebilir.

Bu nedenle kuantum algoritmalarda faz bilgisi kritik öneme sahiptir.

---

### Ölçüm

Kuantum sistemden klasik bilgi alma işlemidir. Ölçüm yapıldığında qubitin kuantum durumu, ölçüm bazına göre klasik bir sonuca dönüşür.

Ölçüm, klasik programlamadaki "değeri okumak" işlemine benzemez. Çünkü ölçüm, sistemin kuantum durumunu etkiler.

---

### Dolaşıklık

İki veya daha fazla qubitin durumlarının ayrı ayrı değil, ortak bir kuantum durumuyla tanımlanmasıdır.

Örnek Bell state:

```text
(|00⟩ + |11⟩) / √2
```

Bu durumda iki qubit ayrı ayrı bağımsız sistemler gibi düşünülemez. Bir qubit ölçüldüğünde diğer qubitin sonucu onunla korelasyonlu olur. Ancak bu durum ışıktan hızlı iletişim anlamına gelmez.

---

### Girişim

Olasılık genliklerinin birbirini güçlendirmesi veya zayıflatmasıdır. Kuantum algoritmaların önemli bir kısmı, doğru cevaba ait genlikleri güçlendirmeye, yanlış cevaplara ait genlikleri bastırmaya çalışır.

Süperpozisyon olasılık alanını açar; girişim ise hesaplamanın yönünü belirler.

---

### Kuantum kapısı

Qubitlerin kuantum durumlarını değiştiren işlemdir. Klasik mantık kapılarından farklı olarak kuantum kapıları genellikle tersinir, lineer ve üniter dönüşümlerle temsil edilir.

Örnek kapılar:

```text
X, Y, Z, H, S, T, CNOT, CZ, SWAP
```

---

### Kuantum devresi

Kuantum kapılarının ve ölçümlerin belirli bir sırayla uygulandığı hesaplama modelidir. Devrede yatay çizgiler qubitleri, kutular veya semboller kuantum kapılarını, ölçüm sembolleri ise klasik sonucun alındığı noktaları gösterir.

---

### Oracle

Bazı kuantum algoritmalarda kullanılan özel bir kara kutu fonksiyondur. Oracle, aranan özelliğe sahip durumları işaretler veya fazlarını değiştirir.

Grover algoritmasında oracle, doğru cevabı doğrudan vermez; doğru cevaba karşılık gelen durumu işaretler.

---

### Amplitude amplification

Doğru veya aranan çözümlerin olasılık genliğini artırmaya yarayan kuantum algoritma tekniğidir. Grover algoritması bunun en bilinen örneklerinden biridir.

---

### Quantum Fourier Transform

Klasik Fourier dönüşümünün kuantum hesaplama içindeki karşılığıdır. Özellikle periyot bulma, phase estimation ve Shor algoritması gibi yapılarda önemli bir alt yordamdır.

---

### Quantum Phase Estimation

Bir üniter işlemin özdeğer fazını tahmin etmeye yarayan temel kuantum algoritma bileşenidir. Shor algoritması, HHL ve bazı kuantum simülasyon yaklaşımları açısından önemlidir.

---

### NISQ

"Noisy Intermediate-Scale Quantum" ifadesinin kısaltmasıdır. Bugünkü birçok kuantum cihazı bu sınıfa girer: belirli sayıda qubit vardır, fakat cihazlar gürültülüdür ve tam hata düzeltmeli değildir.

NISQ dönemi, kuantum algoritmaları ve donanımları test etmek için değerlidir; ancak geniş ölçekli, güvenilir, üretim seviyesi kuantum hesaplama anlamına gelmez.

---

### Decoherence

Kuantum sistemin çevresiyle etkileşerek kuantum özelliklerini kaybetmesi veya bozulmasıdır. Decoherence, kuantum bilgisayarların güvenilir çalışmasını zorlaştıran temel problemlerden biridir.

---

### Fiziksel qubit

Donanımda gerçekten kontrol edilen qubittir. Süperiletken devre, iyon, atom, foton, spin veya başka fiziksel sistemlerle temsil edilebilir.

---

### Mantıksal qubit

Birden fazla fiziksel qubit kullanılarak hata düzeltme kodlarıyla oluşturulan daha güvenilir qubittir. Büyük ölçekli, hataya dayanıklı kuantum bilgisayarlar için mantıksal qubitler kritik öneme sahiptir.

---

### Quantum error correction

Kuantum sistemlerde oluşan hataları tespit edip düzeltmeye çalışan yöntemler bütünüdür. Klasik hata düzeltmeden farklıdır; çünkü qubitler doğrudan kopyalanamaz ve ölçüm kuantum durumunu bozabilir.

---

### Surface code

Kuantum hata düzeltmede en çok çalışılan yaklaşımlardan biridir. Qubitlerin iki boyutlu bir düzende yerleştirilmesi ve yerel ölçümlerle hata bilgisinin çıkarılması fikrine dayanır. Ölçeklenebilir fault-tolerant kuantum bilgisayar hedeflerinde sıkça gündeme gelir.

---

### Threshold

Kuantum hata düzeltmede fiziksel hata oranlarının belirli bir eşiğin altında olması gerektiğini ifade eder. Hata oranları threshold'un altına indiğinde, daha fazla fiziksel qubit kullanarak mantıksal hata oranını bastırmak teorik ve deneysel olarak mümkün hale gelir.

---

### Fault-tolerant quantum computing

Hatalar oluşmasına rağmen hesaplamanın güvenilir biçimde sürdürülebildiği kuantum hesaplama yaklaşımıdır. Pratik, büyük ölçekli kuantum bilgisayarlar için temel hedeftir.

---

### Quantum advantage

Bir kuantum bilgisayarın belirli bir problemi klasik yöntemlerden daha iyi, daha hızlı, daha ucuz veya daha anlamlı biçimde çözebilmesi durumudur.

---

### Quantum supremacy

Bir kuantum bilgisayarın, klasik bilgisayarlar için pratik olmayan belirli bir görevi gerçekleştirdiğini gösteren kavramdır. Bu kavram genellikle dar ve deneysel bir gösterime işaret eder; doğrudan ticari fayda anlamına gelmeyebilir.

---

### Quantum as a Service

Kuantum bilgisayarlara bulut servisleri üzerinden erişme modelidir. IBM Quantum, Azure Quantum, Amazon Braket ve benzeri platformlar bu yaklaşımın örnekleri arasında sayılabilir.

---

### Post-Quantum Cryptography

Klasik bilgisayarlarda çalışan, fakat kuantum bilgisayarlarla yapılabilecek saldırılara karşı dayanıklı olması hedeflenen kriptografik algoritmalar alanıdır.

---

### Quantum cryptography

Kuantum fiziği ilkelerini kullanarak güvenli iletişim veya anahtar dağıtımı yapmayı hedefleyen alandır. Post-Quantum Cryptography ile karıştırılmamalıdır.

---

## 25.2. Matematiksel notasyon kısa rehberi

Bu doküman matematiksel olarak ağır bir kuantum mekaniği kitabı değildir. Yine de bazı sembolleri anlamak, kuantum bilgisayarları doğru kavramak için faydalıdır.

### Ket gösterimi

Kuantum durumları genellikle Dirac notasyonu ile yazılır:

```text
|0⟩
|1⟩
|ψ⟩
```

Buradaki `|ψ⟩`, "psi ket" olarak okunur ve bir kuantum durumunu temsil eder.

---

### Bra gösterimi

Ket'in eşleniği gibi düşünülebilecek gösterimdir:

```text
⟨ψ|
```

Bra-ket notasyonu kuantum mekaniğinde iç çarpım, ölçüm ve durum dönüşümlerini yazmak için kullanılır.

---

### Temel durumlar

Tek qubit için en yaygın temel durumlar:

```text
|0⟩
|1⟩
```

Bunlar ölçüm sonucunda elde edilebilecek klasik 0 ve 1 sonuçlarıyla ilişkilidir.

---

### Genel tek qubit durumu

```text
|ψ⟩ = α|0⟩ + β|1⟩
```

Burada:

```text
α: |0⟩ durumunun olasılık genliği
β: |1⟩ durumunun olasılık genliği
```

Normalizasyon koşulu:

```text
|α|² + |β|² = 1
```

Bu koşul, ölçüm sonucunda olasılıkların toplamının 1 olması gerektiğini ifade eder.

---

### Ölçüm olasılığı

Eğer qubit durumu şöyleyse:

```text
|ψ⟩ = α|0⟩ + β|1⟩
```

Ölçüm sonucunda:

```text
0 gelme olasılığı = |α|²
1 gelme olasılığı = |β|²
```

---

### İki qubit durumu

İki qubitli bir sistem şöyle yazılabilir:

```text
|ψ⟩ = α|00⟩ + β|01⟩ + γ|10⟩ + δ|11⟩
```

Normalizasyon:

```text
|α|² + |β|² + |γ|² + |δ|² = 1
```

İki qubitli sistemde dört temel durum vardır:

```text
|00⟩
|01⟩
|10⟩
|11⟩
```

---

### n qubit için durum uzayı

n qubitlik bir sistemde temel durum sayısı:

```text
2ⁿ
```

Örneğin:

| Qubit sayısı | Temel durum sayısı |
|---:|---:|
| 1 | 2 |
| 2 | 4 |
| 3 | 8 |
| 10 | 1.024 |
| 20 | 1.048.576 |
| 50 | 1.125.899.906.842.624 |

Bu büyüme kuantum sistemlerin klasik bilgisayarla simüle edilmesini zorlaştırır. Ancak bu, kuantum bilgisayarın bütün durumları doğrudan okuyabildiği anlamına gelmez. Ölçüm sonucunda yine klasik bit dizisi elde edilir.

---

### Matris gösterimi

Kuantum kapıları genellikle matrislerle temsil edilir.

Örneğin X kapısı:

```text
X = [0 1
     1 0]
```

X kapısı, klasik NOT kapısına benzer şekilde `|0⟩` ile `|1⟩` durumlarını değiştirir:

```text
X|0⟩ = |1⟩
X|1⟩ = |0⟩
```

---

### Hadamard kapısı

Hadamard kapısı, temel durumları süperpozisyona taşır:

```text
H|0⟩ = (|0⟩ + |1⟩) / √2
H|1⟩ = (|0⟩ - |1⟩) / √2
```

Hadamard, kuantum algoritmalarda süperpozisyon hazırlamak için sık kullanılır.

---

### Tensor çarpımı

Birden fazla qubitli sistemleri ifade etmek için tensor çarpımı kullanılır.

Örneğin:

```text
|0⟩ ⊗ |1⟩ = |01⟩
```

Kısa gösterim genellikle şu şekildedir:

```text
|0⟩|1⟩ = |01⟩
```

---

### Üniter dönüşüm

Kuantum kapılarının çoğu üniter matrislerle temsil edilir. Üniter dönüşümler tersinirdir ve toplam olasılığı korur.

Basit sezgi:

```text
Kuantum kapısı, kuantum durumunu bozmadan başka bir geçerli kuantum durumuna dönüştürür.
```

---

### Global faz

Bir kuantum durumunun tamamına aynı faz çarpanı uygulanırsa, ölçüm sonuçları değişmeyebilir.

Örneğin:

```text
|ψ⟩
- |ψ⟩
```

Bu iki durum, yalnız başına ölçüm açısından aynı fiziksel durumu temsil edebilir. Ancak göreli fazlar, yani durum bileşenleri arasındaki faz farkları kuantum girişim açısından önemlidir.

---

### Göreli faz

Şu iki durum ölçüm olasılıkları açısından aynı görünebilir:

```text
(|0⟩ + |1⟩) / √2
(|0⟩ - |1⟩) / √2
```

Her ikisinde de 0 ve 1 ölçme olasılığı %50'dir. Fakat faz farkı farklıdır. Bu fark sonraki kuantum kapılarında girişim yoluyla hesaplama sonucunu değiştirebilir.

---

## 25.3. Kuantum kapıları hızlı referans tablosu

Aşağıdaki tablo temel kuantum kapılarını hızlıca hatırlamak için hazırlanmıştır.

| Kapı | Qubit sayısı | Temel etkisi | Kısa açıklama | Tipik kullanım |
|---|---:|---|---|---|
| I | 1 | Durumu değiştirmez | Identity kapısıdır | Devre hizalama, teorik gösterim |
| X | 1 | `|0⟩ ↔ |1⟩` | Klasik NOT kapısına benzer | Bit flip, koşullu dönüşüm |
| Y | 1 | Bit flip + faz etkisi | Pauli-Y dönüşümü | Teorik analiz, rotasyonlar |
| Z | 1 | `|1⟩` fazını değiştirir | Phase flip uygular | Faz kontrolü, girişim |
| H | 1 | Süperpozisyon oluşturur | Hadamard kapısıdır | Süperpozisyon, Bell state, Grover başlangıcı |
| S | 1 | Fazı π/2 döndürür | Phase gate | Faz manipülasyonu |
| T | 1 | Fazı π/4 döndürür | π/8 gate olarak da bilinir | Evrensel kuantum hesaplama, fault-tolerant setler |
| Rx | 1 | X ekseni etrafında rotasyon | Parametrik dönüşüm | VQE, QAOA, variational devreler |
| Ry | 1 | Y ekseni etrafında rotasyon | Parametrik dönüşüm | Hibrit algoritmalar |
| Rz | 1 | Z ekseni etrafında rotasyon | Faz rotasyonu | Faz kodlama, variational devreler |
| CNOT / CX | 2 | Kontrol 1 ise hedefi çevirir | Kontrollü NOT | Dolaşıklık oluşturma, Bell state |
| CZ | 2 | `|11⟩` durumuna faz uygular | Kontrollü Z | Graph state, faz tabanlı algoritmalar |
| SWAP | 2 | İki qubitin durumunu değiştirir | Qubit yer değiştirme | Donanım bağlantı sınırlamalarında routing |
| Toffoli / CCX | 3 | İki kontrol 1 ise hedefi çevirir | Kontrollü kontrollü NOT | Tersinir klasik mantık, oracle tasarımı |
| Fredkin / CSWAP | 3 | Kontrole göre iki qubiti değiştirir | Kontrollü SWAP | Test algoritmaları, kontrollü yönlendirme |

---

### X kapısı

Klasik NOT kapısına en yakın kuantum kapısıdır.

```text
X|0⟩ = |1⟩
X|1⟩ = |0⟩
```

Ancak süperpozisyondaki bir qubit üzerinde çalıştığında yalnızca klasik 0/1 dönüşümü gibi düşünülmemelidir. Tüm kuantum durum vektörü üzerinde işlem yapar.

---

### Z kapısı

Z kapısı ölçüm sonucunu doğrudan değiştirmeyebilir; fakat fazı değiştirir.

```text
Z|0⟩ = |0⟩
Z|1⟩ = -|1⟩
```

Bu faz farkı, daha sonraki girişim adımlarında önemli hale gelebilir.

---

### Hadamard kapısı

Hadamard kapısı kuantum hesaplamada en sık karşılaşılan kapılardan biridir.

```text
H|0⟩ = (|0⟩ + |1⟩) / √2
H|1⟩ = (|0⟩ - |1⟩) / √2
```

Birçok algoritma, başlangıçta qubitleri Hadamard kapılarıyla süperpozisyona alır.

---

### CNOT kapısı

CNOT iki qubit üzerinde çalışır:

```text
Kontrol qubit = 0 ise hedef değişmez.
Kontrol qubit = 1 ise hedef X kapısı ile çevrilir.
```

CNOT, dolaşıklık oluşturmak için temel kapılardan biridir.

Örneğin:

```text
|00⟩
H birinci qubite uygulanır
CNOT uygulanır
Sonuç: (|00⟩ + |11⟩) / √2
```

Bu, Bell state üretmenin en temel yollarından biridir.

---

### SWAP kapısı

İki qubitin durumunu değiştirir:

```text
SWAP |01⟩ = |10⟩
SWAP |10⟩ = |01⟩
```

Gerçek donanımlarda her qubit her qubitle doğrudan bağlantılı olmayabilir. Bu durumda SWAP kapıları, qubit durumlarını bağlantı topolojisine uygun hale getirmek için kullanılır.

---

### Parametrik rotasyon kapıları

Variational algoritmalarda sık görülür:

```text
Rx(θ)
Ry(θ)
Rz(θ)
```

Buradaki `θ`, klasik optimizasyon algoritması tarafından güncellenebilen bir parametre olabilir. VQE ve QAOA gibi hibrit algoritmalar bu tür kapılardan yoğun biçimde yararlanır.

---

## 25.4. Algoritma karşılaştırma tablosu

Aşağıdaki tablo, dokümanda anlatılan önemli kuantum algoritmaları karşılaştırmalı olarak özetler.

| Algoritma | Problem tipi | Temel fikir | Teorik önemi | Pratik olgunluk | Not |
|---|---|---|---|---|---|
| Deutsch-Jozsa | Fonksiyon özelliği belirleme | Tek sorguda sabit/dengeli ayrımı | Eğitimsel olarak çok önemli | Düşük | Pratik faydadan çok kuantum algoritma sezgisi sağlar |
| Bernstein-Vazirani | Gizli bit dizisi bulma | Oracle üzerinden gizli diziyi çıkarma | Kuantum sorgu avantajını gösterir | Düşük | Eğitim ve temel algoritma anlatımı için değerlidir |
| Simon | Gizli periyot/yapı problemi | Fonksiyon yapısından gizli maskeyi bulma | Shor'a giden teorik yolu açar | Düşük | Pratikten çok teorik önemi büyüktür |
| Grover | Yapılandırılmamış arama | Amplitude amplification | Genel aramada karekök hızlanma | Orta-düşük | Faydalı ama hata düzeltme ve oracle maliyeti önemlidir |
| Shor | Çarpanlara ayırma, ayrık logaritma | Period finding + QFT + phase estimation | Kriptografi açısından çok kritik | Bugün düşük, uzun vadede yüksek etki | RSA, DH, ECC için stratejik tehdit |
| Quantum Phase Estimation | Faz/özdeğer tahmini | Kontrollü üniterler ve QFT | Birçok algoritmanın temel bileşeni | Orta-düşük | HHL, Shor, simülasyon için merkezi rol oynar |
| HHL | Lineer denklem sistemleri | Kuantum durum olarak çözüm üretme | Teorik hızlanma iddiası güçlü | Düşük | Veri yükleme ve sonuç okuma kısıtları önemlidir |
| VQE | Molekül enerjisi, kuantum kimya | Parametrik kuantum devresi + klasik optimizasyon | NISQ dönemi için önemli | Orta | Kimya ve malzeme simülasyonu için araştırma değeri yüksek |
| QAOA | Kombinatoryal optimizasyon | Parametrik kuantum devresi + klasik optimizasyon | Optimizasyon için önemli hibrit yaklaşım | Orta-düşük | Klasik yöntemlerle rekabeti problem ve donanıma bağlıdır |

---

### Eğitimsel algoritmalar

Deutsch-Jozsa, Bernstein-Vazirani ve Simon algoritmaları pratik üretim problemlerinden çok kuantum hesaplama mantığını öğretmek açısından önemlidir.

Bu algoritmalar şu sorulara cevap verir:

```text
Kuantum sorgu modeli klasik sorgu modelinden nasıl farklıdır?
Oracle kullanımı ne anlama gelir?
Süperpozisyon ve girişim algoritmik avantaja nasıl dönüşebilir?
```

---

### Stratejik algoritmalar

Shor ve Grover, stratejik etkileri nedeniyle ayrı önem taşır.

Shor algoritması, yeterince büyük ve hataya dayanıklı kuantum bilgisayarlar ortaya çıktığında bugünkü açık anahtarlı kriptografi üzerinde ciddi etki yaratabilir.

Grover algoritması, simetrik anahtar arama problemleri için karekök düzeyinde hızlanma sağlar. Bu nedenle simetrik kriptografide anahtar uzunlukları açısından dikkate alınır.

---

### Hibrit NISQ algoritmaları

VQE ve QAOA, bugünkü gürültülü kuantum cihazlarla çalıştırılabilen hibrit yaklaşımlardır.

Genel akış:

```text
1. Klasik bilgisayar parametreleri belirler.
2. Kuantum devresi çalıştırılır.
3. Ölçüm sonuçları klasik bilgisayara döner.
4. Klasik optimizasyon parametreleri günceller.
5. Döngü tekrar eder.
```

Bu yaklaşım bugünkü cihazlara daha uygundur; ancak geniş ticari avantaj henüz garanti değildir.

---

## 25.5. Donanım yaklaşımları karşılaştırma tablosu

Kuantum bilgisayar donanımı için tek bir baskın yaklaşım henüz kesinleşmiş değildir. Farklı teknolojiler farklı avantajlar ve zorluklar taşır.

| Yaklaşım | Qubit fiziksel temeli | Güçlü yönler | Zorluklar | Olgunluk yorumu |
|---|---|---|---|---|
| Süperiletken qubitler | Süperiletken devreler | Hızlı gate süreleri, güçlü endüstri yatırımı, entegre devre üretim deneyimi | Çok düşük sıcaklık, decoherence, kablolama ve ölçekleme | IBM, Google ve Rigetti gibi oyuncularla en görünür yaklaşımlardan biri |
| Hapsedilmiş iyonlar | Elektromanyetik alanlarla tutulan iyonlar | Yüksek doğruluk, uzun coherence süreleri, tümden-tüme bağlantı potansiyeli | Gate hızları daha yavaş olabilir, ölçekleme mühendisliği zor | IonQ ve Quantinuum gibi oyuncularla güçlü araştırma/ürünleşme alanı |
| Nötr atomlar | Lazer cımbızlarıyla tutulan atomlar | Büyük atom dizileri, esnek geometri, ölçekleme potansiyeli | Gate kalitesi, kontrol, hata düzeltme entegrasyonu | Son yıllarda hızlı ilerleyen alanlardan biri |
| Fotonik | Işık parçacıkları | İletişimle doğal uyum, oda sıcaklığına yakın çalışma potansiyeli | Kayıp yönetimi, kaynak/detektör kalitesi, ölçekli gate tasarımı | Xanadu, PsiQuantum gibi oyuncularla önemli ama zorlu alan |
| Spin qubitler | Elektron/nükleer spin durumları | Yarı iletken üretim altyapısıyla uyum potansiyeli | Hassas kontrol, bağlantı, uniform üretim | Intel, QuTech ve akademik çalışmalarla gelişen alan |
| Topolojik qubitler | Topolojik kuantum durumları / Majorana tabanlı yaklaşımlar | Teorik olarak daha hata dayanıklı qubit potansiyeli | Deneysel kanıt, üretim ve kontrol çok zor | Yüksek potansiyelli ama tartışmalı ve erken aşama |
| Quantum annealing | Enerji minimizasyonu / Ising benzeri sistemler | Optimizasyon problemleri için özel yaklaşım, mevcut ticari erişim | Evrensel gate-based kuantum bilgisayar değildir, avantaj tartışmalıdır | D-Wave ile bilinen özel amaçlı model |

---

### Donanım değerlendirmesinde dikkat edilecek metrikler

Donanım yaklaşımlarını yalnızca qubit sayısıyla karşılaştırmak doğru değildir.

Daha anlamlı metrikler:

```text
- Fiziksel qubit sayısı
- Gate hata oranları
- Ölçüm hata oranları
- Coherence süresi
- Gate süresi
- Bağlantı topolojisi
- Crosstalk seviyesi
- Kalibrasyon kararlılığı
- Logical qubit oluşturma kapasitesi
- Logical error rate
- Hata düzeltme overhead'i
- Gerçek uygulama benchmark'ları
```

---

### Fiziksel qubit sayısı neden tek başına yeterli değil?

Çünkü çok sayıda düşük kaliteli qubit, daha az sayıda yüksek kaliteli qubitten daha faydasız olabilir. Ayrıca pratik fault-tolerant hesaplama için önemli olan, fiziksel qubit sayısından çok **güvenilir mantıksal qubit** üretebilme kapasitesidir.

Bu nedenle "en çok qubit kimde?" sorusu tek başına yanıltıcıdır. Daha doğru soru şudur:

```text
Bu donanım, düşük hata oranıyla, yeterince uzun süre, ölçeklenebilir şekilde ve hata düzeltmeye uygun biçimde çalışabiliyor mu?
```

---

## 25.6. PQC algoritmaları kısa özeti

Post-Quantum Cryptography, kuantum bilgisayarlara karşı dayanıklı olması hedeflenen ve klasik bilgisayarlarda çalışan kriptografik algoritmaları kapsar.

NIST, 2024 yılında ilk üç post-quantum cryptography standardını onaylamıştır:

```text
FIPS 203 — ML-KEM
FIPS 204 — ML-DSA
FIPS 205 — SLH-DSA
```

Bu standartlar, kurumların kuantum-kırılgan açık anahtarlı kriptografi kullanımını azaltması ve uzun vadeli kriptografik dayanıklılığa geçmesi açısından önemli bir dönüm noktasıdır.

---

### FIPS 203 — ML-KEM

| Özellik | Açıklama |
|---|---|
| Tam ad | Module-Lattice-Based Key-Encapsulation Mechanism |
| Kısa ad | ML-KEM |
| Köken | CRYSTALS-Kyber |
| Kullanım amacı | Anahtar kapsülleme / güvenli anahtar paylaşımı |
| Problem ailesi | Lattice-based cryptography |
| Tipik kullanım | TLS, VPN, güvenli kanal kurulumu, anahtar değişimi |
| NIST rolü | Genel şifreleme / key establishment için birincil standart |

ML-KEM, iki tarafın ortak gizli anahtar oluşturması gereken senaryolarda kullanılır. RSA veya Diffie-Hellman tabanlı anahtar değişimlerinin kuantum sonrası alternatifleri arasında temel adaylardan biridir.

---

### FIPS 204 — ML-DSA

| Özellik | Açıklama |
|---|---|
| Tam ad | Module-Lattice-Based Digital Signature Algorithm |
| Kısa ad | ML-DSA |
| Köken | CRYSTALS-Dilithium |
| Kullanım amacı | Dijital imza |
| Problem ailesi | Lattice-based cryptography |
| Tipik kullanım | Kod imzalama, sertifika imzalama, belge imzalama, protokol kimlik doğrulama |
| NIST rolü | Genel amaçlı dijital imza standardı |

ML-DSA, RSA veya ECDSA gibi geleneksel dijital imza algoritmalarının kuantum sonrası alternatifi olarak değerlendirilir.

---

### FIPS 205 — SLH-DSA

| Özellik | Açıklama |
|---|---|
| Tam ad | Stateless Hash-Based Digital Signature Algorithm |
| Kısa ad | SLH-DSA |
| Köken | SPHINCS+ |
| Kullanım amacı | Dijital imza |
| Problem ailesi | Hash-based cryptography |
| Tipik kullanım | Uzun vadeli güven gerektiren imza senaryoları |
| NIST rolü | Alternatif dijital imza standardı |

SLH-DSA, lattice tabanlı olmayan hash tabanlı bir imza yaklaşımıdır. İmza boyutları ve performans özellikleri ML-DSA'dan farklıdır; bu nedenle kullanım senaryosuna göre değerlendirilmelidir.

---

### Ek adaylar ve geçiş süreci

NIST'in ilk standartları tamamlamış olması, kriptografik geçişin bittiği anlamına gelmez. Kurumlar için asıl iş bundan sonra başlar:

```text
1. Kripto envanteri çıkarılır.
2. RSA, Diffie-Hellman, ECC, ECDSA gibi kuantum-kırılgan kullanımlar belirlenir.
3. Kullanım yerleri risk ve veri ömrüne göre sınıflandırılır.
4. Crypto agility hedeflenir.
5. Öncelikli sistemlerde hibrit veya PQC tabanlı geçiş planlanır.
6. Tedarikçi ve ürün bağımlılıkları değerlendirilir.
7. Test, uyumluluk ve performans etkileri ölçülür.
8. Migration roadmap oluşturulur.
```

---

### PQC ile quantum cryptography farkı

| Başlık | Post-Quantum Cryptography | Quantum Cryptography |
|---|---|---|
| Çalıştığı ortam | Klasik bilgisayarlar | Kuantum fiziksel sistemler |
| Amaç | Kuantum saldırılarına dayanıklı algoritmalar | Kuantum ilkeleriyle güvenli iletişim |
| Örnek | ML-KEM, ML-DSA, SLH-DSA | Quantum Key Distribution |
| Kurumsal uygulanabilirlik | Yazılım/protokol geçişiyle daha yaygın uygulanabilir | Özel donanım ve altyapı gerektirebilir |
| Ana konu | Algoritma ve migration | Fiziksel iletişim kanalı ve kuantum güvenliği |

---

### Store now, decrypt later riski

Saldırgan bugün şifreli veriyi ele geçirip saklayabilir. Yeterince güçlü kuantum bilgisayarlar ileride kullanılabilir hale gelirse, bu eski verilerin çözülmesi hedeflenebilir.

Bu nedenle şu tür veriler için PQC hazırlığı daha acildir:

```text
- Uzun süre gizli kalması gereken finansal veriler
- Devlet ve savunma bilgileri
- Sağlık verileri
- Kişisel veriler
- Kritik altyapı sırları
- Fikri mülkiyet ve Ar-Ge verileri
- Uzun ömürlü sertifika ve imza zincirleri
```

---

## 25.7. Kaynakça ve İleri Okuma Listesi

Bu kaynakça, dokümanda kullanılan ana kavramları doğrulamak ve okuyucunun daha ileri araştırma yapabilmesi için hazırlanmıştır. Kaynaklar konu başlıklarına göre gruplanmıştır.

---

### Temel kuantum bilgisayar anlatımları

1. **NIST — Quantum Computing Explained**  
   Kuantum bilgisayarları, qubitleri, süperpozisyonu, dolaşıklığı ve mevcut sınırları sade biçimde anlatan güvenilir giriş kaynağı.  
   <https://www.nist.gov/quantum-information-science/quantum-computing-explained>

2. **NIST — Quantum Information Science**  
   Kuantum bilgi bilimi alanına genel bakış.  
   <https://www.nist.gov/quantum-information-science>

3. **IBM Think — What is Quantum Computing?**  
   Kuantum hesaplamanın temel kavramlarını iş dünyası ve teknoloji perspektifinden anlatır.  
   <https://www.ibm.com/think/topics/quantum-computing>

4. **Microsoft Azure Quantum — Understand quantum computing**  
   Kuantum bilgisayarların temel çalışma mantığına ve Azure Quantum ekosistemine giriş.  
   <https://learn.microsoft.com/en-us/azure/quantum/overview-understanding-quantum-computing>

---

### Qubit, notasyon ve matematik

5. **Microsoft Learn — The Qubit in Quantum Computing**  
   Qubit, durum vektörü, Bloch küresi ve ölçüm kavramlarını açıklar.  
   <https://learn.microsoft.com/en-us/azure/quantum/concepts-the-qubit>

6. **Microsoft Learn — Dirac Notation**  
   Bra-ket notasyonu ve kuantum durumlarının matematiksel gösterimi için kısa açıklama.  
   <https://learn.microsoft.com/en-us/azure/quantum/concepts-dirac-notation>

7. **IBM Quantum Learning — Bloch Sphere**  
   Bloch küresi üzerinden tek qubit durumlarının geometrik gösterimi.  
   <https://quantum.cloud.ibm.com/learning/en/courses/general-formulation-of-quantum-information/density-matrices/bloch-sphere>

8. **Nielsen & Chuang — Quantum Computation and Quantum Information**  
   Kuantum bilgi ve kuantum hesaplama alanının klasik temel kitaplarından biri.  
   Kitap: Michael A. Nielsen, Isaac L. Chuang, *Quantum Computation and Quantum Information*

---

### Kuantum kapıları, devreler ve algoritmalar

9. **IBM Quantum Learning — Bits, gates, and circuits**  
   Kuantum kapıları, CNOT ve devre kavramları için uygulamalı giriş.  
   <https://quantum.cloud.ibm.com/learning/courses/utility-scale-quantum-computing/bits-gates-and-circuits>

10. **IBM Quantum Learning — Grover's Algorithm**  
    Grover algoritması ve amplitude amplification için eğitim içeriği.  
    <https://quantum.cloud.ibm.com/learning/en/courses/utility-scale-quantum-computing/grovers-algorithm>

11. **IBM Quantum Learning — Quantum Fourier Transform**  
    QFT ve phase estimation için temel modül.  
    <https://quantum.cloud.ibm.com/learning/modules/computer-science/qft>

12. **IBM Quantum Learning — Shor's Algorithm**  
    Shor algoritması, order finding ve kriptografi etkileri için eğitim içeriği.  
    <https://quantum.cloud.ibm.com/learning>

13. **Harrow, Hassidim, Lloyd — Quantum algorithm for linear systems of equations**  
    HHL algoritmasının orijinal akademik çalışması.  
    <https://arxiv.org/abs/0811.3171>

14. **Farhi, Goldstone, Gutmann — A Quantum Approximate Optimization Algorithm**  
    QAOA algoritmasının temel akademik çalışması.  
    <https://arxiv.org/abs/1411.4028>

---

### Kuantum programlama ve SDK'lar

15. **IBM Quantum / Qiskit**  
    Qiskit SDK, kuantum devreleri, primitives ve IBM Quantum servisleri.  
    <https://www.ibm.com/quantum/qiskit>

16. **Qiskit Documentation**  
    Qiskit API ve kuantum devreleri dokümantasyonu.  
    <https://quantum.cloud.ibm.com/docs>

17. **Microsoft Azure Quantum Documentation**  
    Q#, Azure Quantum, kaynak tahmini, hibrit kuantum hesaplama ve bulut servisleri.  
    <https://learn.microsoft.com/en-us/azure/quantum/>

18. **Google Quantum AI — Cirq**  
    Cirq devre modeli, moment, operation ve simülasyon yapıları.  
    <https://quantumai.google/cirq>

19. **PennyLane Documentation**  
    Hibrit kuantum-klasik algoritmalar, QML ve quantum chemistry çalışmaları için Python kütüphanesi.  
    <https://docs.pennylane.ai>

20. **Amazon Braket Documentation**  
    AWS üzerinde kuantum donanımı, simülatörler ve hybrid jobs modeli.  
    <https://docs.aws.amazon.com/braket/>

---

### Donanım ve güncel durum

21. **IBM Quantum Hardware**  
    IBM'in süperiletken kuantum işlemcileri, cryostat yapısı ve donanım yaklaşımı.  
    <https://www.ibm.com/quantum/hardware>

22. **IBM Quantum Roadmap / Fault-Tolerant Quantum Computing**  
    IBM'in Starling ve Blue Jay gibi fault-tolerant kuantum bilgisayar hedefleri.  
    <https://www.ibm.com/quantum/blog/large-scale-ftqc>

23. **Google Quantum AI — Making quantum error correction work**  
    Willow işlemcisi ve surface code hata düzeltme çalışmaları hakkında Google'ın açıklaması.  
    <https://research.google/blog/making-quantum-error-correction-work/>

24. **Nature — Quantum error correction with below-threshold surface code memory**  
    Google Willow hata düzeltme sonuçlarının akademik yayını.  
    <https://www.nature.com/>

25. **Microsoft — Majorana 1 announcement**  
    Microsoft'un topolojik qubit ve Majorana 1 duyurusu.  
    <https://news.microsoft.com/source/features/innovation/microsofts-majorana-1-chip-carves-new-path-for-quantum-computing/>

26. **D-Wave — Quantum Annealing Approach**  
    D-Wave'in annealing tabanlı yaklaşımı ve optimizasyon odağı.  
    <https://www.dwavequantum.com/learn/d-wave-s-approach/>

27. **Quantinuum Documentation and Research**  
    Hapsedilmiş iyon yaklaşımı ve kuantum donanım çalışmaları.  
    <https://www.quantinuum.com/>

28. **IonQ Technology**  
    Trapped-ion kuantum bilgisayar yaklaşımı.  
    <https://ionq.com/technology>

29. **Xanadu**  
    Fotonik kuantum hesaplama ve PennyLane ekosistemi.  
    <https://www.xanadu.ai/>

30. **PsiQuantum**  
    Fotonik, fault-tolerant kuantum bilgisayar yaklaşımı.  
    <https://www.psiquantum.com/>

---

### Hata düzeltme, NISQ ve fault tolerance

31. **John Preskill — Quantum Computing in the NISQ era and beyond**  
    NISQ kavramını popülerleştiren önemli akademik çalışma.  
    <https://arxiv.org/abs/1801.00862>

32. **Nature Index — Quantum error correction in quantum computing systems**  
    Kuantum hata düzeltmenin önemine dair güncel genel bakış.  
    <https://www.nature.com/nature-index/topics/l4/quantum-error-correction-in-quantum-computing-systems>

33. **Microsoft Azure Quantum — Resource Estimation**  
    Hata düzeltmeli kuantum algoritmaların kaynak gereksinimlerini tahmin etmeye yönelik araçlar.  
    <https://learn.microsoft.com/en-us/azure/quantum/overview-resources-estimator>

---

### Post-Quantum Cryptography ve güvenlik

34. **NIST — Post-Quantum Cryptography Project**  
    NIST'in PQC standartlaştırma sürecinin ana sayfası.  
    <https://www.nist.gov/pqc>

35. **NIST — FIPS 203: ML-KEM**  
    Module-Lattice-Based Key-Encapsulation Mechanism standardı.  
    <https://csrc.nist.gov/pubs/fips/203/final>

36. **NIST — FIPS 204: ML-DSA**  
    Module-Lattice-Based Digital Signature Algorithm standardı.  
    <https://csrc.nist.gov/pubs/fips/204/final>

37. **NIST — FIPS 205: SLH-DSA**  
    Stateless Hash-Based Digital Signature Algorithm standardı.  
    <https://csrc.nist.gov/pubs/fips/205/final>

38. **NIST News — First 3 finalized post-quantum encryption standards**  
    2024'te yayımlanan ilk üç PQC standardının duyurusu.  
    <https://www.nist.gov/news-events/news/2024/08/nist-releases-first-3-finalized-post-quantum-encryption-standards>

39. **NIST NCCoE — Migration to Post-Quantum Cryptography**  
    Kurumların PQC migration süreci için referans çalışma.  
    <https://www.nccoe.nist.gov/applied-cryptography/migration-to-pqc>

40. **CISA / NSA / NIST — Quantum-Readiness Guidance**  
    Kurumların quantum-readiness ve crypto inventory hazırlığı için güvenlik rehberleri.  
    <https://www.cisa.gov/>

---

### İş dünyası, strateji ve raporlar

41. **McKinsey — Quantum Technology Monitor**  
    Kuantum teknolojileri yatırımları, piyasa beklentileri ve stratejik değerlendirmeler.  
    <https://www.mckinsey.com/>

42. **IBM Institute for Business Value — Quantum computing reports**  
    İş dünyası ve sektörel kuantum kullanım alanları üzerine raporlar.  
    <https://www.ibm.com/thought-leadership/institute-business-value>

43. **WEF — Quantum Economy / Quantum Technologies reports**  
    Kuantum teknolojilerinin ekonomi, güvenlik ve sektörler üzerindeki etkilerine dair raporlar.  
    <https://www.weforum.org/>

---

### Türkiye ve bölgesel perspektif

44. **TÜBİTAK — QuantERA çağrıları**  
    Türkiye'nin kuantum teknolojileri alanındaki uluslararası Ar-Ge çağrılarına katılımı.  
    <https://tubitak.gov.tr/>

45. **TÜBİTAK BİLGEM**  
    Kuantum teknolojileri, kriptografi ve siber güvenlik çalışmaları açısından önemli kurum.  
    <https://bilgem.tubitak.gov.tr/>

46. **QuantERA Programme**  
    Avrupa kuantum teknolojileri araştırma ağı.  
    <https://quantera.eu/>

47. **Eureka Quantum Technologies**  
    Uluslararası kuantum teknolojileri iş birlikleri için program.  
    <https://www.eurekanetwork.org/>

---

### Kitap önerileri

48. **Quantum Computation and Quantum Information**  
    Michael A. Nielsen, Isaac L. Chuang  
    Alanın en temel teknik referanslarından biridir.

49. **Quantum Computing for Computer Scientists**  
    Noson S. Yanofsky, Mirco A. Mannucci  
    Bilgisayar bilimciler için kavramsal ve matematiksel köprü kurar.

50. **Quantum Computing: A Gentle Introduction**  
    Eleanor G. Rieffel, Wolfgang H. Polak  
    Daha erişilebilir bir kuantum hesaplama başlangıcı sağlar.

51. **Dancing with Qubits**  
    Robert S. Sutor  
    Yazılımcılar ve teknoloji profesyonelleri için okunabilir bir giriş kitabıdır.

52. **Quantum Computing Since Democritus**  
    Scott Aaronson  
    Kuantum hesaplama, karmaşıklık teorisi ve bilgi kavramlarını daha teorik bir perspektiften ele alır.

---

## Bölüm Özeti

Bu ekler bölümü, dokümanda anlatılan kuantum bilgisayar kavramlarını hızlı başvuru formatında toparladı.

Öne çıkan mesajlar:

```text
- Qubit, klasik bitin yalnızca daha gelişmiş hali değildir.
- Süperpozisyon ve dolaşıklık tek başına mucize yaratmaz; girişim ve algoritma tasarımı belirleyicidir.
- Kuantum kapıları, kuantum durumlarını tersinir biçimde dönüştürür.
- Kuantum algoritmaların pratik değeri problem tipine, donanım kalitesine ve hata düzeltmeye bağlıdır.
- Donanım yarışında qubit sayısı tek başına anlamlı değildir.
- PQC, kurumlar için bugünden başlaması gereken stratejik bir hazırlık alanıdır.
- Kuantum bilgisayarları doğru anlamak, hem teknik gerçekleri hem de iş dünyası beklentilerini dengeli okumayı gerektirir.
```

Bu dokümanın bütününde amaç, kuantum bilgisayarları ne gereğinden fazla büyütmek ne de bugünkü sınırlılıkları nedeniyle önemsizleştirmektir. Doğru yaklaşım, kuantum bilgisayarları **özel problem sınıfları için potansiyel taşıyan, hâlâ gelişmekte olan, stratejik etkileri bugünden hissedilmeye başlayan yeni bir hesaplama paradigması** olarak değerlendirmektir.
