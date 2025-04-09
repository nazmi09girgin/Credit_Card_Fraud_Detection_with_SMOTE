# Credit Card Fraud Detection with SMOTE
Bu projede, kredi kartı dolandırıcılığı tespiti için Credit Card Fraud Detection adlı Kaggle veri seti kullanılarak çeşitli makine öğrenmesi modelleri değerlendirilmiştir. Veri seti 284,807 kredi kartı işleminden oluşmaktadır, bunlar arasında yalnızca 492'si dolandırıcılık işlemidir (Class = 1). Bu nedenle, veri seti dengesiz bir yapıdadır ve dolandırıcılık işlemleri genellikle çok nadir gözlemler olarak bulunur.

Proje, aşağıdaki adımlarla gerçekleştirilmiştir:

1)Veri Ön İşleme:

Eksik Veri Kontrolü ve Temizliği: Veri setindeki eksik değerler ve tekrarlayan satırlar temizlenmiştir.  
Özellik Ölçekleme (Normalization): "Amount" özelliği, StandardScaler kullanılarak normalize edilmiştir.  
Zaman Özelliği Kaldırıldı: Modelin eğitiminde gereksiz olan "Time" özelliği veri setinden çıkarılmıştır.  

2)Dengesiz Veri Setiyle Çalışma:

Veri setinde Class (Hedef) sütunu, 0 (dolandırıcılık olmayan işlem) ve 1 (dolandırıcılık işlemi) sınıflarından oluşmaktadır. Bu sınıflar oldukça dengesizdir (yani, dolandırıcılık işlemleri çok nadirdir).  
SMOTE (Synthetic Minority Over-sampling Technique), dengesiz veri setinin Class 1 (dolandırıcılık) sınıfındaki örnekleri artırarak modelin daha doğru tahminler yapabilmesini sağlamaktadır.  

3)Modelleme ve Eşik Değeri Ayarlama:

Dört farklı model (LogisticRegression, DecisionTree, Random Forest, XGBoost) kullanılarak class 1 (dolandırıcılık) tespiti yapılmıştır.  
Modellerin çıktılarında, 0.5 olan eşik değeri varsayılan olarak kullanılmıştır. Ancak, dolandırıcılık tespitinin hassasiyetini artırmak amacıyla eşik değeri 0.8 olarak manuel olarak ayarlanmıştır. Bu sayede model yalnızca yüksek olasılıkla dolandırıcılık olan işlemleri pozitif olarak sınıflandırmıştır.  

4)Değerlendirme:

Modellerin başarısı Confusion Matrix, Precision, Recall, F1-Score, ve ROC-AUC skorları kullanılarak değerlendirilmiştir.  
ROC eğrileri çizilerek her bir modelin doğruluk performansı görsel olarak sunulmuştur. 

5)Sonuç

Bu projede, dengesiz kredi kartı dolandırıcılığı veri seti üzerinde SMOTE yöntemi ile veri dengelenmiş, ardından çeşitli makine öğrenmesi modelleri uygulanmıştır. Ayrıca, sınıflandırma eşik değeri manuel olarak 0.8’e çıkarılarak, özellikle azınlık sınıf olan "fraud" tespitinde precision oranı iyileştirilmiştir.

Model karşılaştırmalarında, XGBoost algoritması, fraud sınıfı için en yüksek başarıyı sağlamış; precision (0.87) ve recall (0.80) değerleriyle diğer modellerin önüne geçmiştir. Random Forest da güçlü bir alternatif olarak öne çıkmıştır.
