+++
title = "Bölüm 012 - Dinozorlar Paket Avında! Paket Cehennemine Hoş Geldiniz"
date = "2026-04-19T10:00:00+03:00"
description = "Modern yazılımcının görünmez kâbusu Dependency Hell! NPM'de 3.1 milyon paket, Axios saldırısı, 'everything' paketinin absürtlüğü, Shai-Hulud solucanı ve Notepad++ riski — paket cehennemine hoş geldiniz."
youtube_url = "https://youtu.be/N_mIqIcfMoQ"
youtube_id = "N_mIqIcfMoQ"
duration = "31:20"
tags = ["dependency hell", "paket cehennemi", "npm", "nuget", "axios", "package manager", "supply chain attack", "yazılım güvenliği", "dependabot", "shai-hulud", "open source", "javascript", "node.js"]
notebooklm_url = "https://notebooklm.google.com/notebook/dcb9a3a5-8d23-43ea-95d7-43e9c94d406d"
draft = false
+++

## Özet

Serinin 12. bölümünde modern yazılımcının görünmez ama kaçınılmaz kâbusunu masaya yatırdık: **Dependency Hell**. NPM'de 3.1 milyon paket, NuGet'te 895 milyar indirme — kullandığımız her şey aslında başkalarının kodlarından örülü. "everything" paketinin absürt hikayesinden Axios'un haftada 100 milyonluk indirmesine, Shai-Hulud solucanından Notepad++ olayına kadar paket dünyasının iyi, kötü ve çirkin yönlerini konuştuk. Sonuç: kaçış yok, ama strateji ile hayatta kalınabilir.

## Video

{{< youtube N_mIqIcfMoQ >}}

## Konular

- Paket yöneticileri neden hayatımızın ayrılmaz parçası oldu?
- Rakamlarla paket dünyası: NPM, NuGet, Crates, PIP, Gem
- 3.1 milyon paket, 17 milyon developer: NPM ekosisteminin büyüklüğü
- "everything" paketi: Tek `npm install` ile diskinizi doldurma sanatı
- Versiyon çakışmaları ve Dependency Hell'in doğuşu (Axios 1.0 vs 1.1)
- Linux paket yöneticileri ve App Store benzetmesi
- Axios güvenlik zafiyeti ve 2025-2026 saldırı dalgası
- Qix vakası ve maintainer hesaplarının ele geçirilmesi
- Shai-Hulud: NPM'in kendi kendine yayılan ilk solucanı
- Yapay zekanın iki yüzü: Saldırgan kodu yazmak, sorgulamayı azaltmak
- Dependabot, CVE bültenleri ve PR otomasyonu
- "Bir versiyon geriden gitme" stratejisi
- Notepad++ olayı: Risk artık son kullanıcıya kadar uzanıyor
- ThoughtWorks Tech Radar: Endüstriyel ispat aramak
- GitHub Actions ve `pull_request_target` tehlikesi
- Cehennemden çıkış stratejileri ve `package-lock.json`'ın savunma değeri

## Detaylı İnceleme

### Paket Cehennemine Hoş Geldiniz: Modern Yazılım Dünyasının Görünmez Tehlikeleri

#### 1. Giriş: Görünmez Bağlılıklar ve Modern Yazılımcının Merakı

Modern yazılım geliştirme dünyasında artık hiçbirimiz sıfırdan başlamıyoruz. DKU'nun bu bölümünde masaya yatırdığımız o acı gerçekle yüzleşelim: Bugün kod yazmak, aslında devasa bir "başkalarının kodları" yığınının üzerine ince bir cila çekmekten ibaret.

Peki, hiç kendinize sordunuz mu; sadece üç satır mantıksal kod yazıp derleme tuşuna bastığınızda, o devasa `node_modules` klasörü nasıl oluyor da megabaytlarca, hatta bazen gigabaytlarca yer kaplıyor? İşte bu, **Dependency Hell** (Bağımlılık Cehennemi) dediğimiz görünmez ve kaotik ağın ilk katmanı. Modern bir yazılımcı için merak, artık sadece algoritma kurmak değil; "Bu kodun içine benden habersiz kimler, neler sızdırdı?" sorusunu soracak siber-farkındalığa sahip olmaktır.

#### 2. "Everything" Paketi ve Bağımlılık Şişkinliği

NPM ekosistemindeki paket sayısı 3.1 milyonu aşmış durumda ve topluluk adeta "yürü ya kulum" diyerek bu sayıları her geçen gün katlıyor. Ancak bu hız, beraberinde **bloatware** dediğimiz kontrolsüz bir şişkinliği getirdi. Bölümde bahsettiğimiz "everything" paketi vakası bunun en trajikomik örneği: Bir paketi merak edip indirdiğinizde, alt bağımlılıkların ucu kaçıyor ve farkında olmadan NPM'in neredeyse tamamını diskinize indirirken buluyorsunuz kendinizi.

Bu devasa ekosistemin büyüklüğünü şu rakamlarla bir perspektife oturtalım:

| Platform | Paket Sayısı | Toplam / Haftalık İndirme Örneği |
| -------- | ------------ | -------------------------------- |
| NPM | 3.1 Milyon+ | Axios: Haftalık 100 Milyon+ |
| NuGet | 500 Bin+ | 895 Milyar+ (Toplam İndirme) |
| NuGet (Newtonsoft.Json) | — | 284 Milyon İndirme (tek paket) |

> "Sorgulamadan paketler alıp kullanıyoruz... 'Bu paketin gerçekten bu kadar alt bağımlılığa ihtiyacı var mı?' diye durup bir sormamız lazım."

#### 3. Güven Paradoksu ve Maintainer'ların Hedef Alınması

Yazılımcılar olarak bizler, haftalık milyonlarca kez indirilen paketlere sarsılmaz bir güven duyuyoruz. Ancak Eylül 2025'te yaşanan **Qix vakası**, bu güvenin ne kadar kırılgan olduğunu gösterdi. `chalk` ve `color-convert` gibi temel kütüphanelerin maintainer'ı olan Qix'in hesabı, sahte bir "2FA reset" oltalama (phishing) e-postasıyla ele geçirildi.

İşin korkutucu tarafı şu: Qix, bu paketleri NPM'in en popüler ismi olan Sindre Sorhus ile birlikte yönetiyordu. Saldırganlar Qix'in hesabını ele geçirerek, haftalık 2-3 milyar indirmeye sahip bir "Blast Radius"a (etki alanı) hükmetme şansı buldular. Maintainer'ın stresli bir anında yaptığı tek bir hata, tüm küresel yazılım tedarik zincirini felç etmeye yetiyor.

#### 4. Versiyonlama Stratejisi: En Yeni Her Zaman En İyisi mi?

Yazılım dünyasında "en güncel olan en iyisidir" miti, güvenlik söz konusu olduğunda tehlikeli bir yanılgıya dönüşebilir. Bölümde önerdiğimiz **"bir versiyon geriden takip etme"** stratejisi, aslında modern bir hayatta kalma rehberidir.

Bunun en taze örneği 31 Mart 2026 tarihli **Axios 1.14.1 vakasıdır**. Kuzey Kore bağlantılı UNC1069 grubu, Axios'un maintainer hesabını ele geçirerek paketin içine `plain-crypto-js` adlı bir backdoor yerleştirdi. Bu güncellemeyi "cutting edge" olma arzusuyla anında yapanlar, sistemlerine Windows, macOS ve Linux'ta çalışan WAVESHAPER.V2 zararlısını buyur ettiler. Temkinli davranıp güncellemeyi bekletenler ise bu felaketi sadece bir haber metni olarak okumakla yetindiler.

#### 5. Derleme Ortamlarının Silahlandırılması

Saldırganlar artık sadece koda değil, o kodun paketlendiği build süreçlerine, yani mutfağa sızıyor. **Ultralytics** ve **s1ngularity (Nx)** vakaları, GitHub Actions üzerindeki "script injection" açıklarının ne kadar ölümcül olabileceğini gösterdi.

Teknik detayda yatan canavar şu: `pull_request_target` trigger'ı. Temizlenmemiş bir Pull Request başlığı, bu trigger ile birleştiğinde saldırgana write yetkili bir `GITHUB_TOKEN` teslim ediyor. Saldırganlar bu yetkiyle build sürecine sızıp, terminalinize `sudo shutdown -h 0` gibi şaka görünümlü ama sistemi kilitleyen payload'lar bırakabiliyor.

Daha da fenası, Eylül 2025'te ortaya çıkan **Shai-Hulud solucanı**. Bu, NPM ekosistemindeki ilk başarılı kendi kendine yayılan (self-propagating) worm saldırısıdır. Shai-Hulud sadece bir secret stealer değil; ele geçirdiği NPM token'larını kullanarak kurbanın erişimi olan tüm paketlerin zararlı versiyonlarını otomatik olarak yayınlayan bir "paket-zehirleme makinesi"dir. Bir sabah uyandığınızda tüm private repolarınızın 'public' olduğunu hayal edin — Shai-Hulud tam olarak bu.

#### 6. Yapay Zeka: Saldırganın Yeni Sağ Kolu

Yapay zeka sadece kod yazmamıza yardım etmiyor, saldırganların keşif (reconnaissance) sürecini de otomatize ediyor. s1ngularity vakasında gördüğümüz üzere, saldırganlar Claude, Gemini ve Q gibi developer makinesinde kurulu AI CLI araçlarını birer silah olarak kullanıyor.

`--dangerously-skip-permissions` veya `--yolo` gibi bayraklarla AI araçlarını manipüle eden zararlılar, dosya sistemindeki hassas bilgileri, SSH key'lerini ve cüzdanları saniyeler içinde tarayabiliyor. Kodun artık insanlar tarafından değil, AI tarafından üretilip (genelde denetlenmeden) yayına alındığı bu düzende, "nasıl olsa AI halletti" diyerek sorgulama seviyemizi düşürmek, cehennemin kapılarını sonuna kadar aralamaktır.

#### 7. Sonuç: Cehennemden Çıkış Stratejisi

Paket cehenneminde yanmamak için "ayağımızı yorganımıza göre uzatmak" şart. Somut bir stratejiyle hareket etmeliyiz:

1. **Versiyon Sabitleme (Pinning):** `package-lock.json` sadece bir dosya değil, bir savunma hattıdır.
2. **Otomasyonu Denetleyin:** Dependabot'un her açtığı PR'ı sorgusuz sualsiz merge etmeyin.
3. **İç Framework'ler:** Kritik iş mantığı için dış paket bağımlılığını minimize edip kendi iç kütüphanelerinizi geliştirin.
4. **Endüstriyel Standartlar:** Açık kaynak dünyasındaki başıboş özgürlüğü, otomotivdeki ISO standartları gibi disipline edecek yaklaşımları (Wiz veya Socket gibi araçlarla) benimseyin.

Haftada 100 milyon kez indirilen bir paketin bile bir sabah "zehirli" uyanabildiği, Shai-Hulud gibi solucanların repoları otomatik olarak istila ettiği bir dünyada, gerçekten hangi koda güvenebiliriz? Belki de tek güvenli yol, her bağımlılığa bir gün sizi satacakmış gibi şüpheyle bakmaktır.

## İnfografik

{{< infografik src="infografik.webp" alt="Dinozorlar Paket Avında - Bölüm 12 İnfografik" >}}

## Sesli Özetler

### Kısa Özet

{{< audio src="https://media.dinozorlarlakafautuleme.com/bolum-012/audio-brief.m4a" >}}

### Derin Dalış

{{< audio src="https://media.dinozorlarlakafautuleme.com/bolum-012/audio-deepdive.m4a" >}}

## Kaynaklar

- Bu bölümün içeriğini [NotebookLM](https://notebooklm.google.com/notebook/dcb9a3a5-8d23-43ea-95d7-43e9c94d406d) üzerinden de inceleyebilirsiniz.
