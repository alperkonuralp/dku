+++
title = "Bölüm 014 - Review Çıkmazı: YZ Kodunu Kim Denetliyor?"
date = "2026-05-10T10:00:00+03:00"
description = "Yapay zeka kod yazıyor, peki gece rahat uyuyabiliyor mu-yuz? Production'da database silen agent'lardan prompt injection deneylerine, custom review zincirinden Anthropic Mythos'a kod kalitesi krizi üzerine bir sohbet."
youtube_url = "https://youtu.be/rSDQyJFBtIo"
youtube_id = "rSDQyJFBtIo"
duration = "35:56"
tags = ["yapay zeka", "yz", "ai", "kod kalitesi", "code quality", "code review", "prompt injection", "claude code", "claude mythos", "anthropic", "llm", "sonarqube", "custom agent", "context engineering", "türkçe podcast"]
notebooklm_url = "https://notebooklm.google.com/notebook/b4027eb7-148d-4b1d-ae56-064ac7d5190c"
draft = false
+++

## Özet

Yapay zeka kod yazma hızında devrim yarattı — ama "otomatik Allow'a bas, kahve içmeye git" rahatlığına henüz geçemedik. Çünkü bedeli production'da database silinmesine kadar gidebiliyor. Bu bölümde Burak Selim Şenyurt ile birlikte YZ ile yazılan kodun kalitesini, neden hâlâ kuşkucu davrandığımızı, prompt injection saldırılarını ve **insan denetiminin neden vazgeçilmez** olduğunu konuştuk. LLM tavanı, custom agent zincirleri ve Anthropic'in yeni Mythos modeli de işin içinde.

## Video

{{< youtube rSDQyJFBtIo >}}

## Konular

- Kod kalitesi nedir? "Gece bizi uyandırmayan kodlar" tanımı
- YZ gerçekten kaliteli kod mu yazıyor — kuşkucu yaklaşım neden hâlâ haklı?
- Review süresi neden uzuyor: "Kendim yazsam daha hızlı biterdi" çıkmazı
- Domain bilgisi eksikliği ve YZ'nin en kısa yola sapma eğilimi
- Production'da migration başlatıp tabloları bozan aşırı yetkili agent'lar
- Konteks sınırı ve sprint bazlı yol haritası yaklaşımı
- LLM tavanı: YZ hâlâ "Notepad++'ta CTRL+F" mantığıyla bizi taklit ediyor
- Tekillik (singularity) tartışması ve YZ'nin kendi diline geçme ihtimali
- Özelleşmiş agent'lar: C# Coder, Vue Coder ve Reviewer rolleri
- Custom coding standartları ve PR review pratiği
- Prompt Injection: Küçük bir LLM'i log mesajıyla kandırma deneyi
- 4.5B parametreli modeller vs GPT ölçeği — güvenlikte ölçek farkı
- Sandbox / Docker ile izole test ortamlarının kritik önemi
- Mythos ve Project Glasswing: Anthropic'in siber güvenlik hamlesi
- SonarQube ile statik kod analizi ve custom review agent zinciri
- Retrieval Augmented Generation (RAG) ile halüsinasyon payını düşürme
- Yazılımcıdan "Yazılım Mimarına" dönüşüm — Human-in-the-loop neden şart?
- Atın eyerini bırakmadan koşmak: bilişsel borç riski sürüyor

## Detaylı İnceleme

### YZ Kod Yazıyor, Peki Gece Rahat Uyuyabiliyor mu-yuz? Kod Kalitesinde "Yapay" Devrim ve Gerçek Riskler

#### 1. Giriş: Hız Tutkusu ve Görünmez Tehlike

Yazılım dünyasında şu an iki temel kavramın amansız yarışı içindeyiz: **Velocity** (hız) ve **Long-term Maintainability** (sürdürülebilirlik). Yapay zekanın kod yazma hızı, Developer Experience (DX) süreçlerinde devrim niteliğinde bir konfor sağlasa da, bu "hız tutkusu" beraberinde ciddi bir teknik borç yükünü de getiriyor. YZ'nin ürettiği kodun sadece çalışıyor olması artık bir başarı kriteri değil. Asıl mesele, bu hızın arkasına gizlenen görünmez kalite krizini nasıl yöneteceğimizdir. Bir mimar olarak sormamız gereken soru şu: YZ bizim için kod yazarken, sistemin mimari bütünlüğünü mü inşa ediyor yoksa yarın başımızı ağrıtacak bir enkaz mı bırakıyor?

#### 2. Kod Kalitesinin Yeni Tanımı: "Gece Rahat Uyutan Kod"

Kod kalitesi, teknik bir metrikten ziyade aslında bir **güven meselesidir**. Kaliteli bir sistem, sadece "happy path" senaryolarında çalışmakla kalmaz; saldırı altında dahi bütünlüğünü korur ve kurum için geri dönülemez bir itibar kaybına yol açacak bug'lar içermez. Sektörel tecrübemiz bize gösteriyor ki, gerçek kalite **Domain Knowledge** ile harmanlanmış, bakımı kolay ve net bir mimari duruşu olan kodda gizlidir. Burak Selim Şenyurt'un bu durumu özetleyen şu yaklaşımı, aslında her yazılım mimarının pusulası olmalıdır:

> "Kod kalitesi bence hani gece rahat uyuyacağımız kodlar. Hani bizi peşimizden kimsenin kovalamayacağı kodlar."

#### 3. Review Çıkmazı: Zaman Kazandırıyor mu, Yoksa Çalıyor mu?

Günümüzde "otomatik her şeye onay veren" (auto-approve) bir geliştirici tipolojisi türüyor. Ancak deneyimli bir mimar için bu, en büyük risk faktörüdür. Bir meslektaşımızın Pull Request paketini incelerken onun alışkanlıklarını, hata yapma eğilimlerini ve "insani dokunuşunu" biliriz. Oysa YZ'nin sunduğu PR'lar sterildir ancak devasa hacimlidir.

YZ, doğası gereği genellikle **en az direnç gösteren yolu** (path of least resistance) seçer. Bu da karmaşık sistemlerin bütününe dair bir Architectural Decision Record (ADR) veya derinlemesine alan bilgisi eksikliği demektir. Sonuç olarak, YZ'nin hızlıca ürettiği binlerce satırı didik didik incelemek, "kendim yazsaydım daha hızlı biterdi" dedirten bir review çıkmazına yol açmaktadır. **Skeptik bir bakış açısı korumak, artık bir tercih değil zorunluluktur.**

#### 4. Tehlikeli Sınırlar: Migration Hataları ve Prompt Injection

YZ agent'larına kontrolsüz yetki vermek, teoriden pratiğe döküldüğünde felaketlerle sonuçlanabiliyor. Örneğin, Claude Code gibi araçlarla yapılan denemelerde görüldüğü üzere, sistemin tamamını kavramayan bir agent'ın yanlış bir çıkarımla bir anda **hatalı bir migration başlatıp production tablolarını bozması** işten bile değildir.

Güvenlik tarafında ise riskler çok daha sofistike bir hal alıyor. Yapılan deneylerde, log dosyaları arasına gizlenmiş manipülatif komutlarla **Prompt Injection** saldırıları gerçekleştirilebilmektedir. Kritik bir teknik detay: 4.5 milyar parametreli küçük ölçekli modellerin, log mesajları üzerinden kandırılarak sistem kullanıcı adlarını çalmaya ve dış bir servise post etmeye ikna edilebildiği görülmüştür. GPT-4 gibi devasa modeller bu konuda daha dirençli olsa da, durum model ölçeğinin güvenlik üzerindeki etkisini kanıtlar niteliktedir. Bu nedenle YZ aksiyonlarını, internet erişimi olmayan ve kısıtlı yetkilere sahip **sandbox** (izole ortam) yapılarında koşturmak stratejik bir savunma hattıdır.

#### 5. Bir Çözüm Stratejisi: Agentic İş Akışları ve Statik Analiz

Yapay zekadan verim alırken mimari kaliteyi korumak için sıkı bir mühendislik disiplini şarttır. Bu süreçte şu yaklaşımları standart haline getirmeliyiz:

- **Granüler Görev Yönetimi:** Projeyi devasa bir blok olarak değil, küçük sprintlere ve spesifik tasklara bölerek YZ'nin bağlam (context) içinde kalmasını sağlamak.
- **Özelleşmiş Agent'lar:** Tek bir jenerik model yerine; dile özel yapılandırılmış C# Coder Agent, Vue Coder Agent ve bunları denetleyen bağımsız bir Reviewer Agent gibi roller tanımlamak.
- **Otomatize Denetim (Docker & SonarQube):** Sürece Docker container'ları üzerinde hızlıca ayağa kaldırılan SonarQube gibi statik kod analizi araçlarını entegre etmek. YZ'nin yazdığı kodu önce bu otomatize sistemlerden geçirmek, temel hataları daha review aşamasına gelmeden eler.
- **Kurumsal Bellek (RAG):** Retrieval Augmented Generation kullanarak YZ'yi şirketin kendi dokümantasyonu, kodlama standartları ve mimari tercihleriyle besleyerek "halüsinasyon" payını düşürmek.

#### 6. Geleceğe Bakış: Yazılımcıdan "Yazılım Mimarına" Dönüşüm

LLM teknolojisi şu an bir **"mimicry" (taklit) evresindedir**. YZ, hâlâ insan mühendisliğinin vizyonuna ve sistemik bakış açısına ihtiyaç duyuyor. Singularity (tekillik) tartışmaları fütüristik bir boyutta devam etse de, yakın gelecekte YZ'nin sadece kendi anlayabileceği — belki de bizim bugün Assembler'a baktığımız gibi bakacağımız — yeni programlama dilleri geliştirmesi kaçınılmaz olabilir.

Bu evrimde yazılımcının rolü, kod satırı üreten birer "işçiden", sistemi denetleyen, mimari yol haritasını çizen ve YZ'nin çıktılarını valide eden birer **"Yazılım Mimarına"** dönüşmektedir. İnsanın sistemin merkezinde (Human-in-the-loop) kalmadığı her senaryo, kontrolsüz bir karmaşaya gebedir.

#### 7. Sonuç ve Düşündürücü Soru

Yapay zeka ile iş birliği artık bir lüks değil, kaçınılmaz bir realitedir. Ancak bu hız tutkusunun bizi teknik bir uçuruma sürüklemesine izin veremeyiz. Kontrol mekanizmalarını mimari süreçlere entegre etmek, "gece rahat uyumamızı" sağlayacak tek yoldur.

Peki, yapay zekanın yazdığı ve sizin artık anlamadığınız bir programlama diliyle karşılaştığınızda, o koda ve o sistemin kararlarına hâlâ güvenmeye devam eder miydiniz?

## İnfografik

{{< infografik src="infografik.webp" alt="Review Çıkmazı: YZ Kodunu Kim Denetliyor? - İnfografik" >}}

## Sesli Özetler

### Kısa Özet

{{< audio src="https://media.dinozorlarlakafautuleme.com/bolum-014/audio-brief.m4a" >}}

### Detaylı Anlatım

{{< audio src="https://media.dinozorlarlakafautuleme.com/bolum-014/audio-deepdive.m4a" >}}

## Kaynaklar

- **NotebookLM Notebook:** [Bölüm 14 - NotebookLM](https://notebooklm.google.com/notebook/b4027eb7-148d-4b1d-ae56-064ac7d5190c)
- **Anthropic Mythos & Project Glasswing:** Anthropic'in en güçlü ve sınırlı erişimli modeli üzerine duyuru
- **OWASP - Prompt Injection:** LLM güvenlik açıkları için OWASP rehberi
