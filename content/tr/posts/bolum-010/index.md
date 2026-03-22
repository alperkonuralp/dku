+++
title = "Bölüm 010 - Çözüme Problem mi Uyduruyoruz? Teknolojide Déjà Vu!"
date = "2026-03-22"
description = "Teknolojide zamanın döngüselliğini konuştuk. Aynı problemler farklı isimlerle tekrar tekrar karşımıza çıkıyor. Spotify bile mikroservisten modüler monolite geri döndü!"
youtube_url = "https://youtu.be/NVrLpP61lqA"
youtube_id = "NVrLpP61lqA"
duration = "31:17"
tags = ["hype döngüsü", "mikroservis", "monolit", "design patterns", "transaction", "vendor lock-in", "POC", "MVP", "loose coupling", "yapay zeka"]
notebooklm_url = ""
draft = false
+++

## Özet

Teknolojide zamanın döngüselliğini konuştuk. Aynı problemler farklı isimlerle tekrar tekrar karşımıza çıkıyor — biz buna "Teknolojide Déjà Vu" diyoruz. Spotify bile mikroservisten modüler monolite geri döndü! 10 yıl önce begin transaction deyip çözdüğümüz dert, mikroservislerle birlikte saga pattern ve outbox pattern derken tekrar başımıza geldi. Design pattern'lar zamansız ama hype'lar geçici. Yapay zekaya balığı tutturmayın, tutmayı öğrenin.

## Video

{{< youtube NVrLpP61lqA >}}

## Konular

- Teknolojide Déjà Vu: Neden hep aynı döngüdeyiz?
- Çözüme problem mi uyduruyoruz yoksa probleme çözüm mü arıyoruz?
- Mikroservis → Monolit → Modüler Monolit: Spotify bile geri döndü!
- Kütüphane bağımlılığı ve loose coupling'in önemi
- Transaction kavramı: 10 yıl önce çözdüğümüz dert tekrar başımıza geldi
- Design Pattern'lar neden zamansız?
- POC ve MVP: Hype'a kanmadan önce test edin!
- Yapay zeka size balık tutmayı öğretsin, balığı siz tutun!
- Vendor lock-in tehlikesi ve güvenlik açıkları

## Detaylı İnceleme

### Teknoloji Dünyasında Déjà Vu: Çözüme Problem mi Uyduruyoruz?

#### Giriş: Tekerrür Eden Teknoloji Tarihi

Yazılım dünyasında 20 yılı devirmiş bir mimar olarak geriye dönüp baktığımda, zamanın ne kadar devingen ama bir o kadar da döngüsel olduğunu görüyorum. Bugün "devrim" olarak sunulan pek çok yaklaşım, aslında on beş-yirmi yıl önce farklı isimlerle tartıştığımız, çözdüğümüz ve hatta bazen rafa kaldırdığımız konulardan ibaret.

Geçmişin tecrübelerini heybemize katmadan sadece yeniye odaklanmak, bizi aynı hataları daha modern ve daha pahalı araçlarla yapmaya itiyor.

#### Hype Trenine Binmek: Çözüme Problem mi Uyduruyoruz?

Günümüz yazılım ekosisteminde en büyük tehlike, bir teknolojinin mühendislik başarısından ziyade hype seviyesine göre seçilmesidir. Netflix, Spotify veya Amazon gibi devlerin kendi devasa ölçekleri için geliştirdiği mimari pratikler, çoğu zaman bağlamından koparılarak her ölçekteki şirkete "tek doğru" gibi pazarlanıyor.

Mevcut bir problemi çözmek için araç aramak yerine, elimizdeki popüler araca uygun bir problem icat etmeye başlıyoruz.

> "Elimizde bir çözüm var; hadi bu çözümü uygulayacağımız problemi çıkartalım diye oradan gidiyoruz."

#### Mikroservis Paradoksu: 10 Yıl Önce Çözülen Dertlerin Dönüşü

Mikroservisler bize ölçeklenebilirlik vaat etti ama beraberinde operasyonel bir kabusu da getirdi. 10 yıl önce monolitik sistemlerde tek bir `begin transaction` ve `commit` komutuyla hallettiğimiz veri tutarlılığı, bugün dağıtık sistemlerin en büyük sancısı haline geldi.

**Dağıtık Transaction Çıkmazı:** Eskiden MSDTC gibi araçlarla yönetilen yapılar, Linux ve Container dünyasına geçişle birlikte tarih oldu. Bu bizi Saga Pattern veya Outbox Pattern gibi çok daha zor ve maliyetli kurgulara mecbur bıraktı.

**Operasyonel Anksiyete:** "Veri gitti mi? Senkron oldu mu?" soruları artık sadece teknik birer detay değil; gecenin bir yarısı çalan telefonların ve bitmek bilmeyen senkronizasyon hatalarının ana kaynağı.

#### Bağımlılık Tuzağı: Vendor Lock-in

Bir kütüphaneyi projenin merkezine araya bir soyutlama katmanı koymadan yerleştirmek, o satıcıyla "evlenmek" demektir. Üstelik bu evlilikte boşanma bedeli bazen tüm projeyi baştan yazmaktır.

Risk sadece performansla sınırlı değil; güvenlik ve lisanslama maliyetleri de bu bağımlılık tuzağının birer parçasıdır. Kurtuluş her zaman aynı: **Loose Coupling** ve doğru **Abstraction**.

#### Devlerin Dönüşü: Spotify Neden Modüler Monolite Geçti?

Mikroservislerin "poster çocuğu" Spotify'ın bugün Modüler Monolit yapılarına yönelmesi, tüm sektör için bir ders niteliğindedir. Bu bir geri adım değil, bir olgunlaşma belirtisi. Milyonlarca podu yönetmenin operasyonel maliyeti, network trafiğinin yarattığı baş ağrısı ve veri tutarlılığı sorunları, devleri bile SOA prensiplerini monolitik bir çatı altında toplamaya itti.

İyi tasarlanmış bir modüler monolit, kötü tasarlanmış bir mikroservis yığınından her zaman daha verimli ve sürdürülebilirdir.

#### Yapay Zeka Çağında Mühendislik: Balık Tutmayı Öğrenmek

Yapay zeka sektöre yeni bir soluk getirdi ancak temel mühendislik disiplinlerine olan ihtiyacı azaltmadı, aksine artırdı. AI bize hızlı kod yazdırabilir ama o kodun "belleğe bir bomba bırakıp bırakmadığını" anlayacak olan yine insan zekası ve disiplinidir.

- **POC Aracı Olarak AI:** Yeni bir teknolojinin etkisini görmek için AI'yı kullanın. Hızlıca bir Proof of Concept hazırlatın ve test edin.
- **Disiplinli Mühendislik:** Design pattern'ları ve SOLID prensiplerini bilmeden AI'ya kod yazdırmak, kontrolsüz bir güçtür.
- **Öğrenme Yaklaşımı:** Yapay zeka size balık tutmayı öğretsin, balığı siz tutun.

#### Sonuç: Heyecanı Bir Kenara Bırakın, Checklist Kullanın

Bir mimari kararı vermeden önce kendinize şu soruları sorun:

- Bu yapıyı kolayca test edebilecek miyim?
- Canlıya alma süreci ne kadar karmaşıklaşacak?
- Sistem yük altında nasıl tepki veriyor?
- Bu araca ne kadar göbekten bağlıyım?
- Kullandığım dış enstrüman bir güvenlik açığı barındırıyor mu?

Bugün heyecanla uyguladığınız o modern çözüm, yarın çözmek zorunda kalacağınız yeni bir problem mi, yoksa gerçekten ihtiyacınız olan anahtar mı?

## İnfografik

{{< infografik src="infografik.webp" alt="Teknolojide Déjà Vu: Çözüme mi Problem Uyduruyoruz?" >}}

## Sesli Özetler

### Kısa Özet
{{< audio src="https://media.dinozorlarlakafautuleme.com/bolum-010/audio-brief.m4a" >}}

### Derin Dalış
{{< audio src="https://media.dinozorlarlakafautuleme.com/bolum-010/audio-deepdive.m4a" >}}

---

📓 Bu bölümün NotebookLM çalışma alanı yakında eklenecektir.
