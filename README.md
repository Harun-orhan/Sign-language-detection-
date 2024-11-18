Kod İncelemesi ve Rapor
Amaç:
Bu kod, gerçek zamanlı video akışında insan hareketlerini algılayıp işaret diline çevirmek için geliştirilen bir sistemdir. Mediapipe kullanılarak vücut, yüz ve el işaretleri algılanır. Tespit edilen hareketler, önceden eğitilmiş bir model yardımıyla sınıflandırılır ve algılanan hareketlerin metin karşılıkları sesli olarak ifade edilir.

Kullanılan Kütüphaneler ve Amaçları:
OpenCV:
Kameradan görüntü almak, işlemek ve kullanıcıya göstermek için kullanılır.
NumPy:
Sayısal hesaplamalar ve dizi işlemleri için kullanılır.
Mediapipe:
İnsan vücudu, yüz, el ve poz işaretlerini algılamak için kullanılır.
TensorFlow/Keras:
LSTM (Long Short-Term Memory) modeli ile hareket sınıflandırma gerçekleştirilir.
pyttsx3:
Tespit edilen hareketlerin sesli bir şekilde ifade edilmesini sağlar.
Threading:
Konuşma işleminin eş zamanlı olarak yapılabilmesi için kullanılır.
Kodun Genel Yapısı:
Model Tanımlama ve Yükleme:

Kodda, önceden eğitilmiş bir LSTM modeli (action.h5) yüklenir.
Modelin girdi boyutları (30, 1662) olup, 30 zaman diliminden oluşan verileri işler.
Mediapipe Algılama Fonksiyonları:

mediapipe_detection: Görüntü işleme ve insan işaretlerinin algılanmasını sağlar.
draw_landmarks ve draw_styled_landmarks: Algılanan işaretlerin videoya çizilmesini sağlar.
extract_keypoints: Algılanan işaretlerden anahtar noktaları çıkarır.
Gerçek Zamanlı İşlem Döngüsü:

Kamera görüntüsü okunur ve aynalama uygulanır.
Mediapipe ile işaretler algılanır ve anahtar noktalar modele verilir.
Model, bu verileri sınıflandırarak hareketleri tespit eder.
Tespit edilen hareketler ekrana yazdırılır ve sesli olarak ifade edilir.
Sesli İfade:

pyttsx3 kütüphanesi kullanılarak tespit edilen hareketler konuşulur. async_speak_action fonksiyonu sayesinde konuşma işlemi eş zamanlı yürütülür.
Kullanıcı Arayüzü:

Tespit edilen hareketler OpenCV penceresinde metin olarak gösterilir.
Kullanıcı, q tuşuna basarak uygulamayı kapatabilir.
Kodun Güçlü Yönleri:
Modüler Yapı:

Algılama, işleme ve sınıflandırma işlemleri farklı fonksiyonlar altında toplanmış.
Bu yapı, kodun okunabilirliğini ve bakımını kolaylaştırır.
Gerçek Zamanlı Performans:

Mediapipe kullanımı sayesinde işaretler hızlı ve doğru bir şekilde algılanır.
LSTM modeli ile zaman bağımlı hareketler etkili bir şekilde sınıflandırılır.
Sesli Geri Bildirim:

Tespit edilen hareketlerin sesli olarak ifade edilmesi kullanıcı deneyimini artırır.
Esneklik:

Klasifikasyon hassasiyeti, threshold parametresiyle kolayca ayarlanabilir.


Kodun Genel Çalışma Mantığı:
Kod, kamera akışından gerçek zamanlı olarak insan hareketlerini algılar, bu hareketleri önceden eğitilmiş bir model ile sınıflandırır ve ardından bu hareketlerin adını hem ekranda gösterir hem de sesli olarak ifade eder. Bu sistem, işaret dilinin anlaşılmasını kolaylaştırmak için özellikle faydalıdır.
