# Özellik Ölçekleme (Feature Scaling) Nedir?

Makine öğrenmesi algoritmalarında kullanılan veri setlerindeki öznitelikler (features), farklı ölçeklerde olabilir. Örneğin, bir sütun yaş (0-100 arasında), bir diğeri ise gelir (1000-100000 arasında) olabilir. Bu tür farklılıklar, bazı algoritmaların performansını olumsuz etkileyebilir.

Özellik ölçekleme, bu farklılıkları ortadan kaldırmak için tüm özniteliklerin benzer ölçeklere getirilmesidir. Özellikle **mesafeye dayalı algoritmalar** (örneğin K-Means, KNN, PCA) için ölçekleme **olmazsa olmaz** bir adımdır.

## Neden Özellik Ölçekleme Yapılır?

- Ölçek farkları bazı algoritmaların özniteliklere **ağırlık vermesine** neden olur.
- Modelin **daha hızlı ve doğru öğrenmesini** sağlar.
- Özellikle **kümeleme (clustering)** yöntemlerinde (örneğin Davies-Bouldin skoru kullanıldığında) doğru benzerlik hesapları için gereklidir.

## Yaygın Özellik Ölçekleme Yöntemleri

### 1. Min-Max Normalizasyonu (Normalization)
Her değeri 0 ile 1 arasına sıkıştırır.
```
x_{scaled} = (x - x_min) / (x_max - x_min)
```

### 2. Standardizasyon (Z-Score Standardization)
Verinin ortalaması 0, standart sapması 1 olacak şekilde dönüştürülür.
```
x_{scaled} = (x - mu) / sigma
```

### 3. Robust Scaling
Aykırı değerlere karşı daha dayanıklıdır. Ortanca (median) ve çeyrekler arası açıklığı (IQR) kullanır.

## Python'da Özellik Ölçekleme

```python
from sklearn.preprocessing import StandardScaler, MinMaxScaler

# Örnek veri
X = [[1, 100], [2, 200], [3, 300]]

# Standardizasyon
scaler = StandardScaler()
X_standardized = scaler.fit_transform(X)

# Min-Max Normalizasyonu
min_max_scaler = MinMaxScaler()
X_normalized = min_max_scaler.fit_transform(X)
```
