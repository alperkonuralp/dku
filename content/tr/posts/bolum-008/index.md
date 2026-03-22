+++
title = "Bölüm 008 - Yapay Zeka Araçlarında CLI mı, Editör mü?"
date = "2026-03-01"
description = "Yapay zeka araçlarını kullanırken editör mü yoksa CLI mı tercih edilmeli? Alper CLI tarafında, Burak editör tarafında. İki dinozorun samimi tartışması."
youtube_url = "https://youtu.be/uToDVhVwktU"
youtube_id = "uToDVhVwktU"
duration = "28:14"
tags = ["CLI", "editör", "Claude Code", "VS Code", "Copilot", "Cursor", "Windsurf", "MCP", "agent", "yapay zeka araçları"]
notebooklm_url = "https://notebooklm.google.com/notebook/9bb8cd8a-6b64-4a22-a835-92f60209b8ec"
draft = false
+++

## Özet

Yapay zeka araçlarını kullanırken editör mü yoksa CLI mı tercih edilmeli? Alper CLI tarafında (Claude Code), Burak editör tarafında (VS Code + Copilot). DOS günlerinden bugüne siyah ekran kültüründen, agent sistemleri ve paralel çalışmaya, MCP server entegrasyonundan token ekonomisine kadar her iki yaklaşımın güçlü ve zayıf yanlarını tartıştık. Sonuç: Konfor alanınızdan çıkın!

## Video

{{< youtube uToDVhVwktU >}}

## Konular

- VS Code + Copilot vs Claude Code CLI karşılaştırması
- Terminal sevgisi: DOS günlerinden bugüne siyah ekran kültürü
- Agent'lar, multi-agent sistemler ve paralel çalışma
- Doğru dokümantasyon ve prompt hazırlamanın önemi
- Cursor, Windsurf, Anti-Gravity: VS Code alternatifleri
- Plugin ekosistemi ve editör bağımlılığı sorunu
- Kendi CLI araçlarını yazma ve MCP server entegrasyonu
- Aynı anda birden fazla agent çalıştırmanın token maliyeti
- Hangi profil CLI'ya, hangi profil editöre gitsin?

## Detaylı İnceleme

### AI Çağında Yazılımcıların Yeni İkilemi: CLI mı, Editör mü?

#### Giriş: Terminalin Dönüşü ve Modern Yazılımcı İkilemi

Yazılım dünyasında "dinozor" tecrübesine sahip olanlar — Windows 3.1'in siyah ekranlarından ve saf Linux terminallerinden gelenler — için komut satırı her zaman güvenli bir limandı. Modern IDE'lerin sunduğu konfor terminali uzun süre gölgede bıraktı. Bugün yapay zeka araçlarının yükselişiyle birlikte bu eski dost, çok daha güçlü bir şekilde geri döndü. Artık mesele sadece bir arayüz tercihi değil; AI araçlarını CLI üzerinden mi yoksa görsel bir editör içinden mi kullanmanın daha verimli olduğu tartışmasıdır.

#### Hız ve Verimlilik: CLI Neden Gizli Bir Silah Olabilir?

Claude Code gibi modern CLI araçları, terminali sadece bir metin giriş alanı olmaktan çıkarıp otonom bir geliştirme merkezine dönüştürüyor. Görsel render yükünün olmaması sayesinde özellikle çoklu dosya işlemlerinde editörlerden çok daha hızlı bir deneyim sunuyor.

Asıl fark **"Agent Mode"** yeteneklerinde ortaya çıkıyor. Modern CLI ajanları artık sadece kod yazmıyor; üzerinde çalıştığı işletim sistemini tanıyor, hatalı bir dizine girdiğinde kendi yolunu düzeltebiliyor ve otonom olarak test koşturabiliyor.

> "Eğer kodun kendisine dokunmak istemiyorsanız, CLI tarafı çok daha basit ve hızlı bir çözüm sunuyor. CLI'ın sonuçları çok daha hızlı getirdiğini ve birçok dosyayı çok daha süratli oluşturduğunu düşünüyorum."

#### Editörlerin Gücü: Kontrol, Görselleştirme ve Eklenti Tuzağı

Yazılımcıların yaklaşık %80'i hâlâ görsel kontrolü elinde tutabildiği VS Code gibi editörleri tercih ediyor. "Gör-ve-onayla" (diff) operasyonları, AI'nın önerdiği değişiklikleri anlık olarak takip etmek isteyenler için büyük bir güven kaynağı.

Ancak kritik bir **"eklenti tuzağı"** söz konusu. Microsoft VS Code altyapısını açık kaynaklı hale getirince Cursor, Windsurf ve Anti-Gravity gibi güçlü alternatifler doğdu. Fakat kritik Docker yönetim eklentisi gibi bazı araçlar sadece orijinal VS Code üzerinde çalışabiliyor — en yeni AI özelliklerini kullanmak için alternatif editörlere geçen yazılımcılar, kendilerini bir anda temel eklentilerden mahrum kalmış bulabiliyorlar.

#### Stratejik Bir Kayma: "Beş Ölç, Bir Biç"

Modern yazılım mimarisinde AI kullanımı, doğrudan kod yazımına atlamaktan ziyade stratejik bir hazırlık aşamasını gerektiriyor. Dil modelleri, bilinen endüstriyel standartlar üzerinde çalıştığında performansları %100'e kadar çıkabiliyor. Bu nedenle, işe doğrudan CLI veya IDE üzerinden başlamak yerine, Claude Desktop veya tarayıcı tabanlı arayüzlerle dökümanları olgunlaştırmak, ardından bu standartlaşmış dökümanları kod geliştirme ajanlarına teslim etmek hata payını minimize ediyor.

#### Ajanların Yükselişi: MCP, Token Ekonomisi ve Zaman-Maliyet Dengesi

AI kullanımı, basit bir sohbetten artık kendi kendine hata düzelten ajan sistemlerine evrildi. Bu evrimin en dikkat çekici parçası **MCP (Model Context Protocol)** sunucularıdır. Artık kendi alanımıza özgü CLI araçları yazıp bunları MCP üzerinden ajanlara birer "yetenek" olarak tanımlayabiliyoruz.

Bir geliştirici ajanı kod yazarken, bir inceleme ajanının onu denetlediği paralel akışlar, normalde 1 saat sürecek bir işi 10 dakikada bitirebiliyor. Teknik olarak bu, zamanı token maliyetiyle satın almak demektir — ancak bir mimar için bu, projenin time-to-market süresini kısaltan bilinçli bir yatırımdır.

#### Sonuç: Konfor Alanınızdan Çıkın

CLI veya editör seçimi sadece bir araç tercihi değil, geliştirici deneyimini yönetme biçimidir. Editör tutkunuysanız Claude Code gibi CLI araçlarını deneyin; sadece terminaldeyseniz Cursor gibi araçların görsel diff avantajlarını inceleyin.

**Bir aracı sadece alışkanlık olduğu için mi kullanıyorsunuz, yoksa o araç gerçekten projenizin mimari ihtiyaçları için en verimli çözümü mü sunuyor?**

## İnfografik

{{< infografik src="infografik.webp" alt="Yapay Zeka Geliştirme Araçları: CLI mı, Editör mü?" >}}

## Sesli Özetler

### Kısa Özet
{{< audio src="https://media.dinozorlarlakafautuleme.com/bolum-008/audio-brief.m4a" >}}

### Derin Dalış
{{< audio src="https://media.dinozorlarlakafautuleme.com/bolum-008/audio-deepdive.m4a" >}}

---

📓 [Bu bölümün NotebookLM çalışma alanını inceleyin](https://notebooklm.google.com/notebook/9bb8cd8a-6b64-4a22-a835-92f60209b8ec)
