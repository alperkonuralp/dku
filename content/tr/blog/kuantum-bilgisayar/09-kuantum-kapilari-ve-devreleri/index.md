+++
title = "9. Kuantum Kapıları ve Kuantum Devreleri"
description = "Kuantum kapılarının qubit durumlarını nasıl dönüştürdüğü ve kuantum devrelerinin nasıl oluşturulduğu."
date = "2026-05-18T00:00:00+03:00"
weight = 9
type = "guide"
draft = false
+++

Bu bölümde kuantum bilgisayarların hesaplama işlemini nasıl gerçekleştirdiğini ele alacağız. Önceki bölümlerde qubit, süperpozisyon, ölçüm, dolaşıklık ve girişim kavramlarını ayrı ayrı inceledik. Şimdi bu kavramların bir kuantum programı içinde nasıl kullanıldığını göreceğiz.

Klasik bilgisayarlarda hesaplama, bitler üzerinde çalışan mantık kapıları ve işlemci komutlarıyla gerçekleştirilir. Kuantum bilgisayarlarda ise hesaplama, qubitlerin kuantum durumlarını dönüştüren **kuantum kapıları** ve bu kapıların belirli bir sırada yerleştirildiği **kuantum devreleri** ile modellenir.

Bu noktada kuantum bilgisayarları anlamak için kritik fikir şudur:

> Kuantum kapıları, qubitlerin içindeki "gizli değeri" okumaz; qubitlerin kuantum durumunu kontrollü biçimde dönüştürür.

Kuantum devresi ise bu dönüşümlerin sırasını, hangi qubitlere uygulandığını ve sonunda hangi qubitlerin ölçüldüğünü gösteren hesaplama şemasıdır.

---

## 9.1. Kuantum kapısı nedir?

Kuantum kapısı, bir veya birden fazla qubit üzerinde çalışan ve onların kuantum durumunu değiştiren temel işlemdir. Klasik mantık kapılarının bitleri dönüştürmesine benzer şekilde, kuantum kapıları da qubit durumlarını dönüştürür. Ancak aradaki fark çok büyüktür: kuantum kapısı yalnızca 0 ve 1 değerleri üzerinde değil, qubitin süperpozisyon, faz ve dolaşıklık yapısı üzerinde işlem yapar.

Bir qubitin genel durumu şu şekilde ifade edilebilir:

```text
|ψ⟩ = α|0⟩ + β|1⟩
```

Bir kuantum kapısı bu durumu başka bir kuantum durumuna dönüştürür:

```text
U|ψ⟩ = |ψ'⟩
```

Buradaki `U`, kuantum kapısını temsil eden matematiksel operatördür. Teknik olarak kuantum kapıları çoğunlukla **üniter matrisler** ile temsil edilir. Üniterlik, bu dönüşümün kuantum durumunun toplam olasılığını koruması anlamına gelir. Başka bir deyişle, kapı uygulandıktan sonra da ölçüm sonuçlarının toplam olasılığı 1 olmaya devam eder.

Bu durum klasik programlamadan farklı bir düşünme biçimi gerektirir. Klasik programlamada bir değişkenin değeri doğrudan değiştirilebilir. Kuantum programlamada ise qubitin durumunu, geçerli kuantum mekanik kurallarına uygun dönüşümlerle yönlendiririz.

Basit bir örnek verelim. Klasik dünyada NOT kapısı 0'ı 1'e, 1'i 0'a çevirir:

```text
0 -> 1
1 -> 0
```

Kuantum dünyasında buna karşılık gelen kapı genellikle **X kapısı** olarak adlandırılır. X kapısı da temel baz durumlarında şunu yapar:

```text
|0⟩ -> |1⟩
|1⟩ -> |0⟩
```

Fakat qubit süperpozisyondaysa, X kapısı yalnızca basit bir değer değiştirme yapmaz; qubitin tüm kuantum durumunu dönüştürür:

```text
α|0⟩ + β|1⟩  ->  β|0⟩ + α|1⟩
```

Bu örnek bile kuantum kapısının klasik kapıdan daha genel bir nesne olduğunu gösterir. Kuantum kapısı, yalnızca görünen ölçüm sonucuyla değil, ölçümden önceki durumun tamamıyla ilgilidir.

---

## 9.2. Klasik mantık kapıları ile kuantum kapıları arasındaki fark

Klasik mantık kapıları, klasik bitler üzerinde çalışır. AND, OR, NOT, XOR gibi kapılar, giriş bitlerini alır ve çıkış bitleri üretir. Örneğin AND kapısı iki bit alır ve her iki bit de 1 ise 1 üretir:

```text
0 AND 0 = 0
0 AND 1 = 0
1 AND 0 = 0
1 AND 1 = 1
```

Bu hesaplama mantığı günlük bilgisayarların temelini oluşturur. İşlemciler, bellek sistemleri, kontrol yapıları ve yazılım katmanları en altta bu tür mantıksal işlemlere dayanır.

Kuantum kapıları ise qubitler üzerinde çalışır. Qubit yalnızca 0 veya 1 değerinde olmadığı için, kuantum kapısı da sadece klasik doğruluk tablosu ile tam olarak açıklanamaz. Bir kuantum kapısı şu unsurları etkileyebilir:

- Ölçümde 0 veya 1 gelme olasılıklarını,
- Qubit durumunun fazını,
- Birden fazla qubit arasındaki dolaşıklığı,
- Olasılık genliklerinin daha sonra nasıl girişim yapacağını.

Bu nedenle kuantum kapılarını yalnızca "kuantum versiyonlu klasik kapılar" gibi düşünmek eksik olur. Bazı kapıların klasik dünyada sezgisel karşılığı vardır; örneğin X kapısı klasik NOT kapısına benzer. Ancak H, S, T, CNOT veya CZ gibi kapıların etkisi klasik mantık kapılarından çok daha farklıdır.

Önemli farklardan biri de şudur: Kuantum kapıları, ölçüm haricinde, genellikle **tersinir** işlemler olarak modellenir. Bir kuantum kapısını uyguladıktan sonra teorik olarak onun tersini uygulayıp eski duruma dönebilirsiniz. Klasik AND kapısı ise tersinir değildir. Çünkü AND kapısının çıktısı 0 olduğunda, girişin 00 mı, 01 mi yoksa 10 mu olduğunu bilemezsiniz. Bilgi kaybolmuştur.

Kuantum kapılarında bilgi bu şekilde kaybolamaz. Ölçüm yapılmadığı sürece kuantum evrimi tersinir olmak zorundadır. Bu, kuantum devre tasarımının en temel kurallarından biridir.

Klasik kapılar ile kuantum kapıları arasındaki farkı şöyle özetleyebiliriz:

| Özellik | Klasik mantık kapısı | Kuantum kapısı |
|---|---|---|
| Temel bilgi birimi | Bit | Qubit |
| Girdi | 0/1 değerleri | Kuantum durumları |
| Çıktı | 0/1 değerleri | Yeni kuantum durumları |
| Süperpozisyonla çalışma | Yok | Var |
| Faz bilgisi | Yok | Var |
| Dolaşıklık oluşturma | Yok | Çok-qubit kapılarla mümkün |
| Tersinirlik | Her zaman gerekli değil | Ölçüm dışındaki kapılar için temel özellik |
| Matematiksel temsil | Boolean fonksiyonları | Üniter operatörler / matrisler |

Bu tablo, kuantum bilgisayarların neden yalnızca "farklı donanımda çalışan klasik bilgisayar" olmadığını da gösterir.

---

## 9.3. Tek qubit kapıları: X, Y, Z, H, S, T

Tek qubit kapıları, bir qubitin durumunu dönüştüren kapılardır. Bu kapılar Bloch küresi üzerinde qubit durumunun yönünü döndürmek gibi sezgisel olarak düşünülebilir. Her kapının matematiksel bir matris karşılığı vardır; ancak burada amacımız önce sezgisel anlamı kurmak, sonra gerektiği kadar matematiksel ifadeyi vermektir.

### 9.3.1. X kapısı

X kapısı, klasik NOT kapısına en çok benzeyen kuantum kapısıdır.

Temel baz durumları üzerindeki etkisi:

```text
X|0⟩ = |1⟩
X|1⟩ = |0⟩
```

Süperpozisyon durumunda ise genliklerin yerini değiştirir:

```text
X(α|0⟩ + β|1⟩) = β|0⟩ + α|1⟩
```

Bloch küresi sezgisiyle X kapısı, qubit durumunu X ekseni etrafında 180 derece döndürür.

### 9.3.2. Y kapısı

Y kapısı da bit-flip benzeri bir etki üretir, ancak faz değişimi de içerir. Temel durumlar üzerindeki etkisi şu şekilde ifade edilir:

```text
Y|0⟩ = i|1⟩
Y|1⟩ = -i|0⟩
```

Buradaki `i`, sanal birimdir. Bu kapı, yalnızca 0 ile 1'i değiştirmekle kalmaz; aynı zamanda kuantum durumunun fazını da etkiler. Bu nedenle klasik dünyada doğrudan basit bir karşılığı yoktur.

### 9.3.3. Z kapısı

Z kapısı temel baz durumlarında ölçüm sonucunu değiştirmez; yani |0⟩ durumunu |0⟩ olarak, |1⟩ durumunu da ölçüm açısından yine |1⟩ olarak bırakır. Fakat |1⟩ bileşeninin fazını değiştirir:

```text
Z|0⟩ = |0⟩
Z|1⟩ = -|1⟩
```

Bu ilk bakışta önemsiz görünebilir. Çünkü ölçümde |1⟩ ile -|1⟩ aynı sonucu verir. Ancak kuantum algoritmalarda faz bilgisi daha sonra girişim etkisiyle ölçüm olasılıklarını değiştirebilir. Bu yüzden Z kapısı kuantum hesaplamada çok önemlidir.

### 9.3.4. Hadamard kapısı: H

Hadamard kapısı, kuantum devrelerinde en sık karşılaşılan kapılardan biridir. Genellikle süperpozisyon oluşturmak için kullanılır.

Temel etkisi:

```text
H|0⟩ = (|0⟩ + |1⟩) / √2
H|1⟩ = (|0⟩ - |1⟩) / √2
```

Bu şu anlama gelir: Eğer |0⟩ durumundaki bir qubite H kapısı uygularsanız, ölçümde 0 ve 1 sonuçları eşit olasılıkla gelebilecek bir süperpozisyon elde edersiniz.

Ancak H kapısını sadece "rastgelelik oluşturan kapı" gibi düşünmek yanlıştır. H kapısı aynı zamanda faz bilgisini de farklı bazlar arasında taşır. Örneğin iki kez H uygulamak başlangıç durumuna geri döndürür:

```text
H(H|0⟩) = |0⟩
H(H|1⟩) = |1⟩
```

Bu durum, kuantum hesaplamada kapıların rastgelelik üretmekten çok daha fazlasını yaptığını gösterir.

### 9.3.5. S kapısı

S kapısı bir faz kapısıdır. |0⟩ durumunu değiştirmez, |1⟩ bileşenine `i` fazı ekler:

```text
S|0⟩ = |0⟩
S|1⟩ = i|1⟩
```

S kapısı ölçüm sonucunu doğrudan değiştirmeyebilir; fakat sonraki kapılarla birlikte girişim desenini etkileyebilir. Bu nedenle faz kapıları kuantum algoritmalarda kritik öneme sahiptir.

### 9.3.6. T kapısı

T kapısı da bir faz kapısıdır, fakat S kapısına göre daha küçük bir faz dönüşümü uygular. Kuantum hesaplamada T kapısı özellikle evrensel kapı kümelerinde önemlidir.

Sezgisel olarak T kapısı, qubit durumunu faz açısından daha ince bir adımla döndürür. Bu tür kapılar, karmaşık kuantum işlemleri daha küçük temel işlemlerden oluşturmak için kullanılır.

### 9.3.7. Tek qubit kapılarını birlikte düşünmek

Tek qubit kapıları yalnız başına bile güçlüdür; çünkü bir qubitin ölçüm olasılıklarını, fazını ve bazlar arasındaki temsilini değiştirebilirler. Ancak tek qubit kapıları tek başına çok-qubitli kuantum avantaj için yeterli değildir. Birden fazla qubitin birlikte anlamlı şekilde çalışabilmesi için çok-qubit kapılara, özellikle dolaşıklık oluşturabilen kapılara ihtiyaç vardır.

---

## 9.4. Çok qubit kapıları: CNOT, CZ, SWAP

Çok qubit kapıları, iki veya daha fazla qubit üzerinde aynı anda işlem yapan kapılardır. Kuantum bilgisayarların asıl gücünün ortaya çıkmaya başladığı yer burasıdır. Çünkü çok qubit kapıları, qubitler arasında dolaşıklık oluşturabilir veya mevcut dolaşıklığı dönüştürebilir.

### 9.4.1. CNOT kapısı

CNOT, "Controlled NOT" anlamına gelir. İki qubit üzerinde çalışır:

- Bir qubit **kontrol qubit**tir.
- Diğer qubit **hedef qubit**tir.

CNOT kapısı şu mantıkla çalışır:

```text
Kontrol qubit |1⟩ ise hedef qubite X uygulanır.
Kontrol qubit |0⟩ ise hedef qubit değişmez.
```

Temel baz durumlarında CNOT etkisi şöyle yazılabilir:

```text
|00⟩ -> |00⟩
|01⟩ -> |01⟩
|10⟩ -> |11⟩
|11⟩ -> |10⟩
```

Burada ilk qubit kontrol, ikinci qubit hedef olarak düşünülmüştür.

CNOT kapısı klasik XOR benzeri bir davranış gösterir; ancak kuantum durumları üzerinde çalıştığı için çok daha güçlü sonuçlar üretebilir. Örneğin bir qubit süperpozisyondayken CNOT kullanılırsa iki qubit dolaşık hale gelebilir.

Basit Bell state örneği:

```text
Başlangıç:
|00⟩

İlk qubite H uygula:
(|0⟩ + |1⟩) / √2 ⊗ |0⟩
= (|00⟩ + |10⟩) / √2

Sonra CNOT uygula:
(|00⟩ + |11⟩) / √2
```

Son durumda iki qubit artık bağımsız değildir. Bu, daha önceki bölümde gördüğümüz Bell state örneklerinden biridir.

### 9.4.2. CZ kapısı

CZ, "Controlled Z" anlamına gelir. İki qubit üzerinde çalışır ve kontrol-hedef ayrımı CNOT kadar belirgin hissedilmeyebilir; çünkü CZ simetrik bir kapı olarak düşünülebilir.

Temel baz durumlarında etkisi:

```text
|00⟩ -> |00⟩
|01⟩ -> |01⟩
|10⟩ -> |10⟩
|11⟩ -> -|11⟩
```

CZ kapısı yalnızca iki qubit de |1⟩ durumundayken faz değişimi uygular. Ölçüm bazında bakıldığında bu değişiklik hemen görünmeyebilir; fakat girişim açısından çok önemlidir. Birçok kuantum algoritma, faz işaretlemeleri ve kontrollü faz dönüşümleri üzerine kuruludur.

### 9.4.3. SWAP kapısı

SWAP kapısı iki qubitin durumunu yer değiştirir:

```text
|a⟩|b⟩ -> |b⟩|a⟩
```

Temel baz durumlarında:

```text
|00⟩ -> |00⟩
|01⟩ -> |10⟩
|10⟩ -> |01⟩
|11⟩ -> |11⟩
```

SWAP kapısı algoritmik olarak da, donanım düzeyinde de önemlidir. Gerçek kuantum işlemcilerde her qubit her qubitle doğrudan bağlı olmayabilir. Bu durumda iki qubit arasında işlem yapabilmek için qubit durumlarını donanım bağlantı yapısına göre hareket ettirmek gerekebilir. SWAP kapıları bu tür durumlarda kullanılır.

Ancak SWAP kapıları maliyetlidir. Çünkü her ek kapı hata ihtimalini artırır. Bu yüzden kuantum devre optimizasyonunda gereksiz SWAP kapılarını azaltmak önemli bir konudur.

### 9.4.4. Çok qubit kapıların önemi

Tek qubit kapıları bir qubitin durumunu dönüştürür. Çok qubit kapılar ise qubitler arasında ilişki kurar. Bu ilişki klasik korelasyon değil, kuantum dolaşıklık olabilir.

Bu nedenle kuantum algoritmalar için genel resim şudur:

```text
Tek qubit kapıları:
Durumu hazırlar, döndürür, fazı değiştirir.

Çok qubit kapıları:
Qubitler arasında bağımlılık kurar, dolaşıklık oluşturur, koşullu dönüşüm yapar.

Ölçüm:
Kuantum durumundan klasik sonuç üretir.
```

---

## 9.5. Tersinir hesaplama neden önemlidir?

Kuantum hesaplamada ölçüm dışındaki işlemler tersinirdir. Bunun temel nedeni, kuantum durumlarının zaman içindeki evriminin üniter dönüşümlerle modellenmesidir. Üniter dönüşümler tersine çevrilebilir. Yani bir kuantum kapısının teorik olarak bir ters kapısı vardır.

Bu durum klasik hesaplama açısından alışılmadıktır. Klasik bilgisayarlarda birçok işlem tersinir değildir. Örneğin AND kapısına tekrar bakalım:

```text
0 AND 0 = 0
0 AND 1 = 0
1 AND 0 = 0
1 AND 1 = 1
```

Çıktı 1 ise girdinin 1 ve 1 olduğunu anlarsınız. Ama çıktı 0 ise hangi girişin verildiğini bilemezsiniz. Bu işlem bilgi kaybettirmiştir.

Kuantum hesaplamada ise ölçüm yapılmadığı sürece bilgi bu anlamda kaybolmaz. Kuantum sistemin durumu dönüştürülür ama bu dönüşüm geri alınabilir olmalıdır. Bu yüzden kuantum devrelerinde kullanılan kapılar tersinir olacak şekilde tasarlanır.

Bu kuralın birkaç önemli sonucu vardır:

1. Klasik algoritmaları kuantum devreye doğrudan çevirmek her zaman kolay değildir.
2. Silme, kopyalama, koşullu akış gibi klasik programlama alışkanlıkları yeniden düşünülmelidir.
3. Yardımcı qubitler, geçici hesaplama alanları ve "uncomputation" teknikleri önem kazanır.
4. Ölçüm, tersinir kuantum evrimden farklı bir işlem olarak özel şekilde ele alınır.

### Uncomputation fikri

Kuantum devrelerde bazen ara hesaplamalar için yardımcı qubitler kullanılır. Bu yardımcı qubitlerin üzerinde artık gereksiz bilgi kaldığında, bu bilginin gelişigüzel silinmesi mümkün değildir. Bunun yerine hesaplama adımları tersine çalıştırılarak yardımcı qubitler başlangıç durumuna döndürülür. Bu işleme genellikle **uncomputation** denir.

Basit sezgi:

```text
1. Yardımcı qubitlerle ara sonucu hesapla.
2. Ara sonucu asıl hedefe aktar.
3. Yardımcı hesaplamayı tersine çevir.
4. Yardımcı qubitleri temiz başlangıç durumuna döndür.
```

Bu yaklaşım, kuantum algoritmaların tasarımında klasik programlamadan çok farklı bir disiplin gerektirir.

---

## 9.6. Kuantum devresi nasıl okunur?

Kuantum devresi, qubitler üzerinde uygulanan kapıların görsel veya sembolik temsilidir. Devrede genellikle her yatay çizgi bir qubiti temsil eder. Zaman, çoğu diyagramda soldan sağa doğru akar.

Basit bir devreyi düşünelim:

```text
q0: ──H──■──M──
         │
q1: ─────X──M──
```

Bu devre şöyle okunur:

1. `q0` ve `q1` adında iki qubit vardır.
2. İlk olarak `q0` üzerine H kapısı uygulanır.
3. Sonra `q0` kontrol, `q1` hedef olacak şekilde CNOT uygulanır.
4. En sonunda iki qubit de ölçülür.

Bu devre, başlangıç durumu |00⟩ ise Bell state üretir:

```text
(|00⟩ + |11⟩) / √2
```

Ölçüm sonucunda 00 veya 11 elde edilir. 01 veya 10 elde edilmez. Bu, iki qubitin sonuçlarının korele olduğunu gösterir.

### Devredeki yaygın semboller

| Sembol | Anlam |
|---|---|
| Yatay çizgi | Qubit hattı |
| H | Hadamard kapısı |
| X | X kapısı / NOT benzeri işlem |
| Z | Z faz kapısı |
| ■ | Kontrol noktası |
| ⊕ veya X hedef sembolü | CNOT hedefi |
| M veya ölçüm göstergesi | Ölçüm |
| Çift çizgi | Klasik bit / ölçüm sonucu hattı |

### Devre okurken dikkat edilecekler

Bir kuantum devresi okurken şu soruları sormak faydalıdır:

```text
1. Başlangıç durumu nedir?
2. Hangi qubitlere tek qubit kapıları uygulanıyor?
3. Hangi qubitler arasında çok-qubit kapılar var?
4. Dolaşıklık oluşuyor mu?
5. Faz bilgisi nerede değişiyor?
6. Ölçüm ne zaman yapılıyor?
7. Ölçümden sonra klasik bilgi nasıl kullanılıyor?
```

Kuantum devreyi anlamak için her zaman tüm matematiği elle hesaplamak gerekmez. Ancak devrede hangi kapının hangi tür etki ürettiğini bilmek, algoritmanın fikrini anlamayı kolaylaştırır.

---

## 9.7. Basit bir kuantum devresi örneği

Bu bölümde Bell state üreten basit bir devreyi adım adım inceleyelim. Başlangıçta iki qubitimiz olsun:

```text
|q0 q1⟩ = |00⟩
```

Amacımız şu dolaşık durumu üretmek:

```text
(|00⟩ + |11⟩) / √2
```

### Adım 1: Başlangıç durumu

İki qubit de |0⟩ durumunda başlasın:

```text
|00⟩
```

### Adım 2: İlk qubite Hadamard uygula

İlk qubite H kapısı uygularız:

```text
H|0⟩ = (|0⟩ + |1⟩) / √2
```

İki qubitli sistemin durumu:

```text
(|00⟩ + |10⟩) / √2
```

Burada birinci qubit süperpozisyona girmiştir; ikinci qubit hâlâ |0⟩ durumundadır.

### Adım 3: CNOT uygula

Şimdi birinci qubiti kontrol, ikinci qubiti hedef yaparak CNOT uygularız.

CNOT kuralı:

```text
Kontrol 0 ise hedef değişmez.
Kontrol 1 ise hedef ters çevrilir.
```

Bu nedenle:

```text
|00⟩ -> |00⟩
|10⟩ -> |11⟩
```

Son durum:

```text
(|00⟩ + |11⟩) / √2
```

Artık iki qubit dolaşıktır.

### Adım 4: Ölçüm

Bu durum ölçüldüğünde iki olası sonuç vardır:

```text
00 veya 11
```

Her biri yaklaşık %50 olasılıkla gelir. Ancak 01 veya 10 sonucu beklenmez. Bu, iki qubitin ölçüm sonuçlarının birlikte davrandığını gösterir.

### Devrenin gösterimi

```text
q0: ──H──■──M──
         │
q1: ─────X──M──
```

Bu küçük devre, kuantum hesaplamanın birçok temel fikrini aynı anda gösterir:

- H kapısı süperpozisyon oluşturur.
- CNOT kapısı qubitler arasında ilişki kurar.
- Dolaşıklık oluşur.
- Ölçüm sonucunda klasik bitler elde edilir.
- Sonuçlar olasılıksal ama yapısal olarak koreledir.

Bu nedenle Bell state devresi, kuantum devreleri öğrenirken en temel örneklerden biridir.

---

## 9.8. Devre modeli dışındaki kuantum hesaplama yaklaşımları

Kuantum bilgisayarlar çoğunlukla kuantum devre modeli üzerinden anlatılır. Bunun nedeni, devre modelinin klasik mantık devrelerine benzer bir şema sunması ve kuantum algoritmaların önemli bir kısmının bu modelle ifade edilebilmesidir.

Ancak kuantum hesaplama yalnızca devre modelinden ibaret değildir. Farklı kuantum hesaplama yaklaşımları da vardır.

### 9.8.1. Quantum annealing

Quantum annealing, özellikle optimizasyon problemleri için kullanılan farklı bir yaklaşımdır. Bu modelde problem, bir enerji manzarası gibi temsil edilir ve sistemin düşük enerjili, yani iyi çözüm temsil eden durumlara ulaşması hedeflenir.

Quantum annealing, gate-based evrensel kuantum hesaplamadan farklıdır. Bu nedenle D-Wave gibi sistemleri doğrudan IBM veya Google'ın gate-based kuantum işlemcileriyle aynı kategoriye koymak doğru değildir. İkisi de kuantum ilkelerden yararlanır, ancak hesaplama modeli ve kullanım alanları farklıdır.

### 9.8.2. Adiabatic quantum computing

Adiabatic quantum computing, sistemin başlangıçta kolay hazırlanabilen bir temel durumdan başlayıp, yavaşça problem Hamiltonian'ının temel durumuna evrilmesi fikrine dayanır. Uygun koşullar altında sistemin son durumu problemin çözümünü temsil eder.

Adiabatic model ile quantum annealing arasında yakın ilişki vardır; ancak pratik uygulamalar, gürültü, sıcaklık ve donanım özellikleri nedeniyle teorik modelden farklılık gösterebilir.

### 9.8.3. Measurement-based quantum computing

Measurement-based quantum computing modelinde önce büyük ve dolaşık bir kaynak durum hazırlanır. Daha sonra hesaplama, bu durum üzerindeki ölçümler aracılığıyla gerçekleştirilir. Burada ölçüm, yalnızca hesaplamanın sonunda yapılan bir okuma işlemi değil, hesaplamanın kendisinin aktif parçasıdır.

Bu model, önceki bölümde gördüğümüz "ölçüm pasif bir okuma değildir" fikrini daha ileri bir noktaya taşır.

### 9.8.4. Analog quantum simulation

Analog kuantum simülasyonda amaç, belirli bir fiziksel sistemi başka bir kontrollü kuantum sistemle taklit etmektir. Bu yaklaşım özellikle kuantum kimyası, malzeme bilimi ve çok-cisim fiziği gibi alanlarda önemlidir.

Analog simülatörler her problemi çözmek için genel amaçlı olmayabilir; ancak belirli fiziksel sistemleri incelemek için çok güçlü araçlar olabilir.

### 9.8.5. Neden devre modeliyle başlıyoruz?

Bu dokümanda ana anlatım devre modeli üzerinden ilerliyor. Bunun birkaç nedeni var:

1. Qubit, kapı, ölçüm ve algoritma kavramlarını sistematik olarak anlatmayı kolaylaştırır.
2. Qiskit, Cirq, Q# gibi yazılım araçları devre modelini doğrudan destekler.
3. Grover, Shor, Phase Estimation gibi temel algoritmalar devre modeliyle iyi açıklanır.
4. Yazılımcı bakışıyla öğrenmeye en uygun modeldir.
5. Kuantum kapıları ve devreler, klasik bilgisayar mühendisliğiyle sezgisel köprü kurar.

Ancak ilerleyen bölümlerde kullanım alanları, donanım yaklaşımları ve kuantum programlama araçları incelenirken devre modeli dışındaki yaklaşımlara da tekrar değinilecektir.

---

## Bölüm Özeti

Bu bölümde kuantum hesaplamanın işlem düzeyindeki temel yapı taşlarını inceledik.

Öne çıkan fikirler şunlardır:

- Kuantum kapısı, qubit durumunu dönüştüren temel işlemdir.
- Kuantum kapıları, klasik mantık kapılarından farklı olarak süperpozisyon, faz ve dolaşıklık üzerinde çalışır.
- X, Y, Z, H, S ve T gibi tek qubit kapıları bir qubitin durumunu değiştirir.
- CNOT, CZ ve SWAP gibi çok qubit kapıları birden fazla qubit arasındaki ilişkiyi yönetir.
- CNOT gibi kapılar dolaşıklık oluşturmak için kullanılabilir.
- Kuantum hesaplamada ölçüm dışındaki işlemler tersinirdir.
- Kuantum devreleri, kapıların hangi sırayla ve hangi qubitlere uygulandığını gösterir.
- Bell state devresi, süperpozisyon ve dolaşıklığın nasıl birlikte kullanıldığını gösteren temel örnektir.
- Devre modeli yaygın ve öğretici bir modeldir; ancak quantum annealing, adiabatic computing, measurement-based computing ve analog quantum simulation gibi başka yaklaşımlar da vardır.

Bu bölümü anlamak, sonraki bölümde ele alınacak kuantum algoritmaların temel mantığını kavramak için önemlidir. Çünkü kuantum algoritmalar, bu kapıları rastgele değil; doğru cevabın olasılığını artıracak şekilde dikkatle düzenlenmiş devreler halinde kullanır.

---

## Kaynaklar ve İleri Okuma

- IBM Quantum Learning — *Bits, gates, and circuits*  
  <https://quantum.cloud.ibm.com/learning/en/courses/utility-scale-quantum-computing/bits-gates-and-circuits>

- IBM Quantum Learning — *Quantum circuits*  
  <https://quantum.cloud.ibm.com/learning/en/courses/basics-of-quantum-information/quantum-circuits/circuits>

- IBM Quantum Documentation — *Qiskit circuit API*  
  <https://quantum.cloud.ibm.com/docs/api/qiskit/0.46/circuit>

- IBM Quantum — *Qiskit*  
  <https://www.ibm.com/quantum/qiskit>

- Michael A. Nielsen, Isaac L. Chuang — *Quantum Computation and Quantum Information*  
  <https://michaelnielsen.org/qcqi/QINFO-book-nielsen-and-chuang-toc-and-chapter1-nov00.pdf>

- Microsoft Learn — *Azure Quantum documentation*  
  <https://learn.microsoft.com/en-us/azure/quantum/>
