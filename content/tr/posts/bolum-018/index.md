+++
title = "Bölüm 018 - En İyi Programlama Dili Hangisi?"
date = "2026-06-21T10:00:00+03:00"
description = "En iyi programlama dili diye bir şey var mı? Dillerin felsefesinden DNA'sına, thread'lerin doğuşundan yeni nesil dillere; 'birinci'yi seçmek yerine doğru soruyu sormayı konuştuk."
youtube_url = "https://youtu.be/XZRB4LqJouU"
youtube_id = "XZRB4LqJouU"
duration = "34:51"
tags = ["programlama dilleri", "programming languages", "yazılım", "software engineering", "c#", "python", "rust", "zig", "gleam", "thread", "paralel programlama", "nesne yönelimli programlama", "dotnet", "dkü", "en iyi programlama dili"]
notebooklm_url = "https://notebooklm.google.com/notebook/0cec889d-7664-4e34-9a1f-adef22314973"
draft = false
+++

## Özet

Bu bölümde yapay zekadan biraz uzaklaşıp yazılımın köküne döndük ve yıllardır forumları, ofis koridorlarını meşgul eden o soruyu masaya yatırdık: "En iyi programlama dili hangisi?" Cevabı vermeden önce sorunun kendisini sorguladık, çünkü bütün dillere hükmeden tek bir şampiyon yok. Diller birer söz dizimi yığını değil; kendi tarihleri, felsefeleri ve "DNA"larıyla yaşayan ekosistemler. Sonunda vardığımız yer şu: **asıl mesele "en iyi dil" değil, çözmeye çalıştığın problemin felsefesine uygun dili seçebilmek.**

## Video

{{< youtube XZRB4LqJouU >}}

## Konular

- "En iyi programlama dili" diye tek bir şey neden yok?
- Doğru soru: "bu proje için doğru dil hangisi?"
- Yapay zekadan uzaklaşıp yazılımın köküne dönüş
- Her dilin bir felsefesi ve "DNA"sı olması
- Nesne yönelimli paradigmanın kökeni: 1960'lar, Oslo Üniversitesi ve `Simula`
- Simula felsefesi + C'nin derleyicisi = `C++`'ın doğuşu
- Method overloading örneği: teknik kısıt değil, felsefi bir duruş
- "Fan boyluğu" tuzağı ve profesyonel pragmatizm
- Python paradoksu: sintaksını sevmesek de YZ ekosisteminde rakipsiz
- Doğru iş için doğru dil: YZ/veri, paralel işleme, sistem seviyesi
- Donanım evrimi: tek çekirdekten çok çekirdeğe
- "Time slicing"den gerçek paralelliğe: `thread` mantığının doğuşu
- Dil değil ekosistem: standart kütüphanelerin önemi
- Bir dili derinlemesine bilmenin yeni dilleri hızlı öğrenmeye etkisi
- 20+ yıllık `C#`/`.NET` deneyiminin pattern tanımaya katkısı
- Agentic sistemlerin bellek çeşitleri ile insan hafızasının kıyası
- Yeni diller hep çıkacak: `Rust`, `Zig`, `Gleam` ve Stack Overflow anketleri
- Yapay zeka bile sonunda bir dille çalışmak zorunda
- Düşük seviyeye saygı: `C` veya Assembly ile bir pencere çizmeyi denemek

## Detaylı İnceleme

### "Mükemmel Dil" Arayışının Sonu

Her yazılımcının yolun başında sorduğu o kadim soruyla açtık bölümü: "Hangi dili öğrenmeliyim?" ya da onun biraz daha iddialı hali, "En iyi programlama dili hangisi?" Yirmi yılı aşkın süredir bu işin içinde olan iki "dinozor" olarak rahatlıkla söyleyebiliriz ki, bir "birinci" seçme telaşı çoğu zaman yanlış soruyu sorduğumuzun işaretidir.

Ortalıkta yüzlerce dil dolaşıyor ve popülerlik listeleri her ay bu dillerin sıralamasının nasıl oynadığını gösteriyor. Ama asıl mesele bir şampiyon ilan etmek değil; bu dillerin neden var olduğunu, hangi ihtiyaçtan doğduğunu ve yazılımın doğasını nasıl şekillendirdiğini anlamak. Dile sadece bir araç değil, bir çözüm mimarisi ve bir yaşam felsefesi olarak bakmak, bütün bu kalabalığın içinde yolunu bulmanın ilk adımı.

### 1. Dilin İsmi Değil, DNA'sı ve Felsefesi Önemli

Bir dili öğrenirken yalnızca söz dizimine odaklanmak, bir kitabın sadece yazı tipine bakıp hikâyeyi kaçırmaya benziyor. Her dilin arkasında derin bir "DNA" ve belirli bir felsefe var. Mesela bir dilin neden `method overloading` desteklediği ya da desteklemediği yalnızca teknik bir detay değil; o dili tasarlayanların dünyaya bakışını yansıtan felsefi bir tercih. Bazı diller "kardeşim, metodun imzası da farklı olacak" diye direnir; bu bir kısıt değil, bilinçli bir duruştur.

Bu genetik mirasın izini sürünce iş 1960'lara, Oslo Üniversitesi'nde atılan `Simula` tohumlarına kadar gidiyor. Nesne yönelimli felsefenin ilk kıvılcımı orada çakıyor. Yıllar sonra `C++`'ın mimarları o felsefeyi alıp C'nin derleyicisinin ham gücüyle birleştiriyor; ortaya makineye yakın kalırken karmaşıklığı da yönetebilen melez bir dil çıkıyor. Alper'in ifadesiyle, dillerin hep bir yerlerden esinlenen, başka bir dilin özelliğini alıp yeni bir çözüm için yeniden yorumlayan bir tarafı var.

> Dilin adından önce sanki dilin sahip olduğu felsefe ve DNA'sı hakkında fikir sahibi olmak daha anlamlı olabilir.

Felsefeyi anladığında derleyiciyle kavga etmeyi bırakıyorsun; onun neyi neden zorladığını görüyorsun.

### 2. "Fan Boyluğu" Tuzağı ve Python Paradoksu

Yazılımda yapılabilecek en büyük hatalardan biri, projenin ihtiyacına bakmadan bir dile fanatiklik derecesinde bağlanmak. Buna "fan boyluğu tuzağı" diyoruz. Profesyonel hayatta tercih değil pragmatizm kazanır; her dilin parladığı bir alan, bir de zorlandığı bir sınır vardır.

Burada güzel bir paradoks çıkıyor karşımıza. Alper, `Python`'ın sintaksını pek sevmediğini açıkça söylüyor; ama yapay zeka ve büyük dil modeli dünyasında Python'ın tartışmasız kral olduğunu da kabul ediyor. YZ tarafında bir şey geliştiriyorsan, estetik kaygılarla Python'ı görmezden gelmek profesyonel bir hata olur. Kütüphaneler, topluluk, hazır modeller... O ekosistem yok sayılamayacak kadar güçlü. Aracı "sevdiğimiz için" değil, "işi en iyi yaptığı için" seçeriz.

Tersi de geçerli: özellikle çok `thread`'li, paralel yürümesi gereken süreçlerde her şeyi Python'la zorlamak yerine başka dilleri denemekte ciddi fayda var. Doğru iş için doğru alet:

| Alan | Tercih edilen diller | Öne çıkan güç |
| --- | --- | --- |
| Yapay zeka / veri | `Python` | Ekosistem ve kütüphane zenginliği |
| Yüksek eşzamanlılık / paralellik | Çok çekirdeği yönetmek için tasarlanmış diller | Gerçek paralel işleme |
| Sistem seviyesi / performans | `C++`, `Rust` | Donanıma yakınlık, kontrol |

### 3. Donanım, Görünmez Mimar

Programlamaya çoğu zaman soyut bir mantık bulmacası gibi bakarız; oysa dillerimizin evrimini, üzerinde koştukları "metal" belirliyor. Eskiden tek işlemciyle, tek çekirdekle çalışıyorduk. Çoklu görevi "taklit ediyorduk" aslında: işlemcinin zamanını küçük dilimlere bölüp her uygulamaya sırayla bir parça veriyor, böylece bilgisayar aynı anda birden çok iş yapıyormuş gibi görünüyordu.

Sonra çekirdek sayısı arttı, bir işlemci bloğunun içine birden fazla işlemci girdi. Diller de "algılanan" çoklu görevi yönetmekten, çekirdekler arası gerçek paralelliği yönetmeye evrilmek zorunda kaldı. Burak'ın hatırlattığı gibi, eskiden `thread` diye bir kavram bile yokken sonradan bu mantık oturdu ve dillerin merkezine yerleşti.

Bazen eski bir dile yeni özellik eklemek yetmiyor; temiz bir sayfa açmak gerekiyor. `Rust` gibi dillerin yükselişinin bir sebebi de bu: bellek güvenliğini en baştan tasarımın merkezine koyan bir yaklaşım. İşletim sistemi olmayan donanım üzerinde, yani "bare metal" tarafta yazarken çoğu zaman standart kütüphaneyi bir kenara koyup mimariyle doğrudan konuşmak gerekiyor — yüksek seviye framework'lerin bizden sakladığı bir zihniyet değişimi bu.

### 4. Derin Kökler, Hızlı Dallanma

Yaygın bir efsane var: "Bir dile çok uzun süre gömülürsen demode olursun." Bizim deneyimimiz tam tersini söylüyor. `C#` gibi bir dilde yirmi yıl geçirmek seni yalnızca C# uzmanı yapmıyor; derin bir örüntü tanıma yetisi kazandırıyor.

Bir "dinozor" yeni bir dile baktığında yabancı bir söz dizimi görmüyor; o dilin evrensel problemleri nasıl çözdüğünü görüyor. "Bunun bağımlılıkları nasıl yönetiyor — Java'daki `Maven` gibi mi, yoksa bir `.NET` solution şablonu gibi mi?" diye soruyor. Alper'in deyişiyle, bilmediği bir dile baktığında "`.NET`'te şöyleydi, Java'da böyleydi, `PHP`'de şuydu" diye kıyaslayarak çok daha hızlı anlamlandırabiliyor. Bir tarafta tecrübeni en üst noktaya çıkarırken, diğer taraflarda "ne varmış" diye bakmak müthiş bir hızlandırıcı.

Nereye geldiğimizi takdir etmek için arada Assembly'ye bir "spor" gözüyle bakmakta fayda var. Bugün saniyeler içinde bir arayüz çiziyoruz; ama bir pencereyi, üzerine bir butonu ve o butona basınca açılan bir pop-up'ı `C` ya da Assembly ile elle yazmayı bir kez deneyen, sahip olduğu modern araçların kıymetini bambaşka anlıyor.

### 5. Yapay Zeka Bile Bir Söz Dizimine Muhtaç

Bu yeni çağda kimileri "programcının devri kapanıyor" diyor. Biz katılmıyoruz. Agentic sistemler, yani kendi başına iş yürütebilen otonom YZ araçları giderek özerkleşse de, sonuçta bir "çalıştırma katmanına" muhtaçlar. Bir YZ ajanı bir işi yaparken onu havadan var etmiyor; donanımla ve işletim sistemiyle konuşmak için Shell script, `Python` veya `JavaScript` yazıp çalıştırıyor. Ortamda Python varsa hemen ona uzanıyor.

Yapay zeka bu dilleri işini görmek için öğreniyorsa, o çalıştırma katmanının ustası olmaya devam etmemiz gereken biz oluruz: üreteni doğrulayan, kontrol eden, mantığı mimarileyen taraf.

Bölümde buradan tatlı bir yan yola da saptık: agentic sistemlerin bellek çeşitleriyle insan hafızası arasındaki o felsefi benzerlik. Yıllarca biriktirdiğimiz tecrübe "kalıcı hafızada" dururken, yeni şeyleri öğrenme hızımız bir yaştan sonra değişen "kısa süreli belleğe" bağlı kalıyor — kısa süreli hafıza, uzun süreli hafıza, deneyimsel bellek derken yapay zekanın bellek katmanlarıyla şaşırtıcı şekilde örtüşüyor.

### 6. Sonuç: Challenge Aramaktan Korkmayın

Tek bir dilin sınırlarına hapsolmak, dünyayı tek bir pencereden izlemek gibi. Farklı dillerin kısıtları altında çözüm üretmek zihni esnetiyor, bakışı zenginleştiriyor. Yeni diller hep çıkacak; birileri bir dilin felsefesini beğenmeyip oturup kendi derleyicisini, kendi yorumlayıcısını yazacak ve açık kaynağa sunacak. Tutturduğunda da Stack Overflow anketlerinde bir anda üst sıralara tırmanan `Gleam`, `Rust`, `Zig` gibi isimler çıkacak karşımıza. Donanım da değişiyor; kuantum gibi olasılığın işin içine girdiği, sıfır-bir ikiliğinin dışına çıktığımız bir dünyada bambaşka diller işi hızlandırabilir.

Bölümü Burak'ın o güzel cümlesiyle bağladık: yapay zeka bile bir programlama dili öğreniyorsa, bizim de mutlaka öğrenmemiz lazım. Mesele en trend dilin söz dizimini ezberlemek değil; merak etmek, zorluk aramak. Asıl soru şu: bir sonraki dili bir popülerlik yarışmasına bakarak mı seçiyorsun, yoksa çözmeye çalıştığın problemin felsefesine göre mi?

## İnfografik

{{< infografik src="infografik.webp" alt="En İyi Programlama Dili Hangisi? - İnfografik" >}}

## Sesli Özetler

### Kısa Özet

{{< audio src="https://media.dinozorlarlakafautuleme.com/bolum-018/audio-brief.m4a" >}}

### Derinlemesine İnceleme

{{< audio src="https://media.dinozorlarlakafautuleme.com/bolum-018/audio-deepdive.m4a" >}}

## Kaynaklar

- [NotebookLM defteri](https://notebooklm.google.com/notebook/0cec889d-7664-4e34-9a1f-adef22314973)
- [Simula (Wikipedia)](https://tr.wikipedia.org/wiki/Simula)
- [Stack Overflow Developer Survey](https://survey.stackoverflow.co/)
