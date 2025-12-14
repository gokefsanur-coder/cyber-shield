# Cyber Shield – Siber Olay Müdahale İstasyonu

Bu proje, siber saldırı altındaki bir ortamda delil toplamak ve analiz etmek için hazırlanmış bir “Blue Team – Incident Response” istasyonudur.

Bu dosya, **Hafta 1 – Hazırlık Aşaması** kapsamında yapılan işlemleri içerir.

---

## 📁 1. GitHub Deposu Oluşturuldu
- Proje adı: **cyber-shield**
- Açık kaynak lisans: **GPL-3.0**
- `.gitignore` dosyası oluşturuldu ve gereksiz dosyaların repoya eklenmesi engellendi.

---

## 🔐 2. Delil (evidence) Klasörü Oluşturuldu
Olay sırasında toplanacak dosyaların güvenli şekilde saklanması için özel bir delil klasörü oluşturuldu:

```bash
mkdir evidence
---

## 🔒 3. Delil Klasörüne Katı İzinler Verildi

Delil klasörüne sadece root ve analysts grubunun erişebilmesi için temel izinler ayarlanmıştır:

```bash
sudo groupadd analysts
sudo chown root:analysts evidence
sudo chmod 750 evidence
sudo setfacl -m g:analysts:rx evidence
sudo setfacl -m o::--- evidence
sudo setfacl -d -m g:analysts:rx evidence
sudo setfacl -d -m o::--- evidence
---

## Hafta 2 – Analiz (DÖÇ-4 & DÖÇ-5)

### 2.1. Süreç Yönetimi (DÖÇ-4)
Bu aşamada sistemde çalışan süreçler incelenmiş, CPU ve RAM kullanımına göre sıralama yapılmıştır.  
`ps aux --sort=-%cpu` ve `ps aux --sort=-%mem` komutları kullanılarak en fazla kaynak tüketen süreçler belirlenmiştir.  

Ayrıca `ps aux | grep 'Z'` komutu ile Zombie process kontrolü gerçekleştirilmiş ve sistemde zombie sürece rastlanmadığı doğrulanmıştır.

---

### 2.2. Metin İşleme ve Log Analizi (DÖÇ-5)
Web sunucusuna ait `access.log` dosyası üzerinde `awk`, `sed` ve `regex` araçları kullanılarak analiz yapılmıştır.

Bu analiz kapsamında:
- IP adreslerinin istek sayıları çıkarılmış,
- 4xx ve 5xx hata kodları filtrelenmiş,
- IP bazlı hata / saldırı sayıları hesaplanmış,
- `sed + awk` kullanılarak log satırları sadeleştirilmiştir.

Analiz sonucunda en çok istek yapan IP adresi listenin en başında gösterilmiştir.  
Tüm işlemler **DÖÇ-4 ve DÖÇ-5** gereksinimlerini karşılamaktadır.
