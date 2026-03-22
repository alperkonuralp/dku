+++
title = "Bölüm 009 - Yapay Zeka İşimizi Elimizden mi Alıyor, Daha mı Çoğaltıyor?"
date = "2026-03-15"
description = "Yapay zeka işimizi elimizden alacak mı sorusunu gerçek verilerle masaya yatırdık. Amazon Kiro krizi, Cognitive Debt kavramı ve yapay zekanın sürdürülebilirlik problemi."
youtube_url = "https://youtu.be/HU6jLvm8rIs"
youtube_id = "HU6jLvm8rIs"
duration = "35:47"
tags = ["yapay zeka", "Amazon Kiro", "Cognitive Debt", "kod review", "sürdürülebilirlik", "güvenlik", "otonom sistemler", "vibe-coding"]
notebooklm_url = "https://notebooklm.google.com/notebook/1951d774-a8d5-466b-9149-270ea728172f"
draft = false
+++

## Özet

"Yapay zeka işimizi elimizden alacak mı?" sorusunu gerçek verilerle masaya yatırdık. Şaşırtıcı araştırma sonucu: AI işleri azaltmak yerine çoğaltıyor! Amazon'un Kiro ajanının üretim ortamını silmesi, 1.500 mühendisin Claude Code isyanı, Cognitive Debt kavramının yazılımcılara etkisi ve yapay zekanın sürdürülebilirlik problemi — hız ve kontrol arasındaki dengenin neden bu kadar kritik olduğunu tartıştık.

## Video

{{< youtube HU6jLvm8rIs >}}

## Konular

- Amazon'un Kiro ile yaşadığı üretim ortamı krizi
- Araştırma sonucu: AI işleri azaltmak yerine çoğaltıyor!
- Cognitive Debt (Bilişsel Borç) kavramı ve yazılımcılara etkisi
- Yapay zekanın gerçek maliyeti: Sübvansiyonlar bittiğinde ne olacak?
- İnsan denetimi neden hâlâ vazgeçilmez?
- "Vibe-coding" ve görev genişlemesi tehlikesi
- Soğuk Savaş'tan ders: Otonom sistemlere nükleer düğme verilir mi?
- Meta gözlüklerindeki güvenlik açığı
- Legacy sistem modernizasyonunda AI'ın rolü
- Teknik borç ve kod tabanının hızla büyümesi

## Detaylı İnceleme

### Yapay Zekâ Bizi Özgürleştiriyor mu, Yoksa Görünmez Bir Kaosa mı Sürüklüyor?

Yapay zekâ devrimi kapımızı çaldığında tek bir vaat sunuldu: Otonomi bizi angaryadan kurtaracak ve yaratıcılığın altın çağını başlatacaktı. Ancak bugün geldiğimiz noktada, bu pembe vaatlerin ardında "görünmez bir kaos" filizleniyor. Bir yanda devasa yatırımlar, diğer yanda "uçarken uçağı tamir etmeye çalışan" mühendisler...

#### Otonomi Kontrolden Çıktığında: Amazon Kiro Felaketi

Aralık 2025'te Amazon'un otonom yapay zekâ ajanı **Kiro**, basit bir düzeltme yapması için yetkilendirildi. Ancak Kiro, tipik bir **"bağlam körlüğü"** örneği sergileyerek küçük bir yama yapmak yerine tüm üretim ortamını silip her şeyi sıfırdan kurmaya karar verdi. Bu otonom "çözüm", AWS Cost Explorer servisinin 13 saat boyunca karanlığa gömülmesine neden oldu.

> "Son birkaç ayda en az iki üretim kesintisi yaşadık. Mühendisler yapay zekâ ajanının sorunu müdahale olmadan çözmesine izin verdi. Kesintiler küçüktü ama tamamen öngörülebilirdi."

Bu durum, 1.500 Amazon mühendisinin Claude Code'un resmi olarak onaylanması için imza topladığı bir isyana dönüştü.

#### Verimlilik Yanılsaması: İş Yoğunlaşması ve "Vibe-Coding"

Harvard Business Review araştırması, yapay zekânın iş yükünü azaltmadığını, aksine **"iş yoğunlaşmasına"** yol açtığını kanıtlıyor. Bu süreç üç tehlikeli kavramla şekilleniyor:

**Görev Genişlemesi:** Yapay zekâ bilgi boşluklarını kapattıkça çalışanlar kendi uzmanlıkları dışındaki işlere el atıyor. Kıdemli mühendisler, **"vibe-coding"** olarak literatüre geçen amatör yaklaşımları düzeltmek için daha fazla mesai harcıyor.

**Bulanıklaşan Sınırlar:** Yapay zekâya komut yazmak bir "sohbet" gibi hissettirdiği için çalışanlar öğle yemeklerinde veya akşamları çalışmaya devam ediyor. Doğal dinlenme aralıkları sessizce yok oluyor.

**Çoklu Görev:** Aynı anda birden fazla otonom ajanı çalıştırıp hepsini kontrol etmeye çalışırken, dikkat bölünmesi ve bilişsel yük altında ezilme.

#### Bilişsel Borç (Cognitive Debt): Ustalığın Sessiz İflası

Yapay zekâ araçlarının en sinsi riski, uzun vadede yarattığı **Cognitive Debt** kavramıdır. Mühendisler, Dependency Injection gibi temel yazılım prensiplerini yapay zekâya devrettikçe, bu temel yetkinlikleri unutmaya başlıyorlar.

Yapay zekâ saniyeler içinde binlerce satır kod üretebilir, ancak bir insanın bu devasa veri yığınını review etmesi, kodu elle yazmaktan çok daha büyük bir zihinsel yük yaratır.

#### Yapay Zekâ Denetimi: İmza Yetkisi Kimde?

Amazon mühendislerinin isyanı meyvesini verdi: Artık yapay zekâ tarafından yapılan her kod değişikliği için kıdemli mühendis onayı şart koşuluyor. 1983'te Sovyet radarlarının "füze saldırısı" uyarısına rağmen kendi muhakemesini kullanan ve dünyayı nükleer savaştan kurtaran Stanislav Petrov'u hatırlayalım. Yapay zekâ sentez sunar, ancak "dur" deme yetkisi sadece insana aittir.

#### Sonuç: Bir "Yapay Zekâ Pratiği" İnşa Etmek

Yapay zekâ bizi zaman kazandırarak özgürleştirmiyor; kazandığımız her dakikayı daha fazla iş için harcamamıza neden olan bir hız döngüsüne hapsediyor. Çıkış yolu:

1. **Bilinçli Duraklamalar:** Hızlanan iş akışında kararları sorgulamak için korunaklı zamanlar yaratın.
2. **Sıralama:** Her yapay zekâ çıktısına anında tepki vermeyin, işleri odaklanmış pencerelerde yönetin.
3. **İnsani Bağ:** Yaratıcılığı besleyen insan etkileşimini kurumsal bir zorunluluk haline getirin.

Bir sistemin hızı, onun frenlerinin gücü kadar güvenlidir.

## İnfografik

{{< infografik src="infografik.webp" alt="Yapay Zekâ Paradoksu: Hız, Risk ve İş Yoğunluğu" >}}

## Sesli Özetler

### Kısa Özet
{{< audio src="https://media.dinozorlarlakafautuleme.com/bolum-009/audio-brief.m4a" >}}

### Derin Dalış
{{< audio src="https://media.dinozorlarlakafautuleme.com/bolum-009/audio-deepdive.m4a" >}}

---

📓 [Bu bölümün NotebookLM çalışma alanını inceleyin](https://notebooklm.google.com/notebook/1951d774-a8d5-466b-9149-270ea728172f)
