# 12. Kuantum Bilgisayar Donanımları

Kuantum bilgisayarları anlamaya çalışırken çoğu zaman algoritmalara, qubit kavramına, süperpozisyona veya dolaşıklığa odaklanırız. Bu kavramlar gerçekten merkezîdir; fakat kuantum bilgisayarların bugün hâlâ neden yaygın, güvenilir ve üretim ortamlarında kullanılan makineler hâline gelmediğini anlamak için donanım tarafına da bakmak gerekir.

Çünkü kuantum bilgisayar yalnızca soyut bir matematiksel model değildir. Gerçek dünyada çalışması için qubitlerin fiziksel bir sistem üzerinde temsil edilmesi, bu qubitlerin kontrol edilmesi, birbirleriyle etkileştirilmesi, ölçülmesi, hatalarının yönetilmesi ve tüm bu sürecin yeterince uzun süre kararlı biçimde sürdürülebilmesi gerekir.

Bu bölümde kuantum bilgisayar donanımlarını yalın ama derinlikli biçimde inceleyeceğiz. Amaç, okuyucunun şu sorulara cevap verebilmesidir:

- Fiziksel qubit üretmek neden bu kadar zordur?
- Farklı donanım yaklaşımları hangi fiziksel sistemleri kullanır?
- Süperiletken, iyon, nötr atom, fotonik, spin, topolojik ve annealing yaklaşımları birbirinden nasıl ayrılır?
- Bir donanım yaklaşımını değerlendirirken sadece qubit sayısına bakmak neden yeterli değildir?
- Bugünkü kuantum donanım yarışı aslında hangi mühendislik problemleri etrafında şekillenmektedir?

Bu bölümde anlatılan donanım yaklaşımlarının hiçbiri tek başına “kesin kazanan” olarak görülmemelidir. Alan hâlâ aktiftir; farklı şirketler, üniversiteler ve araştırma kurumları farklı fiziksel mimariler üzerinde ilerlemektedir. Bazı yaklaşımlar bugün daha görünürdür, bazıları daha erken aşamadadır, bazıları ise uzun vadede daha dayanıklı bir mimari vaat ettiği için önemlidir.

---

## 12.1. Fiziksel qubit üretmek neden zordur?

Klasik bilgisayarlarda bilgi, fiziksel olarak çok kararlı sistemlerle temsil edilir. Modern işlemcilerde bitler, transistörlerin elektriksel durumlarıyla ifade edilir. Bir transistörün belirli bir anda 0 mı yoksa 1 mi temsil ettiğini anlamak oldukça güvenilir bir işlemdir. Elbette klasik bilgisayarlar da fiziksel sistemlerdir ve hata yapabilirler; fakat günümüz yarı iletken teknolojisi bu hataları son derece düşük seviyeye indirmiştir.

Kuantum bilgisayarlarda ise durum çok farklıdır. Qubit, klasik bit gibi yalnızca iki kararlı durumdan birinde bekleyen bir anahtar değildir. Qubit, süperpozisyon ve faz bilgisi taşıyan hassas bir kuantum durumudur. Bu durum dış dünyayla etkileşime girdiğinde kolayca bozulabilir. İşte fiziksel qubit üretmenin zorluğu buradan başlar.

Bir fiziksel qubitin işe yarar olabilmesi için birkaç temel şartı sağlaması gerekir:

1. **İyi tanımlanmış iki durum:** Qubit olarak kullanılacak sistemin `|0⟩` ve `|1⟩` gibi iki ayırt edilebilir temel durumu olmalıdır.
2. **Süperpozisyon oluşturabilme:** Sistem yalnızca 0 veya 1 durumunda kalmamalı; bu durumların kuantum süperpozisyonlarını da taşıyabilmelidir.
3. **Yeterli coherence süresi:** Qubit, kuantum durumunu hesaplama yapılabilecek kadar uzun süre koruyabilmelidir.
4. **Kontrol edilebilirlik:** Qubit üzerinde kapılar uygulanabilmeli, yani kuantum durumu istenen şekilde dönüştürülebilmelidir.
5. **Ölçülebilirlik:** Hesaplamanın sonunda qubit ölçülerek klasik sonuç alınabilmelidir.
6. **Bağlanabilirlik:** Birden fazla qubit arasında dolaşıklık oluşturulabilmelidir.
7. **Ölçeklenebilirlik:** Bu işlemler yalnızca birkaç qubit için değil, çok sayıda qubit için uygulanabilir olmalıdır.
8. **Hata oranı düşüklüğü:** Kapı, ölçüm ve bekleme hataları hata düzeltme eşiğinin altında tutulmalıdır.

Bu şartların her biri ayrı bir mühendislik problemidir. Üstelik bu problemler çoğu zaman birbirini zorlaştırır. Örneğin bir qubiti çevreden çok iyi izole ederseniz coherence süresini artırabilirsiniz; fakat bu kez onu kontrol etmek ve ölçmek zorlaşabilir. Qubiti daha kolay kontrol ederseniz çevreyle daha fazla etkileşime açık hâle getirebilir, dolayısıyla hataları artırabilirsiniz.

Bu yüzden kuantum donanımı tasarlamak, sürekli bir denge arayışıdır:

```text
İzolasyon isteriz → çünkü qubit bozulmasın.
Kontrol isteriz → çünkü qubit üzerinde işlem yapalım.
Ölçüm isteriz → çünkü sonucu okuyalım.
Bağlantı isteriz → çünkü çok-qubitli hesaplama yapalım.
Ölçek isteriz → çünkü gerçek problemler çok sayıda qubit ister.
```

Bu isteklerin hepsini aynı anda sağlamak zordur.

Bir diğer önemli konu da fiziksel qubit ile mantıksal qubit ayrımıdır. Bugün haberlerde duyduğumuz qubit sayıları çoğunlukla fiziksel qubit sayılarıdır. Fakat faydalı, uzun ve hataya dayanıklı kuantum hesaplama için asıl ihtiyaç duyulan şey mantıksal qubitlerdir. Bir mantıksal qubit, hata düzeltme kodlarıyla çok sayıda fiziksel qubitin birlikte kullanılmasıyla oluşturulur. Bu yüzden “1000 fiziksel qubit” kulağa büyük gelebilir, ama hata düzeltmeli büyük ölçekli hesaplama için yeterli mantıksal qubit anlamına gelmeyebilir.

Donanım alanındaki temel yarış, aslında şu soruya verilen farklı cevaplardan oluşur:

> Kuantum bilgisayar için en iyi fiziksel qubit hangi sistem üzerinde kurulmalıdır?

Bu sorunun bugün tek bir kesin cevabı yoktur. Aşağıdaki bölümlerde başlıca yaklaşımları inceleyeceğiz.

---

## 12.2. Süperiletken qubitler

Süperiletken qubitler, günümüz kuantum bilgisayar yarışının en görünür donanım yaklaşımlarından biridir. IBM, Google, Rigetti ve bazı başka şirketler bu yaklaşımı kullanır veya kullanmıştır. Süperiletken qubitler, çok düşük sıcaklıklarda çalışan elektrik devreleriyle oluşturulur.

Bu yaklaşımda qubit, atomik bir parçacığın doğal enerji seviyelerinden değil, makroskopik ölçekte tasarlanmış bir elektrik devresinin kuantum davranışından elde edilir. Devre süperiletken hâle getirildiğinde, elektrik direnci pratik olarak ortadan kalkar ve devrenin belirli enerji seviyeleri qubit durumları olarak kullanılabilir.

Süperiletken qubitlerin çalışabilmesi için sistemin aşırı düşük sıcaklıklara soğutulması gerekir. IBM’in kuantum donanım açıklamalarında da belirtildiği gibi bu tür işlemciler mutlak sıfıra çok yakın sıcaklıklarda, özel seyreltme buzdolapları içinde çalışır. Bu, donanımın yalnızca bir çipten ibaret olmadığını; cryostat, mikrodalga kontrol hatları, ölçüm elektroniği, soğutma altyapısı ve kalibrasyon yazılımlarıyla birlikte büyük bir sistem olduğunu gösterir.

Süperiletken qubitlerin önemli avantajları vardır:

- Mikroelektronik üretim teknikleriyle belirli ölçüde uyumludur.
- Kapı işlemleri çok hızlı olabilir.
- Büyük teknoloji şirketleri tarafından yoğun yatırım görmektedir.
- Devre modeli kuantum hesaplama için uygun bir platform sağlar.
- Bulut üzerinden erişilebilir kuantum işlemcilerde yaygın biçimde kullanılır.

Ancak ciddi zorlukları da vardır:

- Çok düşük sıcaklık gerektirir.
- Qubitler çevresel gürültüye hassastır.
- Kablolama ve kontrol elektroniği ölçek büyüdükçe zorlaşır.
- Qubitler arasındaki bağlantı topolojisi mimariyi sınırlar.
- Hata oranları, büyük ölçekli fault-tolerant hesaplama için hâlâ önemli bir problemdir.

Süperiletken qubitlerde tipik olarak mikrodalga darbeleriyle tek-qubit ve iki-qubit kapıları uygulanır. Qubitler arasındaki etkileşim, tasarıma bağlı olarak doğrudan bağlantılar veya ara kuplörler üzerinden sağlanır. Fakat her qubitin her qubitle doğrudan konuşması genellikle mümkün değildir. Bu nedenle donanım topolojisi algoritma derleme sürecini etkiler. Örneğin iki qubit arasında CNOT uygulanması gerekiyorsa, bu iki qubit fiziksel olarak bağlı değilse devreye SWAP işlemleri eklenebilir. Bu da hata ve derinlik maliyeti yaratır.

Süperiletken yaklaşımın bugünkü stratejik önemi büyüktür. IBM’in yol haritalarında fiziksel qubit sayısı kadar gate sayısı, bağlantı mimarisi, hata azaltma teknikleri ve fault-tolerant sistemlere geçiş hedefleri vurgulanır. Bu da alanın artık yalnızca “daha çok qubit” değil, “daha kaliteli, daha derin devre çalıştırabilen ve mantıksal qubitlere ilerleyen sistemler” ekseninde değerlendirildiğini gösterir.

Sade bir benzetmeyle süperiletken qubitler için şunu söyleyebiliriz:

> Süperiletken kuantum bilgisayar, çok özel koşullarda kuantum davranışı gösterecek şekilde tasarlanmış elektrik devrelerinden oluşan, son derece hassas ve büyük bir mühendislik sistemidir.

---

## 12.3. Hapsedilmiş iyonlar

Hapsedilmiş iyonlar, kuantum bilgisayar donanımı için en köklü ve başarılı yaklaşımlardan biridir. Bu yaklaşımda qubitler, elektrik yükü taşıyan atomlar yani iyonlar üzerinde temsil edilir. İyonlar elektromanyetik alanlarla boşlukta hapsedilir, lazerler veya mikrodalga sinyalleriyle kontrol edilir.

İyon tabanlı sistemlerde qubit olarak genellikle atomun belirli iç enerji seviyeleri kullanılır. İyonlar doğaları gereği birbirinin aynısıdır; bu, üretim kusurlarından kaynaklanan bazı problemleri azaltır. Bir yarı iletken çipteki yapay qubitlerin küçük üretim farkları olabilir; fakat aynı elementin iyonları fiziksel olarak özdeştir. Bu, hapsedilmiş iyon yaklaşımının önemli avantajlarından biridir.

Hapsedilmiş iyon sistemlerinin güçlü yönleri şunlardır:

- Çok yüksek gate fidelitesi elde edilebilir.
- Coherence süreleri genellikle uzundur.
- Qubitler doğaları gereği özdeş fiziksel sistemlerdir.
- Bazı mimarilerde qubitler arasında daha esnek bağlantı sağlanabilir.
- Hata düzeltme araştırmaları için güçlü bir platformdur.

Zorlukları ise şunlardır:

- Kapı işlemleri süperiletken qubitlere göre daha yavaş olabilir.
- Lazer kontrol sistemleri karmaşıktır.
- Çok büyük sayıda iyonu tek sistemde ölçeklemek zordur.
- İyonları hareket ettirme, bölgelere ayırma ve yeniden birleştirme işlemleri karmaşık mühendislik gerektirir.
- Sistemler ultra yüksek vakum ve hassas optik altyapı ister.

Hapsedilmiş iyon mimarilerinde sık geçen kavramlardan biri **QCCD** yani Quantum Charge-Coupled Device mimarisidir. Bu yaklaşımda iyonlar farklı bölgeler arasında taşınabilir; bazı bölgelerde bellek, bazı bölgelerde işlem, bazı bölgelerde ölçüm yapılabilir. Bu, klasik bilgisayarlardaki veri yolu ve işlem birimi ayrımına benzetilebilir; fakat kuantum ölçekte gerçekleştirilmesi çok daha zordur.

Quantinuum ve IonQ gibi şirketler hapsedilmiş iyon yaklaşımının öne çıkan oyuncuları arasındadır. Quantinuum, trapped-ion sistemlerde yüksek doğruluk, uzun coherence süreleri ve fault-tolerant kuantum hesaplama yolunda ilerlemeyi vurgular. IonQ da iyon tabanlı sistemlerin doğalarından gelen avantajlara ve ölçeklenebilir mimari hedeflerine odaklanır.

Hapsedilmiş iyonları anlamak için şu sezgisel ifade işe yarar:

> Süperiletken qubitler yapay devrelerden qubit üretmeye çalışırken, hapsedilmiş iyonlar doğanın zaten kararlı biçimde sunduğu atomik sistemleri qubit olarak kullanır.

Bu yaklaşım, qubit kalitesi açısından güçlüdür; fakat çok büyük ölçekli, hızlı ve ekonomik sistemlere dönüşme yolu hâlâ ciddi mühendislik sorunları içerir.

---

## 12.4. Nötr atomlar

Nötr atom kuantum bilgisayarları, son yıllarda çok dikkat çeken bir diğer yaklaşımdır. Bu mimaride qubitler, elektrik yükü taşımayan atomlar üzerinde temsil edilir. Atomlar genellikle lazerlerle oluşturulan **optical tweezers** yani optik cımbızlar aracılığıyla tutulur ve düzenlenir.

Nötr atom yaklaşımının temel fikri şudur: Çok sayıda atomu düzenli bir dizi hâlinde yakalayabilir, her birini qubit olarak kullanabilir ve atomlar arasında kontrollü etkileşimler oluşturarak kuantum kapıları uygulayabilirsiniz. Özellikle Rydberg atomları ve Rydberg blockade etkisi, nötr atom sistemlerinde iki-qubit kapıları oluşturmak için önemli bir mekanizmadır.

Nötr atom sistemlerinin avantajları şunlardır:

- Çok sayıda atomu aynı anda düzenleme potansiyeli yüksektir.
- Atomlar doğaları gereği özdeş sistemlerdir.
- Optik cımbızlarla esnek geometri oluşturulabilir.
- Bazı sistemlerde atomlar fiziksel olarak yeniden düzenlenebilir.
- Kuantum simülasyon için doğal ve güçlü bir platformdur.

Zorlukları ise şunlardır:

- Yüksek doğruluklu iki-qubit kapıları uygulamak zordur.
- Lazer kararlılığı, atom kaybı ve kalibrasyon önemli problemlerdir.
- Büyük ölçekli hata düzeltme için gereken operasyonel güvenilirlik henüz olgunlaşmamıştır.
- Ölçüm ve yeniden hazırlama süreçlerinin algoritma akışına entegrasyonu dikkat ister.
- Atom dizilerinin kusursuz doldurulması ve korunması teknik olarak zor olabilir.

Nötr atom sistemleri hem analog kuantum simülasyon hem de gate-based dijital kuantum hesaplama için kullanılabilir. Bu yönüyle oldukça esnek bir platformdur. Örneğin belirli fiziksel sistemlerin davranışını simüle etmek için atomların etkileşimleri doğrudan kullanılabilir. Diğer yandan, gate-based modelde qubitler üzerinde kapılar uygulanarak evrensel kuantum hesaplamaya doğru ilerlenebilir.

Nötr atomların önemli cazibelerinden biri ölçeklenme potansiyelidir. Lazer teknolojileriyle çok sayıda atomu düzenlemek, bazı diğer mimarilere göre daha doğal görünebilir. Ancak çok sayıda qubit oluşturmak tek başına yeterli değildir. Bu qubitlerin her biri güvenilir biçimde kontrol edilmeli, iki-qubit işlemleri yeterince düşük hata ile uygulanmalı ve hata düzeltme için gereken mantıksal yapılar kurulabilmelidir.

Nötr atom yaklaşımını sadeleştirerek şöyle düşünebiliriz:

> Bir satranç tahtası gibi düzenlenmiş atomlar düşünün. Her atom bir qubit olabilir. Lazerler bu atomları yerinde tutar, hareket ettirir, uyarır ve birbirleriyle etkileştirmeye çalışır.

Bu yaklaşımın geleceği parlaktır; fakat bugünkü başarısını değerlendirirken yalnızca atom sayısına değil, gate doğruluğuna, atom kaybına, devre derinliğine, hata düzeltme entegrasyonuna ve gerçek algoritmik performansa bakmak gerekir.

---

## 12.5. Fotonik kuantum bilgisayarlar

Fotonik kuantum bilgisayarlar, qubitleri ışık parçacıkları yani fotonlar üzerinde temsil etmeye çalışır. Fotonlar kuantum bilgi için çok doğal taşıyıcılardır; çünkü ışık hızlıdır, uzun mesafelerde taşınabilir ve optik fiber altyapısıyla uyumludur.

Fotonik yaklaşımda bilgi farklı biçimlerde kodlanabilir:

- Fotonun polarizasyonu
- Fotonun hangi optik yoldan geçtiği
- Fotonun geliş zamanı, yani time-bin kodlama
- Sürekli değişkenli optik modlar
- Sıkıştırılmış ışık durumları

Fotonik sistemlerin avantajları şunlardır:

- Fotonlar çevresel gürültüye bazı sistemlere göre daha dayanıklı olabilir.
- Kuantum iletişim ve kuantum ağlarıyla doğal uyumludur.
- Oda sıcaklığına daha yakın çalışma potansiyeli vardır.
- Optik fiber ve entegre fotonik teknolojilerle ölçeklenme umudu taşır.
- Dağıtık kuantum hesaplama için güçlü bir adaydır.

Buna karşılık zorlukları da büyüktür:

- Foton kaybı ciddi bir problemdir.
- Deterministik iki-qubit kapıları fotonlarla doğal olarak kolay değildir.
- Yüksek kaliteli tek foton kaynakları ve dedektörler gerekir.
- Ölçüm, routing ve senkronizasyon karmaşıktır.
- Büyük ölçekli fault-tolerant mimari için çok sayıda optik bileşenin birlikte çalışması gerekir.

Fotonik kuantum hesaplama içinde farklı modeller vardır. Bunlardan biri **measurement-based quantum computing** yaklaşımıdır. Bu modelde önce büyük ve dolaşık bir kaynak durum oluşturulur; sonra ölçümler yapılarak hesaplama gerçekleştirilir. Bir diğer önemli yaklaşım **fusion-based quantum computation** olarak bilinir. Bu modelde küçük dolaşık kaynak durumları, “fusion” adı verilen ölçüm temelli işlemlerle daha büyük hesaplama yapıları hâline getirilir. Fotonik sistemlerde deterministik kapılar zor olduğundan, ölçüm temelli ve fusion tabanlı yaklaşımlar özellikle önemlidir.

PsiQuantum ve Xanadu gibi şirketler fotonik kuantum bilgisayar alanında öne çıkar. Xanadu, fotonik mimaride modülerlik ve optik ağlarla ölçeklenebilirlik üzerinde durur. PsiQuantum ise faydalı ve fault-tolerant kuantum bilgisayar hedefini fotonik teknolojiyle gerçekleştirmeyi amaçlayan iddialı bir yol izler.

Fotonik yaklaşımı şöyle özetleyebiliriz:

> Fotonik kuantum bilgisayar, bilgiyi elektronlar veya atomlar yerine ışık parçacıklarıyla taşımaya ve işlemeye çalışan bir kuantum hesaplama mimarisidir.

Bu yaklaşımın güçlü yanı iletişim ve ölçeklenebilir optik altyapı potansiyelidir. Zayıf yanı ise foton kaybı, kaynak üretimi, dedeksiyon ve etkin etkileşim oluşturma zorluklarıdır.

---

## 12.6. Spin qubitler

Spin qubitler, kuantum bilgiyi bir parçacığın spin özelliği üzerinde temsil eder. En yaygın ele alınan örneklerden biri, silikonda hapsedilmiş tek elektronların spin durumlarıdır. Elektronun spin-up ve spin-down durumları qubitin `|0⟩` ve `|1⟩` durumları olarak kullanılabilir.

Spin qubitlerin en büyük cazibelerinden biri, yarı iletken üretim teknolojileriyle potansiyel uyumluluğudur. Özellikle silikon spin qubitler, modern mikroelektronik endüstrisinin kullandığı malzemeler ve üretim süreçleriyle belirli ölçüde uyumlu bir yol vaat eder. Intel, spin qubit araştırmalarını bu açıdan konumlandırır ve silikon tabanlı qubit çipleri üzerinde çalışır.

Spin qubitlerin avantajları şunlardır:

- Silikon üretim altyapısıyla uyum potansiyeli vardır.
- Qubitler çok küçük fiziksel boyutlarda üretilebilir.
- Yüksek yoğunluklu entegrasyon için umut verir.
- Yarı iletken endüstrisinin deneyiminden yararlanabilir.
- Uzun vadede klasik kontrol elektroniğiyle yakın entegrasyon mümkün olabilir.

Zorlukları ise şunlardır:

- Tek tek elektronların hassas kontrolü zordur.
- Üretim kusurları ve malzeme saflığı önemlidir.
- Qubitler arası bağlantı ve ölçeklenebilir mimari hâlâ araştırma konusudur.
- Çok-qubitli güvenilir işlemler sınırlı ölçektedir.
- Okuma ve kontrol donanımının ölçeklenmesi ciddi bir mühendislik problemidir.

Spin qubitler genellikle quantum dot adı verilen yapılarda ele alınır. Bir elektron küçük bir potansiyel kuyusunda hapsedilir ve spin durumu kuantum bilgi taşıyıcısı olarak kullanılır. Kontrol için mikrodalga sinyalleri, manyetik alanlar ve elektriksel kapılar kullanılabilir.

Spin qubit yaklaşımının uzun vadeli vaadi, “kuantum işlemciyi yarı iletken endüstrisinin ölçekleme mantığına yaklaştırmak” olarak özetlenebilir. Ancak klasik işlemcilerdeki milyarlarca transistörü üretmekle, milyonlarca yüksek kaliteli spin qubiti üretmek aynı zorluk seviyesinde değildir. Kuantum durumda gürültü, coherence, kontrol ve hata düzeltme çok daha hassas konulardır.

Bu yaklaşımı sade biçimde şöyle ifade edebiliriz:

> Spin qubitler, kuantum bilgisayarı yarı iletken dünyasına yaklaştırma iddiası taşıyan, çok küçük ve potansiyel olarak yoğun entegrasyona uygun qubitlerdir.

Bugün spin qubitler umut vericidir, ancak süperiletken veya hapsedilmiş iyon sistemleri kadar büyük ve yaygın erişilebilir kuantum işlemci ekosistemine henüz sahip değildir. Yine de uzun vadeli donanım yarışı içinde önemli adaylardan biridir.

---

## 12.7. Topolojik qubitler

Topolojik qubitler, kuantum donanım alanındaki en ilginç ve aynı zamanda en tartışmalı yaklaşımlardan biridir. Bu yaklaşımın temel iddiası, kuantum bilgiyi yerel gürültülere karşı daha doğal biçimde koruyabilecek bir fiziksel yapı kurmaktır.

Normal qubitlerde bilgi genellikle belirli bir parçacığın, atomun, devrenin veya modun hassas durumunda saklanır. Bu durum çevresel etkilerle kolayca bozulabilir. Topolojik qubit fikri ise bilgiyi daha küresel, topolojik özelliklerde saklamaya çalışır. Böylece küçük yerel bozulmaların bilgiyi hemen yok etmemesi hedeflenir.

Topolojik qubitler çoğu zaman Majorana sıfır modları, anyonlar ve topolojik süperiletkenlik gibi ileri fizik kavramlarıyla ilişkilidir. Bu nedenle konu, diğer donanım yaklaşımlarına göre daha teorik ve deneysel açıdan daha tartışmalıdır.

Topolojik qubitlerin vaat ettiği avantajlar şunlardır:

- Gürültüye karşı doğal koruma potansiyeli
- Daha düşük hata düzeltme yükü ihtimali
- Uzun vadede daha kararlı mantıksal qubitler oluşturma umudu
- Fault-tolerant kuantum hesaplama için teorik cazibe

Ancak zorlukları çok büyüktür:

- Topolojik qubitlerin deneysel olarak kesin ve ölçeklenebilir biçimde gösterilmesi zordur.
- Majorana modlarının varlığı ve kontrolü konusunda bilimsel tartışmalar vardır.
- Üretim, ölçüm ve doğrulama süreçleri karmaşıktır.
- Diğer mimarilere göre daha az olgun bir ekosistemdir.
- Büyük ölçekli çalışan sistemler henüz net biçimde gösterilmemiştir.

Microsoft’un Majorana 1 duyurusu bu alanı yeniden gündeme taşımıştır. Microsoft, topolojik qubit yaklaşımının kuantum bilgisayarları daha hızlı biçimde fault-tolerant seviyeye taşıyabileceğini savunur. Bununla birlikte bilimsel çevrelerde bu iddialara yönelik ihtiyatlı değerlendirmeler ve tartışmalar devam etmektedir. Bu nedenle topolojik qubitleri değerlendirirken iki uçtan da kaçınmak gerekir: Ne “kesin çözüldü” demek doğrudur, ne de “tamamen önemsiz” demek.

Topolojik qubitleri şöyle özetleyebiliriz:

> Topolojik qubitler, qubit bilgisini daha dayanıklı fiziksel yapılarda saklamayı hedefleyen, teorik olarak çok cazip ama pratikte hâlâ kanıtlanması ve ölçeklenmesi gereken bir yaklaşımdır.

Bu yaklaşım başarılı olursa kuantum hata düzeltme maliyetini ciddi biçimde azaltabilir. Ancak bunun gerçekleşip gerçekleşmeyeceği, önümüzdeki yıllarda deneysel kanıtların gücüne bağlıdır.

---

## 12.8. Quantum annealing

Quantum annealing, gate-based evrensel kuantum bilgisayar modelinden farklı bir yaklaşımdır. Bu nedenle ayrı ele alınmalıdır. D-Wave bu alanın en bilinen şirketidir.

Gate-based kuantum bilgisayarlarda hesaplama, qubitler üzerinde belirli kuantum kapılarının sıralı olarak uygulanmasıyla yapılır. Quantum annealing ise özellikle optimizasyon problemleri için tasarlanmış bir yaklaşımdır. Burada sistem, bir problemin çözümünü temsil eden enerji manzarasında düşük enerjili yani iyi çözüme karşılık gelen duruma doğru evrilmeye çalışır.

Sezgisel olarak şöyle düşünebiliriz:

```text
Bir dağlık arazi düşünün.
Her nokta bir çözüm adayını temsil eder.
Yükseklik, çözümün maliyetidir.
Amaç en alçak vadiyi bulmaktır.
Quantum annealing sistemi, kuantum etkileri kullanarak düşük enerji durumuna ulaşmaya çalışır.
```

Quantum annealing’in avantajları:

- Optimizasyon problemleri için özel olarak tasarlanmıştır.
- Çok sayıda qubit içeren sistemler inşa edilebilir.
- Belirli problem sınıfları için hızlı deney yapma imkânı sağlar.
- Hibrit klasik-kuantum optimizasyon yaklaşımlarında kullanılabilir.
- Kullanım modeli bazı iş problemlerine daha doğrudan bağlanabilir.

Zorlukları:

- Evrensel gate-based kuantum bilgisayar ile aynı şey değildir.
- Her optimizasyon probleminde klasik yöntemlerden daha iyi olacağı garanti değildir.
- Problem gömme, bağlantı topolojisi ve gürültü performansı etkiler.
- Kuantum avantajın net gösterimi tartışmalı olabilir.
- Algoritma çeşitliliği gate-based modele göre daha sınırlıdır.

D-Wave’in yaklaşımı, quantum annealing ve hibrit çözümler üzerinden optimizasyon problemlerine odaklanır. Bu cihazları değerlendirirken “kaç qubit var?” sorusundan çok, belirli problem türlerinde klasik ve hibrit alternatiflere göre gerçek performansın ne olduğuna bakmak gerekir.

Quantum annealing için dikkat edilmesi gereken en önemli cümle şudur:

> Quantum annealing, kuantum bilgisayar alanının bir parçasıdır; fakat genel amaçlı, kapı tabanlı, evrensel kuantum bilgisayar modeliyle karıştırılmamalıdır.

Bu ayrım yapılmadığında, kuantum bilgisayar haberleri yanlış anlaşılır. Bir annealing cihazındaki yüksek qubit sayısı ile gate-based bir cihazdaki daha az sayıda ama programlanabilir qubit aynı anlama gelmez.

---

## 12.9. Donanım yaklaşımlarının karşılaştırması

Kuantum donanım yaklaşımlarını karşılaştırırken tek bir metrik kullanmak yanıltıcıdır. Özellikle yalnızca qubit sayısına bakmak ciddi bir hatadır. Bunun yerine şu metrikler birlikte değerlendirilmelidir:

- Fiziksel qubit sayısı
- Tek-qubit kapı doğruluğu
- İki-qubit kapı doğruluğu
- Ölçüm doğruluğu
- Coherence süresi
- Kapı süresi
- Bağlantı topolojisi
- Devre derinliği kapasitesi
- Hata düzeltme uyumluluğu
- Mantıksal qubit üretme potansiyeli
- Ölçeklenebilir kontrol altyapısı
- Üretim tekrarlanabilirliği
- Maliyet ve operasyonel karmaşıklık
- Bulut erişimi ve yazılım ekosistemi

Aşağıdaki tablo, başlıca yaklaşımları yüksek seviyede karşılaştırır.

| Donanım yaklaşımı | Temel fiziksel sistem | Güçlü yönler | Temel zorluklar | Olgunluk değerlendirmesi |
|---|---|---|---|---|
| Süperiletken qubitler | Çok düşük sıcaklıkta çalışan süperiletken devreler | Hızlı kapılar, güçlü endüstri yatırımı, aktif bulut erişimi | Cryogenic altyapı, hata oranları, kablolama ve ölçekleme | Bugün en görünür ve yaygın gate-based yaklaşımlardan biri |
| Hapsedilmiş iyonlar | Elektromanyetik alanlarla hapsedilmiş iyonlar | Yüksek fidelite, uzun coherence, özdeş qubitler | Yavaş kapılar, karmaşık lazer/vakum sistemi, ölçekleme | Yüksek kaliteli qubitler için güçlü aday |
| Nötr atomlar | Lazerlerle tutulan yüksüz atomlar | Büyük atom dizileri, esnek geometri, kuantum simülasyon gücü | Gate fidelitesi, atom kaybı, hata düzeltme entegrasyonu | Hızla yükselen ve ölçek potansiyeli güçlü platform |
| Fotonik sistemler | Işık parçacıkları, optik modlar | İletişimle uyum, dağıtık mimari, oda sıcaklığına yakın çalışma potansiyeli | Foton kaybı, kaynak/dedektör kalitesi, deterministik kapılar | Uzun vadede ölçeklenebilir ağ tabanlı mimari için önemli |
| Spin qubitler | Silikonda elektron/nükleer spin durumları | Yarı iletken üretim uyumu, küçük boyut, yoğun entegrasyon potansiyeli | Kontrol, okuma, bağlantı ve malzeme kusurları | Uzun vadeli ölçeklenebilirlik için umut verici |
| Topolojik qubitler | Topolojik durumlar, Majorana modları vb. | Doğal hata koruması vaadi | Deneysel kanıt, üretim, doğrulama ve ölçekleme | Çok cazip ama hâlâ tartışmalı ve erken aşama |
| Quantum annealing | Optimizasyon için enerji manzarası evrimi | Optimizasyon odaklı, hibrit kullanım, büyük sistem deneyimi | Evrensel gate-based model değildir, avantaj problemi tartışmalı | Belirli optimizasyon deneyleri için ayrı bir kategori |

Bu tabloyu okurken şu noktaya dikkat etmek gerekir: Donanım yaklaşımları doğrudan “iyi-kötü” şeklinde sıralanamaz. Her yaklaşım farklı bir mühendislik felsefesine dayanır. Süperiletken sistemler hızlı ve üretim teknolojilerine yakınken, hapsedilmiş iyonlar yüksek kalite ve uzun coherence ile öne çıkar. Nötr atomlar ölçek ve esneklik vaat eder. Fotonik sistemler dağıtık kuantum mimarileri için caziptir. Spin qubitler yarı iletken endüstrisiyle uyum potansiyeli taşır. Topolojik qubitler hata dayanıklılığı açısından radikal bir vaatte bulunur. Quantum annealing ise genel amaçlı gate-based kuantum bilgisayardan farklı olarak optimizasyon odaklı bir yol sunar.

Bu nedenle kuantum donanımı değerlendirmede en sağlıklı yaklaşım şudur:

```text
Hangi problem için?
Hangi algoritma modeli için?
Hangi hata oranıyla?
Hangi devre derinliğiyle?
Hangi bağlantı topolojisiyle?
Hangi mantıksal qubit hedefiyle?
Hangi maliyet ve operasyonel karmaşıklıkla?
```

Bu sorular sorulmadan yapılan “şu şirket şu kadar qubit yaptı” yorumları eksik kalır.

---

## Bölüm Özeti

Bu bölümde kuantum bilgisayarların donanım tarafını inceledik. En önemli çıkarımlar şunlardır:

- Kuantum bilgisayar donanımı, yalnızca “qubit üretmek” değil; qubiti kontrol etmek, korumak, ölçmek, bağlamak ve ölçeklemek problemidir.
- Fiziksel qubit sayısı tek başına yeterli bir başarı metriği değildir.
- Mantıksal qubitler ve hata düzeltme, faydalı kuantum bilgisayarlar için kritik eşiktir.
- Süperiletken qubitler bugün en görünür yaklaşımlardan biridir; ancak cryogenic altyapı ve hata oranları önemli zorluklardır.
- Hapsedilmiş iyonlar yüksek kalite ve uzun coherence ile güçlüdür; fakat hız ve ölçekleme zorlukları vardır.
- Nötr atomlar büyük ölçekli diziler ve esnek geometri potansiyeliyle hızla yükselen bir platformdur.
- Fotonik sistemler kuantum iletişim ve dağıtık mimariyle doğal uyum taşır; fakat foton kaybı ve kaynak/dedektör problemleri kritiktir.
- Spin qubitler yarı iletken üretim dünyasıyla uyum potansiyeli taşır; ancak çok-qubitli güvenilir sistemler hâlâ araştırma aşamasındadır.
- Topolojik qubitler teorik olarak çok caziptir; fakat deneysel olarak hâlâ tartışmalı ve erken aşamadadır.
- Quantum annealing, gate-based evrensel kuantum bilgisayardan farklı, optimizasyon odaklı bir yaklaşımdır.

Kuantum donanım alanında bugün kesin bir kazanan yoktur. Daha doğru ifade şudur: Farklı donanım yaklaşımları, kuantum bilgisayarların geleceği için farklı yolları test etmektedir. Hangi yolun pratik, ölçeklenebilir ve ekonomik olarak baskın hâle geleceği; hata düzeltme, üretim, kontrol elektroniği, yazılım ekosistemi ve gerçek uygulama performansı gibi birçok faktörün birlikte olgunlaşmasına bağlıdır.

---

## Kaynak Notları

Bu bölüm hazırlanırken özellikle aşağıdaki kaynaklardan yararlanılmıştır:

- NIST — Quantum Computing Explained  
  https://www.nist.gov/quantum-information-science/quantum-computing-explained

- NIST — Quantum Information Science  
  https://www.nist.gov/quantum-information-science

- IBM Quantum — Hardware and Roadmap  
  https://www.ibm.com/quantum/hardware

- IBM Quantum Roadmap 2026  
  https://www.ibm.com/roadmaps/quantum/2026/

- Quantinuum — Trapped-Ion Technology  
  https://www.quantinuum.com/glossary-item/trapped-ion-technology

- IonQ — What is Trapped Ion Quantum Computing?  
  https://www.ionq.com/resources/learn-quantum-what-is-trapped-ion-quantum-computing

- QuEra — Neutral Atoms and the Path to Fault-Tolerant Quantum Computing  
  https://www.quera.com/blog-posts/neutral-atoms-and-the-path-to-fault-tolerant-quantum-computing

- Science — Error-detected quantum operations with neutral atoms  
  https://www.science.org/doi/10.1126/science.adr7075

- Xanadu — Photonics  
  https://www.xanadu.ai/photonics/

- PsiQuantum  
  https://www.psiquantum.com/

- Nature Communications — Fusion-based quantum computation  
  https://www.nature.com/articles/s41467-023-36493-1

- Intel Labs — Quantum Computing  
  https://www.intel.com/content/www/us/en/research/quantum-computing.html

- QuTech — Programmable quantum circuits put silicon qubits to the test  
  https://qutech.nl/2026/04/02/programmable-quantum-circuits-put-silicon-qubits-to-the-test/

- Microsoft — Majorana 1 announcement  
  https://news.microsoft.com/source/features/innovation/microsofts-majorana-1-chip-carves-new-path-for-quantum-computing/

- Science — Debate around Microsoft’s topological quantum computing claims  
  https://www.science.org/content/article/debate-erupts-around-microsoft-s-blockbuster-quantum-computing-claims

- D-Wave — D-Wave’s Approach  
  https://www.dwavequantum.com/learn/d-wave-s-approach/
