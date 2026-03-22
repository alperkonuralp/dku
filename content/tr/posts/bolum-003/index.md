+++
title = "Bölüm 003 - Siber Güvenlik: Tehditler ve Korunma"
date = "2026-01-10"
description = "Siber güvenlik tehditleri yapay zeka ile birleşince ne tür risklerle karşılaşıyoruz? En zayıf halka her zaman insan faktörü. Sosyal mühendislikten veri mahremiyetine kadar konuştuk."
youtube_url = "https://youtu.be/N2xkyUYKhp0"
youtube_id = "N2xkyUYKhp0"
duration = "44:20"
tags = ["siber güvenlik", "sosyal mühendislik", "yapay zeka güvenlik", "veri mahremiyeti", "phishing", "IoT", "Security by Design", "DDoS"]
notebooklm_url = "https://notebooklm.google.com/notebook/daf15f54-143a-4931-833a-a3dbf05de767"
draft = false
+++

## Özet

Siber güvenlik tehditleri yapay zeka ile birleşince karşımıza çıkan riskleri konuştuk. Şifreleri kırmak yerine insanları kandırmak artık çok daha ucuz ve etkili. Sosyal mühendislikten ücretsiz yapay zeka modellerinin veri gizliliği risklerine, Notepad++ tedarik zinciri saldırısından şirket içi tehdit algısına kadar hem bireysel hem kurumsal güvenlik perspektifinden 5 sarsıcı gerçeği masaya yatırdık.

## Video

{{< youtube N2xkyUYKhp0 >}}

## Konular

- Siber güvenlikte en zayıf halka: İnsan faktörü ve sosyal mühendislik
- Çevrimiçiyseniz asla %100 güvende değilsiniz — IoT cihazları ve DDoS
- Yapay zeka ve "bedava" tuzağı — ücretsiz modellere verdiğiniz veriler nereye gidiyor?
- Notepad++ sertifika sızıntısı ve tedarik zinciri saldırıları
- Şirket içi tehdit: "Her şeye yetkili" kullanıcı riski
- Security by Design — güvenliği işin sonuna bırakmayın
- Hükümetler ve siber saldırılar

## Detaylı İnceleme

### Şifreler Değil, İnsanlar Kırılır: Siber Güvenliğin Karanlık Yüzü ve Yapay Zeka Hakkında 5 Sarsıcı Gerçek

#### Giriş: Dijital Dünyanın "Açık Kapı" Paradoksu

Garip bir ironinin içinde yaşıyoruz. Sabah uyanır uyanmaz Instagram'da çocuğumuzun fotoğrafını paylaşıp, öğlen yediğimiz yemeği tüm dünyaya duyurup, akşam da "Verilerim çalınmış, bu nasıl olur?" diye şaşırıyoruz. Her yerimiz yazılım, her şeyimiz internete bağlı; ama kapıyı ardına kadar açık bırakıp içeri hırsız girince hayret eden ev sahibi gibiyiz. Bugün siber güvenlik, sadece şirketlerin sistem odalarına hapsedilecek bir konu değil; cebinizdeki telefondan evinizdeki bebek kamerasına kadar hepimizin en büyük zafiyeti.

#### En Zayıf Halka: Bilgisayarınız Değil, Sizsiniz

Hackerlar artık o filmlerdeki gibi karmaşık şifre algoritmalarıyla boğuşmuyor. Neden uğraşsınlar ki? Bir şifreyi kırmak için binlerce dolar harcamak yerine, o şifreyi giren parmağın sahibini kandırmak çok daha ucuz ve etkili. Biz buna "Sosyal Mühendislik" diyoruz; yani insanı "kırma" sanatı.

İstediğiniz kadar gelişmiş firewall cihazlarınız olsun, içeriye sızmak isteyen birinin tek ihtiyacı olan şey, sizin merakınız veya yardımseverliğiniz.

> "Çünkü biz zaten kandırılabilir durumdaydık ki biliyorsunuz güvenlikte en zayıf nokta insandır."

#### Çevrimiçiyseniz, Asla %100 Güvende Değilsiniz

"Gerçekten güvenli bilgisayar, internete bağlı olmayan bilgisayardır." Ama artık o bile tam olarak doğru değil. Amerika, İran'ın nükleer tesislerini internet üzerinden değil, içeriye sokulan USB'ler üzerinden vurdu. Fiziksel olarak dış dünyaya kapalı bir sistemi bile insan zafiyetiyle çökertebilirsiniz.

Eğer cihazınız online ise, artık sadece bir kullanıcı değil, potansiyel bir askersiniz. Bugün dünyada milyonlarca IP kamera, router ve IoT cihazı hackerlar tarafından köleleştirilmiş durumda. Siz evde çayınızı içerken, salonunuzdaki kamera sizin haberiniz olmadan devasa bir DDoS saldırısının parçası olarak bir dünya devini çökertmeye çalışıyor olabilir.

İnternete bir veri yüklerken şunu unutmayın: O bilgiyi sokağın ortasında avaz avaz bağırmakla aynı şeyi yapıyorsunuz.

#### Yapay Zeka ve "Bedava" Tuzağı: Ürün Siz Misiniz?

Yapay zeka modelleriyle dertleşmek, kod yazdırmak veya şirket verilerini analiz ettirmek harika bir lüks gibi görünüyor. Ancak şu kuralı asla unutmayın: **Eğer bir hizmet bedavaysa, ürün sizsinizdir.**

ChatGPT, Gemini veya Claude gibi modellerin ücretsiz versiyonlarına yazdığınız her satır, o modellerin eğitimi için kullanılan birer yakıta dönüşüyor. Bugün yapay zekaya sorduğunuz o kritik ticari sır veya kurumsal veri, yarın başka bir kullanıcının sorusuna verilen cevap olarak karşınıza çıkabilir.

Şirketler için kurumsal, veriyi dışarı sızdırmayacağını taahhüt eden lisanslı modeller artık bir tercih değil, zorunluluktur.

#### Güvenilir Kaleler Bile Kuşatılabilir: Tedarik Zinciri Saldırıları

Hepimizin elinin altında olan Notepad++ gibi araçlar bile birer silaha dönüşebilir. Notepad++'ın deployment sertifikasının sızdırılması olayını hatırlayın; hackerlar paketi değiştirip içine zararlı kodlar yerleştirdiler. Eğer o riskli sürümlerden birine denk geldiyseniz, sadece "güncelle" demek yetmez — uygulamayı tamamen kaldırıp temiz kurulum yapmanız gerekir.

Aynı tehlike NPM paketleri ve Log4j gibi kütüphaneler için de geçerli. Bu yüzden **"Security by Design"** bizim amentümüz olmalı. Güvenliği işin sonuna bırakırsanız, o bina en ufak sarsıntıda başınıza yıkılır.

#### İçerideki Düşman: Şirket İçi Tehdit Algısı

Tehlike her zaman dışarıdaki o kapüşonlu hacker değildir. En büyük tehdit, içerideki "her şeye yetkili" kullanıcılardır. Bir hackerın şirket networküne sızması için tek bir çalışanı, tek bir VPN şifresini ele geçirmesi yeterlidir.

Çözüm; **"Minimum Yetki" (Least Privilege)** prensibini uygulamaktır. Bir sistemi kurarken her şeyi "kapalı" olarak başlatmalı ve sadece ihtiyaç duyulan kadar yetki tanımlamalısınız. Herkesin admin olduğu bir yapı, felakete davetiye çıkarır.

#### Sonuç: Dijital Hijyen

Siber güvenlik bir varış noktası değil, 7/24 süren bir operasyondur. Karşı taraf da en az bizim kadar profesyonel ve onlar mesai saati gözetmiyorlar. Bizim yapabileceğimiz en iyi şey, bu bitmek bilmeyen savaşta dijital hijyenimize dikkat etmek ve "bana bir şey olmaz" kibrinden kurtulmaktır.

Şimdi kendinize şu soruyu sorun: Bugün internete yüklediğiniz o fotoğraf veya yapay zekaya sorduğunuz o "masum" soru, yarın karşınıza kimin elinde bir anahtar olarak çıkacak?

## İnfografikler

{{< infografik src="infografik.webp" alt="Siber Güvenlik Rehberi: Modern Tehditler ve Korunma Yolları" >}}

{{< infografik src="infografik2.webp" alt="Siber Güvenlik: Tehditler, Yanılgılar ve Korunma Rehberi" >}}

## Sesli Özetler

### Kısa Özet
{{< audio src="https://media.dinozorlarlakafautuleme.com/bolum-003/audio-brief.m4a" >}}

### Derin Dalış
{{< audio src="https://media.dinozorlarlakafautuleme.com/bolum-003/audio-deepdive.m4a" >}}

---

📓 [Bu bölümün NotebookLM çalışma alanını inceleyin](https://notebooklm.google.com/notebook/daf15f54-143a-4931-833a-a3dbf05de767)
