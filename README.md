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
