+++
title = "Bölüm 019 - Bedava Dönem Bitti: Yapay Zeka Ekonomisi Nereye Koşuyor?"
date = "2026-06-28T10:00:00+03:00"
description = "Bedava ve ucuz yapay zeka dönemi kapanıyor. Fiyatlar neden artıyor, token limitleri neyi değiştiriyor, çip krizi nereye varıyor? Anthropic'in kâra geçişinden lokal-cloud dengesine, yapay zeka ekonomisinin nereye koştuğunu masaya yatırdık."
youtube_url = "https://youtu.be/g_0EdwEUdoE"
youtube_id = "g_0EdwEUdoE"
duration = "33:19"
tags = ["yapay zeka", "yz", "yapay zeka ekonomisi", "ai economy", "token", "token limiti", "anthropic", "openai", "sam altman", "çip krizi", "ram", "data center", "lokal model", "rag", "mcp", "türkçe podcast"]
notebooklm_url = "https://notebooklm.google.com/notebook/f7ed580a-d84b-40c0-9971-b053bd8283de"
draft = false
+++

## Özet

Yapay zeka araçlarının ilk çıktığı dönemdeki o "her şey bedava ya da sembolik ücretli" günler hızla geride kalıyor. 19. bölümde bu işin ekonomisini konuştuk: bugüne kadar yatırım parasıyla (`VC`) sübvanse edilen pazar, artık maliyetin gerçek fiyata yansıdığı bir döneme geçiyor. Anthropic ilk kez kâr açıkladı, halka arz konuşuluyor, çip ve `RAM` krizi konsol fiyatlarına kadar uzanıyor, token limitleri "önce düşün" dedirtiyor. Peki bu yeni ekonomi nereye koşuyor — kalıcı bir düzen mi, yoksa kendi içinde dönen bir kısır döngü mü? İki dinozor yazılımcı olarak, kullanan taraftan cebimize ve işimize neyin dokunduğunu konuştuk.

## Video

{{< youtube g_0EdwEUdoE >}}

## Konular

- Bedava ve ucuz yapay zeka döneminin sonu
- Alıştırma dönemi: maliyetin altına ürün sunma stratejisi
- Anthropic'in ilk kez kâra geçmesi ve halka arz beklentisi
- OpenAI'ın kurumsal segmente yönelişi
- Nvidia–OpenAI–Oracle: dairesel yatırım ve "gerçek para nerede?"
- Yapay zeka balon mu, kalıcı bir ekonomi mi?
- `ROI` ve ekonomik sürdürülebilirlik tartışması
- Çip, `RAM` ve `NAND` krizi; Xbox/PlayStation fiyatlarına etkisi
- `Data Center` maliyeti ve enerji darboğazı
- Token limitleri ve 20 dolarlık abonelik deneyimi
- Lokal mı `Cloud` mu? Hibrit modeller ve `SLM`'ler
- 192 GB `RAM` bariyeri ve Apple'ın lokal model çabaları
- Gizlilik, veri egemenliği ve pil ömrü dengesi
- Sam Altman: yapay zeka elektrik/su gibi bir kamu hizmeti mi?
- Token optimizasyonu yeni bir uzmanlık alanı haline geliyor
- Yeni mühendislik katmanı: `MCP`, `RAG`, `Context Caching`, `Guardrails`
- Ölü internet ve ölü ekonomi teorisi; Matrix göndermesi

## Detaylı İnceleme

Yapay zekanın "bedava büfe" dönemi resmen kapanıyor. Bugüne kadar gördüğümüz düşük fiyatlar, şirketlerin kullanıcıyı ekosisteme alıştırmak için maliyetin çok altında ürün sunmasıydı. Şimdi odak kullanıcı sayısından yatırım getirisine (`ROI`) kayıyor. Bu bir çöküş değil, fiyatların gerçeğe oturduğu bir düzeltme. Aşağıda bölümde konuştuğumuz altı başlığı topladık.

### 1. Alıştırma Dönemi Kapandı: "Ederi Bu Değildi"

Şirketlerin kullanıcıları alıştırmak için cepten yediği dönem bitti. Anthropic'in ilk kez kâr açıklaması ve OpenAI'ın kurumsal segmente yönelişi, artık meselenin sadece kullanıcı sayısı değil yatırım getirisi olduğunu gösteriyor. Bugün ödediğimiz 20 dolarlık abonelikler, sağladıkları değerin epey altında fiyatlanmıştı; pazar şimdi bu makası kapatıyor.

Burak'ın bölümdeki ifadesiyle: "Hani ederi bu değil aslında. 20 dolarlık bir şey yaptırıyorsun ama o aslında bayağı bir senin için bir şey yapıyor." Yapay zekanın kattığı değer ile fiyatı arasındaki açık tam da burada.

### 2. Çip Krizi ve "Ağır Sanayi" Bariyeri: Fiyatlar Neden Düşmüyor?

Maliyetlerin sadece yazılımsal optimizasyonla düşeceğini beklemek yanıltıcı olabilir. Karşımızda ciddi bir donanım problemi var: `NAND` diskler, `RAM` ve devasa `Data Center`'ların fiziksel sınırları. Üretim yetersizliği nedeniyle bu donanımların fiyatları kolay kolay inmiyor. Kriz o kadar geniş ki, yapay zeka veri merkezlerinin iştahı yüzünden Xbox ve PlayStation gibi konsollar bile eski fiyat seviyelerinde tutunamıyor. Enerji ve donanım darboğazı, yapay zekayı işletmesi en maliyetli kalemlerden biri yapıyor.

### 3. Yapay Zeka Yeni "Elektrik ve Su" mu?

Sam Altman'ın BlackRock'ta dile getirdiği vizyon, yapay zekayı bir yazılım ürünü olmaktan çıkarıp elektrik ya da su gibi bir kamu hizmetine dönüştürmek üzerine. Tıpkı internet olmadan bugün pek çok temel hizmete erişmenin zorlaştığı gibi, yapay zeka da abonelikle alınan bir altyapıya doğru gidiyor. Bu da bizi büyük ölçüde bulut tarafındaki "şebekeye" bağımlı kılıyor; yapay zeka bir lüks olmaktan çıkıp gündelik bir gider kalemine dönüşüyor.

### 4. "Lokal Yapay Zeka" Hayali ve 192 GB RAM Bariyeri

Kendi makinesinde model çalıştırma isteği sadece maliyetle değil, gizlilik ve veri egemenliğiyle de ilgili. Ama önünde ciddi bir teknik engel var: matris hesaplamaları ve parametre sayıları. En güçlü modelleri lokalde çalıştırmak bugün 192 GB `RAM` gibi uç donanımlar istiyor. Apple'ın hibrit (lokal + bulut) yaklaşımı bu açıdan kıymetli; yine de yoğun işlem yükünün pil ömrünü hızla tüketmesi, orta vadede bizi cloud tarafına yaslanmak zorunda bırakıyor.

### 5. Roller Değişiyor: Artık Yapay Zeka Bizim Disiplinimizi Şekillendiriyor

Bölümün belki en çarpıcı tarafı bu: token tasarrufu ve maliyet baskısı yüzünden kullanıcılar daha derli toplu, daha anlaşılır komutlar üretmeye kendilerini eğitiyor. Yani biz yapay zekayı kullanırken, yapay zeka da bizim çalışma disiplinimizi optimize etmeye başlıyor. Bu yeni düzende verini ve istemlerini optimize etmek, artık teknik bir tercih değil ekonomik bir gereklilik.

### 6. Yeni Bir Mühendislik Katmanı ve "Ölü Ekonomi" Riski

Yapay zeka artık tek başına bir araç değil, bir ekosistem. Sadece istem (prompt) yazmıyoruz; `MCP` (Model Context Protocol), `RAG` (Retrieval-Augmented Generation), `Context Caching`, `Guardrails` ve `Red Teaming` gibi başlıklar üzerinden yeni bir mühendislik mimarisi doğuyor. IBM gibi devlerin bu alanlara yatırımı, işin kalıcılığına işaret ediyor.

Madalyonun öbür yüzünde ise bir risk duruyor: Ölü Ekonomi Teorisi. Yapay zekanın ürettiği içeriğin ve finansal döngülerin bir kısır döngüye girip sistemi kendi içinde boğma ihtimali, iyimser senaryonun tam karşısında bir soru işareti. Bu ekonomi yeni iş alanları açarak mı büyüyecek, yoksa kendi ürettiği verinin içinde durgunlaşacak mı? Bölümün sonunda Matrix'e bir selam gönderip sorduk: bu şebekeyi doğru yönetebilirsek mimarı, yönetemezsek sistemi besleyen birer "pil" olabiliriz.

## İnfografik

{{< infografik src="infografik.webp" alt="Yapay Zeka Ekonomisi Nereye Koşuyor? - İnfografik" >}}

## Sesli Özetler

### Kısa Özet

{{< audio src="https://media.dinozorlarlakafautuleme.com/bolum-019/audio-brief.m4a" >}}

### Detaylı İnceleme

{{< audio src="https://media.dinozorlarlakafautuleme.com/bolum-019/audio-deepdive.m4a" >}}

## Kaynaklar

- [NotebookLM Notebook](https://notebooklm.google.com/notebook/f7ed580a-d84b-40c0-9971-b053bd8283de)
