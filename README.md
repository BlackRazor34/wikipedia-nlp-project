
# Wikipedia Metin Ön İşleme ve Görselleştirme Projesi

Bu proje, Wikipedia metin verilerini içeren bir veri seti üzerinde doğal dil işleme (NLP) teknikleri kullanarak metin ön işleme ve görselleştirme adımlarını içermektedir.

## 📝 Proje Açıklaması

Projenin temel amacı, ham metin verisini yapılandırılmış ve analiz edilebilir bir formata dönüştürmektir. Bu süreçte aşağıdaki adımlar uygulanmıştır:
- Metin verisinin standartlaştırılması (küçük harfe çevirme, noktalama işaretleri ve sayıların kaldırılması).
- Metin içinde sıkça geçen ancak anlamsal değeri düşük olan "stopwords" (etkisiz kelimeler) ve çok seyrek kullanılarak gürültü yaratan kelimelerin temizlenmesi.
- Kelimelerin köklerine indirgenmesi (lemmatization).
- Temizlenmiş veri üzerinden kelime frekanslarının hesaplanması ve görselleştirilmesi.

Tüm bu işlemler, projenin sonunda `wiki_processing` adında tek bir fonksiyonda birleştirilmiştir.

## 📁 Veri Seti

Proje, `wiki_data.csv` adlı bir veri setini kullanmaktadır. Bu dosyanın, Jupyter Notebook (`wiki.ipynb`) dosyasıyla aynı dizinde olması gerekmektedir. Veri seti, her satırda bir Wikipedia makalesinin metnini içeren 'text' adında bir sütuna sahiptir.

## 🛠️ Kullanılan Teknolojiler ve Kütüphaneler

- **Python 3.x**
- **Jupyter Notebook**
- **Pandas:** Veri manipülasyonu ve CSV işlemleri için.
- **NLTK (Natural Language ToolKit):** Stopwords ve lemmatization işlemleri için.
- **TextBlob:** Lemmatization için.
- **WordCloud:** Kelime bulutu görselleştirmesi için.
- **Matplotlib & Seaborn:** Grafik çizimleri için.

## ⚙️ Kurulum ve Bağımlılıklar

Projeyi çalıştırmadan önce gerekli kütüphaneleri yüklemeniz gerekmektedir.

```bash
pip install pandas numpy matplotlib seaborn nltk textblob wordcloud
```

Ayrıca, NLTK ve TextBlob kütüphaneleri için ek kaynakları indirmeniz gerekebilir:
```python
import nltk
from textblob import Word

# NLTK için stopwords ve wordnet verilerini indirme
nltk.download('stopwords')
nltk.download('wordnet')
```

## 🚀 Kullanım

Projedeki tüm adımlar, `wiki_processing` fonksiyonu altında toplanmıştır. Bu fonksiyon, ham metin verisini alıp işler ve isteğe bağlı olarak görselleştirmeleri yapar.

**Fonksiyonun Docstring'i:**
```python
def wiki_processing(text, Barplot=False, wordcloud=False):
    """ Wiki metinlerini işleme fonksiyonu.
    Args:
        text (str): İşlenecek metin.
        Barplot (bool): Kelime frekanslarını barplot olarak gösterir.
        wordcloud (bool): Kelime bulutunu gösterir.
    Returns:
        pd.DataFrame: İşlenmiş metin verisi.
    """
```

**Örnek Kullanım:**

```python
import pandas as pd
from warnings import filterwarnings

# Gerekli ayarlar ve kütüphane indirmeleri
filterwarnings('ignore')
# nltk.download('...') vs.

# Veriyi yükleme
df = pd.read_csv("wiki_data.csv", index_col=0)

# Fonksiyonu çağırarak veriyi işleme
# Sadece metin ön işleme yapmak için:
processed_text = wiki_processing(df["text"])

# Hem ön işleme hem de görselleri oluşturmak için:
processed_text_with_plots = wiki_processing(df["text"], Barplot=True, wordcloud=True)

print(processed_text_with_plots.head())
```
**Not:** Notebook'unuzdaki son hücrede `wiki_processing` fonksiyonunu çağırdığınızda bir `NameError` almışsınız. Fonksiyonu tanımladığınız hücreyi çalıştırdıktan sonra çağırma hücresini çalıştırdığınızda bu hata düzelecektir.

## 📊 Görsel Çıktılar

Bu kısma, kodunuzun ürettiği görsellerin ekran görüntülerini ekleyebilirsiniz.

### Kelime Frekansları Barplot Grafiği
*Frekansı 8000'den fazla olan kelimelerin görseli.*

![Barplot Görseli](path/to/barplot_image.png)

### Kelime Bulutu (WordCloud)
*İşlenmiş metindeki en popüler kelimelerin görsel temsili.*

![WordCloud Görseli](path/to/wordcloud_image.png)

---

Umarım bu içerikler GitHub projenizi daha profesyonel ve anlaşılır bir şekilde sunmanıza yardımcı olur. Başarılar!
