MERT TOSUN 
RESUL EKREM ÖZDEMİR
BEYTULLAH ALKAN

# 🧬 COVID-19 ve Sağlıklı Bireyler Arasında Diferansiyel Gen Ekspresyonu Analizi

Bu projede, Bioconductor tabanlı R kütüphaneleri kullanılarak COVID-19 hastaları ile sağlıklı bireyler arasındaki gen ekspresyon farklılıkları analiz edilmiştir. Analiz, RNA-Seq verilerine dayanmakta ve istatistiksel olarak anlamlı genlerin belirlenmesini hedeflemektedir.

---

## 🎯 Proje Amacı

- COVID-19'un genetik düzeyde vücut üzerindeki etkilerini ortaya koymak
- RNA-Seq sayım verileri üzerinden farklı ifade edilen (diferansiyel) genleri belirlemek
- Biyolojik ve istatistiksel olarak anlamlı genleri filtreleyerek potansiyel biyobelirteçleri tespit etmek

---

## 📁 Kullanılan Veri

- **Veri seti:** [GSE196822](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE196822) (NCBI-GEO)
- **Örnek sayısı:** 40 COVID-19 hastası, 9 sağlıklı birey
- **Veri tipi:** RNA-Seq sayım matrisi (raw counts)

---

## 🧰 Kullanılan R Paketleri

- `edgeR` – Sayım verilerinin normalize edilmesi ve DGEList nesnesi oluşturma
- `limma` – Lineer modelleme ve istatistiksel testler (eBayes ile birlikte)
- `ggplot2` – Volcano plot ile görselleştirme
- `BiocManager` – Bioconductor paketlerini kurmak için

---

## 📊 Anlamlılık Kriterleri

Anlamlı genleri belirlemek için şu iki eşik değeri kullanılmıştır:

- `|log2FC| > 1` → Gen ifadesi en az 2 kat artmış ya da azalmış
- `adj.P.Val < 0.05` → Fark istatistiksel olarak anlamlı (FDR kontrollü)

---

## 🚀 Nasıl Çalıştırılır?

1. Aşağıdaki komutla gerekli paketleri yükleyin:

```r
if (!requireNamespace("BiocManager", quietly = TRUE)) install.packages("BiocManager")
BiocManager::install(c("edgeR", "limma", "ggplot2"))
