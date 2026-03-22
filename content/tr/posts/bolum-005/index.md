+++
title = "Bölüm 005 - 20 Yıl Önce Hangi Dili Öğrenirdin? Basic'ten Rust'a Yolculuk"
date = "2026-01-27"
description = "Programlama dillerinin 30 yıllık evrimini masaya yatırdık. Basic ve Assembly'den Java'ya, .NET'ten Rust ve Zig'e uzanan yolculukta her dönemin kendi zorlukları ve dersleri var."
youtube_url = "https://youtu.be/jVqd5DCabYI"
youtube_id = "jVqd5DCabYI"
duration = "54:17"
tags = ["programlama dilleri", "Basic", "Assembly", "Java", "C#", ".NET", "Rust", "Zig", "Go", "pointer", "memory management", "Borrow Checker", "LINQ"]
notebooklm_url = "https://notebooklm.google.com/notebook/c71ce72c-c053-403f-8580-66523cb2b91a"
draft = false
+++

## Özet

"20 yıl önce olsaydı hangi programlama dilini öğrenirdin?" sorusundan yola çıkarak programlama dillerinin 30 yıllık evrimini masaya yatırdık. GW-Basic ve DOS döneminden Java Applet'lerin heyecanına, pointer'ların "milyon dolarlık hatası"ndan Rust'ın Borrow Checker devrimine, Anders Hejlsberg'in C#'ı yaratmasından LINQ'nun fonksiyonel programlamayı ana akıma taşımasına kadar geniş bir yolculuk. Sonuç: Saatin nasıl çalıştığını anlamak her zaman geçerli.

## Video

{{< youtube jVqd5DCabYI >}}

## Konular

- Basic'ten Assembly'ye: ilk programlama deneyimlerimiz
- 90'ların başı: Java Applet'leri, Netscape Navigator ve World Wide Web
- C, C++, Java ve .NET'in doğuşu — oyun değiştiren diller
- Rust, Zig ve Go'nun getirdikleri
- Pointer kavramı ve "Milyon Dolarlık Hata" (Null Pointer)
- Borrow Checker: Rust'ın memory safety yaklaşımı
- Anders Hejlsberg ve C#'ın programlama dünyasına etkisi
- LINQ ve functional programming'in Object Oriented dünyaya girişi
- Her dilin neden farklı bir amaca hizmet ettiği

## Detaylı İnceleme

### 20 Yıl Öncesinden Bugüne: Yazılım Dünyasının Unutulmuş Çileleri ve Geleceği Şekillendiren 5 Kritik Ders

Bugünkü teknolojik konforun gölgesinde geriye dönüp baktığımda, yazılım dünyasının geçirdiği evrimi sadece bir "gelişim" değil, büyük bir "silkinme" olarak görüyorum. 286 işlemcilerin gürültüsüyle tanışan, GW-Basic ile kodlamanın alfabesini söken ve o meşhur Delphi vs. Visual Basic savaşlarında taraf tutan bizim neslimiz için bugün her şey çok kolay görünebilir. Ancak asıl mesele, bugünkü aklımızla 20 yıl önceye dönseydik hangi dili seçeceğimiz değil; o günün eziyetlerinden süzülen "saatin nasıl çalıştığını anlama" bilgeliğidir.

#### İnternetin Doğuşu ve Java'nın "Kırmızı Burunlu" Devrimi

90'ların ortasında World Wide Web henüz emekleme aşamasındayken, tarayıcılar bugünkü gibi birer işletim sistemi değil, sadece statik metinleri gösteren araçlardı. Netscape Navigator döneminde internete dinamizm getiren en büyük "fitil ateşleyici" Java olmuştu.

> "Kitabın ilk bölümü, o Java'nın ikonu vardı böyle, kırmızı burunlu bir karakter (Duke). Bunu internet browser'da hareket ettirme kodu içeren bir kısım vardı. Çalıştırdığın zaman browser'da hareket ediyor. O zaman hiçbir şey yoktu. O yüzden Applet'in hareket ediyor olması büyük bir şey bizim için."

Java Applet'leri, istemci tarafında çalışan ilk ciddi dinamik yapılar olarak modern webin önünü açtı.

#### "Eziyetin" Öğreticiliği: Neden Hâlâ C/C++ ve Assembly Konuşuyoruz?

Modern diller bize muazzam soyutlamalar sunuyor; ancak bu soyutlamalar bazen "leaky abstractions" haline gelip başımıza iş açtığında, düşük seviyeli dillerin disiplini imdadımıza yetişiyor.

Garbage Collector konforuna alışmadan önce, belleği manuel yönetmek zorundaydık. Pointer aritmetiği bilmek, sadece bir veri tipini değil, verinin donanımla nasıl buluştuğunu kavramaktı. Assembly ile uğraşmak — bir "Hello World" yazmak için bile 10 satır kod yazmanın, register yönetmenin ve DOS'un o meşhur 21h kesmesini bilmenin zorunlu olduğu bir dünya — yazılımcıya optimum çözümü bulma refleksini kazandırır.

#### Her Dil Her İş için Değildir: .NET vs. Node.js

Yazılımda fanatizm, vizyonun en büyük düşmanıdır. Bir dili her probleme yegâne çözüm sanmak, elindeki çekici her şeye çivi muamelesi yapmakla eşdeğerdir.

Node.js, single-thread yapısıyla I/O odaklı işlerde harikalar yaratsa da, video işleme gibi yoğun işlemci gücü gerektiren alanlarda .NET hâlâ üstünlüğünü koruyor. Yapay zekanın bile bu ayrımı yapıp ".NET ile daha iyi yaparsın" demesi, dillerin konfor alanlarını bilmenin önemini kanıtlıyor.

#### "Milyon Dolarlık Hata" ve Rust'ın Durdurulamaz Yükselişi

C ve C++ dünyasının en büyük kabusu olan Null Pointer hataları, literatürde "milyon dolarlık hata" olarak bilinir. Rust, **Borrow Checker** ve katı sahiplik kurallarıyla bu sorunu derleme zamanında çözerek devrim yaptı. Microsoft'un bile Windows çekirdek kodlarını Rust'a geçirmeye başlaması, bellek güvenliğinin artık bir tercih değil, hayati bir zorunluluk olduğunu gösteriyor.

#### Minimalist Gelecek: Zig ve "String"siz Bir Dünya

Modern diller sürekli yeni syntax sugar özellikleriyle şişerken, Zig dili şaşırtıcı bir minimalizm sunuyor. Zig'de yerleşik bir String veri tipi bile yok; metinler sadece birer U8 array olarak temsil ediliyor. Hiçbir fonksiyon gizlice bellek tahsisatı yapmaz — eğer bir fonksiyon bellek kullanacaksa, ona bir allocator parametre olarak geçilmelidir. C'nin modern bir versiyonu gibi duran Zig, "saatin nasıl çalıştığını" anlamak isteyenler için harika bir laboratuvardır.

#### Sonuç: Saatin Çarklarını Bilin

Yazılım dilleri sadece birer araç değil, farklı problem çözme mantaliteleridir. Delphi'nin mimarı Anders Hejlsberg'in C#'ı yaratması ve ardından gelen LINQ hamlesi, sadece .NET dünyasını değil, Java ve JavaScript ekosistemini de silkinmeye ve fonksiyonel özellikleri bünyesine katmaya zorlamıştır.

Bugün yapay zekanın bizim yerimize kod yazabildiği bir dünyada, farkımız sözdizimi ezberlemek olamaz. Yapay zeka kod yazar, ancak o kodun neden patladığını anlamak için saatin içindeki çarkları — bellek yönetimi, thread yapıları, veri modelleri — bilmeniz gerekir. Her dilin felsefesini heybenize katın ama saatin nasıl çalıştığını asla unutmayın.

## İnfografik

{{< infografik src="infografik.webp" alt="Basic'ten Rust'a: 20 Yıllık Bir Programlama Serüveni" >}}

## Sesli Özetler

### Kısa Özet
{{< audio src="https://media.dinozorlarlakafautuleme.com/bolum-005/audio-brief.m4a" >}}

### Derin Dalış
{{< audio src="https://media.dinozorlarlakafautuleme.com/bolum-005/audio-deepdive.m4a" >}}

---

📓 [Bu bölümün NotebookLM çalışma alanını inceleyin](https://notebooklm.google.com/notebook/c71ce72c-c053-403f-8580-66523cb2b91a)
