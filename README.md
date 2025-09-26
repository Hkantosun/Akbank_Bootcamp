# Akbank_Bootcamp
TensorFlow ve Keras kullanılarak Fashion MNIST veri seti üzerinde geliştirilmiş CNN tabanlı bir görüntü sınıflandırma projesi. Veri artırma teknikleri ile model, 10 kıyafet sınıfını yüksek doğrulukla tahmin eder; performans confusion matrix ve sınıflandırma raporu ile analiz edilmiştir

**Giriş**

Bu proje kapsamında, TensorFlow ve Keras kullanılarak Fashion MNIST veri seti üzerinde derin öğrenme tabanlı bir sınıflandırma modeli geliştirilmiştir. Fashion MNIST veri seti, 28x28 boyutunda gri tonlamalı 70.000 adet görüntü ve 10 sınıftan oluşan etiketler içermektedir: Tişört/Üst, Pantolon, Kazak, Elbise, Ceket, Sandalet, Gömlek, Spor Ayakkabı, Çanta ve Bot.

Projenin amacı, Convolutional Neural Network (CNN) mimarisi ile kıyafet görsellerinin doğru sınıflandırılmasını sağlamaktır. Model, eğitim verileri üzerinde öğrenme gerçekleştirir ve test verileri üzerinde doğruluk ve hata oranlarını değerlendirir.

**Kullanılan Yöntemler ve Algoritmalar**

-Veri Ön İşleme ve Görselleştirme-

Etiketler one-hot encoding formatına dönüştürüldü.
Görsellerin boyutu (28,28,1) olacak şekilde yeniden şekillendirildi.
Eğitim ve test veri setlerinin sınıf dağılımları görselleştirildi.

-Data Augmentation (Veri Artırma)-
Eğitim verisine rastgele döndürme (rotation_range=15), yatay/dikey kaydırma (width_shift_range=0.1, height_shift_range=0.1), yatay çevirme (horizontal_flip=True) ve yakınlaştırma (zoom_range=0.1) uygulandı.
Bu sayede model, daha genelleştirilebilir ve overfitting’e karşı dayanıklı hale getirildi.

-CNN Modeli-
Model, iki blok 32 filtreli ve iki blok 64 filtreli Conv2D katmanları ile oluşturuldu.
Her blokta BatchNormalization ve MaxPooling kullanıldı.
Flatten sonrası 128 nöronlu Dense katman ve 10 sınıf için softmax çıkışı eklendi.
Aktivasyon fonksiyonları: ReLU (ara katmanlar), Softmax (çıkış katmanı).

-Modelin Derlenmesi ve Eğitim-

Optimizer: Adam
Kayıp Fonksiyonu: Categorical Crossentropy
Metric: Accuracy
Callbacks: EarlyStopping (10 epoch sabırsızlık), ReduceLROnPlateau (5 epoch sabırsızlık)
Epoch: 50, Batch Size: 64

**Model Performansı**
Eğitim ve Doğrulama Grafikleri

Modelin eğitim ve doğrulama doğruluğu, epochlar boyunca artış gösterdi.
Eğitim kaybı azalarak modelin öğrenme sürecini doğru şekilde tamamladığını gösterdi.

Grafik Özetleri:

Eğitim Accuracy: %93 civarında
Test Accuracy: %92.63
Eğitim Loss: 0.2111
Test Loss: 0.2111

| Sınıf       | Precision | Recall | F1-Score |
| ----------- | --------- | ------ | -------- |
| T-shirt/top | 0.90      | 0.86   | 0.88     |
| Trouser     | 1.00      | 0.99   | 0.99     |
| Pullover    | 0.93      | 0.87   | 0.90     |
| Dress       | 0.94      | 0.90   | 0.92     |
| Coat        | 0.88      | 0.91   | 0.90     |
| Sandal      | 0.98      | 0.99   | 0.98     |
| Shirt       | 0.75      | 0.82   | 0.78     |
| Sneaker     | 0.96      | 0.96   | 0.96     |
| Bag         | 0.98      | 1.00   | 0.99     |
| Ankle boot  | 0.97      | 0.95   | 0.96     |

Macro F1: 0.9267
Macro Precision: 0.9278
Macro Recall: 0.9263

**Sonuçlar ve Gelecek Çalışmalar**

CNN modeli, Fashion MNIST veri setinde yüksek doğruluk (%92.6) elde etti.
Model özellikle pantolon, çanta ve sandalet sınıflarında neredeyse kusursuz sınıflandırma sağladı.
Bazı sınıflar (T-shirt/top, Pullover, Shirt) arasında karışıklıklar gözlemlendi.
Data augmentation ve batch normalization, overfitting’in önlenmesine katkı sağladı.

Gelecekte yapmayı istediğim çalışmalar ve eklemeler : 
Daha derin ve kompleks CNN mimarileri deneyerek doğruluğu artırmak.
Transfer learning yöntemleri ile eğitim süresini kısaltmak ve performansı artırmak.
Gerçek zamanlı veri toplama ve deploy ile modelin end-to-end kullanımını sağlamak.
Streamlit veya benzeri araçlarla interaktif bir UI geliştirmek.

**Proje Linki**

https://www.kaggle.com/code/hakantosun/akbank-bootcamp
