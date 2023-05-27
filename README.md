# 2.KISASINAV2.ODEVIGORSELTANIMA-TESPITETME
Dökümantasyon
OpenCV Image Template mathing yöntemi
OpenCV Image Template Matching, görüntü işleme alanında yaygın olarak kullanılan bir yöntemdir. Bu yöntem, bir şablon (template) görüntüsünü bir kaynak görüntü üzerinde aramak ve şablonun en iyi eşleşen bölgesini bulmak için kullanılır. Template Matching, bir görüntüde belirli bir desenin veya nesnenin varlığını tespit etmek için kullanılabilir.
Yöntemin temel mantığı, şablon görüntüsünü kaynak görüntü üzerinde kaydırarak her konumda bir benzerlik skoru hesaplamaktır. Benzerlik skoru, template ile kaynak görüntü arasındaki benzerlik derecesini temsil eder. Template ve kaynak görüntü arasındaki benzerlik, genellikle piksel değerlerinin karşılaştırılması veya matematiksel hesaplamalar kullanılarak ölçülür.
OpenCV'de Template Matching işlemi cv2.matchTemplate() fonksiyonuyla gerçekleştirilir. Bu fonksiyon, farklı eşleştirme yöntemlerini destekler ve sonuç olarak benzerlik haritasını döndürür. Benzerlik haritası, kaynak görüntü üzerinde her bir pikselin şablon ile olan benzerlik skorunu gösterir. Ardından, bu benzerlik haritası üzerinde belirli bir eşik değeri veya maksimum benzerlik değeri kullanılarak eşleşen bölgeler tespit edilebilir.
Özetle, OpenCV Image Template Matching yöntemi, bir şablon görüntüsünü bir kaynak görüntü üzerinde arayarak benzerlik skorlarını hesaplar ve en iyi eşleşen bölgeyi bulmamıza olanak sağlar. Bu yöntem, nesne tespiti, yüz tanıma, desen tanıma ve görüntü hizalama gibi birçok uygulamada kullanılabilir.
Bu Algoritmamızın Zaman Karmaşıklığı Hesabı
Bu algoritmanın zaman karmaşıklığını analiz etmek için, en önemli faktörlerden biri template dosyalarının sayısı (n) olacaktır. Diğer faktörler, template ve görüntü boyutları gibi değişkenler olarak ele alınabilir.
Algoritmanın genel zaman karmaşıklığı şu adımları içerir:
1.	Template dosyalarını okuma: Bu adım, template dosyalarının diskten okunması işlemidir. Template dosyalarının sayısı (n) ve dosya boyutlarına bağlı olarak karmaşıklık O(n).
2.	Template'leri ölçeklendirme: Her bir template, 20x20 piksel boyutuna ölçeklendirilir. Bu işlem, template dosyalarının sayısı (n) ile doğrusal olarak artar. Karmaşıklık O(n).
3.	Template matching işlemi: Her bir template için template matching işlemi yapılır. Bu işlem, görüntü boyutu ve template boyutuna bağlı olarak farklılık gösterir. Template matching işleminin karmaşıklığı genellikle O(m * n), burada m görüntü boyutu ve n template boyutudur.
4.	Benzerlik oranlarının sıralanması: Benzerlik oranlarına göre sıralama yapmak için bir sıralama işlemi yapılır. Bu işlem, benzerlik oranlarının sayısına bağlı olarak genellikle O(n log n) karmaşıklığına sahiptir.
Bu adımları birleştirdiğimizde, algoritmanın genel zaman karmaşıklığı aşağıdaki gibi olur:
O(n) + O(n) + O(m * n) + O(n log n)
Bu, genel karmaşıklığı temsil eden bir ifadedir. Ancak, template dosyalarının sayısı (n) ve görüntü boyutu (m) gibi faktörlerdeki değişiklikler bu ifadeyi etkileyecektir. 

Kodumuzun Çalışma Zamanı Hesabı 
Bu algoritmanın çalışma zamanını analiz ederken, dikkate alabileceğimiz bazı faktörler şunlardır:
1.	Template Dosyalarının Sayısı (n): Algoritmanın template dosyalarını okuma ve benzerlik oranlarını hesaplama süresi, template dosyalarının sayısına bağlı olarak doğrusal olarak artar.
2.	Görüntü Boyutu: Template matching işlemi, görüntü boyutuna bağlı olarak süreye etki eder. Daha büyük görüntüler daha uzun süreler gerektirebilir.
3.	Template Boyutu: Template'leri 20x20 piksel boyutuna ölçeklendirme işlemi, her bir template için sabit bir süre gerektirir.
4.	Template Matching Algoritması: Bu örnekte cv2.matchTemplate fonksiyonu kullanılıyor. Template matching algoritmasının karmaşıklığı, template boyutuna ve görüntü boyutuna bağlı olarak değişebilir. Bu algoritmanın özellikle büyük görüntülerle ve çok sayıda template ile çalıştığında performans etkisi gösterebilir.
Bu faktörleri birleştirerek algoritmanın yaklaşık çalışma zamanını tahmin edebiliriz. Ancak, tam bir değer vermek için belirli bir senaryo ve veri seti üzerinde testler yapmak gerekmektedir.
Örneğin, 100 template dosyası ve 100x100 piksel boyutunda bir görüntü kullanırsak, algoritmanın çalışma süresi birkaç saniye civarında olabilir. Ancak, template dosyalarının ve görüntünün boyutları arttıkça, algoritmanın çalışma süresi de artacaktır.

Kodumuzun Açıklaması
Bu kodda, öncelikle OpenCV (cv2) ve NumPy (np) kütüphaneleri içe aktarılıyor. Ardından, glob modülü kullanılarak bir dizindeki dosyaların listesi alınıyor.
template_matching fonksiyonu, template matching işlemini gerçekleştiriyor. Verilen bir template ve bir görüntü üzerinde template matching uygulayarak benzerlik oranını döndürüyor.
image_path değişkeni, template matching uygulanacak olan görüntünün yolunu temsil ediyor. Bu görüntü cv2.imread fonksiyonu ile okunuyor.
templates_dir değişkeni, template dosyalarının bulunduğu dizini temsil ediyor. glob.glob fonksiyonu kullanılarak tüm template dosyalarının listesi alınıyor.
Daha sonra, template dosyaları okunuyor ve benzerlik oranları hesaplanıyor. Her bir template önce cv2.resize fonksiyonu ile 20x20 piksel boyutuna ölçeklendiriliyor. Sonrasında template_matching fonksiyonu ile template ve görüntü arasındaki benzerlik oranı hesaplanıyor. Benzerlik oranları similarities listesine ekleniyor.
similarities listesi, benzerlik oranlarına göre sıralanıyor. similarities.sort fonksiyonu kullanılarak, benzerlik oranına göre sıralama yapılıyor.
get_decimal_places fonksiyonu, benzerlik oranının virgülden sonraki kısmını sayı olarak alıyor.
Son olarak, similarities listesindeki sonuçlar ekrana yazdırılıyor. for döngüsü ile liste üzerinde gezilerek template yolunu ve benzerlik oranını yazdırılıyor.
Kodun karmaşıklığı, template dosyalarının sayısına bağlı olarak değişir. Template dosyalarının sayısı arttıkça, template matching işlemi ve benzerlik oranlarının hesaplanması daha fazla zaman alabilir. Ancak, bu kodun karmaşıklığı genel olarak O(n), yani template dosyalarının sayısına bağlı olarak doğrusal olarak artar.

