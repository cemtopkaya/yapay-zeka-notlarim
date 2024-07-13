**Genel Bakış: Prompting**
**Giriş**

İleri seviye prompt mühendisliği teknikleri, büyük dil modellerinin daha doğru, tutarlı ve ilgili çıktılar üretmesini sağlayarak performanslarını önemli ölçüde artırabilir. 
Bu yazıda, dil modellerinin yeteneklerini etkili bir şekilde kullanmayı öğrenerek, belirli kullanım senaryolarına uyum sağlamalarını, önyargıları minimize etmelerini ve yüksek kaliteli çıktılar sunmalarını sağlayacaksınız. 
- İlk olarak, temel prompting tekniklerinin ötesine geçerek, bir modelin performansını artıran ileri teknikleri öğreneceksiniz. 
- Ardından, belirli kullanım senaryoları için prompt optimizasyonunun sanatını keşfedeceksiniz. 
- Son olarak, gecikme ve performansı etkileyen ana faktörleri anlayacak ve bu sorunları hafifletme tekniklerini öğreneceksiniz.  

İlk modülümüz "Genel Bakış: Prompting". Prompt mühendisliğinin temellerini keşfedeceğiz ve 
- sıfır-atış öğrenme,
- az-atış öğrenme ve
- talimat prompting
gibi yaygın teknikleri inceleyeceğiz. Ayrıca promptların neden başarısız olduğunu da gözden geçireceğiz.

## Prompting Temelleri

Öncelikle prompting temelleriyle başlayalım. Prompt mühendisliği nedir? Prompt mühendisliği, insanlar ile yapay zeka modelleri arasındaki iletişimi şekillendirerek daha iyi etkileşim ve istenen sonuçların elde edilmesini sağlar. 
Bu, modelin istenen görevi yerine getirmesi için uygun bağlamın sağlanmasıdır. Prompt mühendisliği, müzisyene ince ayarlı bir enstrüman hazırlamak gibidir. 
Enstrüman, müzisyenin tercihlerine ve çalma tarzına göre ayarlanmalıdır, **tıpkı promptların dil modelini yönlendirecek şekilde dikkatle tasarlanması gibi**. 
Promptları ayarlayarak, modelin davranışını ince ayarlar ve mükemmel sesi elde edersiniz. 

* Bir prompt, "Pinot Noir ile en iyi uyum sağlayan peyniri söyleyebilir misin?" kadar basit olabilir ve modelin cevabı "brie" olacaktır.
* Daha karmaşık bir prompt olan **talimat promptu** ise, "Bu makale özetini düzeltin, daha eğlenceli hale getirin, APA stil kılavuzuna uygun olmasını sağlayın ve teknik bir okuyucuya yönelik olsun, çıktınızı markdown formatında döndürün" kadar detaylı olabilir ve özetlenecek metni de içerebilir.

Promptlar genellikle birkaç öğe içerir ve tüm öğeler gerekli değildir. 
- BAĞLAM
  İlk olarak, modelin görevi veya istenen çıktıyı anlamasına yardımcı olan bağlamınız vardır. Bağlam, modelin daha iyi yanıtlar vermesini sağlar.
- GİRDİ
  Girdi verileriniz, modelin işlemesini istediğiniz gerçek veridir.
- TALİMAT
  Ardından, modelden ne yapmasını istediğinizi metinsel olarak tanımlayan talimatlar
- ÖRNEKLER
  modelin doğru davranışını gösteren örnekler
- KISITLAR
  ve belirli gereksinimlere dayalı olarak modelin çıktısını kısıtlayan kısıtlamalar vardır.

İşte bir örnek prompt:
  * İlk olarak, **bağlam** var: "Kullanıcı tercihleri temelinde kişiselleştirilmiş kitap önerileri oluşturan bir yapay zeka asistanısınız."
  * Sonra **girdi** verisi var: "Bir kullanıcı profili."
  * Sonra **talimat**: "Bu kullanıcı için beş kitap önerebilir misiniz?"
  * Ayrıca **örnekler** de ekleyebilirsiniz, yani örnek girdi ve örnek çıktı, ve kısıtlamalar ekleyebilirsiniz.
    Örneğin, "Oluşturulan önerilerin kullanıcının tercih ettiği türler içinde olmasını ve favori yazarlarıyla uyumlu olmasını sağlayın.
    Örneklerdeki kitapları önermeyin ve yanıtlarınızda dostça ve ilgi çekici bir ton koruyun."
Artık promptların nasıl oluşturulduğunu daha iyi anladığınıza göre, bir promptın nasıl çalıştığını görelim.

### Demo: ChatGPT'nin Çalışması

Bu demoda, ChatGPT'nin promptumuza yanıtını inceleyeceğiz. Yanıt aynı zamanda tamamlanma olarak da adlandırılır. Jupyter Notebook'a geçelim. Bu Jupyter Notebook'ta, ChatGPT ile etkileşim kurmak için OpenAI'nın API'sini kullanıyoruz. Bunu yapmak için, OpenAI, urllib gibi birkaç kütüphaneyi kurmamız gerekiyor. Bu kütüphaneleri zaten kurdum, bu yüzden bu kod satırlarını çalıştırmayacağım. OpenAI API'sine programatik olarak erişmek için bir API anahtarı kurmanız gerekecek çünkü API anahtarı kullanılarak güvence altına alınır ve bunu kurmak için bir OpenAI hesabı oluşturmanız ve ardından hesabınıza giderek bu anahtarı oluşturmanız gerekecek. Bu anahtarı yerel olarak bir ortam dosyasında sakladım ve bu dosyayı çekip anahtarı almam gerekiyor. İşte bu kod parçasında yaptığım şey bu. Önce OS'u içe aktarıyorum, sonra OpenAI'yi içe aktarıyorum ve burada, Satır 5 ve 6'da, ortam dosyamı okuyorum. Ardından, API anahtarı kullanarak API'ye kimlik doğrulaması yapmanız gerekiyor ve bunu yapmanın yolu, OpenAI kütüphanesinden API anahtarını başlatmaktır ve ben onu ortam değişkenimden çekiyorum. Sonra prompt geliyor. Bu, büyük dil modeline göndereceğimiz şey. Bu, daha önce gördüğümüz prompt. Bu ilk satırda, Satır 4 ve 5'te, bağlamı belirliyorum: "Kullanıcı tercihleri temelinde kişiselleştirilmiş kitap önerileri oluşturan bir yapay zeka asistanısınız." Sonraki birkaç satırda, örnek girdiler ve örnek çıktılar gönderiyorum. Burada, Satır 10'da, ilk girdi bir kullanıcı profili. Satır 14'te, modelden kitap önerilerini bekliyorum. Bu, modelin istediğiniz belirli çıktıyı üretmesini yönlendirmenin bir yoludur. Burada, Satır 21'de, başka bir örnek girdi, kullanıcı profili ve örnek çıktı sağlıyorum. Satır 30'da, kısıtlamaları detaylandırıyorum, bu nedenle oluşturulan önerilerin kullanıcının tercih ettiği türler içinde olmasını sağlayın. Modelin sağladığım örneklerden kitapları önermesini istemiyorum ve yanıtlar boyunca dostça ve ilgi çekici bir ton korumasını istiyorum. Burada, girdi verilerini sağlıyorum, yani kullanıcı profilini. Kişi 12 yaşında. Tercih edilen tür bilim kurgu. Ayrıca iki favori yazarını da geçiyorum. Satır 42'de, modele özel talimatı veriyorum: "Bu kullanıcı için beş kitap önerebilir misiniz?" Bu kodu çalıştıracağım çünkü çalışması biraz zaman alıyor ve çalışırken ne yaptığımızı açıklayayım. Burada, OpenAI kütüphanesini kullanarak ChatCompletion API'sini çağırıyoruz ve Satır 2'de, çağırmak istediğimiz modeli belirtiyoruz, bu durumda gpt-3.5, yani ChatGPT. Mesajları gönderdiğimizde bir yanıt alacağız. Burada, Satır 1'de, modelin yanıtını yazdırmak için bu kodu çalıştırıyorum ve modelin yanıtında beş kitap görüyoruz. Model, "Kesinlikle, tercihlerinize göre, beğeneceğinizi düşündüğüm beş kitap seçtim: A Wrinkle in Time, Superfudge, Ender's Game, The Giver ve The Hitchhiker's Guide to the Galaxy." diyor. Ve model yanıtını çok dostça bir tonla bitiriyor: "Bu kitap önerilerini beğeneceğinizi umuyorum. İyi okumalar." Yerel olarak bilgisayarınızda bu kodu çalıştırdığınızda yanıtların farklı olabileceğini fark edebilirsiniz ve bu beklenendir. Yanıtlar girdiye bağlı olarak rastgele üretilir ve hatta girdi aynı olsa bile, çıktı farklı olabilir çünkü model stokastik olarak kabul edilir. Aynı promptu kullanırsanız bile, her seferinde farklı sonuçlar görürsünüz. Stokastikliği, modelin değişkenliği veya rastgeleliği olarak düşünebilirsiniz çünkü belirli bir çıktı asla kesin olarak tahmin edilemez. İşte böyle. ChatGPT'yi çalışırken gördünüz.

**Prompt Geliştirme**

Şimdi prompt geliştirmenin yinelemeli doğasını konuşalım. Prompt mühendisliği, modelin performansını artırmak için promptun sürekli olarak

 iyileştirilmesini içerir. Bu yinelemeli süreç, bir bilim insanının titizlikle deney yapmasına benzer. Bir bilim insanı, sürekli olarak teorilerini test eder, verileri analiz eder ve hipotezlerini rafine eder. Benzer şekilde, bir prompt mühendisi, modelin çıktıları üzerinde deney yapar, performansı değerlendirir ve optimize edilmiş sonuçlar elde etmek için promptu ayarlar. İlk yineleme, mevcut performansı değerlendirip iyileştirme fırsatlarını belirlerken, sonraki yinelemeler modelin çıktıları üzerinde hassas ayar yapar. Amaç, modelin belirli görevlerde daha doğru ve tutarlı yanıtlar üretmesini sağlamaktır. Yinelemeli prompt mühendisliği yaklaşımı, doğruluğu artırarak modelin performansını önemli ölçüde artırır. Bu süreç, kapsamlı testler, kullanıcı geri bildirimleri ve çıktılara ince ayar yapmayı içerir. Performansın sürekli olarak değerlendirilmesi ve promptların optimize edilmesi, modelin daha güvenilir ve etkili hale gelmesini sağlar. Bu yöntemle, dil modellerinin potansiyelini tam anlamıyla kullanabilir ve belirli kullanım senaryolarına en iyi şekilde hizmet etmelerini sağlayabilirsiniz. İleri seviye prompt mühendisliği tekniklerini kullanarak, dil modellerinin yeteneklerini etkili bir şekilde kullanmayı öğrenerek, belirli kullanım senaryolarına uyum sağlamalarını, önyargıları minimize etmelerini ve yüksek kaliteli çıktılar sunmalarını sağlayacaksınız.

**Sıfır ve Az-Atış Öğrenme**

Sıfır-atış öğrenme, dil modeline belirli bir görevi yerine getirmesi için herhangi bir örnek sağlamadan yapılan prompting türüdür. Sıfır-atış prompting, modelin daha önce görmediği görevleri gerçekleştirmesi için kullanılabilir. İşte sıfır-atış prompting örneği. Prompt: "Bir panda hakkında beş eğlenceli gerçek yazabilir misin?" Modelin tamamlanması: "Kesinlikle! İşte bir panda hakkında beş eğlenceli gerçek: 1. Pandalar neredeyse tamamen bambu yerler, diyetlerinin %99'u bu bitkiden oluşur. 2. Bir panda günde 12 saat boyunca yemek yiyebilir ve bu süre içinde 12-38 kilogram bambu tüketebilir. 3. Pandalar yalnız yaşamayı tercih ederler ve bölgelerini korurlar. 4. Panda yavruları doğduklarında sadece 100-200 gram ağırlığındadırlar ve tamamen kördürler. 5. Pandaların siyah beyaz kürkleri, kamuflaj ve sıcaklık düzenlemesi için evrimleşmiştir." Az-atış öğrenme ise, modelin belirli bir görevi yerine getirmesi için birkaç örnek sağlanarak yapılan prompting türüdür. Az-atış prompting, modelin belirli bir görevde daha iyi performans göstermesi için kullanılabilir. İşte az-atış prompting örneği. Prompt: "Aşağıdaki girdilere dayanarak benzer girdiler oluştur: Örnek girdi: 'Bir köpek hakkında beş eğlenceli gerçek.' Örnek çıktı: 'Kesinlikle! İşte bir köpek hakkında beş eğlenceli gerçek: 1. Köpekler dünyadaki en çeşitli türlerden biridir, yaklaşık 340 farklı ırk vardır. 2. Köpekler insan kokularını ve duygularını tespit edebilirler. 3. Bir köpeğin burun izi, bir insanın parmak izi gibi benzersizdir. 4. Köpekler, insanların konuşmalarındaki yaklaşık 250 kelimeyi ve hareketi anlayabilirler. 5. Köpekler, sahiplerinin ruh hallerini ve sağlığını algılayabilirler.' Girdi: 'Bir panda hakkında beş eğlenceli gerçek.'"

**Talimat Prompting**

Talimat prompting, modelden belirli bir görevi yerine getirmesini istemek için talimatlar sağlamayı içeren prompting türüdür. İşte talimat prompting örneği. Prompt: "Aşağıdaki cümleleri İngilizceye çevir: Cümle 1: 'Merhaba, nasılsın?' Cümle 2: 'Bugün hava çok güzel.'" Modelin tamamlanması: "Cümle 1: 'Hello, how are you?' Cümle 2: 'The weather is very nice today.'" Şimdi, az-atış prompting, sıfır-atış prompting ve talimat prompting örneklerini gördünüz. Bir promptun başarısız olduğu zamanlar olabilir. Bunu neden olduğunu öğrenmek önemlidir.

**Promptların Neden Başarısız Olduğunu Anlamak**

Promptların neden başarısız olduğunu anlamak, daha etkili promptlar oluşturmanın anahtarıdır. Bir promptun başarısız olmasının birkaç yaygın nedeni vardır: Bağlam eksikliği: Model, belirli bir görevi yerine getirmek için yeterli bağlam veya bilgiye sahip olmayabilir. Net olmayan talimatlar: Talimatlar belirsiz veya yetersiz olabilir, bu da modelin istenen görevi yanlış anlamasına neden olabilir. Yanlış örnekler: Sağlanan örnekler, istenen çıktıyı yeterince temsil etmeyebilir, bu da modelin doğru sonuçlar üretmesini zorlaştırabilir. Aşırı kısıtlamalar: Kısıtlamalar, modelin istenen çıktıyı üretmesini zorlaştırabilir. Şimdi, promptların neden başarısız olabileceğini daha iyi anladığınıza göre, etkili promptlar oluşturmak için bu bilgiyi kullanabilirsiniz. İlk modülümüzü tamamladınız. Artık prompting temellerini, sıfır ve az-atış öğrenmeyi, talimat prompting ve promptların neden başarısız olduğunu anlıyorsunuz. Bir sonraki modülde, belirli kullanım senaryoları için ileri prompting tekniklerini keşfedeceğiz.

**Özet ve İleri Düzey Prompting'e Geçiş**

Bu modülde öğrendiklerimizi özetleyelim. İlk olarak, prompting temellerini keşfettik ve sıfır-atış öğrenme, az-atış öğrenme ve talimat prompting gibi yaygın teknikleri inceledik. Ardından, bir promptun nasıl çalıştığını ve ChatGPT'nin promptumuza yanıtını inceledik. Son olarak, promptların neden başarısız olabileceğini ve bu durumlardan nasıl kaçınılacağını öğrendik. Şimdi, ileri düzey prompting tekniklerine geçiş yapacağız. Bu teknikler, modelin performansını daha da artırarak, belirli kullanım senaryolarına uyum sağlamasını, önyargıları minimize etmesini ve yüksek kaliteli çıktılar sunmasını sağlayacak. Bir sonraki modülde görüşmek üzere.
