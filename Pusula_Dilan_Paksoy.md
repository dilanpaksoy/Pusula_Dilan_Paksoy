import pandas as pd
import seaborn as sns
import numpy as np
import matplotlib.pyplot as plt
from sklearn.impute import SimpleImputer
from sklearn.preprocessing import OneHotEncoder 
from sklearn.preprocessing import LabelEncoder

# Veriyi Yükle
def veri_yukle(dosya_yolu):
    return pd.read_excel(dosya_yolu)

# Veriyi Keşfet
def veri_keşfet(df):
    print(df.shape)
    print(df.info())
    print(df.describe().T)
    print(df.columns)
    print(df.Yan_Etki.unique())
    print(df.Yan_Etki.value_counts())

# Veriyi Temizle
def veri_temizle(df):
    df = df.drop(["Kullanici_id"], axis=1, errors='ignore')
    df["Cinsiyet"] = df["Cinsiyet"].replace({"female": "Kadın", "male": "Erkek"})
    # Cinsiyet ile ilgili kısım kaldırıldı
    df.rename(columns={
        "Kronik Hastaliklarim": "Kronik_Hastaliklarim",
        "Baba Kronik Hastaliklari": "Baba_Kronik_Hastaliklari",
        "Anne Kronik Hastaliklari": "Anne_Kronik_Hastaliklari",
        "Kiz Kardes Kronik Hastaliklari": "Kiz_Kardes_Kronik_Hastaliklari",
        "Erkek Kardes Kronik Hastaliklari": "Erkek_Kardes_Kronik_Hastaliklari",
        "Kan Grubu": "Kan_Grubu"
    }, inplace=True)
    return df

# Veriyi Görselleştir
def veri_gorsellestir(df):
    df.Yan_Etki.value_counts().plot(kind="pie", autopct="%.1f%%")
    plt.ylabel("YAN ETKİ")
    plt.show()
    
    sns.boxplot(data=df)
    plt.xticks(rotation=90)
    plt.show()

    plt.figure(figsize=(12, 8))
    sns.heatmap(df.corr(), annot=True, cmap='coolwarm', fmt='.2f')
    plt.show()

# Eksik Değerleri İşle
def eksik_degerleri_isle(df):
    imputer = SimpleImputer(strategy='median')
    df[['Kilo', 'Boy']] = imputer.fit_transform(df[['Kilo', 'Boy']])
    return df

# Kategorik Değişkenleri One-Hot Kodla
def kategorik_degiskenleri_kodla(df):
    kategorik_kolonlar = ['Il', 'Ilac_Adi', 'Yan_Etki', 'Alerjilerim', 
                          'Kan_Grubu', 'Kronik_Hastaliklarim', 'Baba_Kronik_Hastaliklari',
                          'Anne_Kronik_Hastaliklari', 'Kiz_Kardes_Kronik_Hastaliklari', 
                          'Erkek_Kardes_Kronik_Hastaliklari']
    
    encoder = OneHotEncoder(sparse=False)
    kodlanmis_veri = encoder.fit_transform(df[kategorik_kolonlar])
    kodlanmis_kolonlar = encoder.get_feature_names_out(kategorik_kolonlar)
    kodlanmis_df = pd.DataFrame(kodlanmis_veri, columns=kodlanmis_kolonlar)
    
    df_final = pd.concat([df.drop(columns=kategorik_kolonlar), kodlanmis_df], axis=1)
    return df_final

# Cinsiyet Değişkenini Encode Et
def cinsiyet_degiskeni_kodla(df):
    le = LabelEncoder()
    df['Cinsiyet_Encoded'] = le.fit_transform(df['Cinsiyet'])
    return df

# Ana Pipeline Fonksiyonu
def ana_pipeline(dosya_yolu):
    df = veri_yukle(dosya_yolu)
    veri_keşfet(df)
    df = veri_temizle(df)
    df = cinsiyet_degiskeni_kodla(df)  # Cinsiyet kodlama fonksiyonu eklendi
    veri_gorsellestir(df)
    df = eksik_degerleri_isle(df)
    df_final = kategorik_degiskenleri_kodla(df)
    print(df_final.head())
    print(le.classes_, df[['Cinsiyet', 'Cinsiyet_Encoded']].head())  # Cinsiyet sınıfları ve kodlaması

# Pipeline'ı Çalıştır
dosya_yolu = "C:\\Users\\dell\\Downloads\\side_effect_data 1.xlsx"
ana_pipeline(dosya_yolu)

