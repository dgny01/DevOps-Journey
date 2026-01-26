#  DevOps Icin Linux Hayat Kurtarma Kiti

## 1. Dosya Sistemi Hiyerarsisi (File System)
> Windows'taki C: D: yok. Her sey "/" (Root) altindadir.

* **`/` (Root):** Her seyin basladigi yer.
* **`/home`**: Kullanici dosyalarim burada. (Orn: `/home/yildiz`)
* **`/etc`**:  **AYARLAR.** (Configuration). Sunucu ayarlari burada.
* **`/var`**:  **LOGLAR.** (`/var/log`). Surekli degisen dosyalar.
* **`/bin`**: Temel komutlar (ls, cp gibi) burada durur.

## 2. Kritik Komutlar (Komut - Ne Ise Yarar)

### Gezinti ve Listeleme
* `pwd`: "Neredeyim?" (Print Working Directory).
* `ls -la`: Gizli dosyalar (. ile baslayanlar) dahil her seyi detayli listeler. **(Cok Onemli)**
* `cd ~`: Direkt eve (/home/kullanici) isinlanma tusu.
* `cd ..`: Bir ust klasore cik.

### Dosya Islemleri
* `mkdir [isim]`: Klasor olustur.
* `touch [isim]`: Bos dosya olustur.
* `rm -rf [isim]`: ⚠️ **TEHLIKE!** Klasoru icindekilerle birlikte soru sormadan siler.
* `cp -r [kaynak] [hedef]`: Klasoru icindekilerle kopyalar.
* `mv [eski] [yeni]`: Hem tasima hem de **isim degistirme** komutudur.

### Dosya Okuma (Editorsuz)
* `cat [dosya]`: Dosyanin tamamini ekrana basar (Kisa dosyalar icin).
* `tail -f [dosya]`:  **CANLI LOG IZLEME.** Dosyanin sonuna eklenenleri anlik gosterir.
* `head [dosya]`: Dosyanin sadece ilk 10 satirini gosterir.

---
** Gunun Notu:**
Root (`/`) ile Root kullanicisi (`admin`) ayni sey degilmis. Biri mekan, biri sofor.