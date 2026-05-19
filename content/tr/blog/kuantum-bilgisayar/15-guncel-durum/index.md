+++
title = "15. Kuantum Bilgisayarların Güncel Durumu"
description = "2026 itibarıyla kuantum bilgisayarlar nerede? Hype ile gerçek ilerlemeyi ayırt etmek."
date = "2026-05-18T00:00:00+03:00"
weight = 15
type = "guide"
draft = false
+++

> Bu bölüm, kuantum bilgisayarların 2026 itibarıyla nerede durduğunu anlamak için hazırlanmıştır. Önceki bölümlerde temel kavramları, donanım yaklaşımlarını, hata problemini ve kuantum hata düzeltmeyi ayrı ayrı ele aldık. Bu bölümde ise bunları güncel tabloyla birleştiriyoruz: Hangi oyuncular neyi hedefliyor? Hangi gelişmeler gerçekten önemli? Hangi duyurulara temkinli yaklaşmak gerekir? Hype ile gerçek ilerleme nasıl ayırt edilir?

---

## 15.1. 2026 itibarıyla genel tablo

2026 itibarıyla kuantum bilgisayarlar artık yalnızca akademik laboratuvarlarda konuşulan teorik sistemler değildir. Büyük teknoloji şirketleri, uzmanlaşmış kuantum girişimleri, üniversiteler, kamu destekli araştırma merkezleri ve bulut sağlayıcıları bu alanda ciddi yatırımlar yapmaktadır. Ancak bu durum, kuantum bilgisayarların bugün genel amaçlı, yaygın ve klasik bilgisayarların yerini alabilecek olgunlukta olduğu anlamına gelmez.

Bugünkü tabloyu en sağlıklı şekilde şu cümle özetler:

> Kuantum bilgisayarlar, belirli alanlarda çok büyük potansiyel taşıyan; fakat hâlâ hata oranı, ölçekleme, maliyet, algoritmik pratiklik ve gerçek iş değeri açısından olgunlaşma sürecinde olan sistemlerdir.

Bu nedenle 2026 resmi iki uçtan da kaçınarak değerlendirilmelidir:

- "Kuantum bilgisayarlar hiçbir işe yaramaz, tamamen hype" demek doğru değildir.
- "Kuantum bilgisayarlar artık klasik bilgisayarların yerini almaya başladı" demek de doğru değildir.

Alan, özellikle şu eksenlerde ilerlemektedir:

1. **Daha kaliteli fiziksel qubitler üretmek**
2. **Hata oranlarını düşürmek**
3. **Mantıksal qubitlere geçmek**
4. **Hata düzeltmeli hesaplamayı ölçeklemek**
5. **Gerçek kuantum avantajı gösterebilecek problemleri belirlemek**
6. **Kuantum bilgisayarları klasik sistemlerle hibrit çalıştırmak**
7. **Bulut üzerinden erişilebilir kuantum servisleri sunmak**
8. **Kriptografi tarafında post-quantum dönüşüme hazırlanmak**

Bugünkü cihazların büyük bölümü hâlâ NISQ döneminin özelliklerini taşır: gürültülüdürler, hata düzeltme tam olgunlaşmamıştır, uzun ve derin kuantum devreleri çalıştırmak zordur, sonuçlar çoğu zaman istatistiksel yorum gerektirir.

Bununla birlikte son yıllardaki önemli değişim şudur: Alan artık yalnızca "kaç fiziksel qubit var?" sorusuna bakmıyor. Asıl sorular değişmiştir:

- Kaç **mantıksal qubit** üretilebiliyor?
- Mantıksal hata oranı düşüyor mu?
- Daha fazla fiziksel qubit eklemek gerçekten hata oranını azaltıyor mu?
- Sistem uzun kuantum devrelerini çalıştırabiliyor mu?
- Hata düzeltme gerçek zamanlı uygulanabiliyor mu?
- Donanım mimarisi ölçeklenebilir mi?
- Gerçek dünyadaki bir probleme klasik yöntemlerden daha iyi çözüm üretebiliyor mu?

Bu değişim önemlidir. Çünkü kuantum bilgisayarların pratik değeri fiziksel qubit sayısından çok, güvenilir ve ölçeklenebilir hesaplama yapabilme kapasitesine bağlıdır.

---

## 15.2. IBM Quantum yol haritası

IBM, kuantum bilgisayar alanında en görünür ve en sistematik yol haritalarından birine sahiptir. IBM'in stratejisi uzun süredir yalnızca daha fazla fiziksel qubit üretmekten ibaret değildir; şirket, modüler mimari, hata düzeltme, mantıksal qubitler ve fault-tolerant quantum computing yönünde açık bir yol haritası sunmaktadır.

IBM'in güncel yol haritasında dikkat çeken hedeflerden biri **Starling** sistemidir. IBM, Starling'i 2029 için planlanan fault-tolerant kuantum bilgisayar adımı olarak konumlandırmaktadır. Şirketin açıklamasına göre Starling'in 200 mantıksal qubit üzerinde 100 milyon quantum gate çalıştırabilecek bir sistem olması hedeflenmektedir.

Bu hedef önemli görünür; çünkü burada konuşulan şey artık yalnızca fiziksel qubit sayısı değildir. IBM, mantıksal qubit, hata düzeltme ve uzun devre çalıştırabilme kabiliyetini merkeze almaktadır.

IBM'in yol haritasında genel çizgi şu şekilde okunabilir:

1. **Fiziksel qubit kalitesini artırmak**
2. **Modüler kuantum işlemciler geliştirmek**
3. **Qubitler arası bağlantı ve iletişimi ölçeklemek**
4. **Hata düzeltme maliyetini azaltacak kodlara yönelmek**
5. **Mantıksal qubit sayısını artırmak**
6. **Fault-tolerant hesaplama dönemine geçmek**
7. **Daha büyük ölçekli sistemlerle algoritmik karmaşıklığı artırmak**

IBM'in 2033 sonrası için daha büyük ölçekli **Blue Jay** hedefinden de bahsetmesi, yol haritasının yalnızca kısa vadeli gösterimlerden değil, uzun vadeli fault-tolerant sistemlerden oluştuğunu gösterir.

Ancak burada dikkatli olmak gerekir. Yol haritası, gerçekleşmiş sonuç değil, hedeftir. IBM'in güçlü tarafı, bu hedefleri belirli teknik kilometre taşlarına bağlamasıdır. Zayıf veya belirsiz taraf ise, her büyük donanım yol haritasında olduğu gibi, gerçek mühendislik zorluklarının takvimi geciktirme ihtimalidir.

IBM yol haritasını değerlendirirken şu sorular sorulmalıdır:

- Açıklanan hedef fiziksel qubit mi, mantıksal qubit mi?
- Hedeflenen gate sayısı hata düzeltmeli çalışma için mi?
- Qubitler modüller arasında nasıl bağlanacak?
- Hata düzeltme overhead'i nasıl düşürülecek?
- Sistemin gerçek uygulamalarda klasik yöntemlere göre avantajı gösterilebilecek mi?

IBM'in güçlü yanı, kuantum bilgisayarı yalnızca laboratuvar gösterimi olarak değil, tam yığın bir mühendislik problemi olarak ele almasıdır. Donanım, yazılım, derleyici, hata düzeltme, bulut erişimi ve eğitim ekosistemi birlikte düşünülmektedir.

---

## 15.3. Google Willow ve hata düzeltme iddiaları

Google'ın **Willow** işlemcisi, kuantum hata düzeltme alanında son yılların en dikkat çekici gelişmelerinden biri olarak öne çıkmıştır. Google, Willow ile surface code tabanlı hata düzeltmede önemli bir eşik gösterdiğini duyurmuştur. Nature'da yayımlanan çalışmada, Willow üzerinde distance-5 ve distance-7 surface code memory deneyleri raporlanmış; daha büyük kod mesafesine geçildiğinde mantıksal hata oranının bastırılabildiği gösterilmiştir.

Bu sonuç neden önemlidir?

Çünkü kuantum hata düzeltmenin temel vaadi şudur: Eğer fiziksel hata oranları belirli bir threshold'un altındaysa, daha fazla fiziksel qubit kullanarak daha güvenilir mantıksal qubitler üretilebilir. Yani ölçek büyüdükçe sistem daha kötü değil, daha iyi davranmalıdır.

Google'ın Willow çalışması bu açıdan önemli bir deneysel işarettir. Çalışmada, surface code memory'nin belirli koşullarda threshold altında çalıştığı ve kod mesafesi artırıldığında mantıksal hata oranının bastırıldığı raporlanmıştır.

Bunu sade biçimde şöyle okuyabiliriz:

> Willow, "hata düzeltme teoride işe yarar" fikrinden "belirli bir fiziksel sistemde, belirli ölçekte, deneysel olarak işe yaradığı gösterildi" noktasına doğru önemli bir adımdır.

Ancak bu, "Google artık pratik genel amaçlı kuantum bilgisayar yaptı" anlamına gelmez.

Willow'un gösterdiği şey çok değerlidir ama sınırlıdır:

- Bu bir genel amaçlı fault-tolerant kuantum bilgisayar değildir.
- Kriptografiyi kırabilecek ölçekte bir sistem değildir.
- Her gerçek dünya problemini çözebilen üretim sistemi değildir.
- Kuantum hata düzeltmenin ölçeklenebilirliği için güçlü bir deneysel kanıttır.

Google Willow'un önemini doğru konumlandırmak gerekir. Bu çalışma, kuantum bilgisayarların en kritik darboğazlarından biri olan hata düzeltme konusunda güçlü bir ilerlemedir. Ancak pratik kuantum avantaj için hâlâ daha fazla mantıksal qubit, daha düşük hata oranı, daha uzun devreler ve daha gerçekçi uygulama gösterimleri gereklidir.

Google'ın yaklaşımında dikkat çeken nokta, surface code ve süperiletken qubitler etrafında hata düzeltmeye yoğunlaşmasıdır. Bu yaklaşım mühendislik açısından zor ama teorik olarak iyi anlaşılmış bir yoldur. Yüksek fiziksel qubit overhead'i yaratabilir; buna karşılık threshold davranışı ve hata düzeltme teorisi bakımından güçlü bir zemine sahiptir.

---

## 15.4. Microsoft Majorana 1 ve topolojik qubit tartışması

Microsoft'un kuantum bilgisayar stratejisi uzun süredir topolojik qubit fikrine dayanmaktadır. Topolojik qubit yaklaşımı, kuantum bilgiyi daha doğal biçimde hatalara dayanıklı hale getirme vaadi taşır. Eğer gerçekten ölçeklenebilir topolojik qubitler üretilebilirse, hata düzeltme maliyetinin geleneksel yaklaşımlara göre ciddi biçimde azalması mümkün olabilir.

Bu yüzden Microsoft'un **Majorana 1** duyurusu büyük ilgi çekmiştir. Şirket, topolojik qubit mimarisi ve "topoconductor" yaklaşımı üzerinden farklı bir yol izlediğini açıklamıştır.

Ancak bu konu özellikle dikkatli ele alınmalıdır. Microsoft'un iddiaları, kuantum camiasında heyecan kadar tartışma da üretmiştir. Bazı bağımsız değerlendirmeler ve bilim insanları, Microsoft'un topolojik qubit iddiaları için sunulan kanıtların henüz yeterince doğrudan veya ikna edici olup olmadığı konusunda soru işaretleri bulunduğunu belirtmiştir.

Buradaki ayrımı net yapmak gerekir:

- Microsoft'un yaklaşımı **teorik olarak çok cazip** olabilir.
- Eğer başarıya ulaşırsa, hata düzeltme maliyetini önemli ölçüde azaltabilir.
- Ancak topolojik qubitlerin pratik ve doğrudan gösterimi hâlâ tartışmalı bir konudur.
- Şirket duyuruları ile bağımsız bilimsel doğrulama aynı şey değildir.

Topolojik qubit konusunun çekici tarafı şudur: Geleneksel qubitlerde kuantum durumlar çevresel gürültüye karşı çok hassastır. Topolojik qubitler ise kuantum bilgiyi sistemin daha küresel/topolojik özelliklerinde saklamayı hedefler. Bu, yerel gürültülerin bilgiyi bozmasını teorik olarak zorlaştırabilir.

Ancak bu fikri laboratuvarda güvenilir, kontrol edilebilir, ölçeklenebilir ve programlanabilir bir qubit mimarisine dönüştürmek son derece zordur. Majorana zero mode gibi yapılarla ilgili deneysel kanıtların yorumlanması da karmaşıktır.

Bu yüzden Microsoft Majorana 1, 2026 itibarıyla şu şekilde konumlandırılmalıdır:

> Çok yüksek potansiyel taşıyan, ancak bağımsız ve ikna edici deneysel doğrulama açısından temkinli değerlendirilmesi gereken iddialı bir araştırma hattı.

Bu başlıkta en sağlıklı tutum ne aşırı heyecan ne de peşin reddiyedir. Doğru yaklaşım şudur:

- Hakemli yayınlar izlenmeli.
- Bağımsız tekrarlar beklenmeli.
- Gerçek qubit kontrolü ve gate operasyonları gösterilmeli.
- Hata oranları ve ölçekleme kabiliyeti açıklanmalı.
- Topolojik korumanın gerçekten çalıştığı gösterilmeli.

---

## 15.5. IonQ, Quantinuum, Rigetti, D-Wave ve diğer oyuncular

Kuantum bilgisayar alanında IBM, Google ve Microsoft dışında çok sayıda önemli oyuncu vardır. Bu oyuncuların her biri farklı donanım yaklaşımları, iş modelleri ve teknik öncelikler üzerinden ilerlemektedir.

### IonQ

IonQ, trapped-ion yani hapsedilmiş iyon tabanlı kuantum bilgisayar yaklaşımıyla öne çıkar. Trapped-ion sistemlerin güçlü yönleri yüksek qubit kalitesi, uzun coherence süreleri ve yüksek doğruluklu gate operasyonlarıdır. IonQ, kuantum sistemlerini bulut üzerinden erişilebilir hale getiren şirketlerden biridir ve fault-tolerant kuantum bilgisayar yol haritasını duyurmaktadır.

IonQ'nun anlatısında öne çıkan fikir, daha az ama daha kaliteli qubitlerle daha derin ve daha güvenilir devreler çalıştırabilmektir. Bu, süperiletken sistemlerde sık görülen "çok sayıda qubit" anlatısından farklı bir vurgudur.

Ancak trapped-ion sistemlerin de zorlukları vardır:

- Gate hızları genellikle süperiletken sistemlere göre daha yavaş olabilir.
- Büyük ölçekli iyon zincirlerini veya modüler yapıları kontrol etmek zordur.
- Lazer kontrolü, vakum sistemleri ve modüler bağlantılar ciddi mühendislik gerektirir.
- Gerçek fault-tolerant ölçeğe ulaşmak hâlâ açık bir problemdir.

IonQ, bu zorluklara karşı modüler mimari, fotonik bağlantılar, satın almalar ve full-stack yaklaşım üzerinden ilerlemeye çalışmaktadır.

### Quantinuum

Quantinuum da trapped-ion yaklaşımının en güçlü temsilcilerinden biridir. Şirket, yüksek doğruluklu operasyonlar, kuantum yazılımı ve donanımı birlikte geliştirme stratejisiyle öne çıkar. 56 qubit trapped-ion sistemi, yüksek fidelity iddiaları ve mantıksal qubit çalışmaları ile dikkat çekmiştir.

Quantinuum'un yol haritası, universal fault-tolerant quantum computing hedefine doğru ilerlediğini belirtmektedir. Şirketin özellikle hata düzeltme ve mantıksal qubit çalışmaları, trapped-ion sistemlerin güçlü yönlerinin pratik hata düzeltmeye nasıl taşınabileceği açısından önemlidir.

Quantinuum'un güçlü yanları:

- Yüksek doğruluklu trapped-ion operasyonları
- Donanım ve yazılım entegrasyonu
- Hata düzeltme ve mantıksal qubit araştırmaları
- Kurumsal ve akademik iş birlikleri

Zorlukları:

- Ölçekleme
- Operasyon hızları
- Modüler mimari
- Geniş uygulama avantajının gösterilmesi

### Rigetti

Rigetti, süperiletken qubit yaklaşımını izleyen önemli şirketlerden biridir. IBM ve Google gibi süperiletken mimariye yakın bir teknoloji hattında ilerler, ancak daha küçük ve daha girişimci bir şirket yapısına sahiptir.

2026 itibarıyla Rigetti tarafında öne çıkan başlıklardan biri **Cepheus-1-108Q** sistemidir. Şirket, 108 qubitlik sistemini bulut platformları üzerinden erişilebilir hale getirmiş ve iki-qubit gate fidelity değerlerini yükseltmeye odaklandığını açıklamıştır.

Rigetti'nin durumunda önemli olan nokta şudur: Şirket yalnızca qubit sayısını artırma anlatısından performans ve fidelity anlatısına geçmeye çalışmaktadır. Bu doğru yönde bir değişimdir; çünkü düşük kaliteli çok sayıda qubit, pratik hesaplama değeri üretmekte yeterli değildir.

Rigetti'nin güçlü yanları:

- Süperiletken mimaride deneyim
- Bulut erişimi
- Chiplet yaklaşımı
- On-premises kuantum sistem vizyonu

Zorlukları:

- Büyük oyuncularla rekabet
- Finansal sürdürülebilirlik
- Fidelity değerlerini yeterince yükseltmek
- Gerçek kuantum avantajı göstermek

### D-Wave

D-Wave, kuantum annealing yaklaşımıyla bilinir. Bu yaklaşım, gate-based evrensel kuantum bilgisayarlardan farklıdır. D-Wave sistemleri özellikle optimizasyon problemleri ve hibrit çözümler bağlamında konumlandırılır.

D-Wave'in **Advantage2** sistemleri ticari erişim ve annealing tabanlı optimizasyon kullanımı açısından dikkat çekmektedir. Şirket aynı zamanda gate-model kuantum bilgisayar alanına da yöneldiğini açıklamaktadır.

D-Wave'i değerlendirirken en önemli ayrım şudur:

> D-Wave'in annealing sistemleri, IBM/Google/IonQ/Quantinuum gibi gate-based evrensel kuantum bilgisayarlarla birebir aynı sınıfta değerlendirilmemelidir.

Quantum annealing, belirli optimizasyon problemleri için faydalı olabilir; fakat Shor gibi genel gate-based algoritmaları çalıştıran evrensel kuantum bilgisayar modeliyle aynı şey değildir.

D-Wave'in güçlü yanları:

- Ticari erişilebilirlik
- Optimizasyon problemlerine odaklanma
- Hibrit solver ekosistemi
- Advantage2 ile ölçek ve bağlantı iyileştirmeleri

Zorlukları:

- Annealing avantajının problemden probleme değişmesi
- Evrensel gate-based modelden farklı olması
- Gerçek ve genellenebilir kuantum avantajının gösterilmesi
- Klasik optimizasyon yöntemleriyle sürekli rekabet halinde olması

### Diğer oyuncular

Kuantum bilgisayar alanında başka önemli oyuncular da vardır:

- **PsiQuantum**: Fotonik kuantum bilgisayar yaklaşımı
- **Xanadu**: Fotonik kuantum hesaplama ve PennyLane ekosistemi
- **Pasqal**: Nötr atom sistemleri
- **QuEra**: Nötr atom tabanlı kuantum sistemleri
- **Intel**: Spin qubit ve silikon tabanlı üretim yaklaşımları
- **AWS Braket**: Farklı kuantum donanımlarına bulut üzerinden erişim
- **Azure Quantum**: Kuantum yazılımı, servisleri ve farklı donanım sağlayıcılarıyla entegrasyon
- **NVIDIA, AMD ve HPC ekosistemi**: Kuantum simülasyon, hibrit hesaplama ve kuantum-klasik iş akışları

Bu çeşitlilik önemlidir. Çünkü 2026 itibarıyla hangi donanım yaklaşımının uzun vadede baskın olacağı kesinleşmiş değildir. Süperiletken, trapped-ion, nötr atom, fotonik, spin ve topolojik yaklaşımların her biri farklı avantaj ve risklere sahiptir.

---

## 15.6. Akademik araştırmalar ve endüstriyel yarış

Kuantum bilgisayar alanı bugün akademik araştırma ile endüstriyel yarışın iç içe geçtiği bir alandır. Üniversiteler, kamu araştırma merkezleri ve şirket laboratuvarları aynı anda temel fizik, donanım mühendisliği, hata düzeltme, algoritma geliştirme, yazılım araçları ve uygulama senaryoları üzerinde çalışmaktadır.

Bu yarışın birkaç karakteristik özelliği vardır.

### 15.6.1. Bilimsel ilerleme ile şirket duyurusu aynı şey değildir

Kuantum alanında şirketler sık sık yol haritaları, yeni işlemciler, rekor fidelity değerleri, qubit sayıları veya özel benchmark sonuçları duyurur. Bunların bir kısmı gerçekten önemlidir. Ancak şirket duyurusu ile bağımsız bilimsel doğrulama aynı şey değildir.

Bir gelişmenin ağırlığını anlamak için şu ayrım yapılmalıdır:

| Duyuru türü | Güven seviyesi | Açıklama |
|---|---:|---|
| Pazarlama duyurusu | Düşük/orta | Teknik ayrıntı az olabilir |
| Teknik blog | Orta | Faydalıdır ama şirket perspektifi taşır |
| Whitepaper | Orta | Ayrıntılı olabilir, ancak bağımsız doğrulama gerekebilir |
| Hakemli yayın | Yüksek | Bilimsel denetimden geçmiştir |
| Bağımsız tekrar | Çok yüksek | İddianın sağlamlığını ciddi biçimde artırır |
| Gerçek üretim kullanımı | Uygulama açısından çok yüksek | Laboratuvar dışı değeri gösterir |

Bu tablo, şirket duyurularını değersiz saymak için değil, doğru ağırlıkla okumak için kullanılmalıdır.

### 15.6.2. Hata düzeltme araştırmaları merkezî hale geldi

2010'lu yıllarda ve 2020'lerin başında kuantum bilgisayar haberleri çoğunlukla qubit sayısı, quantum supremacy deneyleri veya yeni donanım prototipleri etrafında şekilleniyordu. 2026 itibarıyla odak daha fazla hata düzeltmeye kaymıştır.

Bunun nedeni açıktır: Hata düzeltme olmadan büyük ölçekli, uzun süreli ve güvenilir kuantum hesaplama yapmak mümkün değildir.

Bu nedenle akademik araştırmalarda şu konular öne çıkmaktadır:

- Surface code
- Quantum LDPC kodları
- Mantıksal qubit mimarileri
- Real-time decoding
- Leakage hataları
- Correlated errors
- Hata düzeltme overhead'ini azaltma
- Fault-tolerant gate setleri
- Magic state distillation
- Modüler kuantum mimarileri

### 15.6.3. Donanım çeşitliliği devam ediyor

Klasik bilgisayar tarihinde CMOS tabanlı silikon teknolojisi baskın hale geldi. Kuantum bilgisayarda ise henüz böyle tek baskın mimari kesinleşmiş değildir. Farklı donanım yaklaşımları eş zamanlı olarak yarışmaktadır.

Bu durum, alanı hem heyecanlı hem de belirsiz yapar. Bir teknoloji kısa vadede öne çıkabilir, ancak uzun vadeli ölçekleme yarışında başka bir teknoloji avantaj kazanabilir.

### 15.6.4. Kuantum-klasik hibrit yaklaşım güçleniyor

Pratik kuantum hesaplamanın yakın vadede tamamen bağımsız kuantum bilgisayarlar üzerinden değil, klasik sistemlerle hibrit mimariler üzerinden ilerlemesi beklenmektedir.

Bu hibrit yaklaşımda:

- Klasik bilgisayar problemi hazırlar.
- Kuantum işlemci belirli bir alt problemi çalıştırır.
- Klasik bilgisayar parametre optimizasyonu yapar.
- Sonuçlar istatistiksel olarak analiz edilir.
- Gerekirse döngü tekrar edilir.

Bu model özellikle VQE, QAOA ve optimizasyon odaklı iş akışlarında önemlidir.

### 15.6.5. Kriptografi baskısı stratejik etki yaratıyor

Kuantum bilgisayarların bugünkü en somut stratejik etkilerinden biri, doğrudan kuantum bilgisayar kullanımından ziyade post-quantum cryptography dönüşümüdür. Yeterince büyük fault-tolerant kuantum bilgisayarlar henüz mevcut olmasa bile, kriptografi geçişi uzun sürdüğü için kurumların bugünden hazırlık yapması gerekir.

Bu yüzden kuantum bilgisayarların güncel durumu yalnızca donanım yarışından ibaret değildir. Siber güvenlik, standartlar, regülasyonlar, veri koruma ve uzun vadeli gizlilik riski de bu tablonun parçasıdır.

---

## 15.7. Hype ile gerçek ilerleme nasıl ayırt edilir?

Kuantum bilgisayar alanında hype kaçınılmazdır. Çünkü konu hem bilimsel olarak zor, hem stratejik olarak önemli, hem de yatırım açısından çekicidir. Bu nedenle her duyuru aynı ciddiyetle değerlendirilmemelidir.

Aşağıdaki kriterler, bir kuantum duyurusunun gerçek ilerleme mi yoksa ağırlıklı olarak pazarlama mı olduğunu ayırt etmek için kullanılabilir.

### 15.7.1. Fiziksel qubit mi, mantıksal qubit mi?

Bir duyuru "1000 qubit" diyorsa, ilk sorulması gereken şudur:

> Bunlar fiziksel qubit mi, mantıksal qubit mi?

Fiziksel qubit sayısı önemlidir ama tek başına yeterli değildir. Mantıksal qubit sayısı, hata düzeltme ve güvenilir hesaplama açısından daha anlamlıdır.

### 15.7.2. Hata oranları açıkça veriliyor mu?

Ciddi bir teknik duyuru şu metriklerden bahsetmelidir:

- Tek-qubit gate fidelity
- İki-qubit gate fidelity
- Ölçüm hatası
- Coherence süresi
- Crosstalk seviyesi
- Logical error rate
- Circuit depth
- Real-time decoding latency
- Calibration stability

Yalnızca "daha güçlü", "devrimsel", "çığır açıcı" gibi ifadeler teknik değerlendirme için yeterli değildir.

### 15.7.3. Ölçek büyüdükçe hata azalıyor mu?

Kuantum hata düzeltmede kritik soru şudur:

> Daha fazla fiziksel qubit eklenince mantıksal hata oranı gerçekten düşüyor mu?

Eğer sistem büyüdükçe hata oranı artıyorsa veya kontrol edilemez hale geliyorsa, qubit sayısının artması tek başına iyi haber değildir.

### 15.7.4. Benchmark neyi ölçüyor?

Kuantum bilgisayar duyurularında benchmark konusu çok hassastır. Bazı benchmark'lar gerçek dünyadaki uygulama değerini değil, belirli bir cihazın belirli bir görevdeki performansını ölçer.

Şu ayrımlar önemlidir:

- Random circuit sampling ile gerçek iş uygulaması aynı şey değildir.
- Synthetic benchmark ile endüstriyel problem aynı şey değildir.
- Küçük ölçekli demo ile üretim değeri aynı şey değildir.
- "Klasik bilgisayar simüle edemiyor" ile "müşteri problemi çözüldü" aynı şey değildir.

### 15.7.5. Sonuç hakemli yayında mı?

Hakemli yayın tek başına mutlak doğruluk garantisi değildir. Ancak teknik iddiaların bilimsel denetimden geçmesi önemlidir. Özellikle büyük iddialar için hakemli yayın, bağımsız tekrar ve açık metodoloji aranmalıdır.

### 15.7.6. İddia bağımsız olarak tekrarlandı mı?

Bir deney yalnızca tek laboratuvarda gösterildiyse değerlidir ama sınırlıdır. Başka gruplar tarafından tekrarlandığında güvenilirliği artar.

Bu özellikle şu alanlarda önemlidir:

- Topolojik qubit iddiaları
- Majorana zero mode gözlemleri
- Kuantum avantaj deneyleri
- Hata düzeltme threshold iddiaları
- Endüstriyel uygulama başarıları

### 15.7.7. Klasik alternatiflerle adil karşılaştırma yapılıyor mu?

Kuantum avantaj iddiası varsa, klasik yöntemlerle karşılaştırma çok dikkatli yapılmalıdır. Çünkü klasik algoritmalar ve donanımlar da sürekli gelişmektedir.

Adil karşılaştırma için:

- En iyi klasik algoritmalar kullanılmalı
- GPU/HPC optimizasyonları dikkate alınmalı
- Problem boyutu anlamlı olmalı
- Çözüm kalitesi karşılaştırılmalı
- Toplam maliyet ve süre hesaplanmalı
- Veri hazırlama ve post-processing dahil edilmeli

### 15.7.8. Gerçek iş problemi mi, laboratuvar problemi mi?

Kuantum bilgisayarların ticari değeri için en önemli soru şudur:

> Bu sistem gerçek bir iş problemini, klasik yöntemlerden daha iyi, daha hızlı, daha ucuz veya daha kaliteli çözebiliyor mu?

Bugün birçok çalışma hâlâ laboratuvar, PoC veya araştırma aşamasındadır. Bu kötü değildir; alanın doğası böyledir. Ancak "ticari olarak hazır" iddiaları bu bağlamda dikkatle okunmalıdır.

### 15.7.9. Roadmap ile gerçekleşmiş sonuç ayrılıyor mu?

Şirketler yol haritası açıklayabilir. Bu değerlidir. Ancak yol haritası gerçekleşmiş sonuç değildir.

Bir değerlendirme yaparken şu ayrım korunmalıdır:

```text
Bugün çalışan şey
Yakın vadede planlanan şey
Uzun vadeli hedef
Teorik potansiyel
Pazarlama söylemi
```

Bu ayrım yapılmadığında kuantum alanı olduğundan ya çok daha olgun ya da çok daha başarısız görünür.

---

## 15.8. 2026 için gerçekçi sonuç

2026 itibarıyla kuantum bilgisayarlar için en gerçekçi değerlendirme şudur:

1. **Alan bilimsel ve mühendislik açısından ciddi ilerliyor.**
2. **Hata düzeltme artık teorik olmaktan çıkıp deneysel kilometre taşları üretmeye başladı.**
3. **Mantıksal qubitler ve fault-tolerant mimari, alanın ana hedefi haline geldi.**
4. **Farklı donanım yaklaşımları arasında kazanan henüz kesinleşmedi.**
5. **Kuantum bilgisayarlar bugün genel amaçlı klasik bilgisayarların yerini almıyor.**
6. **Yakın vadeli ticari değer daha çok hibrit iş akışları, optimizasyon denemeleri, simülasyon ve araştırma platformlarında aranıyor.**
7. **Kriptografi tarafında post-quantum dönüşüm, kuantum bilgisayarlar tam olgunlaşmadan önce başlaması gereken gerçek bir kurumsal gündemdir.**
8. **Hype çok güçlüdür; bu yüzden teknik metrikler ve bağımsız doğrulama şarttır.**

Kısacası, kuantum bilgisayarlar bugün ne "henüz hiçbir şey değil" ne de "artık her şeyi değiştirdi" noktasındadır. Daha doğru ifade şudur:

> Kuantum bilgisayarlar, pratik ve geniş ölçekli kullanım için hâlâ erken aşamada olan; ancak hata düzeltme, mantıksal qubitler ve donanım ölçekleme alanındaki ilerlemeler nedeniyle stratejik olarak ciddiye alınması gereken bir teknoloji ailesidir.

---

## Bölüm Özeti

Bu bölümde kuantum bilgisayarların 2026 itibarıyla güncel durumunu ele aldık.

Öne çıkan noktalar şunlardır:

- Kuantum bilgisayarlar hâlâ genel amaçlı üretim sistemleri değildir.
- Alanın odağı fiziksel qubit sayısından mantıksal qubit, hata düzeltme ve fault-tolerance tarafına kaymıştır.
- IBM, 2029 Starling hedefiyle fault-tolerant sistem yol haritasını açık şekilde duyurmuştur.
- Google Willow, surface code hata düzeltme konusunda önemli bir deneysel kilometre taşıdır.
- Microsoft Majorana 1 ve topolojik qubit yaklaşımı yüksek potansiyel taşımakla birlikte bağımsız doğrulama açısından temkinli değerlendirilmelidir.
- IonQ ve Quantinuum trapped-ion yaklaşımıyla, Rigetti süperiletken mimariyle, D-Wave ise annealing ve gate-model yönelimiyle farklı stratejiler izlemektedir.
- Akademik araştırmalar ile endüstriyel yarış iç içe geçmiş durumdadır.
- Hype ile gerçek ilerlemeyi ayırt etmek için qubit türü, hata oranı, logical error rate, benchmark niteliği, hakemli yayın, bağımsız tekrar ve gerçek uygulama değeri gibi kriterlere bakılmalıdır.

Bir sonraki bölümde kuantum bilgisayarların potansiyel kullanım alanlarını inceleyeceğiz: kuantum simülasyon, kimya, malzeme bilimi, optimizasyon, finans, lojistik, yapay zekâ ve siber güvenlik.

---

## Kaynaklar ve İleri Okuma

- IBM Quantum Blog — *IBM lays out clear path to fault-tolerant quantum computing*  
  <https://www.ibm.com/quantum/blog/large-scale-ftqc>

- IBM Quantum Roadmap  
  <https://www.ibm.com/roadmaps/quantum/>

- Google Quantum AI Blog — *Meet Willow, our state-of-the-art quantum chip*  
  <https://blog.google/innovation-and-ai/technology/research/google-willow-quantum-chip/>

- Nature — *Quantum error correction below the surface code threshold*  
  <https://www.nature.com/articles/s41586-024-08449-y>

- arXiv — *Quantum error correction below the surface code threshold*  
  <https://arxiv.org/abs/2408.13687>

- Nature News — *Microsoft quantum-computing claim still lacks evidence: physicists are dubious*  
  <https://www.nature.com/articles/d41586-025-00829-2>

- APS Physics — *Microsoft's Claim of a Topological Qubit Faces Tough Questions*  
  <https://link.aps.org/doi/10.1103/Physics.18.68>

- IonQ Roadmap  
  <https://www.ionq.com/roadmap>

- IonQ — *Blueprint for Fault-Tolerant Quantum Computing*  
  <https://www.ionq.com/news/ionq-publishes-definitive-technical-report-establishing-its-fault-tolerant-quantum-computing-trajectory---setting-a-new-standard-for-technical-specificity-and-transparency>

- Quantinuum — *Accelerated Roadmap to Universal Fault-Tolerant Quantum Computing by 2030*  
  <https://www.quantinuum.com/press-releases/quantinuum-unveils-accelerated-roadmap-to-achieve-universal-fault-tolerant-quantum-computing-by-2030>

- Quantinuum — *56-Qubit Trapped-Ion Quantum Computer*  
  <https://www.quantinuum.com/press-releases/quantinuum-launches-industry-first-trapped-ion-56-qubit-quantum-computer-that-challenges-the-worlds-best-supercomputers>

- Rigetti Computing — *Investor Presentation, Cepheus-1-108Q and 2026 fidelity goals*  
  <https://investors.rigetti.com/static-files/fbac3801-223f-4f0f-a207-47d25084a1d7>

- D-Wave — *Advancements in Annealing and Gate-Model Quantum Computing Technologies*  
  <https://www.dwavequantum.com/company/newsroom/press-release/d-wave-announces-advancements-in-annealing-and-gate-model-quantum-computing-technologies/>

- D-Wave — *Advantage2 Systems*  
  <https://www.dwavequantum.com/solutions-and-products/systems/>
