# VERİ YAPILARI - ÖDEV 2
## Öncelikli Kuyruk ve İkili Arama Ağacı Uygulaması

---

## 📋 GENEL BİLGİLER


**Programlama Dili:** C++  
**Derleyici:** MinGW  




## 🎯 ÖDEV KONUSU

Altıgen şekil yapısında organize edilmiş **öncelikli kuyruk** sistemi oluşturulacaktır. Her altıgen yapı maksimum 6 kuyruk içerir ve her kuyruk bir **ikili arama ağacı** tutar.

---

## 📊 VERI YAPISI MİMARİSİ

### Altıgen Yapı
- Her altıgen **6 kuyruk** barındırır
- Her kenar (kuyruk) bir ikili arama ağacı içerir
- Ekranda her satırda maksimum 6 kuyruk gösterilir
- Dosyaya göre birden fazla altıgen oluşabilir

### İkili Arama Ağaçları
- Her kuyruk bir ikili arama ağacı tutar
- **Önemli:** Eşit değerler **SOLA** eklenir
- Ağaç yüksekliği öncelik belirler (yüksek olan öncelikli)

### Öncelik Sistemi
- **Öncelik:** Ağaç yüksekliğine göre belirlenir
- Altıgen üzerindeki sayılar: `çıkacak_ağaç_kökü / öncelikli_ağaç_kökü`
- Örnek: 75/25 = 3
- Tam sayı bölme işlemi yapılır

---

## 📁 DOSYA YAPISI (Data.txt)

### Format
```
73 5 48
91 16 33 7 82
40
12 67 58 94
3 29 77 10 86 54
100 8
```

### Okuma Kuralları
- Her satır bir ikili arama ağacı oluşturur
- Sayılar soldan sağa sırayla ağaca eklenir
- Satır bitince ağaç kuyruğa eklenir
- 6 ağaç (satır) tamamlanınca bir altıgen oluşur
- Altıgen dolarsa yeni altıgen başlar

---

## 🎮 PROGRAM AKIŞI

### 1. Başlangıç Aşaması
- Dosya okunarak toplam altıgen sayısı hesaplanır
- Ekranda boş altıgenler gösterilir
- Dosya okunurken ekran **anlık güncellenir**
- Tüm dosya okununca sayısal durum gösterilir

### 2. Tur Sistemi
- Kullanıcıdan **kaç tur çalışacağı** istenir
- Bir tuşa basınca turlar başlar
- Her tur için:
  - Hangi turda olunduğu gösterilir
  - Sayılar güncellenir
  - **Ekran sürekli yenilenir** (öncekiler temizlenir)
- Turlar bitince **sadece son durum** ekranda kalır

### 3. Tur İşlemleri

#### Tek Numaralı Turlar (1, 3, 5, ...)
- Kuyruktan **normal** (FIFO) veri çıkarılır
- Sağdaki altıgen yapıya eklenir

#### Çift Numaralı Turlar (2, 4, 6, ...)
- Kuyruktan **öncelikli** veri çıkarılır (yüksekliğe göre)
- Sağdaki altıgen yapıya eklenir

### 4. Ekleme Mekanizması
- Çıkarılan ağaç **postorder** sırayla gezilir
- Her düğüm sırayla sağdaki altıgendeki kuyruklara eklenir
- Önden arkaya doğru her kuyruğa bir düğüm
- Kuyruklar biterse başa dönülür (döngüsel)

---

## 🎨 EKRAN GÖSTERİMİ

```
Örnek Görsel (Sayılar temsilidir):

  3     5     2
    7     4
  6     1     8

Her sayı: çıkacak_kök / öncelikli_kök
```

- Ekran sürekli güncellenir
- Önceki yazılar temizlenir
- Her satırda maksimum 6 kuyruk
- Turlar sırasında ekran durmaz

---

## 💻 TEKNİK GEREKSİNİMLER

### Kod Gereksinimleri
- **Nesne yönelimli yaklaşım** şart
- Her sınıfın **başlık (.h)** ve **kaynak (.cpp)** dosyası ayrı
- Başlık dosyasında **metot gövdesi olamaz**
- **Şablon (Generic) veri yapısı KULLANILMAZ**
- **Hazır veri yapısı KULLANILMAZ**
- Sadece C++ kodları

### Performans
- Program **hızlı** çalışmalı (yavaşsa puan kırılır)
- **En az 50.000 satırlık** Data.txt ile test edilmeli
- Süre gözlemlenip optimize edilmeli

### Dosya Başlığı (Tüm Kaynak Kodlarda)
```cpp
/**
* @file Dosya adı
* @description Programın açıklaması
* @course Eğitim türü ve grup
* @assignment Kaçıncı ödev
* @date Oluşturma tarihi
* @author Ad Soyad ve e-posta
*/
```

---

## 📦 TESLİM FORMATI

### Klasör Yapısı
```
B111210090/                    (Öğrenci numaranız)
├── src/                       (Kaynak dosyaları .cpp)
├── include/                   (Başlık dosyaları .h)
├── lib/                       (.o dosyaları)
├── bin/                       (.exe dosyası)
├── doc/                       (Rapor PDF)
├── makefile                   (ZORUNLU!)
└── benioku.txt               (Opsiyonel notlar)
```

