# Data Science Case Study



Bu proje,yan etkiler üzerine veri analizi ve işleme adımlarını içermektedir

# 1.Veri Yükleme

- Veri, Excel dosyasından veri_yukle fonksiyonu ile yüklendi.


# 2. İlk Keşif
- Veri setinin temel bilgileri incelendi (boyut, veri türleri, istatistiksel özetler).
Hedef değişken olan Yan_Etki değerlerinin sayıları ve benzersiz değerleri veri_keşfet fonksiyonu ile analiz edildi.


# 3. Veri Görselleştirme 

- Hedef değişkenin (Yan_Etki) dağılımı pasta grafiği ile görselleştirildi.
- Boxplot grafiği ile verilerde olası aykırı değerler incelendi.
- Değişkenler arası korelasyonları incelemek için bir heatmap oluşturuldu.

# Veri Ön İşleme Adımları 

# 1. Veri Temizleme 
- Gereksiz sütunlar (örn. Kullanici_id) kaldırıldı.
- Cinsiyet verisi, "female" ve "male" değerleri "Kadın" ve "Erkek" ile değiştirilerek standartlaştırıldı.
- Bazı sütun adları daha anlaşılır ve tutarlı hale getirilmek için yeniden adlandırıldı.

# 2. Eksik Değerlerin İşlenmesi
- Kilo ve Boy gibi sayısal sütunlardaki eksik veriler, medyan stratejisi ile dolduruldu (SimpleImputerkullanılarak).

# 3. Kategorik Değişkenlerin Kodlanması
- Il, Ilac_Adi, Yan_Etki gibi kategorik değişkenler, one-hot encoding yöntemi ile kodlandı (OneHotEncoderkullanılarak).
- Cinsiyet değişkeni, LabelEncoder ile etiketlendi ve sayısal formata dönüştürüldü.

# Bulguların Özeti 
 - Hedef Değişken Dağılımı: Hedef değişken (Yan_Etki), veri setinde farklı yan etkilerin dağılımını net bir şekilde gösterdi.

- Korelasyonlar: Heatmap, değişkenler arasındaki potansiyel ilişkileri ortaya koydu; bu ilişkiler, ileriye dönük tahminleme modelleri için değerlendirilebilir.

- Eksik Veri: Boy ve kilo gibi sütunlardaki eksik değerler başarıyla tamamlandı, böylece veri seti daha sağlam hale getirildi.


```python

```
