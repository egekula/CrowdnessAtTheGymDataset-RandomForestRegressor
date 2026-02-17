# Gym Crowdness Prediction - Random Forest Regressor Analysis

## Projenin Amacı
Bu projenin amacı, bir üniversite spor salonundaki yoğunluğu (kişi sayısını) saat, gün, hava durumu ve akademik takvim gibi çeşitli değişkenleri kullanarak tahmin eden bir regresyon modeli geliştirmektir. Proje kapsamında, kullanıcıların spor salonunun ne zaman kalabalık olacağını önceden tahmin edebilmeleri ve en uygun zamanı seçebilmeleri hedeflenmiştir.

## Yapılan İşlemler:
1. **Veri Keşfi ve Temizlik:** Veri seti incelendi, eksik değerler ve yinelenen veriler kontrol edildi. `date` sütunu datetime formatına çevrilerek `year` bilgisi özellik olarak eklendi.
2. **Keşifsel Veri Analizi (EDA):** Veriler görselleştirilerek yoğunluğun saatlere, hafta sonlarına, tatillere ve sömestr durumuna göre değişimi analiz edildi. Akşam saatlerinde ve sömestr dönemlerinde yoğunluğun arttığı gözlemlendi.
3. **Multicollinearity (Çoklu Doğrusallık) Analizi:** `hour` ve `timestamp` özellikleri arasındaki yüksek korelasyon (%100) tespit edildi ve modelin sağlığını korumak amacıyla `timestamp` sütunu veri setinden çıkarıldı.
4. **Veri Ön İşleme:** Veri seti %75 eğitim ve %25 test olacak şekilde ayrıldı. Özellikler `StandardScaler` kullanılarak ölçeklendirildi.
5. **Model Seçimi:** Linear Regression, Ridge, Lasso, KNN, SVR, Decision Tree ve Random Forest modelleri eğitildi. Random Forest Regressor en iyi performansı gösteren algoritma oldu.
6. **Hiperparametre Optimizasyonu:** `RandomizedSearchCV` kullanılarak Random Forest Regressor için en iyi parametreler (n_estimators, max_depth vb.) arandı ve model performansı optimize edildi.

## Sonuçlar:
Modelimiz test seti üzerinde aşağıdaki performans metriklerini elde etmiştir:
- **MAE (Mean Absolute Error):** 4.21
- **MSE (Mean Squared Error):** 38.97
- **R² Skoru:** 0.92
- **Adjusted R²:** 0.92

## Kullanılan Dataset
https://www.kaggle.com/datasets/nsrose7224/crowdedness-at-the-campus-gym
