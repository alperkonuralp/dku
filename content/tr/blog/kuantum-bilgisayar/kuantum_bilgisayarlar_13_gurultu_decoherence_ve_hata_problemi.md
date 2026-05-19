---
draft: true
---
# 13. Gürültü, Decoherence ve Hata Problemi

Kuantum bilgisayarları anlamaya çalışırken çoğu zaman süperpozisyon, dolaşıklık, kuantum kapıları ve algoritmalar öne çıkar. Fakat kuantum bilgisayarların bugün neden hâlâ sınırlı olduğunu anlamak için asıl kritik konu **gürültü, decoherence ve hata problemidir**.

Kâğıt üzerinde tasarlanan bir kuantum algoritma, ideal qubitler ve hatasız kapılar varsayabilir. Gerçek donanımda ise qubitler çevreleriyle etkileşir, kapılar tam istenen dönüşümü yapamayabilir, ölçüm yanlış sonuç verebilir, komşu qubitler birbirini istenmeyen şekilde etkileyebilir ve cihazın kalibrasyonu zaman içinde değişebilir. Bu nedenle kuantum bilgisayar tasarlamak yalnızca “çok sayıda qubit üretmek” değildir; o qubitleri yeterince uzun süre tutarlı, kontrol edilebilir ve güvenilir halde çalıştırabilmektir.

Bu bölümün amacı, kuantum bilgisayarların bugünkü sınırlarını teknik ama yalın bir dille açıklamaktır. Burada göreceğimiz ana fikir şudur:

> Kuantum bilgisayarların önündeki en büyük engellerden biri, kuantum durumlarının çok hassas olması ve hesaplama sırasında hataların hızla birikmesidir.

---

## 13.1. Kuantum sistemler neden hassastır?

Klasik bilgisayarlarda bilgi, fiziksel olarak çok kararlı durumlarla temsil edilir. Örneğin bir transistörün iletimde olup olmaması, bir bellek hücresinin belirli bir elektriksel durumu tutması veya bir manyetik alan yönelimi, pratik olarak 0 ve 1 değerlerini temsil edebilir. Bu durumlar elbette fiziksel dünyada yine gürültüye açıktır; ancak modern klasik bilgisayar mühendisliği, bu gürültüyü çok büyük ölçüde yönetebilecek kadar olgunlaşmıştır.

Kuantum bilgisayarlarda ise bilgi, çok daha hassas kuantum durumlarında tutulur. Bir qubit yalnızca “0” veya “1” gibi klasik bir değerden ibaret değildir. Qubit durumu olasılık genlikleri, faz bilgisi, süperpozisyon ve başka qubitlerle dolaşıklık gibi özellikler taşıyabilir. Bu özellikler kuantum hesaplamanın gücünü oluşturan şeylerdir; fakat aynı zamanda sistemi kırılgan hale getirir.

Bir qubitin durumu çevresiyle kontrolsüz biçimde etkileşirse, taşıdığı kuantum bilgi bozulabilir. Bu çevre çok farklı şekillerde ortaya çıkabilir:

- Isıl titreşimler,
- Elektromanyetik gürültü,
- Kontrol sinyallerindeki küçük sapmalar,
- Donanım kusurları,
- Komşu qubitlerle istenmeyen etkileşimler,
- Ölçüm cihazının sisteme etkisi,
- Zaman içinde değişen kalibrasyon parametreleri.

Bu nedenle kuantum donanımlar genellikle son derece kontrollü ortamlarda çalıştırılır. Süperiletken qubit sistemlerinde çok düşük sıcaklıklar gerekir. İyon tuzaklarında vakum, lazer kontrolü ve elektromanyetik alan hassasiyeti önemlidir. Nötr atom sistemlerinde lazerlerle atomların yakalanması ve düzenlenmesi gerekir. Fotonik sistemlerde kayıplar ve dedektör verimliliği kritik hale gelir.

Klasik bilgisayarlarda da hata vardır, fakat hata oranları çok düşüktür ve hata düzeltme teknikleri son derece olgundur. Kuantum bilgisayarlarda ise Microsoft’un kuantum hata düzeltme açıklamasında belirttiği gibi, bugünkü sistemlerde hata oranları klasik bilgisayarlara göre çok daha yüksektir; gürültü, decoherence ve kuantum kapılarındaki kusurlar hesaplamalarda hatalara yol açar. Microsoft, mevcut kuantum bilgisayarlarda hata oranlarının çoğunlukla yaklaşık yüzde 1 ile yüzde 0,1 aralığında olduğunu belirtir. Bu, ortalama olarak her 100 ile 1000 kuantum kapısı işleminden birinde hata oluşabileceği anlamına gelir.

Bu oranlar kulağa küçük gelebilir, fakat kuantum algoritmalar açısından ciddi bir sorundur. Çünkü anlamlı ve uzun bir kuantum algoritma binlerce, milyonlarca veya daha fazla kapı işlemi gerektirebilir. Her işlemde küçük bir hata olasılığı varsa, bu hatalar devre boyunca birikerek sonucu güvenilmez hale getirebilir.

Kısaca:

```text
Kuantum bilgisayarların zorluğu = qubit üretmek + qubiti korumak + qubiti doğru kontrol etmek + hataları yönetmek
```

Bu dört unsurdan biri zayıfsa, çok sayıda qubit bile tek başına yeterli değildir.

---

## 13.2. Decoherence nedir?

**Decoherence**, bir kuantum sisteminin çevresiyle etkileşime girerek kuantum özelliklerini kaybetmesi sürecidir. Daha yalın söylersek: Bir qubitin süperpozisyon, faz ilişkisi veya dolaşıklık gibi hesaplama için gerekli kuantum özelliklerinin zamanla bozulmasıdır.

Bir qubit ideal olarak şu tür bir durumda bulunabilir:

```text
|ψ⟩ = α|0⟩ + β|1⟩
```

Bu ifade yalnızca 0 ve 1 olasılıklarını değil, aynı zamanda `α` ve `β` genliklerinin büyüklüklerini ve faz ilişkisini de içerir. Kuantum algoritmalarda bu faz ilişkileri çok önemlidir; çünkü girişim mekanizması doğru cevabı güçlendirmek ve yanlış cevabı bastırmak için bu faz bilgisini kullanır.

Decoherence gerçekleştiğinde, qubitin kuantum durumu çevreyle kontrolsüz biçimde ilişkilendiği için sistem artık ideal biçimde korunamaz. Qubit hâlâ ölçüldüğünde 0 veya 1 verebilir; fakat hesaplama için gerekli hassas faz bilgisi veya dolaşıklık yapısı kaybolmuş olabilir.

Bunu klasik bir örnekle sezgisel olarak düşünelim. Çok düzenli bir dalga deseni hayal edelim. Bu dalga deseni, farklı dalgaların birbirini güçlendirmesi veya söndürmesiyle anlamlı bir sonuç üretebilir. Fakat dışarıdan rastgele titreşimler gelirse, dalga deseni bozulur. Artık hangi dalganın hangi dalgayla nasıl girişim yapacağını güvenilir biçimde kontrol edemeyiz.

Kuantum algoritmalar da benzer biçimde düzenli ve kontrollü genlik/faz ilişkilerine ihtiyaç duyar. Decoherence bu düzeni bozar.

Decoherence farklı şekillerde ortaya çıkabilir. En yaygın iki kavram şunlardır:

### Relaxation / enerji gevşemesi

Qubitin yüksek enerji durumundan düşük enerji durumuna geçmesiyle ilişkilidir. Örneğin bir qubitin `|1⟩` durumundan `|0⟩` durumuna istenmeyen biçimde düşmesi gibi düşünülebilir.

Bu süreci tanımlamak için sık kullanılan zaman ölçeği **T1** olarak bilinir. T1, qubitin enerji durumunu ne kadar süre koruyabildiğiyle ilişkilidir.

### Dephasing / faz bozunumu

Qubitin 0 ve 1 bileşenleri arasındaki faz ilişkisinin bozulmasıdır. Qubit enerji olarak aynı kalıyor gibi görünse bile, hesaplama için kritik olan faz bilgisi kaybolabilir.

Bu süreç için sık kullanılan zaman ölçeği **T2** olarak bilinir. T2, qubitin faz bilgisini ne kadar süre koruyabildiğiyle ilişkilidir.

Bu ayrım önemlidir çünkü kuantum hesaplama yalnızca “qubit 0 mı 1 mi?” sorusuyla ilgilenmez. Kuantum algoritmalar için faz bilgisi ve genliklerin ilişkisi çoğu zaman en az ölçüm sonucu kadar önemlidir.

Basitçe:

```text
T1 problemi: Qubit enerji durumunu kaybedebilir.
T2 problemi: Qubit faz bilgisini kaybedebilir.
```

Decoherence süresi, kuantum devrenin ne kadar uzun çalıştırılabileceğini etkiler. Eğer bir algoritmanın çalışması qubitin tutarlı kalabildiği süreden uzun sürüyorsa, sonuç güvenilir olmayabilir. Bu yüzden kuantum donanımda yalnızca qubit sayısı değil, **coherence time**, kapı süresi ve hata oranı birlikte değerlendirilmelidir.

---

## 13.3. Gate hataları

Kuantum kapıları, qubit durumunu kontrollü biçimde dönüştürmek için kullanılır. Örneğin Hadamard kapısı süperpozisyon oluşturabilir, X kapısı bit-flip benzeri bir etki yapabilir, Z kapısı fazı değiştirebilir, CNOT kapısı iki qubit arasında dolaşıklık oluşturmak için kullanılabilir.

İdeal teoride bu kapılar kusursuz matematiksel dönüşümlerdir. Gerçek donanımda ise kuantum kapıları fiziksel kontrol sinyalleriyle uygulanır. Bu sinyallerin her zaman tam istenen işlemi yapması beklenemez.

Gate hatalarının bazı nedenleri şunlardır:

- Kontrol darbesinin süresindeki küçük sapmalar,
- Darbenin genliğindeki veya frekansındaki hata,
- Qubitin beklenenden farklı tepki vermesi,
- Komşu qubitlerle istenmeyen etkileşim,
- Donanımın zaman içinde kalibrasyondan sapması,
- Fiziksel sistemdeki gürültü ve kusurlar.

Örneğin bir Hadamard kapısının ideal olarak qubiti belirli bir süperpozisyon durumuna getirmesi beklenir. Fakat uygulanan kontrol sinyali biraz hatalıysa, qubit tam hedeflenen noktaya gitmeyebilir. Tek bir kapıdaki küçük sapma önemsiz gibi görünebilir; ancak yüzlerce veya binlerce kapıdan oluşan bir devrede bu sapmalar birikerek sonucu bozabilir.

Gate hatalarını iki ana grupta düşünebiliriz:

### Sistematik hatalar

Bunlar tekrar eden, belirli bir yönde sapma gösteren hatalardır. Örneğin bir kapının her çalıştırıldığında hedef dönüşten azıcık fazla döndürmesi gibi. Sistematik hatalar kalibrasyon, modelleme veya kontrol iyileştirmeleriyle azaltılabilir.

### Rastgele hatalar

Bunlar her çalıştırmada farklı şekilde ortaya çıkabilen, daha zor öngörülen hatalardır. Çevresel gürültü, rastgele dalgalanmalar veya ölçüm belirsizlikleri bu tür hatalara katkı sağlayabilir.

Kuantum kapı hatalarının önemli bir sonucu şudur: Devre derinliği arttıkça hata birikimi de artar. **Devre derinliği**, kabaca bir kuantum algoritmanın arka arkaya kaç işlem adımı gerektirdiğini ifade eder. Çok derin devreler, bugünkü gürültülü donanımlarda güvenilir biçimde çalıştırılması zor devrelerdir.

Bu yüzden NISQ döneminde geliştirilen algoritmalarda genellikle daha kısa, daha sığ ve hibrit devreler tercih edilir. VQE ve QAOA gibi algoritmaların öne çıkmasının nedenlerinden biri de budur: Bu algoritmalar, mevcut gürültülü donanımlarda tamamen uzun ve derin fault-tolerant algoritmalardan daha uygulanabilir olabilir.

Ancak bu, NISQ algoritmaların otomatik olarak pratik avantaj sağladığı anlamına gelmez. Gate hataları, ölçüm hataları ve gürültü hâlâ bu algoritmaların performansını sınırlayan temel faktörlerdir.

---

## 13.4. Ölçüm hataları

Kuantum bilgisayarda ölçüm, qubitin kuantum durumundan klasik bilgi elde etme işlemidir. Ölçüm sonucunda genellikle 0 veya 1 gibi klasik bir sonuç alırız. Ancak gerçek donanımda ölçüm de hatasız değildir.

Ölçüm hatası şu şekilde ortaya çıkabilir:

```text
Gerçek durum: 0
Ölçülen sonuç: 1
```

veya:

```text
Gerçek durum: 1
Ölçülen sonuç: 0
```

Bu tür hatalar, özellikle çok sayıda ölçüm sonucu üzerinden olasılık dağılımı çıkarılan kuantum algoritmalarda önemlidir. Kuantum algoritmalar genellikle tek çalıştırmada kesin cevap vermez; devre birçok kez çalıştırılır ve sonuçların dağılımı incelenir. Eğer ölçüm cihazı bazı sonuçları yanlış okuyorsa, elde edilen dağılım gerçek dağılımdan sapabilir.

Ölçüm hatalarının nedenleri donanım mimarisine göre değişebilir. Süperiletken qubitlerde ölçüm rezonatörleri, sinyal ayrımı ve okuma elektroniği önemlidir. İyon tuzaklarında floresans okuma yöntemleri kullanılır ve foton algılama kalitesi belirleyici olabilir. Fotonik sistemlerde dedektör verimliliği ve kayıplar kritik hale gelir.

Ölçüm hataları, gate hatalarından farklı olarak çoğunlukla hesaplamanın sonunda ortaya çıkıyor gibi görünür. Fakat kuantum algoritmalarda ara ölçümler de kullanılabilir. Ayrıca hata düzeltme protokollerinde ölçüm çok daha merkezi bir role sahiptir; çünkü hata sendromlarını tespit etmek için yardımcı qubitler ölçülür. Bu ölçümlerin kendisi hatalıysa, hata düzeltme süreci de yanlış bilgiye dayanabilir.

Bu yüzden ölçüm güvenilirliği, yalnızca sonuç okuma kalitesi değil, hata düzeltme mimarisinin de temel bileşenidir.

Ölçüm hatalarını azaltmak için farklı teknikler kullanılır:

- Ölçüm kalibrasyonu,
- Readout error mitigation,
- Sonuç dağılımlarının istatistiksel düzeltilmesi,
- Daha iyi dedektör ve okuma devreleri,
- Donanım seviyesinde sinyal-gürültü oranını artırma.

Ancak burada dikkat edilmesi gereken nokta şudur: **Error mitigation**, yani hata azaltma, hata düzeltme ile aynı şey değildir. Hata azaltma, mevcut gürültülü sonuçlardan daha iyi tahminler çıkarmaya çalışır. Hata düzeltme ise kuantum hesaplamayı aktif olarak koruyup hataları tespit/düzeltmeyi amaçlar. Bugünkü NISQ cihazlarda error mitigation önemli bir araçtır; fakat büyük ölçekli, güvenilir kuantum hesaplama için tek başına yeterli değildir.

---

## 13.5. Crosstalk ve kalibrasyon problemleri

Kuantum bilgisayarlarda qubitleri tek tek düşünmek yeterli değildir. Gerçek cihazlarda qubitler fiziksel olarak aynı sistemin parçasıdır. Bu nedenle bir qubit üzerinde yapılan işlem, istemeden başka bir qubiti de etkileyebilir. Bu tür istenmeyen etkileşimlere genel olarak **crosstalk** denir.

Crosstalk klasik elektronik sistemlerde de bilinen bir kavramdır. Bir sinyal hattındaki etkinin başka bir hattı etkilemesi klasik devrelerde de sorun olabilir. Kuantum bilgisayarlarda ise crosstalk daha hassas bir problem haline gelir; çünkü qubit durumları faz bilgisi ve dolaşıklık gibi kırılgan özellikler taşır.

Crosstalk şu şekillerde ortaya çıkabilir:

- Bir qubite uygulanan kontrol darbesinin komşu qubiti etkilemesi,
- İki qubit arasındaki bağlaşımın tam kapatılamaması,
- Aynı anda uygulanan kapıların birbirini bozması,
- Frekansların birbirine çok yakın olması,
- Ortak kontrol veya ölçüm hatlarının istenmeyen etkiler üretmesi.

Crosstalk özellikle ölçekleme açısından önemlidir. Az sayıda qubitli bir sistemde her qubit dikkatlice kalibre edilebilir. Ancak qubit sayısı arttıkça, her qubitin diğerleriyle etkileşimini modellemek ve kontrol etmek zorlaşır. Bu nedenle “daha fazla qubit eklemek” her zaman doğrusal bir ilerleme sağlamaz; bazen sistemin kontrol karmaşıklığı çok daha hızlı büyür.

Kalibrasyon problemi de burada devreye girer. Kuantum cihazlar, belirli kapıları doğru uygulayabilmek için sürekli olarak kalibre edilmelidir. Qubit frekansları, kontrol darbeleri, ölçüm eşikleri, kapı süreleri ve bağlaşım parametreleri zaman içinde değişebilir. Bu değişimlere **drift** denir.

Bir cihaz sabah doğru çalışıyor olabilir; fakat gün içinde küçük fiziksel değişimler nedeniyle bazı kapıların performansı düşebilir. Bu yüzden kuantum donanım işletimi yalnızca algoritmayı çalıştırmak değildir; cihazı sürekli izlemek, kalibre etmek ve hata karakterizasyonu yapmak gerekir.

Crosstalk ve kalibrasyon problemleri şunu gösterir:

```text
Kuantum bilgisayar performansı = qubit sayısı + kapı kalitesi + bağlantı mimarisi + kalibrasyon kararlılığı + hata yönetimi
```

Bu nedenle yalnızca qubit sayısına bakarak bir kuantum bilgisayarı değerlendirmek yanıltıcıdır.

---

## 13.6. Noise model kavramı

**Noise model**, kuantum bilgisayardaki hataları ve gürültüyü matematiksel veya simülasyonel olarak temsil etmeye yarayan modeldir. İdeal kuantum devre simülasyonunda kapılar kusursuz kabul edilir. Noise model eklendiğinde ise kapıların, ölçümlerin ve qubitlerin belirli hata olasılıklarıyla davrandığı varsayılır.

Noise model neden gereklidir?

Çünkü gerçek kuantum donanımda algoritma çalıştırmadan önce şu soruları sormak isteriz:

- Bu devre mevcut donanımda çalıştırılabilir mi?
- Hata oranları sonucu ne kadar bozar?
- Devre çok mu derin?
- Ölçüm hataları sonucu ne kadar etkiler?
- Hangi qubit eşleşmeleri daha güvenilir?
- Error mitigation uygulanırsa sonuç iyileşir mi?
- Algoritmanın çıktısı gürültüye ne kadar dayanıklı?

Noise model, bu soruları deneysel ve simülasyonel olarak incelemeye yardımcı olur.

Basit bir noise model şu tür varsayımlar içerebilir:

```text
Tek qubit kapısı hata oranı: %0,1
İki qubit kapısı hata oranı: %1
Ölçüm hata oranı: %2
Relaxation süresi: T1
Dephasing süresi: T2
```

Daha gelişmiş modellerde hata türleri daha ayrıntılı temsil edilir:

- Bit-flip hatası,
- Phase-flip hatası,
- Depolarizing noise,
- Amplitude damping,
- Phase damping,
- Readout error,
- Correlated noise,
- Crosstalk noise.

Noise model kavramı özellikle yazılımcılar için önemlidir. Çünkü kuantum programlama yalnızca ideal devreyi yazmakla bitmez. Gerçek donanımda çalışacak bir kuantum iş akışında şu adımlar gerekir:

1. Problemi kuantum devresine dönüştürmek,
2. Devreyi hedef donanıma uygun hale getirmek,
3. Donanımın bağlantı kısıtlarını dikkate almak,
4. Gate sayısını ve devre derinliğini azaltmak,
5. Noise model ile beklenen hata etkisini analiz etmek,
6. Gerekirse error mitigation uygulamak,
7. Sonuçları istatistiksel olarak yorumlamak.

Bu nedenle kuantum yazılım geliştirme, klasik yazılım geliştirmeden farklı olarak donanım farkındalığı gerektirir. Klasik uygulama geliştirirken CPU’nun en küçük elektronik gürültüsünü düşünmeyiz. Kuantum programlamada ise donanım gürültüsü algoritmanın anlamlı sonuç verip vermeyeceğini doğrudan etkileyebilir.

---

## 13.7. NISQ dönemi

**NISQ**, “Noisy Intermediate-Scale Quantum” ifadesinin kısaltmasıdır. Bu terim John Preskill tarafından 2018 yılında, yakın dönemdeki kuantum bilgisayarların karakterini anlatmak için kullanılmıştır. NISQ cihazlar belirli sayıda qubit içerir; bazı kuantum işlemleri yapabilir; fakat hâlâ gürültülüdür ve tam anlamıyla fault-tolerant değildir.

Preskill’in NISQ tanımındaki önemli nokta şudur: Bu cihazlar bilimsel olarak çok önemlidir, fakat dünyayı hemen değiştirecek genel amaçlı makineler olarak görülmemelidir. Gürültü, çalıştırılabilecek kuantum devrelerin boyutunu ve derinliğini sınırlar.

NISQ döneminin özellikleri şunlardır:

- Qubit sayısı artmaktadır, fakat hata oranları hâlâ sınırlayıcıdır.
- Uzun ve derin kuantum devreleri güvenilir çalıştırmak zordur.
- Tam ölçekli kuantum hata düzeltme henüz yaygın üretim kullanımında değildir.
- Hibrit klasik-kuantum algoritmalar öne çıkar.
- Error mitigation teknikleri önem kazanır.
- Deneysel araştırma, benchmark ve donanım karakterizasyonu merkezi rol oynar.
- Kuantum avantaj iddiaları dikkatli değerlendirilmelidir.

NISQ döneminde kuantum bilgisayarlar en çok şu amaçlarla değerlidir:

- Kuantum donanım mimarilerini test etmek,
- Gürültü ve hata kaynaklarını anlamak,
- Kuantum algoritmaları küçük ölçeklerde denemek,
- Error mitigation ve hata düzeltme tekniklerini geliştirmek,
- Kimya, fizik ve optimizasyon gibi alanlarda prototip çalışmalar yapmak,
- Gelecekteki fault-tolerant sistemlere hazırlık yapmak.

NISQ cihazların sınırlı olması, önemsiz oldukları anlamına gelmez. Tam tersine, bugünkü NISQ cihazlar kuantum bilgisayar mühendisliği için deneysel laboratuvar işlevi görür. Klasik bilgisayarların ilk dönemleri de bugünkü olgun sistemlerden çok uzaktı. Ancak fark şudur: Kuantum bilgisayarların ölçeklenmesi yalnızca daha küçük transistör yapmak gibi bir mühendislik problemi değildir; kuantum durumlarını koruma, hata düzeltme ve kontrollü ölçüm gibi daha derin fiziksel sorunları içerir.

Bu nedenle NISQ dönemi, hem umut hem de sınırlılık dönemidir.

---

## 13.8. Bugünkü kuantum bilgisayarların sınırları

Bugünkü kuantum bilgisayarların sınırlarını anlamak için yalnızca qubit sayısına bakmak yeterli değildir. Bir cihazda yüzlerce veya binlerce fiziksel qubit bulunabilir; fakat bu qubitler yeterince düşük hata oranına, yeterince uzun coherence süresine ve yeterince güçlü hata düzeltme altyapısına sahip değilse, büyük ölçekli algoritmalar için kullanılabilir olmayabilir.

Bugünkü ana sınırlar şunlardır:

### 1. Hata oranları hâlâ yüksektir

Kuantum kapıları ve ölçümler hatasız değildir. Microsoft’un açıklamasına göre bugünkü kuantum bilgisayarlarda hata oranları klasik bilgisayarlara kıyasla çok daha yüksektir ve çoğunlukla yüzde 1 ile yüzde 0,1 aralığında olabilir. Bu oranlar kısa deneyler için yönetilebilir görünse de uzun algoritmalar için ciddi bir engeldir.

### 2. Devre derinliği sınırlıdır

Bir kuantum algoritmanın yararlı sonuç üretmesi için çok sayıda kapı gerekebilir. Fakat her kapı hata riski taşıdığı için, bugünkü cihazlarda çok derin devreler çalıştırmak güvenilir değildir. Bu nedenle NISQ algoritmalar genellikle daha sığ devreler kullanmaya çalışır.

### 3. Coherence süresi sınırlıdır

Qubitler kuantum durumlarını sonsuza kadar koruyamaz. Decoherence nedeniyle hesaplama belirli bir süre içinde tamamlanmalıdır. Kapılar yavaşsa veya algoritma uzun sürüyorsa, qubitler hesaplama bitmeden anlamlı kuantum bilgiyi kaybedebilir.

### 4. Ölçekleme zordur

Daha fazla qubit eklemek, kontrol hatları, ölçüm kanalları, soğutma, lazer sistemleri, kalibrasyon, crosstalk ve hata düzeltme overhead’i gibi birçok yeni problemi beraberinde getirir. Ölçekleme, yalnızca donanıma qubit eklemek değil, sistemin tamamını güvenilir şekilde büyütmektir.

### 5. Mantıksal qubit sayısı yetersizdir

Büyük ölçekli, hataya dayanıklı kuantum hesaplama için fiziksel qubitlerden mantıksal qubitler oluşturmak gerekir. Ancak bir mantıksal qubit oluşturmak, hata düzeltme koduna ve fiziksel hata oranlarına bağlı olarak çok sayıda fiziksel qubit gerektirebilir. Bu nedenle fiziksel qubit sayısı yüksek olsa bile, kullanılabilir mantıksal qubit sayısı çok daha düşük olabilir.

### 6. Benchmark yorumlamak zordur

Kuantum cihazlar için tek bir performans metriği yoktur. Qubit sayısı, quantum volume, circuit layer operations per second, gate fidelity, ölçüm fidelity’si, coherence süresi, bağlantı grafı ve hata düzeltme performansı birlikte değerlendirilmelidir. Bu nedenle pazarlama duyurularındaki tekil rakamlar dikkatli okunmalıdır.

### 7. Uygulama avantajı henüz sınırlıdır

Kuantum bilgisayarların teorik olarak avantaj sağlayabileceği alanlar vardır. Fakat bugünkü cihazlarla, gerçek dünya problemlerinde klasik yöntemlere karşı sürekli, ekonomik ve üretim seviyesinde avantaj göstermek hâlâ zordur. NIST de mevcut kuantum bilgisayarların daha çok fizik, kimya ve matematik problemlerini keşfetmek ve daha güçlü kuantum bilgisayarların nasıl yapılacağını anlamak için test ortamı olarak kullanıldığını belirtir.

Bu tablo karamsar görünmemelidir. Aksine, kuantum bilgisayar alanındaki ilerlemenin gerçek doğasını gösterir. Sorun “kuantum bilgisayarlar çalışmıyor” değildir. Sorun, **yararlı ve büyük ölçekli kuantum hesaplama için hataların yeterince yönetilmesi gerektiğidir**.

Bu nedenle bugünkü stratejik değerlendirme şu olmalıdır:

```text
Bugünün kuantum bilgisayarları: araştırma, öğrenme, prototipleme ve hata yönetimi için değerlidir.
Geleceğin kuantum bilgisayarları: fault-tolerant yapıya ulaştığında belirli problem sınıflarında dönüştürücü olabilir.
```

---

## Bölüm Özeti

Bu bölümde kuantum bilgisayarların bugünkü en önemli teknik darboğazlarından biri olan gürültü ve hata problemini ele aldık.

Öne çıkan noktalar şunlardır:

- Qubitler klasik bitlere göre çok daha hassastır.
- Kuantum bilgi yalnızca 0/1 değerinden ibaret değildir; faz, genlik ve dolaşıklık gibi hassas yapılar içerir.
- Decoherence, kuantum sistemin çevreyle etkileşerek kuantum özelliklerini kaybetmesidir.
- Gate hataları, kuantum kapılarının ideal matematiksel dönüşümleri tam gerçekleştirememesinden kaynaklanır.
- Ölçüm hataları, qubitin gerçek durumuyla okunan klasik sonuç arasındaki sapmalardır.
- Crosstalk, bir qubit veya kontrol işleminin başka qubitleri istemeden etkilemesidir.
- Kalibrasyon, kuantum cihazlarda sürekli ve kritik bir ihtiyaçtır.
- Noise model, gerçek donanım hatalarını simüle etmek ve algoritma davranışını değerlendirmek için kullanılır.
- NISQ dönemi, gürültülü ama bilimsel olarak değerli ara dönem kuantum bilgisayarları ifade eder.
- Bugünkü kuantum bilgisayarların en büyük sınırı, büyük ölçekli ve güvenilir hesaplama için yeterli hata düzeltme altyapısına henüz sahip olmamalarıdır.

Bu bölümün ana mesajı şudur:

> Kuantum bilgisayarların gelecekteki gücünü belirleyecek şey yalnızca daha fazla qubit üretmek değil; qubitleri daha düşük hatayla, daha uzun süre, daha kontrollü ve hata düzeltmeye uygun biçimde çalıştırabilmektir.

---

## Kaynaklar ve İleri Okuma

- NIST — *Quantum Computing Explained*  
  https://www.nist.gov/quantum-information-science/quantum-computing-explained

- Microsoft Learn — *Quantum Error Correction Codes*  
  https://learn.microsoft.com/en-us/azure/quantum/concepts-error-correction

- Microsoft Quantum — *Quantum error correction*  
  https://quantum.microsoft.com/en-us/insights/education/concepts/quantum-error-correction

- John Preskill — *Quantum Computing in the NISQ era and beyond*  
  https://arxiv.org/abs/1801.00862

- Quantum Journal — *Quantum Computing in the NISQ era and beyond*  
  https://quantum-journal.org/papers/q-2018-08-06-79/

- Bharti et al. — *Noisy intermediate-scale quantum algorithms*, Reviews of Modern Physics  
  https://link.aps.org/doi/10.1103/RevModPhys.94.015004
