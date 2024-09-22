# Pusula_Dilan_Paksoy
# dilanpaksoyy@gmail.com
 Data Science Intern Case Study 
## Projenin Amacı 
_Bu proje, ilaç yan etkileriyle ilgili bir veri setini analiz etmeyi ve verileri keşifsel veri analizi (EDA) ve ön işleme adımları aracılığıyla öngörücü modelleme için hazırlamayı amaçlamaktadır. Son çıktı, makine öğrenimi modelleri için kullanılabilen temizlenmiş ve ön işlenmiş verileri içerir._

 ## Proje Yapısı
1. **Veri Yükleme**
 - Proje, bir Excel dosyasından yan etki verilerini yükler.
2. **Keşifsel Veri Analizi (EDA)**
    - Verinin genel yapısı incelenir (boyut, veri türleri, özet istatistikler).
    - Hedef değişken (`Yan_Etki`) dağılımı analiz edilir ve görselleştirilir.
    - Değişkenler arasındaki korelasyonlar bir heatmap ile gösterilir.
3. **Veri Temizleme**
    - Gereksiz sütunlar kaldırılır ve kategorik sütunlar yeniden adlandırılır
    - Cinsiyet sütunundaki değerler (`"female"` ve `"male"`) `"Kadın"` ve `"Erkek"` olarak düzenlenir.
4. **Eksik Değerlerin İşlenmesi**
    - `Kilo` ve `Boy` sütunlarındaki eksik veriler, medyan stratejisi kullanılarak doldurulur.
5. **Kategorik Değişkenlerin Kodlanması**
    - Kategorik değişkenler, `OneHotEncoder` kullanılarak one-hot encoding ile kodlanır.
    - Cinsiyet değişkeni, `LabelEncoder` ile sayısal değerlere dönüştürülür.
6. **Veri Görselleştirme** - Yan etki dağılımı bir pasta grafiği ile görselleştirilir.
   - Tüm değişkenler için boxplot grafikleri oluşturulur.
   - Değişkenler arası korelasyonlar bir heatmap ile görselleştirilir.
   -  ## Kullanılan Teknolojiler
      - **Python**: Veri analizi ve işleme için ana programlama dili.
      - **Pandas**: Veri manipülasyonu için.
      - **NumPy**: Sayısal işlemler ve veri yapıları için.
      - **Matplotlib** ve **Seaborn**: Veri görselleştirme için.
      - **Scikit-learn**: Eksik veri doldurma ve veri ön işleme adımları için.
   


  
