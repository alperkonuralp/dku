+++
title = "Bölüm 017 - Bu Ne Biçim Kod?! Yazılım Sektörü Sandığınız Gibi Değil"
date = "2026-06-14T10:00:00+03:00"
description = "İki yazılım dinozoru, üniversite sınavı öncesi yazılımı meslek seçmeyi düşünen gençlere kafa attı. 18 yaşındaki karar kader mi? Matematik şart mı? Yapay zeka çağında yazılımcılık nereye gidiyor?"
youtube_url = "https://youtu.be/lGyTOWFGorU"
youtube_id = "lGyTOWFGorU"
duration = "36:43"
tags = ["yazılım", "kariyer", "meslek seçimi", "üniversite sınavı", "yazılım mühendisliği", "software engineering", "problem çözme", "teknik borç", "technical debt", "agile", "mikroservis", "yapay zeka", "junior developer", "mühendislik"]
notebooklm_url = "https://notebooklm.google.com/notebook/a56e3c6c-f68c-480d-ace7-7cb9ff66fe2c"
draft = false
+++

## Özet

Üniversite sınavı kapıya dayandığında, 18 yaşındaki bir gençten hayatının geri kalanını belirleyecek bir karar vermesi bekleniyor. Bu bölümde, 20 küsur yılı bu sektörde geçirmiş iki "dinozor" olarak tam da bu baskının üzerine gittik. "Bu ne biçim kod?" diye girip; meslek seçiminden matematik korkusuna, mühendisliğin özünden teknik borca, yapay zekanın geleceğine kadar savrulduk. Çıkan ana fikir net: **18 yaşındaki kararınız kaderiniz değildir; yolu her zaman yeniden çizebilirsiniz — yeter ki çözdüğünüz problemden aldığınız o entelektüel tatmin sizde olsun.**

## Video

{{< youtube lGyTOWFGorU >}}

## Konular

- "Bu ne biçim kod?" — junior arkadaşların koduna bakış
- Üniversite sınavı öncesi sektör seçimi ve baskısı
- 18 yaşında kariyer kararı vermek neden bu kadar zor?
- İnşaat mühendisliğinden yazılıma: Alper'in yolu
- Havacılık hevesi, matematik mühendisliği: Burak'ın hikâyesi
- Yanlış karar verince yön değiştirmek mümkün mü?
- Mentor ve yol gösterici bulmanın önemi
- Yazılım gerçekten ağır matematik gerektirir mi?
- Mühendislik = problem çözme (Lego parçaları metaforu)
- Gerçek dünyadaki problemi bilgisayara indirmek
- "Yazdığımız yazılımın başarılı olduğunu nasıl anlarız?"
- Teknik borç ve idiomatik kod
- C++'ın tarihçesi: Stroustrup ve standart kütüphane
- MySQL'in yıllarca süren bug'ı, Notepad++ ve Axios açıkları
- Agile vs Waterfall, mikroservis vs monolit
- Yapay zekanın yazılım sektörüne ve geleceğe etkisi

## Detaylı İnceleme

### 1. 18 Yaşındaki Karar Kader Değildir

Üniversite sınavı, insanın en "delikanlı" olduğu, kanının en hızlı aktığı dönemde önüne konuyor. O yaşta çoğumuz anne babamızın hiçbir şey bilmediğini sanırız; yıllar sonra "aslında ne kadar haklılarmış" dediğimiz olgunluğa geleceğimizden habersiz. Ama mesele şu: 18 yaşında, ömür boyu neyi seveceğini bilecek kadar veri noktasına sahip değilsin.

Alper'in kendi hikâyesi bunun en somut kanıtı. 5 yıl inşaat mühendisliği yaptıktan sonra asıl yerinin yazılım olduğunu fark edip yön değiştirdi ve son 20 küsur yılı koda adadı. Burak'ın yolu da düz değildi; havacılık hevesiyle başlayıp matematik mühendisliğinden geçti. İkisinin de ortak çıkarımı aynı: yön değiştirebilmek bir kusur değil, bir özellik — yazılımcı diliyle söylersek "a feature, not a bug".

Nevşin Mengü'nün bir sözüyle, daha yeni yetişkin olmuşken verdiğin bir karar yüzünden ölene kadar aynı işi yapmak zorunda hissetmemelisin. Tek gerçek başarısızlık, sana hizmet etmeyen bir döngüde takılı kalmaktır. Burada mentorun da kıymeti ortaya çıkıyor: yolu daha önce yürümüş birinin "şuradan git" demesi, harcanan onca deneme-yanılmadan tasarruf ettirir.

### 2. "Bu Ne Biçim Kod?" ve Mühendisliğin Özü

Bölüme adını veren replik, aslında her kıdemlinin bir junior'ın koduna bakarken içinden geçirdiği o tanıdık cümle. Ama burada bir tuzak var: yazılımcılık sanılanın aksine siyah ekranda satır dizmek değil, gerçek dünyadaki bir problemi dijital ortama doğru şekilde aktarma sanatı.

Alper'in inşaat geçmişinden gelen benzetmesi tam yerine oturuyor: yazılımcı, vahşi bir nehri ehlileştirmek için baraj kuran mühendis gibi çalışır. İnşaat mühendisi nehri fiziksel bir barajla dizginler; yazılım mimarı ise o süreci bir dijital ortamda **simüle eder** ki başkaları için faydalı hale gelsin. İşin özü, bir iş mantığını (business logic) en efektif şekilde simüle etmektir.

İki büyük tuzak da burada: "yazılımcılık körlüğü" ve "over-engineering". Sırf teknik bir beceriyi sergilemek için ihtiyacın ötesinde karmaşık sistemler kurmak, seni asıl problemi çözmekten uzaklaştırır. Alper'in ifadesiyle en iyi kod, en az satırla en büyük problemi çözen koddur.

### 3. Matematik Korkusu: Yazılım Sanıldığı Kadar Ağır Değil

Birçok genç, matematik notu düşük diye yazılım hayalinden vazgeçiyor. Oysa yazılımdaki matematik ihtiyacı, inşaat ya da uçak mühendisliğine kıyasla genellikle daha az. Alper'in örneğiyle: orada alan-hacim hesapları için ağır integral bilgisi gerekiyordu; yazılımda ise süreçler artık modüler mimari ve soyutlama (abstraction) üzerine kurulu.

Günümüz yazılımcılığı her şeyi sıfırdan icat etmek değil; Lego parçalarını — yani hazır kütüphaneleri — güçlü bir mantıksal çerçeveyle birleştirmek. Sektör endüstriyel bir olgunluğa erişti; tekerleği yeniden icat etmiyoruz, dünün çözümlerinin omuzlarına basıyoruz. Beceri, plastik tuğlayı üretmekte değil, o tuğlaları bir insan problemini çözecek şekilde birleştirme mimarisinde. Matematik bir avantajdır, ama mühendislik nosyonuna sahip olmak, karmaşık integralleri çözebilmekten çok daha kritiktir.

### 4. Her Uçak Uçar Ama Her Yazılım Çalışmaz

Havacılıkla yazılımı ayıran şey başarı kriterinde gizli. Uçakta hata toleransı sıfırdır; ya uçar ya düşer. Yazılım ise çok daha devingen.

> "Tasarlanan her uçak uçmuştur ama tasarlanan her yazılım başarılı olmamıştır."

Geleneksel mühendislik fiziksel garantilere yaslanır: yerçekimi değişmez, malzemenin kopma noktası bellidir. Yazılımın böyle fiziksel yasaları yok; o uçucu (ephemeral) bir şey. Bu yüzden "çalışıyor" demek başarı demek değil — asıl ölçüt, ürünün kullanıcı tarafından benimsenmesi ve sürdürülebilir olması. Teknik olarak kusursuz ama kimsenin derdine çare olmayan bir uygulama başarısızdır.

Waterfall'dan Agile'a geçişin sebebi de bu: ilerlemeyi küçük parçalarla göstermezsek, baştan yanlış şeyi inşa etme riskine gireriz. "Teknik olarak başarılı" bir proje, idiomatik kod yazan — yani dilin standartlarına uyan, dolayısıyla üç yıl sonra bir başkasının bakım yapabileceği — projedir.

### 5. Teknik Borç ve Mükemmeliyetçilik Tuzağı

Dışarıdan harika görünen bir uygulamanın arkasında %80'e varan teknik borç birikmiş olabilir: kalitesiz kod, bakım zorluğu, gizli açıklar. Yazılımda hiçbir ürün kusursuz değil ve bu kusurlar ciddi itibar kayıplarına yol açabiliyor. Dünya devi MySQL'de yıllarca fark edilmemiş bug'lar çıkabiliyor; Notepad++ ya da Axios gibi milyonların kullandığı araçlarda beklenmedik açıklar bulunabiliyor.

Burak'ın değindiği C++'ın tarihçesi de bu olgunluğun bir başka yüzü: Bjarne Stroustrup'un dile kattığı standart kütüphane, on yıllar içinde sektörün ortak hafızasına dönüştü. Yazılımcılık, bu kusurları yönetme ve sistemi sürekli güncel tutma (maintenance) becerisidir. Mükemmeliyetçilik uğruna hiç bitmeyecek bir projeyle uğraşmaktansa, sürdürülebilir ve geliştirilebilir kod yazmaya odaklanmak gerekiyor. 20 yıllık sistemlerde bile hata çıkabildiğini bilmek, aslında rahatlatıcı olmalı.

### 6. Yapay Zeka Çağında Yazılımcı: Sözdiziminden Yönetmenliğe

2022'den sonra neredeyse her uygulamaya bir "chat" arayüzü eklenmesi, sektörün ne kadar hızlı değiştiğinin kanıtı. Yapay zeka, işin "amelelik" kısmını — rutin kod yazımını — üstlenecek olsa da insan zekasına duyulan ihtiyaç bitmiyor. Burada gözden kaçan bir nokta var: enerji verimliliği. İnsan beyni, karmaşık ve yaratıcı problemleri, yüksek hesap gücü gerektiren bir modele kıyasla çok daha az enerjiyle çözebiliyor. Şimdilik daha verimli "işlemci" hâlâ biziz.

Yapay zeka mesleği öldürmüyor, rolü kaydırıyor: sözdizimi (syntax) seviyesinden yönetmen (director) seviyesine geçiyoruz. Kavga artık satır dizmek değil; karmaşık mimarileri yönetmek, mikroservis–monolit gerilimini doğru okumak. Önemli olan yapay zekaya doğru soruları sormak ve onu yönlendirecek yazılım nosyonuna sahip olmak. Araçlar değişir; problem tanımlama ve strateji kurma becerisi kalıcıdır.

### 7. Merak ve Heves Filtresi

90'lardan, internetin olmadığı bir dönemden, "Samet Hoca" diye bir öğretmenin dersi kalmış aklımızda. C/C++ öğretirdi ve yıllarca terminale bakmaktan gelen bir bilgeliği vardı. Bir öğrenci "programcı olmak istiyorum" dediğinde teknik becerisini değil, sürdürülebilirliği sordu:

> "Bu işi 10 yıl, 20 yıl severek yapabilecek misin? Bunu düşündün mü?"

Çoğu kişi bu alana maaş için giriyor ama hız bariyerlerine çabuk tosluyor. 0'dan 100'e bir gecede çıkılmıyor; junior'dan senior'a uzanan o yorucu tırmanış derin bir merak istiyor. Araçların üç yılda bir değiştiği bir alanda, tükenmişliğe karşı tek savunman merak ve heves. Sektördeki en tecrübeliler bile bir hata üzerinde günlerce "tırmalar"; ama o tırmalamadan alınan entelektüel keyif, işi sürdürülebilir kılan tek şeydir.

**Peki ya siz:** Bugün kullandığınız araçlar yarın yok olsa, problemi çözmenin verdiği o tatmini yine de hisseder miydiniz? Cevabınız "evet" ise, bu uzun maratona hazırsınız demektir.

## İnfografik

{{< infografik src="infografik.webp" alt="Bu Ne Biçim Kod?! - İnfografik" >}}

## Sesli Özetler

### Kısa Özet

{{< audio src="https://media.dinozorlarlakafautuleme.com/bolum-017/audio-brief.m4a" >}}

### Derinlemesine İnceleme

{{< audio src="https://media.dinozorlarlakafautuleme.com/bolum-017/audio-deepdive.m4a" >}}

## Kaynaklar

- [NotebookLM ile bu bölümün sesli/yazılı özeti](https://notebooklm.google.com/notebook/a56e3c6c-f68c-480d-ace7-7cb9ff66fe2c)
