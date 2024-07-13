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

Büyük dil modelleri çok çeşitli görevler için kullanılabilir:

- **Metin Sınıflandırma:** Gelen metinleri belirli kategorilere ayırmak. Örneğin, müşteri yorumlarını pozitif, negatif veya nötr olarak sınıflandırmak.
- **Soru Cevaplama:** Doğal dilde sorulan soruları yanıtlamak. Örneğin, "2023'te dünya nüfusu ne kadardı?" sorusuna doğru yanıt vermek.
- **Metin Üretimi:** Belirli bir konuda veya tarzda yeni metinler oluşturmak. Örneğin, Shakespeare tarzında bir şiir yazmak.

Örnek: Bard adlı Google AI sohbet botuna şu soruları soralım:
- "Bu yılki satışlar $100,000. Giderler $60,000. Net kar ne kadar?" Bard net karı hesaplayarak cevabı verir: $40,000.
- "Stokta 6,000 birim var. Yeni sipariş 8,000 birim gerektiriyor. Siparişi tamamlamak için kaç birim doldurmam gerekiyor?" Bard doğru cevabı verir: 2,000 birim daha gerekir.

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
