+++
title = "18. Kuantum Programlama"
description = "Qiskit, Q#, Cirq ve PennyLane ile kuantum programlamaya giriş: araçlar, ortamlar ve ilk devreler."
date = "2026-05-18T00:00:00+03:00"
weight = 18
type = "guide"
draft = false
+++

Kuantum bilgisayarları anlamanın bir tarafı fizik, matematik ve donanım ise, diğer tarafı da bu sistemlere nasıl problem tarif edeceğimizi bilmektir. Bu bölümde kuantum programlamayı, klasik yazılım geliştirme alışkanlıklarıyla karıştırmadan ele alacağız. Amaç, bir yazılımcının şu sorulara net cevap verebilmesidir:

- Kuantum programlama tam olarak neyi programlar?
- Kuantum bilgisayar tek başına çalışan bağımsız bir makine midir?
- Klasik bilgisayar ile kuantum bilgisayar birlikte nasıl çalışır?
- Qiskit, Q#, Cirq ve PennyLane gibi araçlar hangi amaçlarla kullanılır?
- Simülatörde çalışan bir kuantum devresi ile gerçek kuantum donanımında çalışan devre arasında ne fark vardır?
- Yazılımcı bu alana nereden başlamalıdır?

Kuantum programlama, klasik programlama dillerindeki gibi veriyi okuyup koşullar, döngüler ve değişken atamalarıyla ilerleyen bir model değildir. Elbette kuantum programlarını çoğu zaman Python, Q#, C++ veya benzeri klasik dillerle yazarız; fakat yazdığımız şey klasik anlamda yalnızca "işlem adımları" değil, çoğunlukla **kuantum durumları üzerinde uygulanacak dönüşümlerin tarifi**dir.

Bir kuantum programı genellikle şu fikre dayanır:

```text
Qubitleri hazırla.
Kuantum kapılarını uygula.
Süperpozisyon, dolaşıklık ve girişim etkilerini oluştur.
Ölçüm yap.
Sonucu klasik bilgisayarda yorumla.
```

Bu nedenle kuantum programlamayı öğrenirken ilk kırılması gereken refleks şudur: "Ben değişkene 5 atadım, sonra onu okudum, sonra if yazdım." Kuantum dünyasında programlama çoğu zaman "qubit durumunu nasıl dönüştürürsem ölçüm sonunda istediğim bilgi daha yüksek olasılıkla ortaya çıkar?" sorusudur.

---

## 18.1. Kuantum programlama neyi programlar?

Kuantum programlama, doğrudan "kuantum bilgisayarın içindeki değeri" programlamak değildir. Çünkü qubitler klasik bitler gibi okunup yazılabilen kararlı değerler değildir. Qubitlerin durumu ölçümden önce olasılık genlikleriyle temsil edilir; ölçüm yapıldığında ise klasik bir sonuç elde edilir.

Bu nedenle kuantum programlama şu nesneleri ve süreçleri tarif eder:

1. **Qubit hazırlama**
2. **Kuantum kapıları**
3. **Kuantum devreleri**
4. **Ölçüm işlemleri**
5. **Klasik kontrol ve post-processing**
6. **Donanım veya simülatör üzerinde çalıştırma**
7. **Sonuçların istatistiksel analizi**

Klasik programlamada aşağıdaki gibi düşünmeye alışığız:

```csharp
int x = 0;
x = x + 1;

if (x == 1)
{
    Console.WriteLine("Sonuç 1");
}
```

Burada `x` değişkeninin değeri her an okunabilir, kopyalanabilir ve denetlenebilir. Kuantum programlamada ise bir qubitin durumunu arada okuyayım dediğinizde, sistemi ölçmüş olursunuz. Ölçüm de çoğu zaman kuantum hesaplamanın devam etmesini engelleyecek şekilde durumu değiştirir.

Bu yüzden kuantum programlama daha çok şu yapıya benzer:

```text
q0 qubitini başlat.
q0 üzerine H kapısı uygula.
q0'ı ölç.
Ölçüm sonucunu klasik bite yaz.
Sonuçları çok sayıda tekrar üzerinden yorumla.
```

Burada `H` yani Hadamard kapısı, qubiti belirli bir süperpozisyon durumuna taşır. Ancak bu durum doğrudan "q0 artık hem 0 hem 1 değerini saklıyor" diye okunmamalıdır. Ölçüm yapıldığında klasik olarak 0 veya 1 sonucu alınır. Aynı devre çok kez çalıştırıldığında, sonuçların dağılımı kuantum durum hakkında bilgi verir.

### Kuantum programı bir devre tarifi olabilir

Bugünkü yaygın kuantum programlama araçlarında en temel model **kuantum devre modeli**dir. Bu modelde program, qubit hatları üzerinde zaman sırasına göre yerleştirilmiş kapılardan oluşur.

Basit bir örnek:

```text
q0: ──H──M──
```

Bu devrede:

- `q0` bir qubittir.
- `H` Hadamard kapısıdır.
- `M` ölçümdür.

İki qubitli bir Bell state hazırlayan devre ise şöyle gösterilebilir:

```text
q0: ──H──■──M──
         │
q1: ─────X──M──
```

Burada:

- İlk qubite Hadamard uygulanır.
- Ardından bir CNOT kapısı ile ikinci qubit birinci qubite bağlı hale getirilir.
- Sonunda iki qubit ölçülür.

Bu devre, dolaşıklık üretmenin en temel örneklerinden biridir. Programlama açısından bakıldığında biz "dolaşıklığı doğrudan yazmayız"; dolaşıklığa yol açan kapı dizisini tarif ederiz.

### Kuantum programı her zaman yalnızca devre değildir

Devre modeli çok yaygın olsa da tek model değildir. Bazı yaklaşımlarda quantum annealing, adiabatic quantum computing veya measurement-based quantum computing gibi farklı modeller kullanılır. Fakat yazılımcılar için başlangıç noktası çoğu zaman devre modelidir; çünkü Qiskit, Cirq, Q# ve PennyLane gibi araçların büyük bölümü kuantum devrelerini ifade etmeye güçlü destek verir.

### Programlanan şey sonuç değil, olasılık yapısıdır

Klasik programlamada çoğunlukla belirli bir girdi için belirli bir çıktı bekleriz. Kuantum programlamada ise devre çoğu zaman bir olasılık dağılımı üretir. Bu dağılım, devrenin çok sayıda çalıştırılmasıyla tahmin edilir.

Örneğin bir devreyi 1 kez çalıştırdığınızda şu sonucu alabilirsiniz:

```text
0
```

Aynı devreyi 1000 kez çalıştırdığınızda ise şöyle bir dağılım görebilirsiniz:

```text
0: 506 kez
1: 494 kez
```

Bu, devrenin yaklaşık olarak %50-%50 sonuç ürettiğini gösterir. Kuantum programlamada sonuçları yorumlamak için bu istatistiksel bakış çok önemlidir.

---

## 18.2. Kuantum bilgisayar tek başına mı çalışır?

Hayır. Pratikte kuantum bilgisayar tek başına, klasik bilgisayardan bağımsız çalışan bir sistem olarak düşünülmemelidir. Bugünkü ve öngörülebilir gelecekteki kuantum hesaplama mimarileri büyük ölçüde **hibrit klasik-kuantum** yapıdadır.

Bir kuantum işlemci çoğu zaman belirli bir alt problemi çalıştırır. Programın hazırlanması, parametrelerin seçilmesi, işin kuantum donanıma gönderilmesi, ölçüm sonuçlarının toplanması ve sonuçların yorumlanması klasik bilgisayar tarafından yapılır.

Genel akış şöyle düşünülebilir:

```text
Klasik bilgisayar:
  Problemi hazırlar.
  Kuantum devresini oluşturur.
  Parametreleri belirler.
  Devreyi kuantum işlemciye gönderir.

Kuantum işlemci:
  Qubitleri hazırlar.
  Kapıları uygular.
  Ölçüm yapar.
  Sonuçları klasik bitler olarak döndürür.

Klasik bilgisayar:
  Sonuçları toplar.
  İstatistiksel analiz yapar.
  Gerekirse parametreleri günceller.
  Nihai çıktıyı üretir.
```

Bu mimari, özellikle NISQ dönemi algoritmalarında çok belirgindir. VQE ve QAOA gibi hibrit algoritmalarda klasik optimizasyon döngüsü ile kuantum devresi birlikte çalışır.

### Kuantum işlemci bir yardımcı hızlandırıcı gibi düşünülebilir

Bugünkü kuantum işlemcileri genel amaçlı CPU gibi değil, belirli problem türleri için kullanılan özel hızlandırıcılar gibi düşünmek daha sağlıklıdır. GPU nasıl her işi CPU'nun yerine yapmıyor ama belirli yoğun hesaplama işlerinde güçlü bir hızlandırıcı olabiliyorsa, kuantum işlemci de bazı özel hesaplama yapılarını hedefler.

Ancak bu benzetmenin de sınırı vardır. GPU klasik deterministik hesaplama yapar. Kuantum işlemci ise kuantum durumları üzerinde olasılıksal ölçüm sonuçları üreten farklı bir hesaplama modelidir.

Daha doğru ifade şu olabilir:

```text
Kuantum işlemci, klasik bilgisayarın yerine geçen genel amaçlı bir makine değil;
klasik sistemle birlikte çalışan, belirli problem sınıfları için tasarlanmış özel bir hesaplama kaynağıdır.
```

### Bulut üzerinden erişim

Çoğu geliştirici gerçek kuantum donanıma doğrudan fiziksel olarak erişmez. Bunun yerine IBM Quantum, Azure Quantum, Amazon Braket veya benzeri bulut servisleri üzerinden kuantum donanımına veya simülatörlere iş gönderir.

Tipik kullanım modeli şöyledir:

```text
Yerel geliştirme ortamı
    ↓
SDK / API
    ↓
Bulut kuantum servisi
    ↓
Simülatör veya gerçek kuantum donanımı
    ↓
Ölçüm sonuçları
    ↓
Yerel analiz / görselleştirme
```

Bu model yazılımcı açısından tanıdıktır: Bir cloud servisine job gönderilir, sonuç alınır, loglar ve metrikler incelenir. Fakat alttaki hesaplama kaynağı klasik bir VM veya container değil, kuantum devrelerini çalıştıran özel bir sistemdir.

### Kuyruk, tekrar sayısı ve istatistik

Gerçek kuantum donanımında bir devre çalıştırmak genellikle anlık bir işlem gibi düşünülmemelidir. Donanımda kuyruk olabilir, cihaz kalibrasyonu değişebilir, çalıştırma süresi kısıtlı olabilir. Ayrıca devre tek kez değil, çok kez çalıştırılır. Bu tekrarlara çoğu araçta `shots` denir.

Örneğin:

```text
shots = 1000
```

Bu, aynı devrenin 1000 kez çalıştırılıp ölçüm sonuçlarının dağılımının toplanacağı anlamına gelir.

Klasik programlamada aynı kodu aynı girdiyle 1000 kez çalıştırdığınızda çoğunlukla aynı sonucu beklersiniz. Kuantum programlamada ise 1000 çalıştırma, olasılık dağılımını görmek için gereklidir.

---

## 18.3. Hibrit klasik-kuantum mimari

Hibrit klasik-kuantum mimari, klasik bilgisayar ile kuantum işlemcinin birlikte çalıştığı mimaridir. Bu, bugünkü kuantum programlamanın merkezinde yer alır.

Bu mimaride klasik taraf genellikle şunları yapar:

- Problemi kuantum devresine dönüştürür.
- Parametreleri belirler.
- Optimizasyon döngüsünü yönetir.
- Kuantum işlerini sıraya koyar.
- Ölçüm sonuçlarını analiz eder.
- Hata azaltma veya istatistiksel yorumlama uygular.
- Nihai sonucu üretir.

Kuantum taraf ise şunları yapar:

- Qubitleri hazırlar.
- Kuantum kapılarını uygular.
- Ölçüm yapar.
- Sonuçları klasik bitler olarak döndürür.

Bu ayrım özellikle VQE ve QAOA gibi algoritmalarda net görülür.

### VQE örneği

VQE, yani Variational Quantum Eigensolver, özellikle kuantum kimya ve enerji seviyesi hesaplamaları için geliştirilmiş hibrit bir yaklaşımdır. Genel akış şöyledir:

```text
1. Klasik bilgisayar parametreli bir kuantum devresi oluşturur.
2. Kuantum bilgisayar bu devreyi çalıştırır.
3. Ölçüm sonuçlarından bir enerji beklenti değeri tahmin edilir.
4. Klasik optimizer parametreleri günceller.
5. Süreç daha iyi sonuç bulunana kadar tekrarlanır.
```

Burada kuantum bilgisayar tek başına cevabı üretmez. Klasik optimizer ile birlikte çalışır.

### QAOA örneği

QAOA, yani Quantum Approximate Optimization Algorithm, kombinatoryal optimizasyon problemleri için önerilen hibrit bir yaklaşımdır. Örneğin Max-Cut gibi problemlerde kullanılabilir.

Akış kabaca şöyledir:

```text
1. Optimizasyon problemi kuantum devresine kodlanır.
2. Parametreli kuantum kapıları uygulanır.
3. Ölçüm sonuçlarından aday çözümler elde edilir.
4. Klasik optimizer parametreleri günceller.
5. Döngü tekrarlanır.
```

Bu yapı, klasik optimizasyon ile kuantum örnekleme / durum hazırlama süreçlerini birleştirir.

### Hibrit mimarinin yazılım mimarisi açısından anlamı

Bir yazılım mimarı için hibrit kuantum mimari, klasik uygulamaya yeni bir "compute backend" eklemek gibi düşünülebilir. Fakat bu backend'in davranışı klasik servislerden farklıdır.

Dikkat edilmesi gereken noktalar:

- Sonuçlar istatistikseldir.
- Çalıştırma maliyeti ve süresi değişken olabilir.
- Gerçek donanım gürültülüdür.
- Aynı devre farklı donanımlarda farklı sonuç kalitesi verebilir.
- Devre derleme/transpilation aşaması donanıma bağımlıdır.
- Parametre optimizasyonu çoğu zaman klasik tarafta yapılır.
- Hata azaltma ve sonuç yorumlama uygulama mantığının parçası olabilir.

Bu nedenle kurumsal bir sistemde kuantum bileşenini doğrudan "REST endpoint çağır, sonucu al" sadeliğinde düşünmek başlangıç için faydalı olsa da yeterli değildir. Performans, hata modeli, kuyruk, maliyet, güvenlik ve sonuç güvenilirliği birlikte değerlendirilmelidir.

---

## 18.4. Qiskit

Qiskit, IBM tarafından geliştirilen ve açık kaynak olarak kullanılan en bilinen kuantum yazılım geliştirme araçlarından biridir. Python tabanlıdır ve kuantum devreleri oluşturmak, simüle etmek, optimize etmek, transpile etmek ve IBM Quantum platformundaki gerçek kuantum donanımlara iş göndermek için kullanılır.

Qiskit'in temel kullanım alanları şunlardır:

- Kuantum devresi oluşturma
- Kapılar ve ölçümler ekleme
- Devreleri simülatörde çalıştırma
- Devreleri gerçek donanıma uygun hale getirme
- Transpilation işlemleri
- Ölçüm sonuçlarını analiz etme
- Algoritma prototipleri geliştirme
- Eğitim ve deneysel çalışma

Basit bir Qiskit devresi şöyle görünebilir:

```python
from qiskit import QuantumCircuit

qc = QuantumCircuit(1, 1)

qc.h(0)
qc.measure(0, 0)

print(qc)
```

Bu örnekte:

- 1 qubit ve 1 klasik bit içeren bir devre oluşturulur.
- Qubite Hadamard kapısı uygulanır.
- Qubit ölçülür ve sonuç klasik bite yazılır.

Daha sonra bu devre bir simülatörde veya uygun bir gerçek donanımda çalıştırılabilir.

### Bell state örneği

İki qubitli basit bir Bell state devresi Qiskit ile şöyle ifade edilebilir:

```python
from qiskit import QuantumCircuit

qc = QuantumCircuit(2, 2)

qc.h(0)
qc.cx(0, 1)

qc.measure(0, 0)
qc.measure(1, 1)

print(qc)
```

Bu devre:

1. İlk qubiti süperpozisyona alır.
2. CNOT kapısıyla ikinci qubiti birinci qubite bağlar.
3. İki qubiti ölçer.

İdeal durumda sonuçlar çoğunlukla şu iki biçimde görülür:

```text
00
11
```

Bu, iki qubit arasında güçlü bir korelasyon olduğunu gösterir. Gerçek donanımda ise gürültü nedeniyle küçük oranlarda `01` veya `10` gibi sonuçlar da görülebilir.

### Transpilation neden önemlidir?

Qiskit'in önemli taraflarından biri, devreyi hedef donanıma uygun hale getirme sürecidir. Buna **transpilation** denir.

Çünkü yazılımcının çizdiği mantıksal devre ile gerçek kuantum cihazın fiziksel kısıtları aynı olmayabilir:

- Her qubit her qubitle doğrudan bağlı olmayabilir.
- Donanım yalnızca belirli temel kapıları destekleyebilir.
- Bazı qubitler diğerlerinden daha düşük hata oranına sahip olabilir.
- Devre derinliği azaltılmak istenebilir.
- Ölçüm ve kapı hataları donanıma göre değişebilir.

Transpiler, devreyi hedef cihazın kapı setine ve bağlantı topolojisine uygun hale getirmeye çalışır. Bu, kuantum programlamayı klasik programlamadan ayıran önemli mühendislik adımlarından biridir.

### Qiskit kimler için uygundur?

Qiskit özellikle şu kullanıcılar için güçlüdür:

- Python bilen yazılımcılar
- Kuantum devre modeliyle öğrenmek isteyenler
- IBM Quantum donanımıyla deney yapmak isteyenler
- Kuantum algoritma prototipi geliştirmek isteyenler
- Eğitim ve araştırma amaçlı çalışanlar
- Transpilation, hata azaltma ve donanım farklarını incelemek isteyenler

Qiskit, yazılımcılar için kuantum programlamaya başlamak adına en erişilebilir araçlardan biridir. Python ekosistemiyle uyumlu olması da öğrenme eşiğini düşürür.

---

## 18.5. Q# ve Azure Quantum

Q#, Microsoft tarafından kuantum programlama için geliştirilen özel bir programlama dilidir. Azure Quantum ise Microsoft'un kuantum hesaplama hizmetlerini, simülatörleri, çözümleyicileri ve farklı kuantum donanım sağlayıcılarına erişimi bir araya getiren platformudur.

Q# klasik bir genel amaçlı dil olmaktan çok, kuantum algoritmalarını ifade etmeye odaklanan bir dildir. Kuantum operasyonlarını, qubit yönetimini, ölçüm işlemlerini ve klasik kontrol yapılarını kuantum programlama bağlamında düzenli şekilde ifade etmeyi amaçlar.

Basit bir Q# örneği şöyle görünebilir:

```qsharp
operation CreateSuperposition() : Result {
    use q = Qubit();

    H(q);
    let result = M(q);

    Reset(q);

    return result;
}
```

Bu örnekte:

- Bir qubit ayrılır.
- Hadamard kapısı uygulanır.
- Qubit ölçülür.
- Qubit sıfırlanır.
- Ölçüm sonucu döndürülür.

### Q#'ın ayırt edici tarafı

Q# dilinin en önemli tarafı, kuantum programlama kavramlarını dil seviyesinde ifade etmesidir. Örneğin `operation`, `Qubit`, `H`, `M`, `Reset` gibi kavramlar doğrudan kuantum programlamaya aittir.

Python tabanlı araçlarda kuantum devresi genellikle bir nesne olarak oluşturulur:

```python
qc = QuantumCircuit(1, 1)
qc.h(0)
qc.measure(0, 0)
```

Q# tarafında ise programlama modeli daha çok kuantum operasyonları tanımlamak üzerine kuruludur.

### Azure Quantum ile çalışma

Azure Quantum, geliştiricilere farklı çalışma seçenekleri sunar:

- Yerel geliştirme ortamında Q# yazmak
- Simülatör üzerinde çalıştırmak
- Azure üzerinden kuantum donanım sağlayıcılarına erişmek
- Python ve Q# birlikte kullanmak
- Hibrit iş akışları geliştirmek
- Optimization ve quantum-inspired yaklaşımları denemek

Kurumsal açıdan Azure Quantum'un önemli tarafı, kuantum hesaplamayı Azure ekosistemi içinde servis olarak konumlandırmasıdır. Bu, güvenlik, erişim yönetimi, kaynak yönetimi ve entegrasyon açısından kurumlara tanıdık bir çerçeve sunabilir.

### Q# kimler için uygundur?

Q# özellikle şu kişiler için anlamlıdır:

- Microsoft ekosisteminde çalışan yazılımcılar
- Azure üzerinde kuantum servisleri denemek isteyen ekipler
- Kuantum algoritmalarını daha özel amaçlı bir dille ifade etmek isteyenler
- QDK ve VS Code entegrasyonu ile çalışmak isteyenler
- Kurumsal PoC yaklaşımında Azure tabanlı servisleri değerlendiren mimarlar

Q# öğrenmek, kuantum programlama kavramlarını dil düzeyinde anlamaya yardımcı olabilir. Ancak Python ekosisteminin yaygınlığı nedeniyle birçok geliştirici başlangıçta Qiskit veya PennyLane gibi araçlarla daha hızlı deney yapabilir. Seçim, ekibin hedeflerine, mevcut teknoloji ekosistemine ve çalışılacak platforma göre yapılmalıdır.

---

## 18.6. Cirq

Cirq, Google Quantum AI tarafından geliştirilen açık kaynaklı Python kütüphanesidir. Kuantum devreleri oluşturmak, düzenlemek, optimize etmek ve simülatörlerde veya desteklenen kuantum donanımlarında çalıştırmak için kullanılır.

Cirq özellikle NISQ dönemi cihazların gerçekçi özelliklerini dikkate almak isteyen araştırmacılar ve geliştiriciler için tasarlanmıştır. Donanım bağlantı yapısı, kapı zamanlaması, moment kavramı ve düşük seviyeli kontrol gibi konular Cirq'te daha görünürdür.

Cirq'te temel kavramlar şunlardır:

- **Qubit**
- **Gate**
- **Operation**
- **Moment**
- **Circuit**
- **Simulator**

Basit bir Cirq devresi şöyle yazılabilir:

```python
import cirq

qubit = cirq.LineQubit(0)

circuit = cirq.Circuit(
    cirq.H(qubit),
    cirq.measure(qubit, key="result")
)

print(circuit)
```

Bu örnekte:

- Bir qubit tanımlanır.
- Hadamard kapısı uygulanır.
- Qubit ölçülür.

### Moment kavramı

Cirq'in önemli kavramlarından biri **Moment** kavramıdır. Bir moment, aynı zaman diliminde uygulanabilecek operasyonları temsil eder. Bu, devrenin zaman yapısını ve paralel uygulanabilecek kapıları anlamak açısından faydalıdır.

Örneğin iki farklı qubit üzerinde aynı anda uygulanabilecek kapılar aynı moment içinde yer alabilir. Aynı qubit üzerinde art arda uygulanması gereken kapılar ise farklı momentlerde bulunur.

Bu özellik, gerçek donanım zamanlaması ve devre optimizasyonu açısından önemlidir.

### Cirq kimler için uygundur?

Cirq özellikle şu kullanıcılar için uygundur:

- Python ile çalışan kuantum araştırmacıları
- Google Quantum AI ekosistemini takip edenler
- NISQ donanım ayrıntılarıyla ilgilenenler
- Devre zamanlaması, moment yapısı ve düşük seviyeli kontrol isteyenler
- Donanım farklarını daha görünür şekilde incelemek isteyenler

Qiskit daha geniş eğitim ve IBM donanım ekosistemiyle öne çıkarken, Cirq özellikle araştırma ve donanım-yakın devre tasarımı açısından güçlü bir alternatiftir.

---

## 18.7. PennyLane

PennyLane, Xanadu tarafından geliştirilen açık kaynaklı, Python tabanlı bir kuantum programlama kütüphanesidir. Özellikle **hibrit kuantum-klasik hesaplama**, **quantum machine learning** ve **kuantum kimya** alanlarında öne çıkar.

PennyLane'in en önemli özelliklerinden biri, kuantum devrelerini otomatik türev alma ve makine öğrenmesi ekosistemiyle birleştirmesidir. PyTorch, TensorFlow, JAX gibi araçlarla entegrasyon kurabilmesi, onu quantum machine learning çalışmaları için cazip hale getirir.

Basit bir PennyLane örneği şöyle olabilir:

```python
import pennylane as qml
import numpy as np

dev = qml.device("default.qubit", wires=1)

@qml.qnode(dev)
def circuit(theta):
    qml.RX(theta, wires=0)
    return qml.expval(qml.PauliZ(0))

result = circuit(np.pi / 4)

print(result)
```

Bu örnekte:

- Bir simülatör cihazı tanımlanır.
- Parametreli bir kuantum devresi oluşturulur.
- Devre bir beklenti değeri döndürür.
- Parametre klasik tarafta değiştirilebilir.

### QNode kavramı

PennyLane'de önemli kavramlardan biri **QNode**'dur. QNode, kuantum devresini klasik hesaplama grafiğine bağlayan yapıdır. Bu sayede kuantum devresi, klasik optimizer veya makine öğrenmesi modeli içinde kullanılabilir.

Bu yapı, hibrit algoritmalar için çok uygundur:

```text
Klasik parametreler
    ↓
Parametreli kuantum devresi
    ↓
Ölçüm / beklenti değeri
    ↓
Kayıp fonksiyonu
    ↓
Klasik optimizer
    ↓
Yeni parametreler
```

### PennyLane kimler için uygundur?

PennyLane özellikle şu kullanıcılar için uygundur:

- Quantum machine learning öğrenmek isteyenler
- Hibrit kuantum-klasik modeller geliştirmek isteyenler
- Kuantum kimya prototipleriyle çalışanlar
- Otomatik türev alma ve optimizer entegrasyonu isteyenler
- PyTorch, TensorFlow veya JAX ekosistemine aşina olanlar

PennyLane, kuantum programlamaya "makine öğrenmesi ve optimizasyon" penceresinden yaklaşan geliştiriciler için güçlü bir araçtır.

---

## 18.8. Basit bir kuantum devresini kodla ifade etmek

Bu bölümde aynı basit fikri farklı araçlarla ifade edelim: Bir qubiti süperpozisyona alıp ölçmek.

Devre fikri:

```text
q0: ──H──M──
```

Beklenti:

- Qubit başlangıçta `|0⟩` durumundadır.
- `H` kapısı uygulanır.
- Ölçüm yapıldığında ideal durumda yaklaşık %50 `0`, %50 `1` sonucu alınır.

### Qiskit ile

```python
from qiskit import QuantumCircuit

qc = QuantumCircuit(1, 1)

qc.h(0)
qc.measure(0, 0)

print(qc)
```

Bu kod devreyi oluşturur. Çalıştırmak için ayrıca bir simülatör veya backend seçilir.

Kavramsal çıktı:

```text
0 sonucu yaklaşık %50
1 sonucu yaklaşık %50
```

### Q# ile

```qsharp
operation MeasureSuperposition() : Result {
    use q = Qubit();

    H(q);
    let result = M(q);

    Reset(q);

    return result;
}
```

Bu kod bir operasyon tanımlar. Her çalıştırmada `Zero` veya `One` sonucu döner. Çok sayıda çalıştırmada sonuçların yaklaşık dengeli olması beklenir.

### Cirq ile

```python
import cirq

q = cirq.LineQubit(0)

circuit = cirq.Circuit(
    cirq.H(q),
    cirq.measure(q, key="m")
)

print(circuit)
```

Cirq devreyi `Circuit`, `Operation` ve `Moment` yapılarıyla ifade eder.

### PennyLane ile

PennyLane'de aynı işlem ölçüm dağılımı veya beklenti değeri üzerinden ifade edilebilir:

```python
import pennylane as qml

dev = qml.device("default.qubit", wires=1, shots=1000)

@qml.qnode(dev)
def circuit():
    qml.Hadamard(wires=0)
    return qml.sample(wires=0)

samples = circuit()

print(samples)
```

Burada aynı devre 1000 shot ile örneklenir ve 0/1 sonuçları toplanır.

### Aynı fikir, farklı araçlar

Dört örnek de aynı temel kuantum işlemi ifade eder:

```text
Başlat → Hadamard uygula → Ölç → Sonuçları yorumla
```

Fakat araçların odakları farklıdır:

| Araç | Ana odak |
|---|---|
| Qiskit | Devre modeli, IBM Quantum ekosistemi, transpilation, gerçek donanım deneyleri |
| Q# | Kuantum algoritmalar için özel dil, Azure Quantum ve QDK entegrasyonu |
| Cirq | Devre yapısı, moment kavramı, NISQ ve donanım-yakın kontrol |
| PennyLane | Hibrit kuantum-klasik hesaplama, QML, otomatik türev alma |

Yazılımcı açısından ilk hedef, araçları ezberlemek değil, aynı kuantum fikrin farklı programlama modellerinde nasıl temsil edildiğini görmektir.

---

## 18.9. Simülatör ile gerçek kuantum donanımı farkı

Kuantum programlamaya başlarken çoğu çalışma simülatör üzerinde yapılır. Simülatör, klasik bilgisayar üzerinde kuantum devresinin davranışını hesaplamaya çalışır. Gerçek kuantum donanımı ise fiziksel qubitler üzerinde çalışır.

Bu iki ortam arasında ciddi farklar vardır.

### Simülatörün avantajları

Simülatörler başlangıç için çok yararlıdır:

- Hızlı deneme yapılabilir.
- Donanım kuyruğu beklenmez.
- Gürültüsüz ideal sonuçlar görülebilir.
- Bazı simülatörlerde statevector incelenebilir.
- Algoritma mantığı test edilebilir.
- Öğrenme maliyeti düşüktür.

Örneğin Bell state devresini ideal simülatörde çalıştırdığınızda çoğunlukla sadece şu sonuçları beklersiniz:

```text
00
11
```

Eğer devre doğruysa `01` ve `10` sonuçlarının görülmemesi beklenir.

### Gerçek donanımın farkları

Gerçek kuantum donanımında ise işler daha karmaşıktır:

- Qubitler gürültülüdür.
- Kapılar hatalı uygulanabilir.
- Ölçüm hataları olabilir.
- Qubitler arasında crosstalk olabilir.
- Cihaz kalibrasyonu zamanla değişebilir.
- Her qubit aynı kalitede değildir.
- Her qubit çifti doğrudan bağlı olmayabilir.
- Devrenin transpile edilmesi gerekir.
- Sonuçlar donanıma ve zamana bağlı değişebilir.

Aynı Bell state devresi gerçek donanımda şöyle bir dağılım verebilir:

```text
00: 470
11: 460
01: 35
10: 35
```

Burada `01` ve `10` idealde beklenmeyen ama gürültü nedeniyle görülebilen sonuçlardır.

### Simülatörde statevector görebilirsiniz, donanımda göremezsiniz

Simülatörlerde bazen kuantum durumunun tamamını, yani statevector'ü inceleyebilirsiniz. Bu, öğrenme açısından çok faydalıdır. Fakat gerçek kuantum donanımında qubitlerin tüm durumunu doğrudan okuyamazsınız. Ölçüm yaptığınızda yalnızca klasik sonuçlar elde edersiniz.

Bu fark çok önemlidir. Simülatör öğrenmek için size "sistemin içini görme" imkânı verir. Gerçek donanımda ise yalnızca deney sonuçlarını toplarsınız.

### Simülasyon neden zorlaşır?

Kuantum simülatörleri klasik bilgisayarlarda çalışır. Bir kuantum sistemini tam olarak simüle etmek için gereken bellek, qubit sayısıyla üstel olarak artar.

Yaklaşık fikir:

```text
n qubit için durum vektöründe 2^n karmaşık genlik gerekir.
```

Bu nedenle küçük devreler simüle edilebilirken, qubit sayısı arttıkça tam simülasyon hızla zorlaşır. Bu da zaten kuantum bilgisayarların neden ilginç olduğunu gösteren noktalardan biridir.

### Gürültülü simülatörler

Bazı simülatörler ideal değildir; gürültü modeli eklenebilir. Böylece gerçek donanıma daha yakın davranışlar test edilebilir:

- Gate error
- Readout error
- Depolarizing noise
- Amplitude damping
- Phase damping
- Thermal relaxation

Bu tür simülatörler, hata azaltma ve donanım etkilerini anlamak için faydalıdır.

### Yazılımcı için doğru yaklaşım

Bir yazılımcı için mantıklı çalışma sırası şu olabilir:

```text
1. Devreyi ideal simülatörde dene.
2. Beklenen teorik sonucu doğrula.
3. Gürültülü simülatörde test et.
4. Devre derinliğini ve kapı sayısını azaltmaya çalış.
5. Hedef donanıma transpile et.
6. Gerçek donanımda küçük ölçekte çalıştır.
7. Sonuç dağılımlarını simülatörle karşılaştır.
8. Hata azaltma veya yorumlama uygula.
```

Bu yaklaşım, kuantum programlamayı yalnızca kod yazma değil, deneysel hesaplama pratiği olarak ele alır.

---

## 18.10. Yazılımcılar için öğrenme yolu

Kuantum programlamaya başlamak isteyen bir yazılımcı için en büyük risk, doğrudan ileri matematik veya ileri fizik kaynaklarına dalıp motivasyonu kaybetmektir. Daha sağlıklı yol, kavramları katman katman öğrenmektir.

Aşağıdaki yol haritası, özellikle klasik yazılım geliştirme geçmişi olan kişiler için tasarlanmıştır.

### Aşama 1: Kavramsal temel

Önce şu kavramlar öğrenilmelidir:

- Bit ve qubit farkı
- Süperpozisyon
- Ölçüm
- Olasılık genliği
- Dolaşıklık
- Girişim
- Kuantum kapıları
- Kuantum devreleri

Bu aşamada amaç, matematiği mükemmel bilmek değil, yanlış sezgileri temizlemektir.

Özellikle şu cümlelerin neden eksik olduğunu anlamak önemlidir:

```text
Qubit aynı anda hem 0 hem 1'dir.
Kuantum bilgisayar tüm ihtimalleri aynı anda dener.
Dolaşıklık ışıktan hızlı haberleşmedir.
Daha çok qubit her zaman daha iyi bilgisayar demektir.
```

### Aşama 2: Basit devreler

İkinci aşamada şu devreler yazılmalıdır:

- Tek qubit Hadamard devresi
- X kapısı ile bit flip
- Z kapısı ile faz değişimi
- H + ölçüm
- CNOT
- Bell state
- GHZ state
- Basit parametrik rotation devreleri

Bu devreler Qiskit, Cirq veya Q# ile yazılabilir. Başlangıç için Qiskit veya Cirq, Python bilenler için daha hızlı olabilir.

### Aşama 3: Simülatör kullanımı

Üçüncü aşamada simülatörle çalışılmalıdır:

- Shot sayısı nedir?
- Ölçüm dağılımı nasıl okunur?
- Statevector nedir?
- İdeal sonuç ile örnekleme sonucu neden farklı olabilir?
- Gürültü modeli nasıl eklenir?

Bu aşamada yazılımcı, kuantum programların çoğu zaman tekil sonuç değil, dağılım ürettiğini içselleştirir.

### Aşama 4: Temel algoritmalar

Dördüncü aşamada temel algoritmalara geçilebilir:

- Deutsch-Jozsa
- Bernstein-Vazirani
- Grover
- Quantum Phase Estimation
- Shor'un temel fikri
- VQE
- QAOA

Burada amaç her algoritmanın tüm matematiksel ispatını bilmek değildir. Önce şu sorulara cevap verilebilmelidir:

```text
Bu algoritma hangi problemi hedefliyor?
Klasik algoritmadan farkı ne?
Süperpozisyon, dolaşıklık ve girişim nerede kullanılıyor?
Ölçüm sonucu nasıl yorumlanıyor?
Bugünkü donanımda pratik mi, teorik mi?
```

### Aşama 5: Hibrit algoritmalar

Bugünün pratik kuantum programlama çalışmaları için hibrit algoritmalar önemlidir. Bu nedenle VQE ve QAOA gibi algoritmalar ayrı incelenmelidir.

Bu aşamada şu kavramlar öğrenilmelidir:

- Parametreli devre
- Ansatz
- Cost function
- Expectation value
- Classical optimizer
- Gradient
- Barren plateau
- Noise etkisi
- Hata azaltma

PennyLane bu aşama için iyi bir araçtır. Çünkü klasik optimizer ve kuantum devre entegrasyonunu doğal biçimde sunar.

### Aşama 6: Gerçek donanım farkları

Altıncı aşamada gerçek donanım etkileri öğrenilmelidir:

- Qubit connectivity
- Native gate set
- Transpilation
- Circuit depth
- Gate fidelity
- Readout error
- Calibration
- Queue time
- Error mitigation

Bu aşamada Qiskit ve Cirq özellikle faydalıdır. Çünkü devrenin donanıma nasıl uyarlanacağını görmek, kuantum yazılım mühendisliğinin önemli parçasıdır.

### Aşama 7: Alan seçimi

Kuantum programlama çok geniş bir alandır. Bir noktadan sonra yazılımcının odak seçmesi gerekir:

| İlgi alanı | Önerilen rota |
|---|---|
| Genel kuantum programlama | Qiskit + temel algoritmalar |
| Microsoft / Azure ekosistemi | Q# + Azure Quantum |
| Donanım-yakın devre çalışmaları | Cirq |
| Quantum machine learning | PennyLane |
| Kuantum kimya | PennyLane, Qiskit Nature, Azure Quantum chemistry araçları |
| Kriptografi | Shor, Grover, PQC, kripto migration |
| Yazılım mimarisi | Quantum as a Service, hibrit mimari, güvenlik ve entegrasyon |

### 30 günlük başlangıç planı

Aşağıdaki plan, yazılımcıların temel seviyeden uygulamalı denemeye geçmesi için kullanılabilir.

#### 1. Hafta: Temel kavramlar

```text
Gün 1: Bit, qubit, ölçüm
Gün 2: Süperpozisyon ve olasılık genliği
Gün 3: Dolaşıklık
Gün 4: Girişim
Gün 5: Kuantum kapıları
Gün 6: Kuantum devreleri
Gün 7: Tekrar ve küçük notlar
```

#### 2. Hafta: Kod ile ilk devreler

```text
Gün 8: Qiskit kurulumu ve ilk devre
Gün 9: Hadamard + ölçüm
Gün 10: CNOT ve Bell state
Gün 11: GHZ state
Gün 12: Simülatör ve shot kavramı
Gün 13: Statevector inceleme
Gün 14: Sonuç dağılımlarını yorumlama
```

#### 3. Hafta: Algoritmalara giriş

```text
Gün 15: Deutsch-Jozsa
Gün 16: Bernstein-Vazirani
Gün 17: Grover temel fikri
Gün 18: Oracle kavramı
Gün 19: Phase estimation fikri
Gün 20: Shor algoritmasının büyük resmi
Gün 21: Tekrar ve karşılaştırma
```

#### 4. Hafta: Hibrit ve gerçekçi bakış

```text
Gün 22: VQE temel akışı
Gün 23: QAOA temel akışı
Gün 24: PennyLane ile parametrik devre
Gün 25: Gürültülü simülatör
Gün 26: Transpilation
Gün 27: Gerçek donanım kısıtları
Gün 28: Hata azaltma fikri
Gün 29: Küçük bir PoC taslağı
Gün 30: Öğrenilenleri özetleme
```

### Yazılımcı için zihinsel model

Kuantum programlamayı öğrenirken şu modeli korumak faydalıdır:

```text
Klasik programlama:
Veri yapıları + algoritmalar + deterministik yürütme

Kuantum programlama:
Durum hazırlama + üniter dönüşümler + girişim + ölçüm + istatistiksel yorumlama
```

Bir başka ifadeyle:

```text
Klasik programda sonucu doğrudan hesaplamaya çalışırsınız.
Kuantum programda ölçüm sonunda istediğiniz sonucun ortaya çıkma olasılığını artıracak bir süreç tasarlarsınız.
```

Bu fark anlaşılmadan kuantum programlama yalnızca yeni bir SDK öğrenmek gibi görünür. Oysa asıl değişim, hesaplama sezgisindedir.

---

## Bölüm Özeti

Bu bölümde kuantum programlamanın temel yazılımcı perspektifini ele aldık.

Öne çıkan noktalar şunlardır:

- Kuantum programlama, qubitlerin klasik değerlerini doğrudan değiştirmek değil, kuantum durumları üzerinde uygulanacak dönüşümleri tarif etmektir.
- Kuantum bilgisayarlar pratikte tek başına değil, klasik bilgisayarlarla birlikte hibrit mimaride çalışır.
- VQE ve QAOA gibi algoritmalar, klasik optimizer ile kuantum devresini birleştiren hibrit yaklaşımlardır.
- Qiskit, Python tabanlı güçlü bir kuantum geliştirme ekosistemidir ve IBM Quantum ile yakından ilişkilidir.
- Q#, Microsoft'un kuantum programlama dilidir ve Azure Quantum / QDK ile birlikte kullanılır.
- Cirq, Google Quantum AI ekosisteminde özellikle devre, moment ve NISQ donanım ayrıntılarına yakın çalışma için uygundur.
- PennyLane, quantum machine learning, hibrit algoritmalar ve otomatik türev alma entegrasyonu açısından güçlüdür.
- Simülatörler öğrenme ve prototipleme için idealdir; gerçek kuantum donanımı ise gürültü, hata, kalibrasyon ve bağlantı kısıtları içerir.
- Yazılımcı için en doğru öğrenme yolu, kavramlardan basit devrelere, simülatörden algoritmalara, ardından hibrit ve donanım farklarına doğru ilerlemektir.

Bu bölümden sonra kuantum bilgisayarların mevcut kurumsal sistemlerle nasıl ilişkilendirilebileceğini, Quantum as a Service modelini, API/SDK entegrasyonlarını ve yazılım mimarisi açısından dikkat edilmesi gereken noktaları ele alacağız.

---

## Kaynaklar ve İleri Okuma

- IBM Quantum Documentation — Qiskit ve IBM Quantum platformu  
  <https://quantum.cloud.ibm.com/docs>

- IBM Quantum / Qiskit — Qiskit SDK bilgileri  
  <https://www.ibm.com/quantum/qiskit>

- Qiskit GitHub Repository  
  <https://github.com/Qiskit/qiskit>

- Microsoft Quantum Documentation — Azure Quantum ve Q#  
  <https://learn.microsoft.com/en-us/azure/quantum/>

- Microsoft Learn — Introduction to Q#  
  <https://learn.microsoft.com/en-us/azure/quantum/qsharp-overview>

- Microsoft QDK GitHub Repository  
  <https://github.com/microsoft/qdk>

- Google Quantum AI — Cirq  
  <https://quantumai.google/cirq>

- Google Quantum AI — Cirq Circuits documentation  
  <https://quantumai.google/cirq/build/circuits>

- PennyLane Documentation  
  <https://docs.pennylane.ai/>

- PennyLane Quantum Machine Learning  
  <https://pennylane.ai/qml>
