+++
title = "Fiziksel Dünya: Yapay Zekanın En Acımasız Sınavı. Physical AI bu sınava hazır mı?"
date = "2026-06-14T16:00:00+03:00"
author = "Alper Konuralp"
description = "NVIDIA 'Physical AI'ın ChatGPT anı geldi' diyor. Ama parlak demo videolarıyla gerçek fabrika konuşlanması arasındaki uçurum hâlâ derin. Zeka ekrandan inip robotlara taşınırken 2026'da tam olarak nerede durduğumuza dürüst ve şüpheci bir bakış."
tags = ["physical ai", "embodied ai", "humanoid robot", "robotik", "yapay zeka", "vla", "world model", "sim-to-real", "figure", "boston dynamics", "tesla optimus", "nvidia", "yapay zeka ekonomisi", "chatgpt anı"]
draft = false
+++

*Yazan: Alper Konuralp. Deneyimli yazılımcılar ve teknik karar vericiler için; Haziran 2026 itibarıyla mevcut bilgiler ışığında hazırlanmıştır — bu hızla değişen bir alan, rakamlar ve aktörler kısa sürede eskiyebilir.*

## 1. Giriş: Bir "an" mı, yoksa bir eğri mi?

Ocak 2026'da, CES'te NVIDIA'nın bültenine düşen cümle iddialıydı: "Physical AI'ın ChatGPT anı geldi." Mesaj açıktı — yapay zeka nihayet dijital dünyadan, yani metnin ve görüntünün konforlu sınırlarından çıkıyor, fiziksel gerçekliğin içine adım atıyordu.

Ne var ki küçük bir ayrıntı bu cümle hakkında çok şey söylüyor. Aynı CES'te, Jensen Huang sahnedeki keynote konuşmasında bültenden daha temkinliydi ve anın "neredeyse geldiğini" söyledi. Bir yıl önce, CES 2025'te ise aynı an henüz "köşeyi dönmek üzere"ydi. Köşeyi dönmek üzere → neredeyse geldi → geldi. Bu üç adımlık yükseliş, hem teknolojinin nereye vardığı hem de etrafındaki anlatının nasıl kurulduğu hakkında düşündürücü. O günden beri bu çerçeve robotik dünyasında benimsendi, tartışıldı, yer yer alaya da alındı.

Biz bu yazıya tam da o cümleye duyduğumuz şüpheyle başlayalım. Çünkü "ChatGPT anı" benzetmesi, dikkatli kullanılmazsa yanıltıcıdır. ChatGPT'nin asıl kırılması, dil modellerinin bir gecede kusursuzlaşması değildi; uzmanlara ait bir teknolojinin bir *kullanılabilirlik eşiğini* aşıp geniş bir kitleye anlaşılır hale gelmesiydi. Robotik için yapılan benzer iddia şu: temel modeller, robot öğrenmesi, simülasyon, uç (edge) işlem gücü ve olgunlaşan donanım bir araya geliyor ve robotlar artık geleneksel otomasyon projeleri gibi değil, uyarlanabilir fiziksel ajanlar gibi eğitilebilir hale geliyor. Bu gerçek bir kayma. Ama kitlesel konuşlanmanın garantisi değil. Bir "an"dan çok, dik bir eğrinin başlangıcındayız.

### Peki tam olarak neden bahsediyoruz?

Bu yazıda Physical AI'ı **bedenlenmiş (embodied) anlamıyla** ele alıyoruz: fiziksel dünyayı algılayan, onun hakkında akıl yürüten ve bir beden aracılığıyla o dünyaya geri etki eden yapay zeka sistemleri — humanoid'ler, mobil manipülatörler, otonom depo makineleri, cerrahi robotlar, muayene robotları. Doğru zihinsel model "kollu bir sohbet botu" değil; zekanın algılama, planlama, hareket, aktüasyon, güvenlik katmanları, simülasyon, donanım ve operasyona dağıldığı, kapalı bir kontrol döngüsüdür.

Bu döngüyü tarif etmek kolay, mühendisliğini yapmak zordur: **algıla → akıl yürüt → harekete geç → sonucu gözlemle → uyarla.** Bir dil modeli durağan bir ortamda yanılır; bir robot ise hareketli bir dünyada yanılır. Fark burada saklı. Üretken bir model yanlış bir cümle kurduğunda kullanıcı omuz silker, çıktı yeniden üretilir. Oysa fiziksel dünya affetmez: düşen bir redüktör, bir insanla çarpışma, kontamine olmuş bir cerrahi alet ya da dengesini kaybedip devrilen bir humanoid, "başarısız bir tamamlama" gibi geçiştirilemez. İşte bu yüzden Physical AI yalnızca makine öğrenmesi değildir; onu klasik robotikle, güvenlik mühendisliğiyle, mekanik tasarımla, insan faktörleriyle, siber güvenlikle ve regülasyonla birlikte düşünmek zorundayız.

### Bir terim uyarısı

Devam etmeden bir terimi netleştirelim, çünkü kafa karışıklığı buradan başlıyor. "Physical AI" ve "fiziksel zeka" fazlasıyla yüklü terimler. Bazı araştırma toplulukları bunu fiziksel sinir ağları, optik/analog hesaplama tabanları ya da von Neumann mimarisine alternatifler için kullanır. Bazıları ise akıllı malzemeler, yumuşak robotik ve zekanın doğrudan bedenin kendisinden doğduğu morfolojik hesaplama için. Bunlar meşru ve heyecan verici alanlar — ama bu yazının konusu değiller. Burada Physical AI, gerçek dünyada çalışan robotlar ve otonom makineler için **bedenlenmiş yapay zeka** anlamındadır. Bu ayrımı baştan koymazsak, yatırımcı sunumlarında ve haber başlıklarında her şey birbirine karışıyor.

Bir kapsam notu daha: Otonom araçlar ve robotaksiler de bu bedenlenmiş ailenin önemli bir parçası — dünya modelleri ve çok kipli algı gibi aynı teknik temellerden besleniyorlar; NVIDIA da CES 2026'da onları en öne çıkardı. Ama bu yazıda odağımızı manipülasyon ve humanoid/mobil robotlarda tutuyoruz; otonom sürüş kendi başına ayrı bir derinlemesine inceleme konusu.

Bu yazının amacı da bu zaten: gürültüyü ayıklamak. Heyecanın gerçek olduğu yerle, abartının başladığı yeri ayırmak. Önümüzdeki bölümlerde önce bu noktaya nasıl geldiğimize, sonra teknik motora (world model'ler, VLA modeller, simülasyon, NVIDIA yığını), ardından 2026'nın somut sahaya inişlerine, zor problemlere, ekonomiye ve gerçekçi bir geleceğe bakacağız. Demolara değil, çalışan sistemlere; vaatlere değil, ölçülebilir metriklere bakmaya çalışacağız.

## 2. Buraya nasıl geldik: tek bir buluş değil, eğrilerin çakışması

Son dönemdeki heyecan tek bir icattan doğmadı. Birbirinden bağımsız ilerleyen birkaç teknoloji eğrisinin aynı anda olgunlaşıp çakışmasından doğdu. Bu eğrileri ayrı ayrı görmek, "neden tam da şimdi?" sorusunun en dürüst cevabını veriyor.

Birinci eğri **temel modeller**. Transformer mimarisinin önce dilde, sonra görüntüde gösterdiği ölçeklenebilirlik, sektörün beklentilerini değiştirdi. Artık her görev için sıfırdan dar bir model geliştirmek yerine, büyük bir modeli geniş ve çeşitli veriyle önceden eğitip sonra onu tek tek hedef görevlere uyarlamak olağan hale geldi. Robotik bunu uzun süredir istiyordu: nesneler, görevler, ortamlar ve hatta farklı robot bedenleri arasında transfer edebilen genel bir politika.

İkinci eğri, robot öğrenmesinin **pekiştirmeli öğrenmeden (RL) taklit öğrenmeye ve VLA modellerine** kayması. Erken dönem yaklaşımlar ağırlıkla RL'ye dayanıyordu; ama RL ünlü biçimde veri açısından verimsizdi, eğitim dağılımının dışına çıkınca genelleme yapmakta zorlanıyordu. Mühendisler, devasa, internette eğitilmiş görsel-dil modellerini (VLM) doğrudan insan tarafından teleoperasyonla toplanan robot gösterimleri üzerinde ince ayar yapabileceklerini fark ettiler. Böylece robot, internetin anlamsal birikimini miras alıyordu: bir elmanın neye benzediğini, "kırılgan" kavramının ne demek olduğunu, "topla" emrinin neyi ima ettiğini. Eksik halka yalnızca bu anlamsal bilgiyi fiziksel eyleme çevirmekti. Google DeepMind'ın 2023'teki RT-2 modeli burada dönüm noktasıydı: robot eylemlerini bir tür "token" olarak temsil ederek, web ölçeğindeki görsel-dil bilgisini robot kontrolüne aktardı. RT-2 robotiği çözmedi — ama problemi yeniden çerçeveledi.

Üçüncü eğri **çoklu beden (multi-embodiment) verisi**. Geleneksel robot öğrenmesi parçalıydı: tek bir kol, tutucu ve laboratuvarda eğitilen model, başka bir kuruluma taşındığında işe yaramıyordu. Open X-Embodiment çalışması, robotiğin de dil modellerinin geniş metin külliyatından faydalandığı gibi çapraz robot veri setlerinden faydalanıp faydalanamayacağını sordu. 21 kurumun iş birliğiyle 22 farklı robot bedeninden derlenen bir milyonu aşkın yörünge bir araya getirildi ve bedenler arası transferin — hâlâ sınırlı da olsa — mümkün olduğu gösterildi.

Dördüncü eğri **simülasyon**. Robotik hep simülasyon kullandı, ama bugün simülasyon merkeze oturuyor; çünkü gerçek robot verisi pahalı, yavaş, tehlikeli ve seyrek. Dijital ikizler, sentetik veri, alan rastgeleleştirmesi (domain randomization) ve world model'ler artık çekirdek yığının parçası. Simülasyon gerçekliğin yerini tutmaz; ama iterasyon döngülerini sıkıştırır ve modeli sahaya inmeden önce nadir senaryolarla karşılaştırır.

Beşinci eğri **donanım**. Daha iyi aktüatörler, bataryalar, dokunsal algılama, kameralar, bedenlenmiş GPU'lar ve elektrikli araç ile tüketici elektroniğinin beslediği olgun tedarik zincirleri sayesinde, bir zamanlar gösterişli laboratuvar prototipleri olan robotlar ürünleşmeye başladı. Aynı anda, NVIDIA'nın Jetson Thor sınıfı uç (edge) yapay zeka donanımı, büyük modellerin robot üzerinde yerel olarak koşmasını mümkün kılarak zamana duyarlı davranışlarda bulut gecikmesine bağımlılığı azaltıyor.

Son eğri ise saf **ticari ve demografik baskı**. İş gücü kıtlığı, tedarik zinciri dayanıklılığı arayışı, üretimin geri taşınması (reshoring), yaşlanan nüfuslar ve sanayi politikaları — hepsi insan için tasarlanmış ortamlarda çalışabilen robotlara talep yaratıyor. Pazar esnek otomasyon istiyor. Teknoloji tam hazır değil, ama teşvik yapısı son derece güçlü.

Tek başına bu eğrilerden hiçbiri yeterli değildi. Birlikte, sektörün asıl darboğazını mekanik mühendislikten alıp yazılıma, veriye ve güvenilirliğe taşıdılar. Bundan sonrasının hikâyesi, büyük ölçüde bu yeni darboğazla boğuşmanın hikâyesidir.

## 3. Teknik motor: world model'ler, VLA modelleri ve NVIDIA yığını

İşin özündeki teknik soru şu: Bir robot, özenle senaryolanmış bir hücrenin dışında işe yarar biçimde davranabilmek için dünya hakkında nasıl yeterince şey öğrenebilir?

Robotik bu soruya tarihsel olarak *ayrıştırma* ile yaklaştı. Algılama sistemleri nesneleri tanır, planlayıcılar yol üretir, denetleyiciler yörüngeyi yürütür, güvenlik katmanları hareketi sınırlar, entegrasyon mühendisleri de hepsini birbirine bağlar. Bu yaklaşım hâlâ önemli ve ortadan kalkmayacak. Ama yeni dalga, bu yığının ne kadarının veriden öğrenilebileceğini ve genel amaçlı temel modellerin yeniden kullanılabilir önbilgiler (prior) sağlayıp sağlayamayacağını soruyor. Üç ana vektör öne çıkıyor: world model'ler, VLA modelleri ve simülasyon altyapısı.

### World model'ler: kafanın içinde bir simülasyon

World model (dünya modeli), ortamın nasıl evrildiğine dair öğrenilmiş içsel bir tahmin modelidir. Robotikte bu, aday eylemler altında gelecekteki kareleri, nesne hareketini, temas sonuçlarını veya durum geçişlerini öngörmek anlamına gelir. Otonom sürüşte trafiğin nasıl gelişeceğini; manipülasyonda bir kavramanın başarılı olup olmayacağını ya da bir kumaşın beklendiği gibi katlanıp katlanmayacağını tahmin etmek demektir.

NVIDIA'nın Cosmos platformu bu yönelimin en görünür endüstriyel örneği. Temel argüman şu: Physical AI önce dijital olarak eğitilmeli. Bunun için geliştiricinin üç şeye ihtiyacı var — robotun bir dijital ikizi, bir politika modeli ve fiziksel olarak makul senaryolar üretip öngörebilen bir world model. Bu modeller hiper gerçekçi sentetik veri üreteçleri ve kapalı döngü değerlendiriciler olarak çalışıp gerçek dünyada politika eğitmenin maliyetini, süresini ve riskini düşürüyor.

Ama burada kritik bir uyarı var: Bir world model, yalnızca hatalarının sınırlı ve anlaşılır olduğu ölçüde işe yarar. İnsana makul görünen bir sentetik video, yanlış fiziği, hatalı temas dinamiklerini veya gerçekçi olmayan insan davranışlarını pekâlâ içinde barındırabilir. Görsel gerçekçilik, operasyonel geçerlilikle aynı şey değildir. Güvenlik açısından kritik sistemler için bu ayrım her şeydir: bir world model'in ürettiği, gözle kusursuz görünen bir sıçrama videosu, robotun gerçek ağırlık merkezini ya da tork sınırını ihlal eden bir hareketi gösteriyor olabilir.

### Vision-Language-Action (VLA) modeller

Mevcut dalganın en görünür mimari ailesi VLA modelleridir. Bir VLA, duyusal gözlemleri ve dildeki talimatı girdi alıp eylem üretir. Vaadi şu: dil esnek bir görev arayüzü sunar, görüntü görevi mevcut sahneye bağlar, eylem çıktısı da modeli robot bedenine kavuşturur.

RT-2 etkili bir reçete gösterdi: görsel-dil modellerini hem internet ölçeğindeki görsel-dil verisi hem de robot yörüngeleri üzerinde birlikte ince ayar yapmak ve eylemleri dil modeli eğitimiyle uyumlu bir "token" biçiminde ifade etmek. Bu, problemi yeniden çerçeveledi — bir politika, robotik veri setlerinin çok ötesinde eğitilmiş modellerden anlamsal genelleme miras alabiliyordu.

Physical Intelligence'ın π-serisi alanı genel robot kontrolüne doğru taşıyor. Ayırt edici teknik tercihlerinden biri, ayrık token üretimi yerine sürekli eylem üretimi için **akış eşleştirme (flow matching)** kullanması; çünkü yüksek el becerisi gerektiren işler, adım adım token üretiminin sağlayamadığı pürüzsüz ve kesintisiz hareketi ister. π0.5, açık dünya genellemesine ve daha önce görülmemiş gerçek evlerde uzun ufuklu manipülasyona odaklanıyor. Aynı ekibin FAST çalışması ise yüksek frekanslı, becerikli kontrol için eylem token'laştırmayı ele alıyor.

Google DeepMind'ın Gemini Robotics ailesi farklı ama akraba bir yol izliyor: Gemini 2.0 temelini robotiğe genişletiyor. İkili bir yapı var — bir VLA modeli olan Gemini Robotics ve bedenlenmiş akıl yürütme için Gemini Robotics-ER. DeepMind bu işin gerektirdiği nitelikleri genellik, etkileşim ve el becerisi olarak tanımlıyor; gündelik dildeki talimatları, ortam değiştiğinde yeniden planlamayı, çoklu beden uyarlamasını ve katmanlı güvenliği vurguluyor.

NVIDIA'nın GR00T N1 modeli ticari tezi en açık biçimde ortaya koyuyor: bir humanoid'in hem becerikli bir bedene hem de zeki bir zihne ihtiyacı var. GR00T N1, **iki sistemli** bir VLA mimarisi kullanıyor — bir görsel-dil bileşeni sahneyi ve talimatı yorumlarken, bir difüzyon transformer eylem bileşeni motor eylemlerini üretiyor. Eğitim karışımı gerçek robot yörüngelerini, insan videolarını ve sentetik veriyi bir arada içeriyor.

Bu iki sistemli desen muhtemelen kalıcı olacak. Fiziksel eylemin gecikme gereksinimleri, üst düzey akıl yürütmeninkinden çok daha katı. Yavaş bir model iyi plan yapar ama pürüzsüz kontrol edemez; hızlı bir denetleyici iyi tepki verir ama anlamsal kavrayıştan yoksundur. Düşünen yavaş katmanı, yüksek frekanslı hareket üreten hızlı katmandan ayırmak — robotiğin zaten alışkın olduğu "görev planlama vs. kontrol" ayrımını andırıyor; farkı, elle kodlanmış yığının giderek daha büyük bir kısmının öğrenilmiş modüllerle yer değiştirmesi.

### Sim-to-real ve sentetik veri

Simülasyon, Physical AI'ın ekonomik motoru — ama aynı zamanda en tehlikeli yanılsamalarından biri.

Sim-to-real problemi yeni değil. Simülasyonda eğitilen bir robot gerçeklikte başarısız olabilir; çünkü sürtünme, ışık, sensör gürültüsü, aktüatör gecikmesi, kütle, deforme olabilirlik, temas dinamikleri, kalibrasyon ve insan davranışı simülatörden farklıdır. Alan rastgeleleştirmesi, sistem tanımlama, gerçekten simülasyona ayar (real-to-sim) ve hibrit gerçek/sentetik eğitim, bu boşluğu daraltmaya çalışır.

Temel modeller sim-to-real'i ortadan kaldırmaz; aksine daha karmaşık hale getirir. Bir politika anlamsal olarak genelleyebilir ama fiziksel olarak çuvallayabilir. "Ağır olanı alt rafa koy" talimatını anlayabilir, ama tork sınırını, kavrama dengesini ya da çarpışma zarfını yanlış hesaplayabilir. En inandırıcı yığınlar bu yüzden simülasyonu bir kanıt değil, bir doğrulama hattının tek bir katmanı olarak ele alır: ölçek için simülasyon, temellendirme için gerçek veri, nadir durumlar için sentetik veri, ve konuşlanma iddiaları için titiz saha değerlendirmesi.

### NVIDIA yığını: altyapı bir stratejidir

NVIDIA'nın Physical AI'daki rolü hem teknik hem stratejik. Teknik olarak model eğitiminden simülasyona, sentetik veriden uç çıkarıma kadar uzanan bütünleşik bir yığın sunuyor: Isaac Sim ve Omniverse simülasyon ile dijital ikizleri; Cosmos world model ve sentetik veri altyapısını; GR00T humanoid temel modellerini; Jetson Thor sınıfı sistemler de robot üzerinde yerel çıkarımı hedefliyor. Jetson Thor, Blackwell mimarisi üzerine kurulu ve yaklaşık 2.070 FP4 TFLOPS'a varan bir çıkarım gücüyle, büyük modellerin buluta bağımlı kalmadan robot üzerinde koşmasını amaçlıyor.

Stratejik olarak ise NVIDIA, Physical AI üretken yapay zekadan sonraki büyük hesaplama pazarı olursa kazanır. Bu, teknolojiyi ciddiyetsiz kılmaz — ama terminolojiyi ticari okuryazarlıkla okumak gerektiğini gösterir. "Physical AI" kısmen faydalı bir şemsiye terim, kısmen de bir platform anlatısıdır; robotiği, simülasyonu, uç yapay zekayı, otonom araçları, humanoid'leri, endüstriyel dijital ikizleri ve sentetik veriyi tek bir yatırım tezi altında topluyor. Mühendislik liderleri için bu terim ancak daha net bir mimari ve risk analizine yol açıyorsa faydalıdır; sinir ağı taşıyan her makinenin genel etiketine dönüşürse değil.

Motoru tanıdık. Asıl sınav ise fabrika zemininde: bu mimariler gerçekte nerede, ne kadar iyi çalışıyor? Sıradaki bölüm tam da buna bakıyor.

## 4. 2026 ekosistemi: ciddi konuşlanmalar, sahnelenmiş demolar ve stratejik konumlanma

2026 itibarıyla Physical AI artık yalnızca bir araştırma konusu değil — ama henüz olgun bir kitle pazarı da değil. Ekosistemi bir yelpaze olarak görmek en doğrusu. Bir uçta ticari olarak konuşlanmış, dar kapsamlı robotlar var: depo otomasyonu, otonom mobil robotlar (AMR), cerrahi yardımcı platformlar, hastane taşıma robotları, muayene robotları, endüstriyel kollar. Bunlar bilim kurgu gibi görünmeyebilir; ama çoğu zaman humanoid demolarından daha fazla gerçek değer üretirler. Diğer uçta ise dikkat çeken genel amaçlı humanoid'ler var; çünkü hem insan ortamlarına hem de insan hayal gücüne uyuyorlar. Asıl zor soru şu: Bunlar viral videolardan çıkıp güvenilir ürünlere dönüşebilecek mi? Aşağıdaki aktörleri üç mercekle okumak işi kolaylaştırıyor: endüstriyel humanoid üreticileri, yazılım/model odaklı girişimler ve pragmatik görev robotları.

### Figure ve BMW: en somut hikâye

Figure, kamuoyuna en çok ayrıntı veren humanoid konuşlanmalardan birine sahip; çünkü robotları BMW'nin Spartanburg fabrikasında gerçek bir üretim hattında test edildi. Kasım 2025'te paylaşılan sonuçlara göre Figure 02, 11 ay süren bir konuşlanmada sac levha yükleme — otomotivde klasik bir al-yerleştir görevi — üstlendi: bir parça raftan alınıp kaynak fikstürüne yerleştiriliyor, ardından altı eksenli endüstriyel robotlar kaynağı yapıp parçayı ana hatta besliyor.

Rakamlar Figure'ın kendi açıklamasından geliyor: haftanın beş günü 10 saatlik vardiyalar, 90.000'den fazla yüklenen parça, 1.250'yi aşkın çalışma saati ve 30.000'den fazla BMW X3 aracının üretimine katkı. Belirlenen anahtar metrikler de iddialıydı: 84 saniyelik toplam çevrim süresi (37 saniyesi yükleme), vardiya başına hedeflenen %99'un üzerinde yerleştirme doğruluğu ve sıfır müdahale hedefi — parçayı 5 milimetrelik toleransla, yalnızca 2 saniyede yerleştirerek.

Ama dürüst olmak gerekirse: BMW ve Figure, sahada kaç robot çalıştığını ve finansal şartları açıklamadı. Yani konuşlanma, önemsenecek kadar gerçek — fakat kitlesel benimsenmeye doğru ekstrapolasyon yapacak kadar şeffaf değil. Şirketin kendi paylaştığı en öğretici ayrıntı ise teknik: en sık donanım arızası noktası robotun ön kolu oldu ve bu ders doğrudan bir sonraki nesil Figure 03'ün tasarımını şekillendirdi. Figure 02 artık emekliye ayrılıyor. Figure'ın stratejisi bu örnekte netleşiyor: etkileyici donanım üret, sahadan tescilli veri topla, cilalı demolar yayınla, endüstriyel pilotlar kur ve "robotun beyni" katmanına sahip ol. Şirketin Helix modeli de tam olarak bunu hedefliyor — humanoid kontrolünü, üst gövdenin tamamı için bir VLA problemi olarak çerçeveliyor.

### Boston Dynamics, Hyundai ve elektrikli Atlas

Elektrikli Atlas, gösterişli robot demolarından ürün odaklı humanoid'lere geçişin en güçlü sembollerinden biri. Tümü elektrikli platform, eski hidrolik Atlas soyunun yerini alıyor ve açıkça endüstriyel kullanım için tasarlanmış. CES 2026 çevresindeki haberler Atlas'ın Hyundai ile fabrika konuşlanmasına doğru ilerlediğini anlattı — ama daha ölçülü takvim, geniş çaplı kullanımı 2026 değil, 2028 civarına işaret ediyor.

Bu, doğru çerçeve. Boston Dynamics'in yönetimi de Atlas'ın operasyonel olarak işe yarar hale gelmesi için yeni bir fabrika görevini bir iki gün içinde öğrenebilmesi ve son derece yüksek bir güvenilirliğe ulaşması gerektiğini vurguluyor. Zor olan, bir humanoid'e etkileyici bir hareket dizisini bir kez yaptırmak değil; o işi güvenli biçimde, tekrar tekrar, insanların etrafında, vardiyalar boyunca, bakım kısıtları altında ve ölçülebilir bir geri dönüşle yaptırmaktır. Boston Dynamics ayrıca, mekanik üstünlüğünü temel modellerle birleştirmek için Google DeepMind ile stratejik bir iş birliğine gitti.

### Tesla Optimus

Tesla Optimus en kutuplaştırıcı vaka. Tesla'nın elinde ciddi avantajlar var: üretim deneyimi, bataryalar, aktüatörler, yapay zeka çipleri, algılama altyapısı ve dikey entegrasyon iştahı. Ama bir de iddialı takvimler geçmişi var. 2026 itibarıyla Optimus'a dair haberler; cesur üretim hedefleri, belirsizlik ve demolardaki davranışın ne kadarının otonom, ne kadarının yardımlı ya da teleoperasyonla yapıldığına dair şüpheciliğin bir karışımı. Musk üretim rampasını başlangıçta "acı verecek kadar yavaş" diye tanımladı.

İşin sezgiye aykırı tarafı şu: Tesla'nın değer yaratması için Optimus'un evdeki bir genel amaçlı asistan olması gerekmiyor. Fabrika içi görevler, lojistik, malzeme taşıma ve kontrollü operasyonel ortamlar çok daha makul erken hedefler. Ev robotu anlatısı iyi bir pazarlama olabilir; fabrika robotu yolu ise çok daha inandırıcı.

### Physical Intelligence ve yazılım öncelikli bahis

π0'ın arkasındaki şirket olan Physical Intelligence önemli, çünkü tek bir robot bedeninden çok genel amaçlı robot politikalarına odaklanıyor. π-serisi, asıl kilidin yalnızca humanoid donanımı değil, bedenler arasında transfer edebilen genelci bir robot zekası olduğu tezini temsil ediyor. π0.5'in açık dünya genellemesine, heterojen veriye ve uzun ufuklu gerçek dünya manipülasyonuna odaklanması doğrudan bu tezle uyumlu.

Risk ise "genelci" kelimesinin muğlaklığında. Bir sistem, özenle seçilmiş bir dizi robot kolu ve ev görevinde genelleme yaparken, gelişigüzel evlerde ya da fabrikalarda sağlam bir otonomiden hâlâ çok uzak olabilir. Anlamlı soru, bir robotun demoda on görevi yapıp yapamadığı değil; başarı oranının dağılım kayması altında — yeni ışık, dağınıklık, farklı aletler, nesneler, insanlar, yerleşimler ve hata toparlama gereksinimleri karşısında — nasıl değiştiğidir.

### Unitree, AgiBot ve Çin'in ölçek avantajı

Çin'in robotik ekosistemini görmezden gelmek artık imkânsız. Unitree, bacaklı ve humanoid platformların maliyetini düşürüp erişilebilirliğini artırdı; G1 gibi modeller 16.000 dolar civarından başlıyor. Reuters'ın aktardığına göre Unitree Şanghay borsasında halka arz için başvurdu ve 2025'te binlerce humanoid birim sevk etti — fakat aynı haber, kullanımların büyük ölçüde araştırma, eğitim, demo ve sınırlı ticari bağlamlarda yoğunlaştığına da dikkat çekiyor. AgiBot ise kitlesel üretim hazırlığı, endüstriyel ve hizmet kullanım senaryoları ve veri toplama altyapısıyla bir diğer önemli oyuncu.

Ama ölçek otomatik olarak olgunluk demek değil. Kalabalık bir pazar hızlı iterasyon, düşen maliyetler ve etkileyici demolar üretebilir; aynı zamanda atıl kapasite, ince marjlar, güvenlik endişeleri ve hype döngüleri de üretebilir.

### En az gösterişli robotlar önce değer üretebilir

2026'nın ticari olarak en inandırıcı Physical AI sistemleri çoğu zaman tam teşekküllü humanoid'ler değil. Diligent Robotics'in Moxi'si iyi bir örnek: ilaçları, laboratuvar numunelerini ve malzemeleri taşıyan mobil bir hastane robotu. Reuters'a göre 25'ten fazla ABD hastanesinde 1,25 milyondan fazla teslimat gerçekleştirdi. Tasarımı pragmatik: bina içinde istikrarlı gezinme için tekerlekler, asansör ve kapılarla etkileşim için bir kol, ve sağlık sektöründeki iş gücü kıtlığına bağlı dar bir görev alanı.

Buradan çıkan daha geniş ders şu: doğru beden, işe uyan bedendir. Humanoid'ler cazip, çünkü dünya insan için kurulmuş; ama bacaklar pahalı, dengesiz, çok enerji tüketen ve sertifikalandırması zor. Pek çok ticari ortamda tekerlekler ile bir iki kol çok daha akılcı bir tasarım olabilir. Physical AI'ı humanoid'lerle bir tutmak hatadır. Humanoid'ler bir beden stratejisidir — kategorinin kendisi değil.

## 5. Uygulama alanları: Physical AI nerede değer üretiyor?

Physical AI'ın yakın vadeli değeri büyük olasılıkla üç koşulun örtüştüğü yerlerde yoğunlaşacak: iş gücünün pahalı ya da kıt olduğu, ortamın yarı yapılandırılmış olduğu ve hataların mühendislik denetimleriyle sınırlanabildiği yerlerde.

### Üretim

Üretim, humanoid'ler ve mobil manipülatörler için bariz ilk pazar; çünkü fabrikalar zaten sensörlerle donatılmış, güvenlik açısından yönetilen ve otomasyona yatkın ortamlar. Erken kullanım senaryoları arasında makine besleme, parça sıralama, kit hazırlama (kitting), muayene, kutudan parça toplama (bin picking), fikstür yükleme, malzeme taşıma ve ergonomik olarak zor görevler var.

Geleneksel endüstriyel robotlar yüksek hacimli, sabit ve tekrarlı işlere zaten hâkim. Physical AI tam olarak şurada ilginçleşiyor: görev, sert otomasyonu pahalı kılacak kadar değişken; ama bir robotun eğitilip izlenebileceği kadar yapılandırılmış. Bir humanoid, fabrikanın geleneksel bir robot kol etrafında yeniden tasarlanamayacağı ya da robotun insan aletlerini, arabaları, kapıları kullanması gerektiği durumlarda işe yarayabilir. Burada belirleyici benimseme ölçütü "robot bu görevi yapabiliyor mu?" değildir; toplam sahip olma maliyetidir.

### Lojistik ve depo

Depolar zaten robot yoğun, ama konuşlanan robotların çoğu uzmanlaşmış: AMR'ler, ayırma sistemleri, ürünü çalışana getiren (goods-to-person) sistemler, robotik toplama kolları, konveyörler. Physical AI burada uzun kuyruğu ele alabilirse değer katıyor: düzensiz nesneler, istisna yönetimi, boşaltma, paketleme, iadeler. Ama lojistik acımasızdır. Bir robot demoyla değil; insanlarla, forkliftlerle, konveyör sistemleriyle, sabit otomasyonla ve süreç yeniden tasarımıyla yarışır. Basit bir AMR'den daha yavaş, daha pahalı ve daha az güvenilir bir humanoid, sırf insana benzediği için kazanmaz.

### Sağlık

Sağlık güçlü bir Physical AI pazarı — ama mutlaka humanoid hemşireler için değil. Hastaneler lojistik, temizlik, envanter yönetimi, eczane otomasyonu, laboratuvar taşıma, hasta odasına teslimat ve ameliyathane desteğine ihtiyaç duyuyor. Moxi benzeri sistemler pragmatik yolu gösteriyor: klinisyenlerin yerini almak yerine, klinik iş akışından düşük değerli yürüme ve getirme görevlerini çıkarıyorlar. Cerrahide yapay zeka destekli otonomi ilerliyor; ama düzenleyici ve güvenlik çıtası çok daha yüksek. Yakın vadede tümüyle bağımsız robot cerrahlardan ziyade, denetimli otonomi ve simülasyon temelli değerlendirme çok daha makul.

### Tarım, inşaat, enerji ve muayene

Physical AI, işin tehlikeli, uzak, tekrarlı ya da zorlu koşullarda olduğu sektörlere de uyuyor. Tarım seçici hasat, yabani ot temizleme, ilaçlama ve mahsul izleme istiyor. İnşaat aplikasyon, muayene, malzeme taşıma ve saha takibi istiyor. Enerji ve altyapı; trafo merkezlerinin, boru hatlarının, türbinlerin, güneş tarlalarının ve tehlikeli tesislerin muayenesini istiyor. Bu alanlar fabrikalardan daha zor, çünkü ortamlar daha az yapılandırılmış. Ama alternatif tehlikeli insan emeği ya da pahalı duruş süresi olduğunda iş gerekçesi güçlü olabilir.

### Ev robotları

Ev robotları en duygusal olarak çekici, teknik olarak en affetmez uygulama. Evler yapılandırılmamış, özel, dağınık, kültürel olarak değişken; kırılgan nesneler, evcil hayvanlar, çocuklar, merdivenler, kablolar, sıvılar ve muğlak insan tercihleriyle dolu. Bir laboratuvarda beş havlu katlayan bir robot, bir haneyi aylarca güvenle idare eden bir robotla aynı şey değildir. Ev pazarı bir gün gelebilir; ama büyük olasılıkla öncesinde yıllarca kurumsal konuşlanma, teleoperasyon destekli öğrenme, kısıtlı ev pilotları ve hibrit hizmet modelleri olacak. İlk işe yarar "ev humanoid'i" muhtemelen otonomi kadar uzaktan desteğe, görev kısıtlamasına ve abonelik ekonomisine de bağlı olacak.

## 6. Zor problemler

Physical AI tek bir eksik buluş yüzünden tıkalı değil. Birbiriyle etkileşen bir dizi zor problem yüzünden tıkalı.

### Sim-to-real boşluğu

Simülasyon eğitimi ölçekler, ama gerçeklik son vergiyi her zaman tahsil eder. Temas dinamikleri, deforme olabilen nesneler, ışık, sensör artefaktları ve insan davranışı modellemesi zor olgular. World model'ler boşluğu azaltabilir; ama görsel olarak makul sentetik verinin ardına da gizleyebilir. En güvenli varsayım şu: simülasyona dayalı her iddianın, kontrollü değişkenlik altında gerçek dünya doğrulamasına ihtiyacı vardır.

### Veri kıtlığı

Dil modelleri internet ölçeğinde metinle eğitildi. Robotiğin ise eyleme dair eşdeğer, evrensel bir külliyatı yok. Robot verisi pahalıdır; çünkü donanım süresi, insan gözetimi, bakım, kalibrasyon ve güvenlik denetimi gerektirir. Çoklu beden veri setleri yardımcı olur, ama eylem uzayları robottan robota farklıdır; bir tutucu, becerikli bir el, tekerlekli bir taban, iki ayaklı bir robot ve cerrahi bir alet aynı eylem semantiğini temiz biçimde paylaşmaz. Teleoperasyon robotiğin veri çarkına dönüşüyor: insanlar görevleri gösteriyor, robotlar taklit ediyor, hatalar daha çok veri üretiyor. Ama teleoperasyonun ölçeklenme sınırları ve iş gücü sonuçları var — ve "otonom" demoların aslında uzaktan kumanda edilip edilmediği sorusunu da gündeme getiriyor.

### Güvenlik ve öğrenilmiş politikaların öngörülemezliği

Geleneksel otomasyon kısmen sertifikalandırılabilir, çünkü davranışı kısıtlı ve öngörülebilir. Öğrenilmiş robot politikaları daha zordur. Binlerce vakada doğru davranıp bin birinci vakada tuhaf biçimde çuvallayabilirler; dağılım kaymasına, yanıltıcı (adversarial) girdilere ve sensör arızalarına duyarlıdırlar. Gerçekçi yol katmanlı güvenliktir: mekanik sınırlar, kuvvet sınırları, hız ve mesafe izleme, coğrafi sınırlandırma (geofencing), sertifikalı denetleyiciler, çalışma zamanı izleyiciler, anomali tespiti, insanın kontrolü devralması (override) ve denetim kayıtları. Öğrenilmiş politika, tek güvenlik mekanizması olmamalıdır.

### Güvenilirlik

Robotik şirketleri yetenek demolarına bayılır; operatörler ise çalışma süresini (uptime) dert eder. Vakaların %80'inde başarılı olan bir robot, bir araştırma atılımı ve aynı zamanda operasyonel bir baş belasıdır. Endüstriyel sistemler çoğu zaman "etkileyici yapay zeka"dan çok "sıkıcı altyapı"ya yakın bir güvenilirlik ister. Boston Dynamics'in Atlas için son derece yüksek güvenilirlik vurgusu bu yüzden bir muhafazakârlık değil; ürünün gerçek gereksinimidir.

### Maliyet ve toplam sahip olma maliyeti

Donanım maliyeti yalnızca görünen kısımdır. Robotlar entegrasyon, şarj, bakım, yedek parça, yazılım güncellemeleri, bağlanabilirlik, filo yönetimi, güvenlik analizi, personel eğitimi, iş akışı yeniden tasarımı ve sigorta ister. Bir humanoid on binlerce dolara mal olup yoğun gözetim, sık bakım ve yavaş çevrim süreleri gerektiriyorsa, ekonomi tutmayabilir. Çin üretimi ve otomotiv tarzı tedarik zincirleriyle birim maliyetler hızla düşebilir — ama düşen donanım maliyeti otonomiyi, entegrasyonu ya da güvenilirliği kendiliğinden çözmez.

### Siber güvenlik

Bir Physical AI robotu; kameraları, mikrofonları, motorları, ağ bağlantıları, uzaktan güncelleme mekanizmaları ve kimi zaman bulut bağımlılıkları olan siber-fiziksel bir uç noktadır. Ele geçirilmesi yalnızca veri hırsızlığı değil; fiziksel zarar, operasyonel kesinti veya filo çapında saldırı anlamına gelebilir. Robotik güvenliği, tüketici uygulaması güvenliğinden çok endüstriyel kontrol sistemi güvenliği gibi ele alınmalıdır.

### Regülasyon

AB Yapay Zeka Yasası (Regülasyon 2024/1689) önemlidir, çünkü pek çok Physical AI sistemi ürün güvenliği, işyeri güvenliği, tıbbi cihaz, otomotiv ve makine düzenlemeleriyle kesişecek. Yüksek risk sınıflandırması özellikle, yapay zeka düzenlenmiş bir ürünün güvenlik bileşeni olduğunda ya da sağlık, güvenlik, istihdam veya temel hakları etkileyen alanlarda kullanıldığında geçerli — ve bu, üçüncü taraf uygunluk değerlendirmesi, şeffaflık, insan gözetimi ve piyasaya arz sonrası izleme yükümlülüklerini tetikler. Buna ek olarak yenilenen Ürün Sorumluluğu Direktifi, "ürün" tanımını yazılımı ve yapay zekayı kapsayacak biçimde genişletip kusursuz sorumluluğa (strict liability) ve ispat yükünün hafifletilmesine doğru ilerliyor. Sonuç açık: uyum, model eğitiminden sonra eklenebilecek bir şey değil. İzlenebilirlik, risk yönetimi, veri yönetişimi, izleme, siber güvenlik, insan gözetimi ve piyasa sonrası gözetim, baştan mimariye dahil edilmek zorunda.

## 7. İş ve ekonomi boyutu

Physical AI'ın ekonomisini konuşurken ilk kuralı baştan koymak gerekiyor: pazar tahminleri kurumdan kuruma vahşice değişiyor ve bunları kanıt değil, senaryo planlaması olarak okumak gerekiyor.

Yine de eğilim gerçek; robotik yatırımları ve sevkiyatları son birkaç yılda hızla büyüdü. Ama uzun vadeli tahminler birbirinden hayli uzak: Goldman Sachs 2035'e kadar humanoid'ler için yaklaşık 38 milyar dolarlık bir pazar öngörürken, UBS 2035'te işyerinde iki milyon, 2050'de 300 milyon humanoid bekliyor; Morgan Stanley ise bir milyarı aşkın robotla 2050'ye doğru 5 trilyon dolara varan bir toplam adreslenebilir pazardan söz ediyor. SoftBank'ın CEO'su Masayoshi Son, sıradaki trilyon dolarlık şirketin Physical AI ve robotikten çıkacağını ve şu an bu yarışta Çin'in önde olduğunu söylüyor. Bu coşkuyu sermaye de takip ediyor; örneğin Physical Intelligence'ın yaklaşık 11 milyar dolarlık bir değerleme üzerinden yeni bir tur konuştuğu bildirildi.

Bu rakamların hepsi; iş gücü ikamesi, birim maliyetler, otonomi seviyesi, regülasyon ve konuşlanma ölçeğine dair, henüz kanıtlanmamış varsayımlara dayanıyor. Sorumlu yaklaşım onları kesin gerçekler gibi değil, senaryolar gibi ele almaktır.

Ekonomik mantığın özü ise iş gücü maliyet yapısının yeniden kurgulanmasında. Geleneksel endüstriyel otomasyon; güvenlik kafesleri, sabit konveyörler ve tek amaçlı tutucular gibi katı altyapı için büyük peşin sermaye yatırımı (CapEx) gerektiriyordu. VLA temel modelleriyle çalışan humanoid'ler ise esnek bir operasyonel gider (OpEx) alternatifi sunuyor: günde 16-20 saat çalışan, bataryasını kendi değiştirebilen on binlerce dolarlık bir robot, etkili saat maliyetini hızla düşürebiliyor. Ama tekrar etmekte fayda var — düşen donanım maliyeti, otonomiyi, entegrasyonu ya da güvenilirliği kendiliğinden çözmez.

Asıl stratejik içgörü şu: bu ekosistemde donanım hızla emtialaşıyor (özellikle Çin tedarik zincirleriyle). Sürdürülebilir rekabet avantajı artık en iyi aktüatörü tasarlayan şirkette değil; veri çarkını ve temel modelleri elinde tutanlarda. Milyonlarca saatlik, yüksek kaliteli, çapraz beden veriyi ucuza toplayabilenler, altında yatan donanım katmanının değerini de büyük ölçüde belirleyecek.

## 8. Physical AI sadece "embodied AI"ın yeniden markalanması mı?

Kısmen, evet.

Çekirdek araştırma soyu — bedenlenmiş yapay zeka, robot öğrenmesi, pekiştirmeli öğrenme, taklit öğrenme, sim-to-real, mobil manipülasyon, insan-robot etkileşimi, kontrol teorisi — "Physical AI" etiketinin çok öncesine dayanıyor. Bir alanda onlarca yıllık geçmiş varken ortaya satıcı kaynaklı bir şemsiye terim çıkınca, mühendislerin ve araştırmacıların şüphelenmesi anlaşılır.

Ama "sadece yeniden markalama" demek de fazla küçümseyici olur. Etiketler, yatırımı koordine ettiklerinde önem kazanır. "Cloud native" dağıtık sistemleri icat etmedi; "DevOps" operasyonları icat etmedi; "üretken yapay zeka" sinir ağlarını icat etmedi. Bir etiket, gerçek bir yakınsamayı tarif ettiğinde ve kurumların dikkatini doğru yere yönlendirmeye yardım ettiğinde faydalı hale gelir. "Physical AI" şu anlama geliyorsa faydalıdır: bağımsız modeller olarak değil; bedenlenmiş, güvenlik açısından kritik, gerçek zamanlı, siber-fiziksel ajanlar olarak değerlendirilmesi gereken yapay zeka sistemleri. Şu anlama gelirse yanıltıcıdır: herhangi bir robot, artı herhangi bir sinir ağı, artı bir sunum slaydı.

Ticari teşvikler de açık. NVIDIA yapay zeka hesaplama hikâyesini robotiğe genişletmek istiyor; girişimler genel amaçlı robot etrafında yatırımcı anlatıları kurmak istiyor; otomobil üreticileri yeni nesil üretim sinyali vermek istiyor; yapay zeka laboratuvarları modellerinin sohbetin ötesine geçmesini istiyor; hükümetler stratejik robotik endüstrileri istiyor; medya da sohbet botu sonrası bir cephe istiyor. Bu teşvikler alanı geçersiz kılmaz — yalnızca neden şüpheciliğin şart olduğunu açıklar.

### Demo uçurumu

Robotikteki en önemli kural hâlâ geçerli: bir videoya fazla güvenme.

Cilalı bir robot demosu gerçekliği sıkıştırır. Başarısız denemeleri, teleoperasyonu, kontrollü ortamı, prova edilmiş yörüngeleri, sınırlı nesne kümesini, insan müdahaleleriyle yapılan sıfırlamaları, kamera dışındaki altyapıyı ya da özenle seçilmiş başarıyı dışarıda bırakabilir. Kesintisiz videolar bile çoğu zaman konuşlanmanın gerçek yükünü göstermez: bakım, kalibrasyon, güvenlik kısıtları, toparlanma, üretim hızı ve ekonomi.

Faydalı sorular operasyoneldir: Robot, bir insan sıfırlaması olmadan hatadan toparlanabiliyor mu? Ne sıklıkla müdahale gerekiyor? Bir görevi yeniden öğretmek ne kadar sürüyor? Arızalar arası ortalama süre (MTBF) nedir? Işık değiştiğinde ne oluyor? İnsanların etrafında, üretim hızında güvenle çalışabiliyor mu? Bir model güncellemesinden sonra sistem nasıl doğrulanıyor? Hangi veri toplanıyor ve kime ait? Filo öğrenmesiyle gelişiyor mu? Robot başına maliyet değil, tamamlanan görev başına maliyet nedir? Bu sorular Physical AI'ı mühendislik olarak, tiyatrodan ayıran sorulardır.

Buna bir de insan faktörünü ekleyelim. Fiziksel bedenlenmenin sinsi bir yan etkisi var: insanlar, insansı kinematikle hareket eden ve sesle etkileşen bir makineye, gerçekte sahip olduğundan çok daha fazla durumsal farkındalık ve güvenlik bilinci atfetme eğilimindedir. Bu "aşırı güven" (overtrust), yüksek riskli sahalarda operatörlerin gözetimi gevşetmesine yol açabilir — yani bedenin kendisi bir güvenlik açığına dönüşebilir.

## 9. Gerçekçi bir bakış: ne gerçek, ne abartı, neden umurumuzda?

Physical AI gerçek — ama dengesiz.

Gerçek olan kısım, malzemelerin değişmiş olması. Çok kipli temel modeller anlamsal önbilgiler sağlıyor. VLA modelleri dili, görüntüyü ve eylemi birbirine bağlıyor. World model'ler ve simülasyon eğitim ölçeğini büyütüyor. Uç yapay zeka donanımı daha fazla yerel çıkarımı mümkün kılıyor. Daha iyi humanoid ve mobil manipülatör donanımı, fiziksel olarak yetenekli platformları erişilebilir kılıyor. Endüstriyel pilotlar saf laboratuvar işinin ötesine geçiyor. Hastane ve lojistik robotları, bedenlenmiş otonominin şimdiden değer üretebildiğini gösteriyor.

Abartı da gerçek. Pazar tahminleri çok geniş bir aralıkta değişiyor ve çoğu zaman kanıtlanmamış varsayımlara dayanıyor. Doğru tavır onları senaryo olarak görmek.

Yakın vadenin kazananları büyük olasılıkla en insansı görünen robotlar olmayacak. Tekerlekler bacakları yenebilir. Dar otonomi genelliği yenebilir. İnsan gözetimli robotlar tümüyle otonom olanları yenebilir. Fabrika ve hastane iş akışları ev asistanlarını yenebilir. Yalnızca yazılım "robot beyinleri" derin donanım ortaklıklarına ihtiyaç duyabilir. Humanoid platformlar önce ev ürünleri olarak değil, veri toplama ve endüstriyel araçlar olarak başarılı olabilir.

Yazılımcılar ve teknik karar vericiler için asıl çıkarım şu: Physical AI sıradan bir model entegrasyonu problemi değil, bir sistem problemidir. Model önemlidir; ama sensörler, gecikme, kontrol döngüleri, güvenlik zarfları, simülasyon sadakati, veri hatları, gözlemlenebilirlik, siber güvenlik, mekanik güvenilirlik, düzenleyici sınıflandırma ve saha operasyonları da öyle.

"ChatGPT anı" çerçevesi ancak robotlar gerçek ortamlarda dramatik biçimde daha kolay komut verilebilir, uyarlanabilir, konuşlanabilir ve güvenilir hale geldiğinde haklı çıkacak. 2026'da bu geçişin şeklini görebiliyoruz. Ama henüz tamamlandığını ilan edemeyiz.

Doğru duruş ne toptan reddetmek ne de körü körüne inanmak. Disiplinli bir merak: ilerlemeyi takip et, iddiaları test et, operasyonel metrik iste ve şunu unutma — fiziksel dünya, yapay zekanın bugüne dek karşılaştığı en acımasız sınav ortamıdır. Biz de — *Dinozorlarla Kafa Ütüleme*'de — kafa ütülemeye tam buradan, yani heyecanı saygıyla ama gözümüzü kırpmadan süzdüğümüz bu zeminden devam edeceğiz.

## Kaynaklar ve İleri Okuma

- What is Physical AI? — NVIDIA Glossary
  <https://www.nvidia.com/en-us/glossary/generative-physical-ai/>
- What is Physical AI? — IBM
  <https://www.ibm.com/think/topics/physical-ai>
- "ChatGPT moment for physical AI": NVIDIA CEO launches new AI models and chips — Axios
  <https://www.axios.com/2026/01/05/nvidia-ces-2026-jensen-huang-speech-ai>
- RT-2: Vision-Language-Action Models Transfer Web Knowledge to Robotic Control — arXiv
  <https://arxiv.org/abs/2307.15818>
- Open X-Embodiment: Robotic Learning Datasets and RT-X Models — arXiv
  <https://arxiv.org/abs/2310.08864>
- GR00T N1: An Open Foundation Model for Generalist Humanoid Robots — arXiv (NVIDIA)
  <https://arxiv.org/abs/2503.14734>
- Cosmos World Foundation Model Platform for Physical AI — arXiv (NVIDIA)
  <https://arxiv.org/abs/2501.03575>
- π0.5: a Vision-Language-Action Model with Open-World Generalization — arXiv (Physical Intelligence)
  <https://arxiv.org/abs/2504.16054>
- Gemini Robotics: Bringing AI into the Physical World — arXiv (Google DeepMind)
  <https://arxiv.org/abs/2503.20020>
- Introducing Gemini Robotics and Gemini Robotics-ER — Google DeepMind
  <https://deepmind.google/discover/blog/gemini-robotics-brings-ai-into-the-physical-world/>
- F.02 Contributed to the Production of 30,000 Cars at BMW — Figure AI
  <https://www.figure.ai/news/production-at-bmw>
- Boston Dynamics CEO on humanoid deployment timeline and reliability — Business Insider
  <https://www.businessinsider.com/huamnoid-robots-manufacturing-deployment-timeline-robert-playter-ceo-interview-2026-1>
- Elon Musk: Optimus production initially "agonizingly slow" — Business Insider
  <https://www.businessinsider.com/elon-musk-cybercab-optimus-production-agonizingly-slow-robotaxi-robot-2026-1>
- Unitree previews China's bleak robot reality — Reuters Breakingviews
  <https://www.reuters.com/commentary/breakingviews/unitree-previews-chinas-bleak-robot-reality-2026-06-11/>
- Diligent Robotics (Moxi) eyes senior living as it expands beyond hospitals — Reuters
  <https://www.reuters.com/business/healthcare-pharmaceuticals/diligent-robotics-eyes-senior-living-market-it-expands-beyond-hospitals-2025-10-14/>
- Physical AI and Humanoid Robots (Tech Trends 2026) — Deloitte Insights
  <https://www.deloitte.com/us/en/insights/topics/technology-management/tech-trends/2026/physical-ai-humanoid-robots.html>
- Sim-to-Real and Real-to-Sim: The Engine Behind Capable Physical AI — AWS Physical AI Blog
  <https://aws.amazon.com/blogs/physical-ai/sim-to-real-and-real-to-sim-the-engine-behind-capable-physical-ai/>
- Robotic Foundation Models for Industrial Control: A Comprehensive Survey and Readiness Assessment — arXiv
  <https://arxiv.org/abs/2603.06749>
- AI Act — Regulatory framework for AI — European Commission
  <https://digital-strategy.ec.europa.eu/en/policies/regulatory-framework-ai>
- Physical AI and Strict Liability: the EU Product Liability Directive — Osborne Clarke
  <https://www.osborneclarke.com/insights/physical-ai-and-strict-liability-what-impact-eu-product-liability-directive>
