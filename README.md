# UEFA Kulüp Analiz ve Kura Çekimi Simülatörü

Bu proje, UEFA kulüp katsayıları verilerini analiz ederek Türk ve diğer Avrupa kulüplerinin performanslarını görselleştiren ve UEFA Şampiyonlar Ligi / Avrupa Ligi kura çekimi simülasyonu yapan kapsamlı bir Python uygulamasıdır.

## 🎯 Proje Amacı

Bu proje iki ana modül içermektedir:

### 📈 1. UEFA Kulüp Katsayıları Analizi
- Türk kulüplerinin (Galatasaray, Fenerbahçe, Beşiktaş) yıllar içindeki performans analizi
- Diğer ülke kulüpleriyle karşılaştırmalı analiz
- Tarihsel trend analizi ve görselleştirme

### ⚽ 2. UEFA Kura Çekimi Simülatörü
- Şampiyonlar Ligi ve Avrupa Ligi kura çekimi simülasyonu
- Pot sistemine göre otomatik eşleşme algoritması
- İç saha/deplasman dağılımı ve ülke kurallarına uygun kura

## 📊 Veri Setleri

Proje şu veri dosyalarını kullanmaktadır:

### 1. UEFA Katsayıları Analizi
- `takim_puanlari_siralari.csv`: Kulüplerin yıllara göre puan ve sıralama verileri
  - `Takım`: Kulüp adı
  - `Yıl`: Sezon yılı
  - `Puan`: UEFA katsayı puanı
  - `Sıra`: UEFA sıralamasındaki pozisyon

### 2. Kura Çekimi Simülatörü
- `takimlar.json`: UEFA Şampiyonlar Ligi takımları ve pot bilgileri
- `takimlar_eur.json`: UEFA Avrupa Ligi takımları ve pot bilgileri

Her JSON dosyası şu yapıya sahiptir:
```json
[
  {"Ülke": "The Football Association"},
  {"Takım": "Manchester City", "Pot": "Pot 1"},
  {"Takım": "Arsenal", "Pot": "Pot 2"},
  ...
]
```

## 🛠️ Teknolojiler

- **Python 3**
- **Pandas**: Veri manipülasyonu ve analizi
- **Matplotlib**: Grafik oluşturma ve görselleştirme  
- **NumPy**: Sayısal hesaplamalar
- **JSON**: Takım verilerini okuma ve işleme
- **Collections**: Veri yapıları (defaultdict)
- **Random**: Kura çekimi rastgele seçimleri
- **Google Colab**: Geliştirme ortamı

## 📈 Analiz Özellikleri

### 1. UEFA Katsayıları Analizi

#### 1.1 Türk Kulüplerinin Sıralama Analizi

<img width="1005" height="587" alt="indir (66)" src="https://github.com/user-attachments/assets/304269e0-4c20-4645-99d9-3c675dfb2e6e" />
*Galatasaray, Fenerbahçe ve Beşiktaş'ın yıllar içindeki UEFA sıralama pozisyonları*

#### 1.2 Portekiz Kulüpleri Karşılaştırması
<img width="1005" height="587" alt="indir (67)" src="https://github.com/user-attachments/assets/09a6d2de-4553-4188-8cc2-e644b80962d1" />
*Porto, Benfica, Sporting Lizbon ve Braga'nın performans karşılaştırması*

#### 1.3 Takım Bazlı Puan Analizi
<img width="841" height="547" alt="indir (68)" src="https://github.com/user-attachments/assets/8320a2e2-a162-49bc-b4dd-2bbf6ec0f6e7" />

*Beşiktaş'ın yıllar içindeki UEFA katsayı puanları değişimi*

#### 1.4 Şampiyonluk İstatistikleri
Program, hangi takımların hangi yıllarda 1. sırada yer aldığını analiz eder.


### 2. Kura Çekimi Simülatörü

#### 2.1 Otomatik Kura Algoritması

*UEFA kurallarına uygun otomatik kura çekimi algoritması*

#### 2.2 Pot Sistemine Dayalı Eşleşmeler
- **Pot 1**: En güçlü 9 takım
- **Pot 2**: Orta seviye güçlü takımlar
- **Pot 3**: Orta seviye takımlar
- **Pot 4**: Zayıf takımlar

#### 2.3 Kura Kuralları
- Her takım diğer potlardan 2'şer rakip alır
- Aynı ülkeden takımlar eşleşmez
- Bir ülkeden en fazla 2 takım ile oynanabilir
- İç saha/deplasman dengesine uyulur

#### 2.4 Kura Çıktıları
<img width="1349" height="414" alt="Ekran görüntüsü 2025-09-02 002510" src="https://github.com/user-attachments/assets/9b13b041-74c0-4828-8919-536c48b73c27" />

*Şampiyonlar Ligi'nde 4.torba takımların rakipleri ve maç durumları tablosu*

<img width="1287" height="413" alt="Ekran görüntüsü 2025-09-02 002711" src="https://github.com/user-attachments/assets/4b38f123-5abc-4f1a-abe7-a8bbdb2076f8" />

*Avrupa Ligi'nde 2.torba takımların rakipleri ve maç durumları tablosu*

#### 2.5 Pot Bazlı Sonuç Tabloları
- Her pot için ayrı detaylı sonuç tablosu
- İç saha/deplasman bilgileriyle birlikte rakip listesi
- Renkli ve stilize edilmiş görünüm

## 🚀 Kurulum ve Çalıştırma

### Google Colab'da Çalıştırma:

1. **Google Drive Bağlantısı**
```python
from google.colab import drive
drive.mount('/content/drive')
```

2. **Gerekli Kütüphaneleri İçe Aktarma**
```python
import pandas as pd
import matplotlib.pyplot as plt
import numpy as np
import json
from collections import defaultdict
import random
```

3. **Veri Dosyalarını Yükleme**
```python
# UEFA Katsayıları
df = pd.read_csv('/content/drive/MyDrive/takim_puanlari_siralari.csv')

# Şampiyonlar Ligi Takımları
with open("/content/drive/My Drive/takimlar.json", "r", encoding="utf-8") as f:
    takimlar = json.load(f)

# Avrupa Ligi Takımları
with open("/content/drive/My Drive/takimlar_eur.json", "r", encoding="utf-8") as f:
    takimlar_eur = json.load(f)
```

### Yerel Bilgisayarda Çalıştırma:

1. **Gereksinimler**
```bash
pip install pandas matplotlib numpy
```

2. **Veri dosyalarını proje klasörüne yerleştirin**
   - `takim_puanlari_siralari.csv`
   - `takimlar.json`
   - `takimlar_eur.json`

3. **Kodu çalıştırın**

## 📊 Önemli Fonksiyonlar

### 1. Analiz Fonksiyonları

#### `plot_team_rankings()` Fonksiyonu
```python
def plot_team_rankings(dfs, teams, colors=None, title="UEFA Club Coefficients"):
```
- **Parametreler:**
  - `dfs`: DataFrame listesi
  - `teams`: Takım isimleri listesi
  - `colors`: Renk listesi (opsiyonel)
  - `title`: Grafik başlığı

- **Özellikler:**
  - Çoklu takım karşılaştırması
  - Özelleştirilebilir renkler
  - Ters Y ekseni (düşük sıra = daha iyi)
  - Grid ve legend desteği

### 2. Kura Çekimi Fonksiyonları

#### `create_team_dfs_from_list()` Fonksiyonu
Her takım için 8 maçlık DataFrame oluşturur ve pot bilgilerini doldurur.

#### `create_pot_ave_from_df()` Fonksiyonu  
Her pot için İç saha/Deplasman durumlarını içeren DataFrame'ler oluşturur.

#### Pot Draw Fonksiyonları
- `pot1_draw()`: Pot 1'den rakip seçimi
- `pot2_draw()`: Pot 2'den rakip seçimi  
- `pot3_draw()`: Pot 3'den rakip seçimi
- `pot4_draw()`: Pot 4'den rakip seçimi

**Özellikler:**
- Aynı ülkeden takım eşleşmesini engeller
- Ülke başına maksimum 2 rakip kuralı
- İç saha/deplasman dengesi
- Otomatik restart mekanizması (RestartDraw exception)

#### `draw()` Ana Kura Fonksiyonu
Tüm takımlar için kompleks kura algoritmasını çalıştırır ve sonuçları birleştirir.

## 📋 Analiz Çıktıları

### 1. UEFA Katsayıları Analizi Çıktıları

#### 1.1 Şampiyonluk Tablosu
Program şu bilgileri sağlar:
- Hangi takımlar kaç kere birinci oldu
- Hangi yıllarda birinci oldular
- Sıralamaya göre azalan düzen

#### 1.2 Türk Kulüpleri Performans Tablosu
- Her takımın 1., 2., 3. sırada kaç kere yer aldığı
- Yıllara göre pozisyon değişimleri
- Karşılaştırmalı performans analizi

#### 1.3 Özel Takım Analizleri
- Başakşehir'in UEFA sıralama performansı
- Karabağ'ın puan gelişimi
- Diğer dikkat çekici takımların analizleri

### 2. Kura Çekimi Simülatörü Çıktıları

#### 2.1 Ana Fixtures DataFrame
Tüm takımların 8 maçlık programını içeren kapsamlı DataFrame:
- Takım adı ve ülke bilgisi
- Rakip takım ve ülke bilgisi
- Pot bilgileri
- İç saha/Deplasman durumu

#### 2.2 Pot Bazlı Görselleştirme Tabloları
Her pot için ayrı stilize edilmiş tablolar:
- **Pot 1 Tablosu**: En güçlü takımların eşleşmeleri
- **Pot 2 Tablosu**: İkinci seviye takımların programı  
- **Pot 3 Tablosu**: Üçüncü seviye eşleşmeler
- **Pot 4 Tablosu**: Dördüncü pot programları

#### 2.3 Pivot Tablo Çıktısı
- Takım bazlı rakip listesi
- Pot ve durum (İç saha/Deplasman) sütunları
- Virgülle ayrılmış rakip isimleri

#### 2.4 Kura Çekimi Güvenlik Özellikleri
- **RestartDraw Exception**: Uygun rakip bulunamadığında otomatik yeniden başlatma
- **Infinite Loop Protection**: Sonsuz döngü koruması
- **Rule Validation**: Tüm UEFA kurallarının kontrolü
**Not:** UEFA Şampiyonlar Ligi'nde 6 İngiliz, 5 İspanyol 4'er adet Almanya ve İtalya takımı bulunduğundan bu turnuvada uygun bir kura çıkarmak biraz daha uzun sürebilir. UEFA Avrupa Ligi'nde böyle bir problem yok.
  
## 🎨 Görselleştirme Özellikleri

### 1. Analiz Grafikleri
- **Renk Kodlaması**: Her takım için kendine özgü renkler
- **Karanlık Tema**: Siyah arka plan ile profesyonel görünüm  
- **Veri Etiketleri**: Her noktada sıralama/puan değerleri
- **Izgara Sistemi**: Kolay okunabilirlik için grid çizgileri
- **Legend**: Takım ayırt edici göstergeler

### 2. Kura Çekimi Tabloları
- **Çok Seviyeli Başlıklar**: Pot ve durum bilgileri
- **Renkli Stil**: Başlık ve hücre renklendirmesi
- **Pivot Görünüm**: Takım bazlı rakip matrisi
- **Stil Fonksiyonları**: Profesyonel tablo görünümü



## 🔍 Önemli Bulgular

### UEFA Katsayıları Analizi
- **Türk kulüplerinin UEFA sıralamalarındaki tarihsel performansı**
- **En başarılı dönemler ve düşüş trendleri**
- **Avrupa kulüpleriyle karşılaştırmalı durum**
- **Şampiyonluk ve üst sıra istatistikleri**

### Kura Çekimi Simülatörü
- **Gerçekçi UEFA kura kurallarına %100 uyumluluk**
- **36 takımlı yeni format desteği**
- **Otomatik hata düzeltme ve yeniden başlatma sistemi**
- **Kapsamlı ülke ve pot kısıtlamaları uygulaması**

## ⚡ Algoritma Özellikleri

### Kura Çekimi Algoritması
1. **Multi-Stage Process**: Her pot için ayrı çekim aşaması
2. **Constraint Satisfaction**: Tüm UEFA kurallarını simultane kontrol
3. **Backtracking**: Çıkmaz durumda otomatik geri alma
4. **Randomization**: Gerçekçi rastgele seçim algoritması

### Performans Optimizasyonları
- **Memory Efficient**: Büyük veri setleri için optimize edilmiş
- **Error Handling**: Kapsamlı exception yönetimi
- **Data Validation**: Girdi verilerinin otomatik kontrolü

## 🤝 Katkıda Bulunma

1. Fork yapın
2. Feature branch oluşturun (`git checkout -b feature/yeni-ozellik`)
3. Değişikliklerinizi commit edin (`git commit -am 'Yeni özellik eklendi'`)
4. Branch'i push edin (`git push origin feature/yeni-ozellik`)
5. Pull Request oluşturun

## 📝 Lisans

Bu proje açık kaynak kodludur ve MIT lisansı altında dağıtılmaktadır.

## 📞 İletişim

Sorularınız için GitHub Issues bölümünü kullanabilirsiniz.

---

⭐ **Bu projeyi beğendiyseniz yıldız vermeyi unutmayın!**
