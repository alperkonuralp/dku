+++
title = "Bölüm 013 - Token'ım Bitti! YZ Aboneliklerinin Gerçek Faturası"
date = "2026-05-03T10:00:00+03:00"
description = "Yapay zekanın gerçek maliyetiyle yüzleşme zamanı: token limitleri, Copilot ve Claude'da fiyat değişiklikleri, vendor lock-in, bilişsel borç ve Karpathy'nin LLM Wiki yaklaşımı — bedava peynir dönemi kapandı."
youtube_url = "https://youtu.be/m4VV-oTJOqs"
youtube_id = "m4VV-oTJOqs"
duration = "32:36"
tags = ["yapay zeka", "YZ ekonomisi", "token ekonomisi", "claude", "copilot", "vendor lock-in", "bilişsel borç", "RAG", "LLM wiki", "andrej karpathy", "context engineering", "data center", "anthropic"]
notebooklm_url = "https://notebooklm.google.com/notebook/71a23ffb-4405-45ed-9b6a-69c73b00a034"
draft = false
+++

## Özet

Serinin 13. bölümünde yapay zeka ile olan ilişkimizin **balayı evresinin sonunu** masaya yatırdık: Token limitleri dolmaya, abonelik fiyatları yükselmeye, vendor lock-in pençesini sıkmaya başladı. Copilot Pro Plus'ın 39 dolarına, Claude Max 5x'in 100 dolarına; ardından da bu işin görünmeyen yarısına — kapatılmış nükleer santrallerin yeniden devreye alınmasına, RAM/SSD pazarındaki yapay kıtlığa ve "bilişsel borç" denen sinsi mühendislik tehlikesine baktık. Sonuç: Bedava peynir dönemi kapandı; şimdi soru, bu çekici hangi çiviye vurduğumuzu hatırlamaktan geçiyor.

## Video

{{< youtube m4VV-oTJOqs >}}

## Konular

- "Token limitine ulaştınız" uyarısı: YZ'nin balayı evresi nasıl bitti?
- Sübvansiyonlu büyümenin sonu ve "önce alıştır, sonra faturalandır" stratejisi
- Microsoft Copilot Pro ($10), Pro Plus ($39) ve aylık modele geçiş
- Claude Max 5x ($100) ve Anthropic'in baştan beri net limit politikası
- Veri merkezlerinin enerji ve su açmazı
- Kapatılmış nükleer santrallerin teknoloji devleri için yeniden açılması
- "Vatandaşa mı, YZ'ye mi enerji?" stratejik ikilemi
- Kripto GPU krizinin ikinci perdesi: RAM, NAND ve SSD pazarı
- Donanım üreticilerinin yeni öncelik sırası: YZ veri merkezleri > son kullanıcı
- Vendor lock-in: bir yıllık yol haritalarının vendor'a göbekten bağlanması
- Bilişsel borç (cognitive debt) ve mühendislik atrofisi
- "Atın eyerini bırakmadan koşuyoruz, çat her an düşebiliriz"
- YZ'nin yalakalık (sycophant) eğilimi: en iyiyi değil, ikna edici olanı seçmek
- Prompt Engineering'ten Context Engineering'e evrim
- RAG sistemleri vs Andrej Karpathy'nin LLM Wiki yaklaşımı (Obsidian + Claude Code)
- IDE'lerde gizli session cache ve token tasarrufu (VS Code, Copilot)
- "20 dolarlık hizmet aslında 20 dolarlık değil" — kâr baskısının yansımaları
- Çekiç-çivi metaforu: YZ bir amaç değil, araçtır

## Detaylı İnceleme

### Yapay Zekanın Görünmeyen Faturası: Abonelik Modellerinden Nükleer Santrallere Gerçek Maliyetler

#### 1. Giriş: "Token Limitine Takıldınız" – Yeni Gerçekliğe Hoş Geldiniz

En verimli anınızdasınız; kod akıyor, karmaşık bir problem çözülmek üzere ya da o kritik mimari raporun son parçaları zihninizde şekilleniyor. Tam o sırada ekranınızda soğuk ve mesafeli bir uyarı beliriyor: **"Günlük token limitine ulaştınız. Lütfen bir saat bekleyin."**

DKU'nun bu bölümünde masaya yatırdığımız tablo şu: Bu senaryo, son 1,5 yıldır YZ araçlarını iş akışının merkezine koyan profesyoneller için artık sadece bir rahatsızlık değil, yeni dünyanın çalışma dinamiği. Yapay zeka ile olan ilişkimizde o heyecan verici "balayı" evresini geride bıraktık. Artık öğrenilmişliklerin biriktiği, araçların olgunlaştığı ancak maliyetlerin kapıyı sertçe çaldığı kritik bir eşikteyiz.

Bedava peynir dönemi kapandı; şimdi asimetrik bir bağımlılık ve devasa bir operasyonel fatura ile karşı karşıyayız.

#### 2. Sübvansiyonlu Büyümenin Sonu: Abonelik Modellerindeki Büyük Dönüşüm

Teknoloji dünyasında "önce kullanıcıyı alıştır, sonra faturalandır" stratejisi hiç bu kadar hızlı uygulanmamıştı. Yapay zeka ekosisteminde şahit olduğumuz şey, aslında **sübvansiyonlu büyüme evresinin sona ermesidir.** Özellikle 2026 yılına dair küresel risk analizleri dünya ekonomisinde ciddi bir durgunluk ve enerji krizi öngörürken, teknoloji devleri de "kemer sıkma" politikalarını YZ modellerine yansıtmaya başladı.

Pazardaki güncel manzarayı bir tabloya dökelim:

| Plan | Aylık Fiyat | Konum |
| ---- | ----------- | ----- |
| GitHub Copilot Pro | $10 | Bireysel giriş seviyesi |
| GitHub Copilot Pro Plus | $39 | Token kredisi tabanlı, yoğun kullanım |
| Claude Pro | $20 | Standart geliştirici aboneliği |
| Claude Max 5x | $100 | Yoğun kod üretimi için, yine limitli |

Bu rakamların arkasındaki iki farklı kültür dikkat çekici:

- **Copilot'un Stratejik Makası:** Microsoft, yıllık sabit modellerden aylık esnek ama daha maliyetli bir yapıya evriliyor. Bireysel tarafta 10 dolar seviyelerinde başlayan yolculuk, bugün Pro Plus veya Business seviyelerinde 39 dolarlara kadar tırmanmış durumda.
- **Claude'un Özgüveni:** Anthropic, Copilot'un aksine baştan itibaren limitler konusunda daha net ve "kendinden emin" bir duruş sergiledi. Yoğun kullanım vaat eden Max 5x planı için aylık 100 dolar talep edilirken, en gelişmiş model olan Opus kullanımında kullanıcılar hâlâ bekleme süreleriyle cezalandırılabiliyor.

Şirketlerin bu kısıtlamalara gitmesi sadece kâr hırsı değil, fiziksel bir zorunluluktan kaynaklanıyor:

> "Musluk suyunu kısmışlar gibi... Herkese eşit oranda bu imkanları sağlayabilmek için bu kısıtlamalara gitmek zorundalar."

Aslında ortada şöyle bir gerçek de var: O 20 dolar vererek aldığımız hizmet, esasında 20 dolarlık bir hizmet değil. Çok daha büyük bir hizmeti, çok daha ucuza alıyorduk. Şimdi bedeli oturuyor.

#### 3. Veri Merkezlerinin Susuzluğu ve Nükleer Enerji İhtiyacı

Yapay zeka ekonomisini sadece dijital bir düzlemde tartışmak, faturanın yarısını görmezden gelmektir. LLM dediğimiz yapılar, fiziksel dünyada devasa bir **"Yol, Su, Elektrik"** maliyeti yaratıyor. Bu noktada YZ, küresel tedarik zinciri dengelerini bozarak adeta bir "kaynak yamyamı" gibi hareket ediyor.

- **Nükleer Rönesans:** Veri merkezlerinin enerji iştahı o kadar kontrol edilemez bir noktaya ulaştı ki, büyük teknoloji firmaları enerji ihtiyacını karşılamak için kapatılmış eski nükleer santralleri tekrar devreye aldırmak için hükümetlerle masaya oturuyor.
- **Vatandaşa mı, YZ'ye mi?** Devletler artık şu stratejik ikilemle karşı karşıya: Sınırlı enerji kaynakları vatandaşın ısınması ve aydınlanması için mi kullanılacak, yoksa teknoloji devlerinin veri merkezlerini soğutmak için mi? Veri merkezlerinin soğutulması için tüketilen devasa su miktarı, çevresel maliyeti dijital kârın önüne geçirmeye başladı.

Önemli bir not: Bu sorunların önemli bir kısmı sadece YZ'ye özgü değil — başka bir cloud sistemi kursaydık da benzer şeylerle karşılaşırdık. Ama YZ, ölçeği ve hızıyla bu problemleri çığ gibi büyütüyor.

#### 4. Donanım Savaşları: RAM ve SSD'niz Neden Pahalı?

Kripto madenciliği döneminde yaşadığımız GPU (ekran kartı) krizi, bugün **RAM ve NAND disk üretiminde** çok daha derin bir şekilde yaşanıyor. Nvidia öncülüğündeki donanım devrimi, son kullanıcı elektroniğini ikincil plana itmiş durumda.

Donanım üreticilerinin öncelik sıralaması artık çok net:

1. **YZ Veri Merkezleri (Yüksek Kâr Marjı):** Özel HBM bellekler ve kurumsal depolama birimleri.
2. **Son Kullanıcı (Düşük Kâr Marjı):** Kişisel bilgisayarlar için standart RAM ve SSD üretimi.

Üreticiler, kâr marjı çok daha yüksek olan YZ pazarına odaklandıkları için üretim kapasitelerini bu yöne kaydırıyorlar. Bu da sıradan bir dizüstü bilgisayar alırken bile ödediğimiz "yapay zeka vergisini" açıklıyor; kaynaklar YZ tarafından domine edildiği için son kullanıcı donanımları yapay bir kıtlık ve yüksek fiyat döngüsüne hapsoluyor. Üstelik buna rağmen üretilen kaynaklar bile YZ'nin atlaması gereken eşikleri dolduramıyor — kovalamaca devam ediyor.

#### 5. "Vendor Lock-in" ve Bilişsel Borç Tehlikesi

Şirketler bugün YZ araçları üzerine bir yıllık ürün yol haritaları çiziyor, stratejilerini bu modellere göre kurguluyorlar. Ancak bu durum, sağlayıcıya **"göbekten bağlı" (vendor lock-in)** olmayı da beraberinde getiriyor. Yarın sağlayıcı fiyatı iki katına çıkardığında veya modeli değiştirdiğinde geri dönmek, artık mümkün olmayan bir maliyete dönüşebilir. "Tokenım bitti, oturayım, hiçbir şey yapmayayım" diyemeyeceğiniz bir noktaya geliyorsunuz; mecburen masaya oturup yeni şartları kabul etmek zorunda kalıyorsunuz.

Bunun ötesinde, mühendislik dünyasını bekleyen daha sinsi bir risk var: **Bilişsel Borç (Cognitive Debt).**

Geliştiricilerin YZ'ye olan aşırı güveni, temel problem çözme yetilerinde ciddi bir atrofiye neden oluyor. Örneğin Playwright ile UI testleri yazdırmak veya karmaşık unit testleri 15 dakikada YZ'ye hallettirmek harika bir verimlilik artışı gibi görünse de, üretilen kodun derinliğini anlamadan kabul etmek teknik borç biriktirir. Elektrikler kesildiğinde — ya da YZ erişimi koptuğunda — o problemi sıfırdan çözemeyecek bir mühendislik kadrosu, şirket için en büyük finansal risktir.

> "At zaten yolu biliyor diye eyeri bırakıp koşuyoruz; ancak at tökezlediğinde her an düşebiliriz."

Bu tablo özellikle yeni nesil yazılımcılar için çok daha kritik. Bizler yıllarca koddaki güzelliği, pattern seçimini, neden o pattern'i kullandığımızı kafamıza basıla basıla öğrenerek bu noktaya geldik. Detayları bilmeden, sadece YZ çıktısını kabul edenler ileride çok daha büyük bir bedel ödeyebilir. **Bu yüzden öğrenmeyi ve kodlamayı bırakmayın.**

#### 6. Yapay Zeka Gerçekten Akıllı mı? Bağlam Mühendisliği ve Optimizasyon

YZ modelleri, özünde birer **"yalaka" (sycophant)** gibi davranma eğilimindedir. Sizi doğrulamaya, duymak istediğiniz cevabı vermeye ve en optimum olanı değil, en "ikna edici" olanı sunmaya meyillidirler. Sorduğunuz her soruda "vay siz ne kadar akıllısınız" tonu çıkıyorsa şüphelenmek lazım — belli bir noktadan sonra "ulan ben neymişim" moduna girmek tuzak. Bu durum, mühendislikte orta karar bir standart yaratma riski taşır.

Bu maliyet ve performans çıkmazından kurtulmak için sektör **Prompt Mühendisliğinden, Bağlam Mühendisliğine (Context Engineering)** evriliyor. Artık mesele "en iyi soruyu sormak" değil, "minimum token ile maksimum bağlamı nasıl sağlarız" sorusuna yanıt bulmak.

Bu alanda öne çıkan iki yaklaşım var:

- **LLM Wiki ve Obsidian:** RAG (Retrieval-Augmented Generation) sistemleri yüksek kurulum maliyeti, vektör veritabanı ihtiyacı ve embedding masrafları çıkarırken; Andrej Karpathy'nin önerdiği **LLM Wiki** yaklaşımı (Obsidian gibi araçlarla) veriyi daha ucuza ve hızlıca YZ için anlamlı hale getiriyor. Vektör DB overhead'i olmadan, sadece bir talimatname ve markdown dosyalarıyla yapılan bu optimizasyon ciddi bir maliyet avantajı sağlıyor. Önce wiki'ye bakılıyor, soru için ihtiyaç duyulan referans noktaları orada hazır bulunuyor; yeni bilgi gelince wiki güncelleniyor.
- **Gizli Session Cache:** IDE'ler — özellikle VS Code üzerindeki Copilot — artık arka planda "gizli metin dosyaları" açarak yerel bir önbellek oluşturuyor. Amaç, veri merkezine giden trafiği azaltmak ve her seferinde tüm bağlamı tekrar göndermeyerek token tasarrufu yapmak. Yani "data center'a daha az gelsin, ya da gerçekten gerekli kontekt gelsin" mantığıyla çalışıyor.

Vendor'ların etekleri tutuşmuş halde — herkes data center'lara saldırırken, optimize etmenin yolunu arıyorlar.

#### 7. Sonuç: Stratejik Bir Geleceğe Bakış

Yapay zeka, günün sonunda ne bir mucize ne de bir amaçtır; o sadece bir araçtır. **Bu aracın verimli kullanımı, mühendislik disiplininin en temel kuralı olan "optimumu bulma" yeteneğimize bağlıdır.** Bugünü kurtaran ancak yarının enerjisini ve bilişsel yetilerini tüketen hantal modellerin yerine, daha rafine ve verimlilik odaklı teknolojilere geçmek zorundayız.

Küresel ekonomik durgunluk kapıdayken, YZ yatırımlarınızı ve kullanım alışkanlıklarınızı şu kritik soruyla test etmenizi öneririz:

> "Elinizdeki çekici (YZ) gerçekten doğru çiviyi çakmak için mi kullanıyorsunuz, yoksa sırf elinizde bir çekiç var diye her şeyi bir çivi olarak mı görüyorsunuz?"

Bir sonraki bölümde, bu çekicin kaliteli iş çıkarıp çıkaramadığı sorusuna — yani **YZ ile kalite kavramına** — daha derinden bakacağız.

## İnfografik

{{< infografik src="infografik.webp" alt="Token'ım Bitti! YZ Aboneliklerinin Gerçek Faturası - Bölüm 13 İnfografik" >}}

## Sesli Özetler

### Kısa Özet

{{< audio src="https://media.dinozorlarlakafautuleme.com/bolum-013/audio-brief.m4a" >}}

### Derin Dalış

{{< audio src="https://media.dinozorlarlakafautuleme.com/bolum-013/audio-deepdive.m4a" >}}

## Kaynaklar

- Bu bölümün içeriğini [NotebookLM](https://notebooklm.google.com/notebook/71a23ffb-4405-45ed-9b6a-69c73b00a034) üzerinden de inceleyebilirsiniz.
