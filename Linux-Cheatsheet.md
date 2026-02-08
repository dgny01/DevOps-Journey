#  DevOps Icin Linux Hayat Kurtarma Kiti

## 1. Dosya Sistemi Hiyerarsisi (File System)
> Windows'taki C: D: yok. Her sey "/" (Root) altindadir.

* **`/` (Root):** Her seyin basladigi yer.
* **`/home`**: Kullanici dosyalarim burada. (Orn: `/home/yildiz`)
* **`/etc`**:  **AYARLAR.** (Configuration). Sunucu ayarlari burada.
* **`/var`**:  **LOGLAR.** (`/var/log`). Surekli degisen dosyalar.
* **`/bin`**: Temel komutlar (ls, cp gibi) burada durur.



## 2. Kritik Komutlar (Komut - Ne Ise Yarar)

#  Linux Komutlari - Hizli Basvuru (Cheat Sheet)

###  1. Gezinti ve Listeleme (Navigasyon)
* `pwd`: **"Neredeyim?"** (Print Working Directory). Mevcut bulundugun klasor yolunu gosterir.
* `ls -la`: **Detayli Listeleme.** Gizli dosyalar (. ile baslayanlar), dosya boyutu, sahibi ve izinleri dahil her seyi listeler.
* `cd ~`: **Eve Donus.** Seni direkt ana dizinine (/home/kullanici) isinlar.
* `cd ..`: **Geri Vites.** Bir ust klasore cikar.
* `cd -`: **Geri Don.** Bir onceki bulundugun klasore geri doner (TV kumandasindaki "Back" tusu gibi).

###  2. Dosya ve Klasor Islemleri
* `mkdir [isim]`: Yeni bir klasor olusturur.
* `mkdir -p [A/B/C]`: **Zincirleme Klasor.** Ic ice klasorleri tek komutla olusturur.
* `touch [isim]`: Bos bir dosya olusturur veya dosyanin tarihini gunceller.
* `cp -r [kaynak] [hedef]`: **Kopyala.** "-r" parametresini unutma; klasoru icindekilerle beraber kopyalar.
* `mv [eski] [yeni]`: **Tasi ve Isim Degistir.** Hem dosya tasimak hem de ismini degistirmek icin kullanilir.
* `rm -rf [isim]`:  **TEHLIKE!** Klasoru ve icindeki her seyi soru sormadan, kalici olarak siler.

###  3. Izinler ve Yetki (DevOps Icin Kritik)
* `sudo [komut]`: **Yonetici (Root) Yetkisi.** "Erisim engellendi" (Permission denied) hatasi alirsan komutun basina bunu koy.
* `chmod +x [script.sh]`: **Calistirma Izni.** Yazdigin script'e "Sen bir programsin, calisabilirsin" yetkisi verir.
* `chmod 777 [dosya]`: **Tam Yetki.** Okuma, yazma ve calistirma iznini herkese verir. (Guvenlik acigidir ama test icin kullanilir).

###  4. Dosya Okuma ve Duzenleme
* `cat [dosya]`: Dosyanin icerigini hizlica terminal ekranina basar.
* `nano [dosya]`: **Basit Editor.** Dosyayi acar ve icine yazi yazmani saglar.
    * *Cikmak icin:* "CTRL + X" -> "Y" -> "Enter".
* `grep "aranan" [dosya]`: Dosya icinde kelime arar. (Word'deki CTRL+F gibidir).
* `history`: Terminale yazdigin eski komutlarin gecmisini gosterir.

---
** Gunun Notu:**
Root (`/`) ile Root kullanicisi (`admin`) ayni sey degilmis. Biri mekan, biri sofor.



## 3. Linux Dagitim Aileleri (Distro Wars)

Linux dunyasinda "Hangi isletim sistemini kullaniyorsun?" sorusu onemlidir. Iki ana grup (aile) vardir. Aralarindaki temel fark **program yukleme komutlaridir.**

### A) Debian Tabanli (Debian Based)
* **Kimler Var:** Ubuntu, Debian, Kali Linux, Linux Mint.
* **Dosya Uzantisi:** `.deb` (Windows'taki .exe gibi dusun).
* **Yukleme Komutu (Market):** `apt` veya `apt-get`.
* **Ornek:** Chrome yuklemek istersen -> `apt install google-chrome`
* **Kullanim:** Genelde bireysel kullanicilar ve egitim videolari bunu tercih eder.

### B) Red Hat Tabanli (RPM Based)
* **Kimler Var:** RHEL (Red Hat Enterprise), CentOS, Fedora ve **Amazon Linux** (AWS'de bunu cok goreceksin).
* **Dosya Uzantisi:** `.rpm` (Red Hat Package Manager).
* **Yukleme Komutu (Market):** `yum` veya `dnf`.
* **Ornek:** Chrome yuklemek istersen -> `yum install google-chrome`
* **Kullanim:** Bankalar, buyuk sirketler ve AWS sunuculari genelde bunu kullanir.

---
> **Kritik Not:** Eger AWS'de "Ubuntu" sunucu acarsan `apt` komutunu, "Amazon Linux" sunucu acarsan `yum` komutunu kullanmalisin.



## 4. Paket Yonetimi ve Uzantilar (.exe vs .rpm)

Windows kullanicilari `.exe` dosyasina aliskindir. Linux'ta ise dagitima gore degisir.

### Windows Mantigi
* **.exe (Executable):** "Tikla ve Kur" mantigidir. Mobilyayi montajli halde eve getirmek gibidir.

### Linux Mantigi (.deb ve .rpm)
Linux'ta programlar "paket" (package) halindedir. Bunlar **IKEA Kutusu** gibidir. Sen kutuyu indirirsin (`apt` veya `yum` ile), sistem senin yerine kurar.

* **.deb (Debian Package):** Ubuntu ailesi kullanir.
* **.rpm (Red Hat Package Manager):** Red Hat ailesi kullanir.

---
###  Red Hat Ailesi Soyagaci (Kafan Karismasin)
Bu ailenin uyeleri aynidir, sadece amaclar farklidir:

1.  **Fedora:** Deneme tahtasidir. Yeni ozellikler once buraya gelir. (Beta Surum gibi).
2.  **RHEL (Red Hat Enterprise Linux):** Parali ve kararlidir. Sirketler bunu kullanir.
3.  **CentOS:** RHEL'in **UCRETSIZ** kopyasidir. Kodlari aynidir.
4.  **Amazon Linux:** AWS'nin kendi urettigi, Red Hat tabanli isletim sistemidir.

> **Ozet:** Hepsi kardestir. Hepsinde `yum` komutu ve `.rpm` dosyasi gecerlidir.


## 5. Kernel vs Distro (Cekirdek ve Dagitim Farklari)

Cok karistirilan bir konudur. Iki farkli Linux yoktur, tek bir Linux vardir.

### 1. Kernel (Cekirdek)
* Linux'un kalbidir. Donanimla (RAM, CPU) konusan parcadir.
* Dunyadaki TUM Linux dagitimlari (Ubuntu, CentOS, Android) **AYNI KERNEL'i** kullanir.

### 2. Distro (Dagitim)
* Kernel'in uzerine giydirilmis kiyafettir.
* Sirketler veya topluluklar Kernel'i alir; icine dosya yoneticisi, grafik arayuz ve paket programlari ekleyip paketlerler. Buna "Distro" denir.

### 3. Neden Red Hat Parali?
* Linux (Kod) bedavadir, satilamaz.
* Red Hat sirketlere **7/24 Teknik Destek (Support)** sattigi icin paralidir.
* Bankalar ve buyuk sirketler, bir sorun oldugunda muhatap bulabilmek icin Red Hat'e para oder.
* **Debian/Ubuntu:** Topluluk desteklidir (Community Based). Sorun olursa forumlara yazarsin.


## 6. GPL Lisansi (General Public License)

Yazilim dunyasinin anayasasidir. "Copyleft" (Telif Feragati) olarak da bilinir.

### 3 Temel Kurali Vardir:
1.  **Kullanim Ozgurlugu:** Yazilimi istedigin amac icin (ticari dahil) kullanabilirsin.
2.  **Degistirme Ozgurlugu:** Kodlarini degistirebilir, gelistirebilirsin.
3.  **Paylasma Zorunlulugu (EN ONEMLISI):** Eger GPL lisansli bir kodu degistirip dagitirsan, **yeni halinin kaynak kodlarini da** herkese acmak zorundasin.

> **Ozet:** "Al, Kullan, Gelistir ama Saklama!" felsefesidir. Linux'un bugunlere gelmesini saglayan guvence budur.


## 7. Commands & File Systems Iliskisi

Linux kullanimi bu iki kavramin etkilesimidir: "Komutlari kullanarak Dosya Sistemini yonetmek."

### A) File System (Mekan / Yapi)
* Verilerin diskte nasil tutuldugu ve klasor hiyerarsisidir (`/`, `/etc`, `/home`).
* **Altin Kural:** "In Linux, Everything is a File." (Linux'ta her sey dosyadir).
    * Klavye, Mouse, Ekran Karti, RAM... Linux icin hepsi okunabilir/yazilabilir birer dosyadir.

### B) Commands (Araclar / Eylem)
* Dosya sistemi uzerinde islem yapmamizi saglayan kucuk programlardir.
* Aslinda her komut `/bin` veya `/usr/bin` klasorunde duran minik bir dosyadir.
* Biz terminale `ls` yazdigimizda, Linux gider `/bin/ls` dosyasini calistirir.

> **Ozet:** File System bir haritadir, Commands ise o haritada gezen aractir.


## 8. Disk Yonetimi ve "Mount" Kavrami (Cok Onemli)

Linux'ta "D: Surucusu", "E: Surucusu" yoktur. Tum diskler tek bir agacin (`/`) dallaridir.

### Mount (Baglama) Nedir?
Yeni bir Harddisk veya USB taktiginda, onu sistemdeki **bos bir klasore** baglama islemine "Mount" denir.

* **Windows Mantigi:** Yeni disk tak -> Yeni harf ver (D:).
* **Linux Mantigi:** Yeni disk tak -> Mevcut bir klasore bagla (`/mnt` veya `/data` gibi).

### Neden Klasore Bagliyoruz? (DevOps Senaryosu)
Bu yontem sunucularda buyuk esneklik saglar.

1.  **Senaryo:** Veritabani klasorun (`/var/lib/mysql`) doldu. Disk yetmiyor.
2.  **Cozum:**
    * Yeni ve buyuk bir disk satin alirsin.
    * Bu diski, **direkt olarak** `/var/lib/mysql` klasorune MOUNT edersin.
3.  **Sonuc:** Programin (MySQL) haberi bile olmaz! O hala ayni klasore yazdigini sanir ama arkada artik devasa bir disk vardir. Ayar degistirmeye gerek kalmaz.

### Kisa Ozet
* **Windows:** Fiziksel ayrimi sever (C: baska, D: baska).
* **Linux:** Soyutlamayi sever. 10 tane disk de taksan, kullanici sadece klasorler gorur.
* **Not:** Windows da aslinda diski klasore baglayabilir (NTFS Mount Point) ama varsayilan olarak bunu gizler ve surucu harfi kullanir.

