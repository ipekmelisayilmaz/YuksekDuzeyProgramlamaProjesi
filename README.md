# MNIST Sayı Tanıma Modeli

## 1. Proje Amacı ve Genel Bakış
Bu projede, **MNIST** veri kümesi kullanılarak bir derin öğrenme modeli oluşturulmuştur. Modelin amacı, el yazısı rakamları (0-9) doğru bir şekilde sınıflandırmaktır. Proje, görüntü verilerini işleyerek sınıflandırma yapmak için bir yapay sinir ağı (ANN) kullanmaktadır.

## 2. Veri Kümesi

Veri kümesi, **MNIST** veri setinden alınmıştır. Bu veri seti, el yazısı ile yazılmış 28x28 piksel boyutlarında 60.000 eğitim ve 10.000 test görüntüsünden oluşmaktadır. Her görüntü bir rakamı (0'dan 9'a kadar) temsil etmektedir.

- **X_train**: Eğitim verisi (60.000 görüntü).
- **y_train**: Eğitim etiketleri (60.000 etiket).
- **X_test**: Test verisi (10.000 görüntü).
- **y_test**: Test etiketleri (10.000 etiket).

## 3. Verilerin Yüklenmesi ve Ön İşleme

### Verilerin Yüklenmesi
Proje ilk adımda, MNIST veri kümesi `pandas` ile CSV dosyalarından yüklenmiştir:

```python
mnist_dataset_train = pd.read_csv("/kaggle/input/digitrecognizer/train.csv")
mnist_dataset_test = pd.read_csv("/kaggle/input/digitrecognizer/test.csv")

Eğitim ve test veri kümeleri pandas DataFrame'lerine yüklenmiştir. Burada train.csv eğitim verisini ve test.csv test verisini içermektedir.

Verilerin Düzenlenmesi ve Normalizasyon
Eğitim verisi ve test verisi, modelin gereksinimlerine göre işlenmiştir:

X_train = mnist_dataset_train.drop(columns=["label"]).values
y_train = mnist_dataset_train["label"].values
X_test = mnist_dataset_test.values
