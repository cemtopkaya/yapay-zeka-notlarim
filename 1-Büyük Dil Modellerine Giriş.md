# Büyük Dil Modellerine Giriş

## Ajanda
1. **Büyük Dil Modelleri Nedir?**
2. **Büyük Dil Modellerinin Kullanım Durumları**
3. **Prompt Tuning (Ön Ayar) Nedir?**
4. **Google'ın Generative AI Geliştirme Araçları**

---

### 1. Büyük Dil Modelleri Nedir?

**Büyük Dil Modelleri (LLM)**, dil işleme yeteneklerine sahip derin öğrenme modelleridir yani derin öğrenmenin bir alt kümesidir. Büyük veri setleri üzerinde eğitilmişlerdir ve geniş bir parametre setine sahiptirler. LLM'ler ve generative AI (üretici yapay zeka) kesişir ve her ikisi de derin öğrenmenin bir parçasıdır. AI'nin diğer bir alanı ise generative AI'dir. Bu, yeni içerikler üretebilen bir yapay zeka türüdür; metin, görüntüler, ses ve sentetik veri dahil.

![image](https://github.com/user-attachments/assets/ba17922b-c813-4d6e-b91d-603479364ff2)

### _Peki büyük dil modelleri nedir?_
**Büyük, genel amaçlı dil modelleri**, önceden eğitilebilir ve ardından belirli amaçlar için ince ayar yapılabilir modellerdir. 


### _Önceden eğitilmiş ve ince ayar yapılmış ne anlama geliyor?_
Bir köpeği eğitmek gibi düşünün. Genellikle köpeğinize 
- otur,
- gel,
- yat ve
- kal gibi temel komutları öğretirsiniz. Bu komutlar günlük hayat için yeterlidir ancak, bir polis köpeği, rehber köpek veya av köpeği gibi özel bir hizmet köpeğine ihtiyacınız varsa, **özel eğitimler eklemeniz** gerekir. 

Bu benzer fikir, büyük dil modelleri için de geçerlidir. Bu modeller, 
- metin sınıflandırma,
- soru yanıtlama,
- belge özetleme ve
- metin üretimi gibi yaygın dil sorunlarını çözmek için genel amaçlar için eğitilir. 
Modeller daha sonra, ilk eğitimine kıyasla daha küçük bir veri kümesi kullanılarak perakende, finans ve eğlence gibi farklı alanlarda belirli sorunları çözmek için uyarlanabilir.


Büyük dil modelleri kavramını üç ana özelliğe ayırarak daha da inceleyelim. 

"Büyük" iki anlama gelir:
1. İlk olarak, eğitim veri setinin muazzam büyüklüğünü ifade eder, bazen petabayt ölçeğinde. 
2. İkinci olarak, parametre sayısını ifade eder. Makine öğreniminde, parametreler genellikle **hiperparametreler** olarak adlandırılır.
   Parametreler, makinenin model eğitiminden öğrendiği bilgi ve becerilerdir.
   Parametreler, bir modelin bir sorunu çözme yeteneğini tanımlar, örneğin metin tahmini yapma.

"Genel amaçlı" modellerin yaygın sorunları çözmek için yeterli olduğunu ifade eder. Bu fikre iki neden yol açar. 
1. Birincisi, insan dilinin belirli görevlerden bağımsız olarak ortak özellikleri.
2. İkincisi, kaynak kısıtlaması.
   Yalnızca belirli kuruluşlar, büyük veri setleri ve muazzam parametre sayıları ile büyük dil modellerini eğitme yeteneğine sahiptir.
   Peki, bu temel dil modellerini başkalarının kullanması için oluşturmak neden olmasın?
   Bu, son noktaya, yani önceden eğitilmiş ve ince ayar yapılmış, yani genel amaçlar için büyük bir veri seti ile önceden eğitilmiş bir büyük dil modelini daha küçük bir veri seti ile belirli amaçlar için ince ayar yapmaya getirir.


### 2. Büyük Dil Modellerinin Kullanım Durumları

Büyük dil modellerinin kullanımının faydaları açıktır. İlk olarak, tek bir model farklı görevler için kullanılabilir. Petabaytlarca veri ile eğitilmiş ve milyarlarca parametre üreten bu büyük dil modelleri, dil çevirisi, cümle tamamlama, metin sınıflandırma, soru yanıtlama ve daha fazlası dahil olmak üzere farklı görevleri çözebilecek kadar zekidir.

Büyük dil modelleri çok çeşitli görevler için kullanılabilir:

- **Metin Sınıflandırma:** Gelen metinleri belirli kategorilere ayırmak. Örneğin, müşteri yorumlarını pozitif, negatif veya nötr olarak sınıflandırmak.
- **Soru Cevaplama:** Doğal dilde sorulan soruları yanıtlamak. Örneğin, "2023'te dünya nüfusu ne kadardı?" sorusuna doğru yanıt vermek.
- **Metin Üretimi:** Belirli bir konuda veya tarzda yeni metinler oluşturmak. Örneğin, Shakespeare tarzında bir şiir yazmak.

İkincisi, büyük dil modelleri, belirli bir sorunu çözmek için uyarlandığında minimum alan eğitim verisi gerektirir. Büyük dil modelleri, az miktarda alan eğitimi verisi ile bile makul bir performans elde eder. Diğer bir deyişle, az örnekle veya hatta hiç örnekle senaryolar için kullanılabilirler. Makine öğreniminde, **az örnekle eğitim**, bir modeli minimal veri ile eğitme anlamına gelir ve **hiç örnekle eğitim**, modelin daha önce eğitimde açıkça öğretilmemiş şeyleri tanıyabileceği anlamına gelir. 

Üçüncü olarak, daha fazla veri ve parametre eklediğinizde büyük dil modellerinin performansı sürekli olarak artar. Örneğin `PaLM`'ı ele alalım. Nisan 2022'de Google, birden fazla dil görevinde en son performansı elde eden 540 milyar parametreli bir model olan **Pathways Language Model**'i veya kısaca `PaLM`'ı yayınladı. 

`PaLM`, yalnızca bir **kodlayıcı-transformer modelidir**. Bir transformer modeli, bir kodlayıcı (encoder) ve bir kod çözücüden (decoder) oluşur. Kodlayıcı, girdi dizisini kodlar ve kod çözücüye iletir, bu da görevin ilgili temsillerini nasıl kodlayacağını öğrenir. 

![image](https://github.com/user-attachments/assets/a70ea85d-14d8-45af-9f87-9533e5234a40)

540 milyar parametresi vardır. Google'ın birden fazla TPU v4 Pod üzerinde tek bir modeli verimli bir şekilde eğitmesini sağlayan yeni yollar sistemini kullanır. Yollar, birden fazla görevi aynı anda ele alacak, yeni görevleri hızlı bir şekilde öğrenecek ve dünyayı daha iyi anlayacak yeni bir YZ mimarisidir. Sistem, PaLM'nin hızlandırıcılar için dağıtılmış hesaplamayı düzenlemesini sağlar.

Geleneksel programlamadan sinir ağlarına ve üretici modellere kadar uzun bir yol kat ettik. 

> **Geleneksel programlamada**, bir kediyi ayırt etmek için kuralları sert bir şekilde kodlamamız gerekiyordu; 
> ```
> türü: hayvan
> bacakları: 4
> kulakları: 2
> kürkü: var
> ```

> **Sinir ağlarında** (2012 ve sonrasında), ağımıza kedi ve köpek resimleri verip bu bir kedi mi diye sormamız yeterliydi ve kedi olduğunu tahmin ederdi. 

> **Üretken yapay zekada**, kullanıcılar olarak kendi içeriklerimizi üretebiliriz; metin, görüntüler, ses, video veya diğerleri. 

Örneğin, PaLM veya LaMDA (Language Model for Dialog Applications) gibi modeller, internetin çeşitli kaynaklarından çok büyük verileri alır ve sadece bir soru sorarak, ister bir prompt'a yazarak ister sözlü olarak konuşarak, temel dil modelleri oluştururlar. Yani bir kedi nedir diye sorduğunuzda, kedi hakkında öğrendiği her şeyi size verebilir.


### Önceden eğitilmiş modeller kullanarak LLM geliştirmeyi geleneksel ML geliştirme ile karşılaştıralım. 
Öncelikle LLM geliştirmede, bir uzman olmanıza gerek yoktur. Eğitim örneklerine ihtiyacınız yoktur ve bir model eğitmeye gerek yoktur. Yapmanız gereken tek şey, açık, öz ve bilgilendirici bir prompt oluşturmak olan **prompt tasarımı** hakkında düşünmektir. Bu, doğal dil işleme için önemli bir parçadır. 

Geleneksel makine öğreniminde, bir modeli eğitmek için eğitim örneklerine ihtiyacınız vardır. Ayrıca hesaplama süresi ve donanım gereklidir. Bir metin oluşturma kullanım durumu örneğine bakalım. Soru yanıtlama veya QA, doğal dil işleme alt alanıdır ve doğal dilde sorulan soruları otomatik olarak yanıtlamayı içerir. QA sistemleri genellikle büyük miktarda metin ve kod üzerinde eğitilir ve gerçekler, tanımlamalar ve görüşlere dayalı sorular dahil olmak üzere geniş bir yelpazede soruları yanıtlayabilir. Buradaki anahtar, bu soru yanıtlama modellerini geliştirmek için alan bilgisine ihtiyaç duyulmasıdır. Örneğin, müşteri BT desteği, sağlık hizmetleri veya tedarik zinciri için bir soru yanıtlama modeli geliştirmek alan bilgisi gerektirir. Generative QA kullanırken, model doğrudan bağlama dayalı olarak serbest metin üretir. Alan bilgisine ihtiyaç yoktur. Google AI tarafından geliştirilen büyük dil modeli sohbet botu Bard'a sorulan üç soruya bakalım.

Örnek: Bard adlı Google AI sohbet botuna şu soruları soralım:
- "Bu yılki satışlar $100,000. Giderler $60,000. Net kar ne kadar?" Bard net karı hesaplayarak cevabı verir: $40,000.
- "Stokta 6,000 birim var. Yeni sipariş 8,000 birim gerektiriyor. Siparişi tamamlamak için kaç birim doldurmam gerekiyor?" Bard doğru cevabı verir: 2,000 birim daha gerekir.
- Son örneğimizde, 10 coğrafi bölgede 1,000 sensörümüz var. Her bölgede ortalama kaç sensör var? Bard soruyu çözme yöntemini ve ek bağlamla birlikte yanıtlar.

Her bir sorumuzda istenen yanıt elde edildi. Bu, prompt tasarımı nedeniyle oldu. 

### Prompt tasarımı ve prompt mühendisliği
Prompt tasarımı ve prompt mühendisliği, doğal dil işleme ile ilgili iki yakından ilişkili kavramdır. Her ikisi de, sistemin yerine getirilmesi istenen göreve uygun bir prompt oluşturma sürecini içerir. Ancak, aralarında bazı temel farklılıklar vardır. Prompt tasarımı, sistemin yerine getirilmesi istenen göreve uygun bir prompt oluşturma sürecidir. 

Örneğin, sistemden bir metni İngilizceden Fransızcaya çevirmesi isteniyorsa, prompt İngilizce yazılmalı ve çevirinin Fransızca olması gerektiği belirtilmelidir. 

**Prompt mühendisliği**, performansı artırmak için tasarlanmış bir prompt oluşturma sürecidir. Bu, alan bilgisi kullanmayı, istenen çıktının örneklerini sağlamayı veya belirli sistem için etkili olduğu bilinen anahtar kelimeleri kullanmayı içerebilir. 

**Prompt tasarımı** daha genel bir kavramdır, oysa prompt mühendisliği daha özel bir kavramdır. Prompt tasarımı esastır, ancak prompt mühendisliği yalnızca yüksek doğruluk veya performans gerektiren sistemler için gereklidir. 

Üç tür büyük dil modeli vardır: 
1. genel dil modelleri,
2. talimat ayarlı ve
3. diyalog ayarlı.

Her biri farklı şekilde prompt edilmesi gerekenlerdir. 

**Genel dil modelleri**, eğitim verilerindeki dile dayanarak bir sonraki kelimeyi tahmin eder. Bu, genel bir dil modeli örneğidir. Bir sonraki kelime, eğitim verilerindeki dile dayalı olarak bir simgedir. Bu örnekte, kedi oturdu, bir sonraki kelime "the" (ve) olmalıdır ve "the" en olası bir sonraki kelimedir. Bu türü arama otomatik tamamlama gibi düşünün. 

**Talimat ayarlı model**de, model girdi olarak verilen talimatlara yanıt tahmin etmek üzere eğitilmiştir. Örneğin, x metnini özetle, x tarzında bir şiir oluştur, x için anlamsal benzerlik temelli anahtar kelimeler listesi ver. Bu örnekte, metni nötr, olumsuz veya olumlu olarak sınıflandırın. 

**Diyalog ayarlı model**de, model bir sonraki yanıtı tahmin ederek bir diyalog kurmak üzere eğitilmiştir. Diyalog ayarlı modeller, talimat ayarlının özel bir türüdür ve istekler tipik olarak bir sohbet botuna sorular olarak çerçevelenir. Diyalog ayarlama, genellikle daha uzun bir ileri-geri konuşma bağlamında beklenir ve tipik olarak doğal soru benzeri ifadelerle daha iyi çalışır. 

Düşünce zinciri akıl yürütme, modellerin doğru cevabı daha iyi elde ettiklerini gözlemleme sürecidir. 
Soruyu ele alalım: 
- Roger'ın 5 tenis topu var. 2 tane daha tenis topu alıyor. Her kutuda 3 tenis topu var. Şimdi kaç tenis topu var?
  Bu soru başlangıçta hiçbir yanıt verilmeden sorulmuştur. Modelin doğru cevabı doğrudan elde etme olasılığı daha düşüktür. Ancak, ikinci soru sorulduğunda, çıktı doğru cevapla sonuçlanma olasılığı daha yüksektir.

### Görev spesifik ayar
Her şeyi yapabilen bir modelin pratik sınırlamaları vardır. **Görev spesifik ayar**, LLM'leri daha güvenilir hale getirebilir. `Vertex AI`, görev spesifik temel modeller sağlar. 

Diyelim ki, müşterilerinizin ürün veya hizmetiniz hakkındaki duygularını toplamanız gereken bir kullanım durumunuz var. Sınıflandırma görevi **duygu analizi görev modeli**ni kullanabilirsiniz. İşgal analitiği yapmanız gereken aynı hüküm görevlerinde, kullanım durumunuz için görev spesifik bir model vardır. Bir modeli ayarlamak, modeli yerine getirmek istediğiniz görevin örneklerine dayalı olarak yanıtını özelleştirmenizi sağlar. Bu, modeli yeni bir alan veya özel kullanım durumları kümesine uyarlama sürecidir. 

Örneğin, eğitim verileri toplayabilir ve modeli özel olarak yasal veya tıbbi alan için ayarlayabiliriz. Ayrıca kendi veri setinizi getirip her LLM'deki ağırlığı yeniden eğiterek modeli ince ayarlayarak daha da ayarlayabilirsiniz. Bu, büyük bir eğitim işi ve kendi ince ayarlı modelinizi barındırmayı gerektirir. İşte sağlık verileri üzerinde eğitilmiş bir tıbbi temel model örneği. Görevler arasında soru yanıtlama, görüntü analizi, benzer hastaları bulma ve benzeri bulunmaktadır. 

İnce ayar pahalıdır ve birçok durumda gerçekçi değildir. Peki, **daha verimli ayarlama yöntemleri var mı?** 

Evet, parametre verimli ayarlama yöntemleri (`PETM`), büyük bir dil modelini kendi özel verileriniz üzerinde ayarlama yöntemleridir ve modeli kopyalamadan yapabilirsiniz. Temel modelin kendisi değiştirilmez. Bunun yerine, az sayıda ek katman ayarlanır ve bunlar çıkarım sırasında takas edilebilir. Generative AI Studio, Google Cloud'da uygulamalarınızda kullanabileceğiniz üretici AI modellerini hızla keşfetmenize ve özelleştirmenize olanak tanır. Generative AI Studio, geliştiricilere başlamak için çeşitli araçlar ve kaynaklar sağlayarak üretici AI modelleri oluşturmayı ve dağıtmayı kolaylaştırır. Örneğin, önceden eğitilmiş modeller kütüphanesi, modelleri ince ayarlama aracı, modelleri üretime dağıtma aracı ve geliştiricilerin fikirlerini paylaşması ve işbirliği yapması için bir topluluk forumu vardır. Vertex AI Arama ve Konuşma ile müşteriler ve çalışanlar için üretici AI arama ve konuşmalar oluşturun, eski adıyla Gen AI App Builder. Az veya hiç kodlama ve önceden makine öğrenimi deneyimi olmadan inşa edin. Kendi sohbet botlarınızı, dijital asistanlarınızı, özel arama motorlarınızı, bilgi tabanlarınızı, eğitim uygulamalarınızı ve daha fazlasını oluşturabilirsiniz. PaLM API, Google'ın büyük dil modelleri ve üretici AI araçlarıyla test yapmanızı ve deney yapmanızı sağlar. Prototiplemeyi hızlı ve daha erişilebilir hale getirmek için geliştiriciler PaLM API'yi MakerSuite ile entegre edebilir ve grafik kullanıcı arayüzü kullanarak API'ye erişebilir. Suite, model eğitme aracı, model dağıtma aracı ve model izleme aracı gibi çeşitli araçlar içerir. Model eğitme aracı, geliştiricilerin verileri üzerinde ML modelleri eğitmesine yardımcı olur. Model dağıtma aracı, geliştiricilerin modelleri çeşitli dağıtım seçenekleriyle üretime dağıtmasına yardımcı olur. Model izleme aracı, geliştiricilerin modellerinin üretimdeki performansını bir gösterge tablosu ve çeşitli metrikler kullanarak izlemesine yardımcı olur.

### 3. Prompt Tuning (Ön Ayar) Nedir?

**Prompt Tuning**, bir dil modelini belirli bir görev için optimize etme sürecidir. Bu, modelin daha iyi sonuçlar vermesi için uygun prompt'ları (giriş) tasarlamayı içerir. 

Örnek: Bir dil modeline "Bu metni özetle:" prompt'u ile bir paragraf verdiğinizde, model metni özetler. Ancak, daha karmaşık görevlerde daha spesifik prompt'lar gerekebilir. 

### 4. Google'ın Generative AI Geliştirme Araçları

Google, büyük dil modellerini geliştirmek ve kullanmak için çeşitli araçlar sunar:

- **Generative AI Studio:** Üretici AI modellerini keşfetmenize ve özelleştirmenize olanak tanır.
- **Vertex AI:** Özel AI arama ve konuşma uygulamaları oluşturmanızı sağlar.
- **PaLM API ve MakerSuite:** PaLM dil modeli ve diğer üretici AI araçlarıyla çalışmanızı kolaylaştırır.

Örnek: Vertex AI kullanarak, müşteri destek hizmetlerinde bir sohbet botu oluşturabilirsiniz. Bu bot, müşterilerin sorularını yanıtlar ve onlara yardımcı olur. Ayrıca, PaLM API'yi kullanarak bir metin oluşturma uygulaması geliştirebilir ve bunu web sitenize entegre edebilirsiniz.

---

Büyük Dil Modellerine Giriş kursunu tamamladığınız için teşekkürler! Bu bilgilerle büyük dil modellerinin temellerini öğrenmiş oldunuz.
