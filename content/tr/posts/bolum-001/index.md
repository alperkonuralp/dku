+++
title = "Bölüm 001 - Cloudflare Çöktü, Dünya Durdu!"
date = "2025-12-26"
description = "Cloudflare'ın dünya çapındaki kesintisinden yola çıkarak altyapı bağımlılıklarını, Rust'taki unwrap hatasını, mikroservis vs monolit tartışmasını ve Murphy Kanunu'nu konuştuk."
youtube_url = "https://youtu.be/GNZnbC31MX8"
youtube_id = "GNZnbC31MX8"
duration = "34:19"
tags = ["cloudflare", "rust", "mikroservis", "monolit", "dağıtık sistemler", "altyapı", "Murphy kanunu", "resilience", "API gateway"]
notebooklm_url = "https://notebooklm.google.com/notebook/1951d774-a8d5-466b-9149-270ea728172f"
draft = false
+++

## Özet

Serinin ilk bölümünde güncel bir olay olan Cloudflare kesintisinden yola çıktık. Rust dilindeki basit bir `unwrap()` hatası, internetin %20'sine hizmet veren altyapıyı çökertti. Buradan hareketle tek noktaya bağımlılık risklerini, denizaltı kablolarının güvenliğini, mikroservis vs monolit tartışmasını ve Netflix ile Amazon'un neden geri adım attığını konuştuk. Sonuç: Murphy Kanunu dinozor devrinden beri yanımızda!

## Video

{{< youtube GNZnbC31MX8 >}}

## Konular

- Cloudflare neden çöktü? Rust'taki basit bir `unwrap()` hatası nasıl global bir krize dönüştü?
- İnternetin %20'si tek bir servise bağlıyken ne kadar güvendeyiz?
- Denizaltı kabloları, köpek balıkları ve NATO görevleri
- Mikroservis mi, monolit mi? Netflix ve Amazon neden geri adım atıyor?
- Dağıtık sistemlerin gerçek maliyeti ve transaction kabusları
- Murphy Kanunu dinozor devrinden beri yanımızda!

## Detaylı İnceleme

### Cloudflare Neden Çöktü? İnternetin Pamuk İpliğine Bağlı Olduğu 4 Gerçek

#### Giriş: Dijital Dünyanın Durduğu O An

İnternet dünyasında her şeyin tıkır tıkır işlediğini sandığımız bir anda, devasa bir sistemin çökmesiyle dijital hayat bir anda felç olabiliyor. Yakın zamanda yaşanan Cloudflare kesintisi, bu durumun en sarsıcı örneklerinden biriydi. İnternet trafiğinin yaklaşık %20'sinin, yani neredeyse her beş web sitesinden birinin bu servisin arkasında olduğu gerçeği, merkezi yapıların ne kadar "tekil başarısızlık noktası" (single point of failure) haline geldiğini kanıtladı. Günlük hayatımızın ve iş dünyamızın bu kadar devasa sistemlere göbekten bağlı olması, bizi her an kopabilecek bir pamuk ipliğine mahkum ediyor.

#### Rust'ın Gücü Bile İnsan Hatasını Durduramıyor: "Unwrap" Kazası

Cloudflare kesintisinin teknik detaylarına indiğimizde, karşımıza modern ve "güvenli" bir dil olan Rust çıkıyor. Rust, bellek güvenliği (memory safety) konusunda devrim niteliğinde olsa da, en zayıf halka olan insan hatasını devre dışı bırakamıyor. Kesintinin merkezinde, Rust'taki `unwrap()` metodunun yanlış kullanımı yatıyor.

Geliştiriciler, geliştirme aşamasında süreci hızlandırmak için "buradan kesinlikle geçerli bir değer dönecek" varsayımıyla `unwrap()` metodunu kullanırlar. Ancak bu kod parçası canlı ortama (production) taşındığında ve sistem beklenmedik bir durumla karşılaştığında, Rust "panic" durumuna geçer ve tüm süreci durdurur.

> "Murphy dinozor devrinden beri yanımızda ya. Biz ne kadar bu sistemleri çok dayanıklı yaptığımızı düşünsek de çok basit developer hatalarından böyle büyük problemler ortaya çıkabiliyor."

Yazılım mimarisinde asıl mesele, dilin ne kadar güvenli olduğu değil, geliştiricinin o %1'lik istisnai durumu yönetip yönetmediğidir.

#### İnternetin Fiziksel Kırılganlığı: Okyanusun Altındaki Kablolar ve Köpekbalıkları

İnterneti sadece soyut bir "bulut" olarak görmek, gerçek dünyadaki altyapı risklerini ıskalamaktır. Dijital dünya, okyanusların derinliklerinden geçen binlerce kilometrelik fiziksel omurga kablolarına bağımlıdır. Öyle ki NATO, İsveç donanmasına Kuzey Denizi'ndeki bu kabloları drone ve denizaltılarla koruma görevi veriyor.

İşin içinde sadece sabotaj riskleri değil, beklenmedik "aktörler" de var: Köpekbalıkları. Bu canlıların kablolara saldırması bile kıtalararası bağlantıyı kesintiye uğratabiliyor. Bir mimar için bu, **High Availability** ve **Disaster Recovery** senaryolarının sadece yazılımsal değil, fiziksel ve jeopolitik boyutlarını da düşünmek demektir.

#### Kurtarıcı Bir Kalkan Olarak API Gateway

Karmaşık sistemlerde dış dünya ile iletişim kurarken, doğrudan bağlantı kurmak yerine bir **API Gateway** kullanmak hayat kurtarır. API Gateway, sistemler arasında bir "soyutlama katmanı" görevi görür. Daha da önemlisi, bir **Resilience (Dayanıklılık)** kalkanıdır. Dış sistemden gelen aşırı yavaşlamalarda (timeout), Gateway devreye girerek yerel sisteminizin kaos durumuna girmesini engeller.

#### Mikroservis mi, Monolit mi? Karmaşıklık Tuzağı

Her sistemi mikroservislere bölme furyasının yarattığı karmaşıklıkla boğuşuyoruz. Dağıtık sistemlerin kucağına düştüğünüz an, karşınıza devasa bir maliyet çıkar: **Transaction Yönetimi**. Eskiden monolitik yapılarda tek bir hamlede çözdüğümüz veri tutarlılığı, mikroservis dünyasında tam bir curcunaya dönüşmüş durumda.

Amazon ve Netflix gibi devlerin bile bazı kritik noktalarda **"Modular Monolith"** yapısına geri dönmeye başlaması tesadüf değil. "Güçlü bir monolit kurmadan mikroservise geçmemek" temel düsturumuz olmalıdır.

#### Sonuç: Bir Sonraki Kesintiye Hazır mısınız?

En modern dilleri kullansak da, sistemlerimizi en iyi bulut sağlayıcılarına emanet etsek de risk bitmez. İnsan hatası, fiziksel sabotajlar ve mimari karmaşıklık her zaman pusudadır. Sorumlulukları doğru dağıtmak, doğru protokolleri seçmek ve her zaman bir B planına sahip olmak, dijital dünyada ayakta kalmanın tek yoludur.

## İnfografik

![Cloudflare Çöküşünden Dersler: Sistem Dayanıklılığı ve Mimari Stratejiler](infografik.png)

## Sesli Özetler

### Kısa Özet
{{< audio src="audio-brief.m4a" >}}

### Derin Dalış
{{< audio src="audio-deepdive.m4a" >}}

---

📓 [Bu bölümün NotebookLM çalışma alanını inceleyin](https://notebooklm.google.com/notebook/1951d774-a8d5-466b-9149-270ea728172f)
