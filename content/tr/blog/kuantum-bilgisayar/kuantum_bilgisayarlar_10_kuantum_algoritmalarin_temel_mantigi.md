# 10. Kuantum Algoritmaların Temel Mantığı

Önceki bölümlerde qubit, süperpozisyon, ölçüm, dolaşıklık, girişim, kuantum kapıları ve kuantum devreleri gibi temel kavramları inceledik. Bu bölümde artık bu kavramların bir araya gelerek nasıl “algoritma” oluşturduğunu ele alacağız.

Kuantum algoritmaları anlamanın en sağlıklı yolu, onları klasik algoritmaların egzotik bir versiyonu gibi değil, farklı bir hesaplama modelinin ürünleri gibi görmektir. Klasik algoritmada veri genellikle açık biçimde okunur, karşılaştırılır, dallanır, döngülerle işlenir ve sonuç üretilir. Kuantum algoritmada ise çoğu zaman doğrudan “değerlerle” değil, kuantum durumlarıyla çalışılır. Bu durumlar kapılarla dönüştürülür, olasılık genlikleri yönlendirilir, bazı faz bilgileri anlamlı hale getirilir ve sonunda ölçümle klasik bir çıktı elde edilir.

Bu yüzden kuantum algoritma tasarımının merkezinde şu soru vardır:

> Ölçüm yaptığımda istediğim sonucu yüksek olasılıkla elde edebilmek için qubit durumlarını nasıl hazırlamalı, nasıl dönüştürmeli ve nasıl girişime sokmalıyım?

Bu bölüm, bu sorunun temel yapı taşlarını açıklamak için hazırlanmıştır.

---

## 10.1. Kuantum algoritma nedir?

Kuantum algoritma, bir problemi çözmek için kuantum hesaplama modelini kullanan işlem adımları bütünüdür. Bu adımlar genellikle qubitlerin hazırlanmasını, kuantum kapılarının uygulanmasını, gerekiyorsa dolaşıklık oluşturulmasını, faz ve genliklerin düzenlenmesini, ölçüm yapılmasını ve çıkan klasik sonucun yorumlanmasını içerir.

Klasik bir algoritmada işlem adımları çoğunlukla şu şekilde düşünülür:

```text
Girdi al.
Değerleri işle.
Karar ver.
Döngü çalıştır.
Sonuç üret.
```

Kuantum algoritmada ise tipik düşünce şuna daha yakındır:

```text
Başlangıç kuantum durumunu hazırla.
Problemi kuantum devresine kodla.
Süperpozisyon oluştur.
Dolaşıklık ve faz ilişkileri kur.
Girişim yoluyla bazı sonuçların olasılığını artır.
Ölçüm yap.
Klasik sonucu yorumla.
```

Buradaki kritik fark, kuantum algoritmanın çoğu zaman ölçümden önceki ara durumları doğrudan kullanıcıya göstermemesidir. Kuantum durumunun tamamını klasik bir veri yapısı gibi okuyamayız. Ölçüm sonucunda belirli bir klasik çıktı elde ederiz. Bu nedenle kuantum algoritma, ölçüm anında istenen cevabın yüksek olasılıkla ortaya çıkmasını sağlayacak şekilde tasarlanır.

Bir kuantum algoritmanın genel iskeleti şöyle düşünülebilir:

```text
1. Problem klasik dünyada tanımlanır.
2. Problem kuantum devresiyle temsil edilebilir hale getirilir.
3. Qubitler başlangıç durumuna alınır.
4. Kuantum kapıları uygulanır.
5. Olasılık genlikleri ve fazlar istenen şekilde yönlendirilir.
6. Ölçüm yapılır.
7. Ölçüm sonucu klasik olarak işlenir.
8. Gerekirse algoritma birden çok kez çalıştırılır.
```

Bu akıştan da görülebileceği gibi kuantum algoritma çoğu zaman tamamen kuantum dünyasında yaşayan kapalı bir yapı değildir. Klasik bilgisayar, problemin hazırlanmasında, parametrelerin seçilmesinde, deneylerin tekrarlanmasında, ölçüm sonuçlarının istatistiksel olarak değerlendirilmesinde ve nihai kararın verilmesinde önemli rol oynar.

Kuantum algoritma için şu tanım yararlı olabilir:

> Kuantum algoritma, bir problemin çözümünü kuantum durumlarının kontrollü dönüşümü ve ölçüm sonucunda istenen cevabın olasılığını artırma fikri üzerine kuran algoritmadır.

Bu tanım özellikle önemlidir, çünkü kuantum algoritmaların gücü yalnızca süperpozisyondan gelmez. Süperpozisyon olasılık alanını açar; dolaşıklık qubitler arasında klasik olmayan ilişkiler kurabilir; girişim ise doğru cevapların öne çıkmasını sağlayan ana mekanizmalardan biridir.

---

## 10.2. Klasik algoritmadan farkı nedir?

Kuantum algoritmalar ile klasik algoritmalar arasındaki farkı anlamak için önce klasik algoritmanın nasıl çalıştığını düşünelim.

Klasik bir algoritma, genellikle açık değerler üzerinde çalışır. Bellekteki bir değişkenin değeri vardır. Bu değer okunabilir, kopyalanabilir, karşılaştırılabilir ve başka bir yere yazılabilir. Örneğin bir dizide arama yapan klasik algoritma, dizinin elemanlarını belirli bir sırayla kontrol edebilir. Bir sıralama algoritması, iki elemanı karşılaştırabilir ve gerekirse yerlerini değiştirebilir. Bir grafik algoritması, düğümler ve kenarlar üzerinde adım adım ilerleyebilir.

Kuantum algoritmada ise ara bilgi çoğu zaman doğrudan okunabilir biçimde değildir. Qubitlerin durumu ölçülmeden önce olasılık genlikleriyle temsil edilir. Bu durumun tamamını ölçmeden öğrenmek mümkün değildir; ölçüm de durumu değiştirir. Ayrıca bilinmeyen bir kuantum durumunu keyfi biçimde kopyalayamayız. Bu nedenle kuantum algoritma tasarımı, klasik algoritma tasarımından farklı sezgiler gerektirir.

Temel farkları şöyle özetleyebiliriz:

| Boyut | Klasik algoritma | Kuantum algoritma |
|---|---|---|
| Bilgi birimi | Bit | Qubit |
| Ara durum | Okunabilir klasik değerler | Ölçülmediği sürece doğrudan okunamayan kuantum durumları |
| İşlem mantığı | Mantıksal dönüşümler, karşılaştırmalar, dallanmalar | Üniter dönüşümler, faz değişimleri, girişim, ölçüm |
| Kopyalama | Veri kolayca kopyalanabilir | Bilinmeyen kuantum durum genel olarak kopyalanamaz |
| Ölçüm/okuma | Değeri okumak genellikle değeri bozmaz | Ölçüm kuantum durumunu etkiler |
| Rastlantısallık | Genellikle isteğe bağlıdır | Ölçüm doğası gereği olasılıksaldır |
| Sonuç alma | Tek çalıştırma çoğu zaman yeterlidir | Çoğu algoritmada istatistiksel tekrar gerekir |

Kuantum algoritmaların farkı yalnızca daha fazla olasılık kullanmaları değildir. Klasik bilgisayarlar da olasılıksal algoritmalar çalıştırabilir. Örneğin Monte Carlo yöntemleri, randomize arama algoritmaları veya olasılıksal veri yapıları klasik dünyada zaten vardır.

Kuantum algoritmayı ayıran şey, olasılıkların doğrudan değil, olasılık genlikleri üzerinden şekillenmesidir. Olasılık genlikleri negatif veya karmaşık değerler içerebilir; faz bilgisi taşıyabilir; birbirini güçlendirebilir veya söndürebilir. Bu, klasik olasılıksal algoritmalardan farklı bir mekanizma sağlar.

Basitçe söylemek gerekirse:

```text
Klasik olasılıksal algoritma:
Rastgele seçimler yapar ve olasılıklarla çalışır.

Kuantum algoritma:
Olasılık genliklerini ve fazları dönüştürür; girişimle bazı sonuçları öne çıkarır.
```

Bu fark, kuantum algoritmaların bazı problemlerde klasik algoritmalardan çok daha farklı ölçeklenme davranışı gösterebilmesini sağlar. Ancak bu, her problem için geçerli değildir. Kuantum algoritmanın avantaj sağlayabilmesi için problemin kuantum yapıyla ifade edilebilir, girişimden yararlanabilir ve ölçüm sonunda anlamlı klasik sonuç üretebilir olması gerekir.

---

## 10.3. Oracle kavramı

Kuantum algoritmalarda sık karşılaşılan kavramlardan biri **oracle** kavramıdır. Oracle, belirli bir problem hakkında bilgi veren özel bir işlem gibi düşünülebilir. Klasik algoritma teorisinde de oracle kavramı vardır; bir soruya cevap veren kara kutu işlevi gibi kullanılır. Kuantum algoritmalarda oracle genellikle problemin çözüm kriterini kuantum devresine kodlayan bileşendir.

Örneğin arama problemi düşünelim. Elimizde çok sayıda olası aday olsun ve bunlardan bazıları “iyi çözüm” olsun. Klasik bir fonksiyon şöyle çalışabilir:

```text
f(x) = 1 ise x iyi çözümdür.
f(x) = 0 ise x iyi çözüm değildir.
```

Kuantum algoritmada oracle bu fonksiyonu doğrudan klasik şekilde çalıştırıp sonucu ekrana yazdırmaz. Bunun yerine kuantum durumları üzerinde bir dönüşüm uygular. Grover algoritmasındaki tipik oracle, iyi durumların fazını değiştirir. Bu faz değişimi, daha sonra amplitude amplification süreciyle doğru cevabın olasılığını artırmak için kullanılır.

Sezgisel olarak oracle şöyle düşünülebilir:

```text
Oracle, doğru cevabı doğrudan söylemez.
Doğru cevap olan durumları kuantum sistem içinde işaretler.
```

Bu “işaretleme” çoğu zaman faz üzerinden yapılır. Örneğin iyi çözüm durumunun genliği işaret değiştirir:

```text
|x⟩  →  -|x⟩   eğer x iyi çözümdür
|x⟩  →   |x⟩   eğer x iyi çözüm değildir
```

Bu tek başına cevabı vermez. Çünkü ölçüm yaptığınızda doğru cevabın olasılığı hemen büyümüş olmayabilir. Oracle sadece bazı durumları işaretlemiştir. Ardından başka kuantum işlemleri bu işaretlemeyi kullanarak doğru cevabın genliğini artırır.

Oracle kavramı bazı kullanıcılar için ilk başta yapay görünebilir. Çünkü “Problemin cevabını oracle biliyorsa algoritmaya ne gerek var?” sorusu doğabilir. Burada dikkat edilmesi gereken nokta şudur: Oracle cevabı liste halinde vermez; sadece belirli bir adayın çözüm olup olmadığını test eden koşulu kuantum dönüşümü olarak temsil eder.

Klasik dünyadan bir benzetme yapalım:

```text
Bir şifre deniyorsunuz.
Sistem size şifreyi söylemiyor.
Ama girdiğiniz adayın doğru olup olmadığını kontrol edebiliyor.
```

Oracle da buna benzer. Çözümü doğrudan açıklamaz; adayları değerlendiren kuralı sağlar. Kuantum algoritma ise bu kuralı süperpozisyon, faz ve girişim mekanizmalarıyla birlikte kullanarak klasik kaba kuvvet aramadan farklı bir yol izleyebilir.

Oracle özellikle şu algoritmalarda merkezi rol oynar:

- Deutsch-Jozsa algoritması
- Bernstein-Vazirani algoritması
- Simon algoritması
- Grover algoritması
- Amplitude amplification tabanlı yöntemler

Oracle kavramını anlamak, kuantum algoritmaları “sihirli hızlanma” gibi görmemek açısından önemlidir. Kuantum algoritmanın başarısı çoğu zaman oracle’ın nasıl kurulduğuna, problemin kuantum devresine nasıl kodlandığına ve bu kodlamanın maliyetine bağlıdır.

---

## 10.4. Amplitude amplification

**Amplitude amplification**, kuantum algoritmalarda doğru veya istenen sonuçların ölçüm olasılığını artırmak için kullanılan temel bir tekniktir. En bilinen örneği Grover algoritmasıdır.

Bu kavramı anlamak için önce “amplitude” yani genlik kavramını hatırlayalım. Bir kuantum durumda her olası sonucun bir olasılık genliği vardır. Ölçüm sonucunda bir durumun gelme olasılığı, bu genliğin karesiyle ilişkilidir. Dolayısıyla bir durumun genliğini artırabilirsek, ölçümde o sonucu görme olasılığını da artırabiliriz.

Amplitude amplification’ın temel fikri şudur:

```text
1. Tüm aday çözümlerden oluşan bir süperpozisyon hazırla.
2. Oracle ile iyi çözümleri faz açısından işaretle.
3. Diffusion / reflection işlemiyle iyi çözümlerin genliğini artır.
4. Bu adımları uygun sayıda tekrarla.
5. Ölçüm yaptığında iyi çözümü yüksek olasılıkla elde et.
```

Grover algoritması bağlamında süreç çoğu zaman iki ana işlemle anlatılır:

```text
Oracle:
İyi çözüm durumlarını faz işaretiyle işaretler.

Diffusion operator:
Genlikleri ortalama etrafında yansıtarak işaretlenmiş durumların genliğini büyütür.
```

Bu iki adım birlikte tekrarlandığında, doğru cevabın genliği giderek büyür. Ancak burada dikkat edilmesi gereken önemli bir nokta vardır: Bu işlem sonsuza kadar tekrarlanmaz. Gereğinden fazla tekrar, doğru cevabın genliğini yeniden azaltabilir. Bu yüzden Grover algoritmasında tekrar sayısı dikkatli seçilir.

Klasik kaba kuvvet aramada N aday varsa, en kötü durumda N deneme gerekebilir. Grover algoritması ideal koşullarda yaklaşık √N mertebesinde sorgu ile çözüm bulabilir. Bu, üstel değil ama çok önemli bir karekök hızlanmadır.

Örneğin:

```text
1.000.000 adaylık bir arama alanı düşünelim.
Klasik kaba kuvvet yaklaşımı yaklaşık 1.000.000 kontrol gerektirebilir.
Grover tipi ideal kuantum arama yaklaşık 1.000 kontrol mertebesine inebilir.
```

Bu basitleştirilmiş bir örnektir; gerçek sistemlerde oracle kurma maliyeti, hata oranları, devre derinliği ve donanım sınırlamaları hesaba katılmalıdır. Yine de amplitude amplification, kuantum algoritmaların nasıl avantaj üretmeye çalıştığını anlamak için çok güçlü bir örnektir.

Amplitude amplification bize şu dersi verir:

> Kuantum algoritma tüm cevapları okuyarak değil, doğru cevabın ölçüm olasılığını büyüterek çalışır.

Bu fikir, kuantum algoritmaların “paralel evrenlerde tüm çözümleri deneyip doğru olanı seçtiği” gibi popüler ama hatalı anlatımların yerine daha doğru bir zihinsel model koyar.

---

## 10.5. Phase estimation

**Quantum Phase Estimation** veya kısaca **QPE**, kuantum algoritmaların en önemli yapı taşlarından biridir. Shor algoritması gibi büyük tarihsel öneme sahip algoritmalarda merkezi rol oynar. Ayrıca kuantum simülasyon ve bazı lineer cebir tabanlı kuantum algoritmalarında da kullanılır.

Phase estimation’ın amacı, belirli bir üniter işlemin bir özdurum üzerindeki faz bilgisini tahmin etmektir.

Daha teknik ifade ile, elimizde bir `U` üniter işlemi ve bu işlemin bir özdurumu `|ψ⟩` olsun:

```text
U|ψ⟩ = e^(2πiθ)|ψ⟩
```

Burada `θ`, tahmin etmek istediğimiz faz bilgisidir.

İlk bakışta bu çok soyut gelebilir. Daha sezgisel düşünelim: Bazı kuantum işlemler, durumun yönünü veya gözle görünür klasik değerini değiştirmek yerine fazını değiştirir. Bu faz doğrudan ölçüldüğünde görünmeyebilir. Phase estimation, bu gizli faz bilgisini ölçülebilir klasik bilgiye dönüştürmenin bir yoludur.

Basitleştirilmiş akış şöyledir:

```text
1. Bir sayma/register alanı hazırlanır.
2. Bu register süperpozisyona alınır.
3. Kontrollü U işlemleri uygulanır.
4. Faz bilgisi register üzerinde kodlanır.
5. Ters Quantum Fourier Transform uygulanır.
6. Ölçüm yapılarak faz tahmini elde edilir.
```

Phase estimation neden önemlidir?

Çünkü birçok kuantum probleminde asıl aranan bilgi, bir sistemin enerji seviyesi, frekansı, periyodu veya özdeğer yapısıyla ilgilidir. Phase estimation bu tür bilgileri kuantum durumlarından çıkarmak için temel bir araçtır.

Özellikle şu alanlarda önemlidir:

- Shor algoritmasında periyot bulma
- Kuantum kimya simülasyonlarında enerji tahmini
- Hamiltonian simulation
- Bazı lineer sistem algoritmaları
- Quantum Fourier Transform tabanlı algoritmalar

Phase estimation’ın gücü, faz gibi doğrudan okunması kolay olmayan bir kuantum bilgisini ölçülebilir bir klasik çıktıya dönüştürmesidir. Ancak pratikte QPE derin devreler, kontrollü işlemler ve hassas hata yönetimi gerektirebilir. Bu nedenle bugünkü gürültülü kuantum bilgisayarlarda tam ölçekli QPE uygulamaları sınırlıdır.

Burada önemli bir ayrım vardır:

```text
Teorik QPE:
Fault-tolerant kuantum bilgisayarlarda çok güçlü bir temel araçtır.

Bugünkü NISQ cihazlarda QPE:
Gürültü ve devre derinliği nedeniyle sınırlı uygulanabilirliğe sahiptir.
```

Bu ayrım, kuantum algoritmaları değerlendirirken çok önemlidir. Bir algoritmanın teoride güçlü olması, bugünkü donanımda hemen pratik değer üreteceği anlamına gelmez.

---

## 10.6. Quantum Fourier Transform

**Quantum Fourier Transform** veya kısaca **QFT**, klasik ayrık Fourier dönüşümünün kuantum hesaplama modelindeki karşılığıdır. Ancak QFT’yi yalnızca “klasik Fourier dönüşümünün kuantum versiyonu” diye düşünmek eksik olur. Kuantum algoritmalarda QFT, faz ve periyot bilgisini ölçülebilir hale getiren temel bir alt yordamdır.

Klasik Fourier dönüşümü, bir sinyali frekans bileşenlerine ayırmak için kullanılır. QFT de kuantum durumunun baz temsilini değiştirerek faz ve periyot yapısını ortaya çıkarır. IBM Quantum Learning içerikleri QFT’yi kuantum algoritmalarda, özellikle phase estimation içinde kullanılan temel bir alt yordam olarak açıklar.

Sezgisel olarak QFT şunu yapar:

```text
Kuantum durumundaki periyodik veya fazsal yapıyı,
ölçümle anlamlı bilgiye dönüşebilecek başka bir baza taşır.
```

QFT’nin Shor algoritmasındaki rolü özellikle önemlidir. Shor algoritması büyük sayıların çarpanlara ayrılmasını doğrudan “çarpanları tahmin etme” problemi olarak çözmez. Problem, periyot bulma problemine dönüştürülür. QFT ise bu periyot bilgisini ortaya çıkarmada merkezi bir araçtır.

QFT’nin kullanıldığı yerler:

- Quantum Phase Estimation
- Shor algoritması
- Periyot bulma problemleri
- Bazı kuantum simülasyon yöntemleri
- Faz ve frekans yapısı içeren kuantum algoritmalar

QFT’nin önemli taraflarından biri, klasik Fourier dönüşümünün doğrudan tüm çıktısını üretmekten farklı çalışmasıdır. Bir kuantum devre QFT uyguladığında, sonuç yine kuantum durumudur. Bu durumun tamamını klasik olarak okuyamayız. Ölçüm yaptığımızda sınırlı klasik bilgi elde ederiz. Bu nedenle QFT’nin kuantum algoritmalardaki değeri, tek başına “Fourier dönüşümünü hızlı yapmak” değildir; faz ve periyot bilgisini algoritmanın geri kalanıyla birlikte kullanılabilir hale getirmesidir.

Bunu şöyle özetleyebiliriz:

```text
QFT, kuantum algoritmalarda gizli periyot ve faz bilgilerini açığa çıkarmak için kullanılan temel bir baz dönüşümüdür.
```

Burada yine aynı noktaya geliyoruz: Kuantum algoritmaların gücü yalnızca veriyi çok hızlı işlemekten değil, problemin matematiksel yapısını kuantum durumları üzerinde uygun şekilde temsil etmekten gelir.

---

## 10.7. Kuantum algoritmalarda klasik post-processing

Kuantum algoritmalar çoğu zaman ölçümle bitmez. Ölçüm sonucunda elde edilen bit dizileri, genellikle klasik bilgisayarda ayrıca işlenir. Bu adıma **klasik post-processing** denir.

Bu kavram, kuantum bilgisayarların pratikte çoğu zaman hibrit sistemler olarak kullanılacağını anlamak açısından önemlidir. Kuantum işlemci belirli bir alt görevi yerine getirir; klasik işlemci ise hazırlık, kontrol, tekrar, istatistiksel analiz ve nihai yorumlama yapar.

Tipik bir kuantum algoritma akışı şöyle olabilir:

```text
1. Klasik bilgisayar problemi hazırlar.
2. Parametreleri belirler.
3. Kuantum devresini oluşturur.
4. Kuantum işlemci devreyi çalıştırır.
5. Ölçüm sonuçları klasik bit dizileri olarak alınır.
6. Klasik bilgisayar sonuçları istatistiksel olarak değerlendirir.
7. Gerekirse yeni parametrelerle devre tekrar çalıştırılır.
8. Nihai sonuç klasik dünyada raporlanır.
```

Klasik post-processing’in önemli olduğu örnekler şunlardır:

### Shor algoritması

Kuantum bölüm periyot hakkında bilgi üretir. Ancak ölçüm sonucundan çarpanların çıkarılması için klasik sayı teorisi adımları gerekir. Yani kuantum bilgisayar tek başına sonucu sihirli biçimde yazdırmaz; klasik post-processing sonucun anlamlandırılmasında kritik rol oynar.

### Grover algoritması

Ölçüm sonucunda bir aday çözüm elde edilir. Bu adayın gerçekten geçerli olup olmadığı klasik olarak kontrol edilebilir. Özellikle birden fazla iyi çözüm varsa veya oracle karmaşıksa, klasik doğrulama önem kazanır.

### VQE ve QAOA

Bu algoritmalarda klasik optimizasyon döngüsü çok belirgindir. Kuantum devre belirli parametrelerle çalıştırılır; ölçüm sonuçlarından bir maliyet veya enerji tahmini çıkarılır; klasik optimizasyon algoritması yeni parametreler önerir; süreç tekrar eder.

Bu yapı şu nedenle önemlidir:

> Kuantum bilgisayar çoğu gerçek senaryoda klasik bilgisayarın yerine geçmez; onunla birlikte çalışan özel bir hızlandırıcı veya yardımcı hesaplama kaynağı gibi konumlanır.

GPU benzetmesi burada kısmen yardımcı olabilir. GPU, CPU’nun yaptığı her şeyi devralmaz; belirli iş yüklerinde hızlandırıcı olarak kullanılır. Kuantum bilgisayarlar için de gelecekte benzer bir hibrit rol beklenebilir. Ancak bu benzetmeyi fazla ileri götürmemek gerekir; çünkü kuantum bilgisayarların çalışma modeli GPU’dan çok daha farklıdır.

Klasik post-processing aynı zamanda güvenilirlik açısından da gereklidir. Kuantum ölçümleri olasılıksaldır. Bu nedenle algoritmalar çoğu zaman birçok kez çalıştırılır ve sonuç dağılımları analiz edilir. Tek bir ölçüm sonucu çoğu zaman yeterli değildir.

---

## 10.8. Kuantum avantaj ve kuantum üstünlük ayrımı

Kuantum algoritmaların temel mantığını anlamak için iki kavramı dikkatle ayırmak gerekir:

```text
Quantum supremacy / kuantum üstünlük
Quantum advantage / kuantum avantaj
```

Bu terimler bazen birbirinin yerine kullanılsa da aynı şeyi vurgulamazlar.

### Kuantum üstünlük nedir?

Kuantum üstünlük, bir kuantum bilgisayarın klasik bilgisayarlar için pratik olmayan veya makul sürede yapılamayacak bir görevi gerçekleştirdiğini göstermesi anlamında kullanılır. Bu görev pratik olarak faydalı olmak zorunda değildir. Önemli olan, kuantum cihazın belirli bir hesaplama görevinde klasik yaklaşımların erişemeyeceği bir performans göstermesidir.

Bu kavram tarihsel olarak özellikle deneysel dönüm noktalarını anlatmak için kullanılmıştır. Ancak terim zaman zaman tartışmalı bulunur; bazı kurumlar ve araştırmacılar daha nötr ifadeler kullanmayı tercih eder.

### Kuantum avantaj nedir?

Kuantum avantaj ise daha pratik bir beklentiye işaret eder. Bir kuantum bilgisayarın, belirli bir görevde klasik alternatiflere göre anlamlı bir avantaj sağlamasıdır. Bu avantaj hız, maliyet, enerji, doğruluk, ölçeklenebilirlik veya çözülebilir problem boyutu açısından olabilir. Daha önemlisi, kuantum avantaj genellikle pratik değeri olan görevler bağlamında düşünülür.

Basit ayrım:

| Kavram | Ana soru |
|---|---|
| Kuantum üstünlük | Kuantum bilgisayar klasiklerin pratikte yapamayacağı bir görevi yaptı mı? |
| Kuantum avantaj | Kuantum bilgisayar faydalı bir görevde klasik yaklaşımlardan gerçekten daha iyi mi? |

Bu ayrım neden önemlidir?

Çünkü bir kuantum cihazın belirli bir laboratuvar görevinde klasik bilgisayarlardan daha iyi görünmesi, hemen iş dünyasında kullanılabilir değer ürettiği anlamına gelmez. Aynı şekilde, bugün pratik avantaj sınırlı olsa bile bu alandaki temel araştırmaların önemsiz olduğu anlamına da gelmez.

Kuantum avantajı değerlendirirken şu sorular sorulmalıdır:

```text
Problem gerçek dünyada anlamlı mı?
Kuantum algoritma klasik en iyi alternatiflerle karşılaştırıldı mı?
Oracle veya veri yükleme maliyeti hesaba katıldı mı?
Donanım hataları ve tekrar sayısı dahil edildi mi?
Sonuç doğrulanabilir mi?
Avantaj yalnızca teorik mi, deneysel mi, ticari olarak anlamlı mı?
```

Özellikle kurumsal bakış açısından “kuantum avantaj” iddialarına dikkatli yaklaşmak gerekir. Bir sunumda veya basın bülteninde kuantum avantajdan bahsedilmesi, doğrudan üretim sistemlerine uygulanabilir bir çözüm olduğu anlamına gelmez. Problem tanımı, karşılaştırılan klasik yöntemler, donanım koşulları, maliyet ve tekrar edilebilirlik mutlaka incelenmelidir.

Kuantum algoritmaların olgunluk seviyesini değerlendirirken üç farklı düzey düşünülebilir:

```text
1. Teorik avantaj:
Matematiksel olarak klasik algoritmalardan daha iyi ölçeklenme gösterir.

2. Deneysel gösterim:
Belirli donanım üzerinde sınırlı problem için çalıştırılmıştır.

3. Pratik / ekonomik avantaj:
Gerçek dünya probleminde klasik alternatiflerden anlamlı biçimde daha iyi sonuç verir.
```

Bugün birçok kuantum algoritma birinci veya ikinci düzeydedir. Üçüncü düzey, yani geniş pratik ve ekonomik avantaj, hâlâ sınırlı ve aktif araştırma konusudur.

---

## Bölüm Özeti

Bu bölümde kuantum algoritmaların temel mantığını inceledik. Ana fikirleri şöyle özetleyebiliriz:

- Kuantum algoritma, qubit durumlarını kontrollü biçimde dönüştürerek ölçümde istenen sonucu yüksek olasılıkla elde etmeye çalışan algoritmadır.
- Kuantum algoritmalar klasik algoritmalardan yalnızca “daha hızlı” oldukları için değil, bilgi temsil ve işleme biçimleri farklı olduğu için ayrılır.
- Oracle, problemin çözüm kriterini kuantum devresi içinde işaretleyen özel bir işlem gibi düşünülebilir.
- Amplitude amplification, doğru veya istenen durumların ölçüm olasılığını artıran temel tekniktir.
- Phase estimation, kuantum sistemlerde faz bilgisini ölçülebilir klasik çıktıya dönüştürmek için kullanılır.
- Quantum Fourier Transform, faz ve periyot bilgisini ortaya çıkarmada kullanılan temel bir baz dönüşümüdür.
- Kuantum algoritmalar çoğu zaman klasik post-processing gerektirir; bu nedenle pratikte hibrit klasik-kuantum iş akışları önemlidir.
- Kuantum üstünlük ile kuantum avantaj aynı şey değildir; biri deneysel hesaplama sınırını, diğeri pratik faydayı vurgular.

Bu bölümden çıkarılması gereken en önemli sonuç şudur:

> Kuantum algoritmalar, tüm cevapları aynı anda deneyip sonucu sihirli biçimde seçmez. Onlar, kuantum durumlarını öyle dönüştürmeye çalışır ki ölçüm yapıldığında doğru veya yararlı cevabın ortaya çıkma olasılığı artsın.

---

## Kaynaklar ve İleri Okuma

- IBM Quantum Documentation — Grover's algorithm: https://quantum.cloud.ibm.com/docs/tutorials/grovers-algorithm
- IBM Quantum Learning — Quantum algorithms: Phase estimation: https://quantum.cloud.ibm.com/learning/en/courses/utility-scale-quantum-computing/quantum-phase-estimation
- IBM Quantum Learning — Quantum Fourier Transform: https://quantum.cloud.ibm.com/learning/modules/computer-science/qft
- IBM Quantum Documentation — Grover operator: https://quantum.cloud.ibm.com/docs/api/qiskit/qiskit.circuit.library.grover_operator
- Microsoft Learn — Quantum Fourier Transform tutorial: https://learn.microsoft.com/en-us/azure/quantum/tutorial-qdk-qubit-level-program
- Microsoft Q# API Reference — ApplyQFT operation: https://learn.microsoft.com/en-us/qsharp/api/qsharp-lang/std.canon/applyqft
- NIST — Quantum Supremacy: https://www.nist.gov/physics/introduction-new-quantum-revolution/quantum-supremacy
- NIST — Quantum Computing Explained: https://www.nist.gov/quantum-information-science/quantum-computing-explained
