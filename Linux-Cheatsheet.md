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


###  9. Dosya Icerigi Goruntuleme (Okuma)

* `cat [dosya]`: **(Hizli Bakis)** Kisa dosyalarin tum icerigini ekrana basar.
    * *Ornek:* `cat notlar.txt` -> Icinde ne varsa gosterir.
    *  **UYARI:** Cok buyuk dosyalarda (loglar gibi) kullanma, ekrani kilitler!

* `less [dosya]`: **(Akilli Okuyucu)** Buyuk dosyalari sayfa sayfa acar. RAM'i siserrmez.
    * *Kullanim:* `less buyuk_log.txt`
    * *Cikis:* Klavyeden **"q"** tusuna basarak cikilir.
    * *Gezinti:* Bosluk (Space) tusuyla asagi, "b" tusuyla yukari cikilir.

* `head -n [sayi] [dosya]`: **(Bas Kisim)** Dosyanin sadece bastan belirtilen kadar satirini gosterir.
    * *Ornek:* `head -n 10 log.txt` -> Sadece ilk 10 satira bakar.

* `tail -n [sayi] [dosya]`: **(Kuyruk Kisim)** Dosyanin sadece sondan belirtilen kadar satirini gosterir.
    * *Ornek:* `tail -n 20 error.log` -> Hatayi bulmak icin son 20 satira bakar.

* `tail -f [dosya]`: **(Canli Takip - Follow)** Dosyaya yeni yazilan satirlari canli olarak ekrana akitir.
    * *Kullanim:* Sunucu loglarini izlemek icin efsanedir. Cikmak icin **CTRL + C** yapilir.

###  8. Dosya Duzenleme (Editorler)

* `nano [dosya]`: **(Terminalin Not Defteri)** Dosyayi acar ve icinde degisiklik yapmani saglar.
    * **Nasil Kullanilir?**
        1. `nano ayarlar.txt` yazip gir.
        2. Yon tuslariyla gez, yazi yaz veya sil.
        3. **Kaydetmek ve Cikmak icin:** Once `CTRL + X`, sonra `Y` (Yes), sonra `Enter`.

###  9. Arama Islemleri (Google Gibi)

* `grep "aranan" [dosya]`: **(Cimbizla Cekme)** Dosyanin icini acmadan, icinde gecen kelimeyi bulur ve o satiri getirir.
    * *Ornek:* `grep "ERROR" sunucu.log` -> Milyonlarca satir icinden sadece hata olanlari bulur getirir.



###  10. VIM Editor (Profesyonel Editor)

* `vim [dosya]`: Dosyayi Vim editoruyle acar.
    * **DIKKAT:** Vim acilinca hemen yazi yazamazsin! Once "i" tusuna basman gerekir.

#### Vim Hizli Kullanim Klavuzu:
1. **Yazi Yazmak Icin:**
   * `i` tusuna bas (Insert Mode). Artik yazi yazabilirsin.

2. **Komut Moduna Donmek Icin:**
   * `ESC` tusuna bas. (Yazi yazmayi bitirince mutlaka bas).

3. **Kaydetmek ve Cikmak Icin:**
   * Once `ESC`'ye bas.
   * Sonra `:wq` yaz ve `Enter`'a bas. (Write & Quit).

4. **Kaydetmeden Cikmak Icin (Panik Cikisi):**
   * Once `ESC`'ye bas.
   * Sonra `:q!` yaz ve `Enter`'a bas. (Degisiklikleri cope atar ve cikar).


###  11. Dosya Tipleri (File Types)

* `ls -l`: Terminalde dosya listesi aldigimizda en soldaki harfe bakariz.
    * **DIKKAT:** Windows'taki sari klasor ikonlari yoktur, dosyanin kimligini bu ilk harften anlariz.

#### En Cok Karsilasacagin 3 Tip:
1. **Sari Klasor (Directory):**
   * `d` harfi ile baslar. Artik icine `cd` komutuyla girebilirsin.

2. **Normal Dosya (Regular File):**
   * `-` (tire) isareti ile baslar.
   * **DIKKAT:** Icine `cd` ile GIREMEZSIN! Metin veya koddur.

3. **Kisayol (Link):**
   * `l` harfi ile baslar. Asil dosya baska yerdedir, bu sadece ona giden bir koprudur.



###  12. Izinler ve Sahiplik (Permissions)

* `403 Forbidden`: AWS'de site yayina alirken "Erisim Reddedildi" hatasi alirsan %99 sebebi budur.
    * **DIKKAT:** Linux paranoyaktir, dosyayi kimin okuyacagini/yazacagini bilmek ister.

#### A) Izinlerin Mantigi (rwx):
1. **Okuma (Read):**
   * `r` harfi ile gosterilir. Dosyayi okuyabilir mi? (Puani = 4)

2. **Yazma (Write):**
   * `w` harfi ile gosterilir. Dosyayi degistirebilir/silebilir mi? (Puani = 2)

3. **Calistirma (Execute):**
   * `x` harfi ile gosterilir. Bu bir programsa calistirabilir mi? (Puani = 1)

#### B) Hayat Kurtaran "chmod" Komutlari:
1. **Hayat Opucugu (Calistirma Izni):**
   * `chmod +x [script.sh]` yazarak kendi koduna calisma yetkisi verirsin.

2. **Saatli Bomba (Tam Yetki):**
   * `chmod 777 [dosya]` yazarak herkese tam yetki verirsin. (Canli sunucuda ASLA yapilmaz!)

3. **Standart Web Dosyasi:**
   * `chmod 644 [dosya]` yazarak siteye girenlerin sadece okumasini saglarsin.

4. **AWS Sunucu Guvenligi:**
   * `chmod 400 [anahtar.pem]` yazarak gizli sunucu anahtarini kilitlersin. Yoksa AWS seni iceri almaz.

#### C) Tapu Devri (chown Komutu):
1. **Sahibi Degistirmek Icin:**
   * `sudo chown [yeni_sahip]:[yeni_grup] [dosya_adi]` komutu kullanilir.
   * **DIKKAT:** Root'un olusturdugu dosyayi duzenleyebilmek icin once tapusunu alman gerekir.


   ###  13. Filtreleme Islemleri (Filtreler - Veri Ayiklama)

* `Filter`: Bir veri yigininin (dosya veya komut ciktisi) icinden sadece ihtiyacimiz olan kismi suzmeye yarar. Genelde `|` (Pipe) isareti ile baska komutlarla beraber kullanilir.

#### En Cok Kullanilan Filtre Komutlari:

1. **grep (Aranan Kelimeyi Bul):**
   * En onemli filtredir. Dosya icinde kelime arar.
   * *Kullanim:* `grep "ERROR" server.log` -> Log dosyasi icindeki tum hatalari listeler.

2. **sort (Sirala):**
   * Metinleri alfabetik veya sayisal olarak siralar.
   * *Kullanim:* `sort isimler.txt` -> Isimleri A'dan Z'ye dizer.

3. **uniq (Tekrar Edenleri Sil):**
   * Dosyadaki pes pese gelen ayni satirlari teke dusurur. Genelde `sort` ile beraber kullanilir.

4. **wc (Kelime Sayaci - Word Count):**
   * Dosyada kac satir veya kac kelime oldugunu soyler.
   * *Kullanim:* `wc -l [dosya]` -> Dosyanin toplam kac satir oldugunu yazar.

5. **awk ve sed (Ileri Seviye):**
   * Dosya icindeki belirli sutunlari cekmek veya kelimeleri topluca degistirmek icin kullanilir.


   * Ornek Senaryo: "Sunucuda kac tane Python dosyasi var?"
    ls -l | grep ".py" | wc -l

    ls -l: Her seyi listeler.

    | grep ".py": Sadece sonu .py olanlari secer.

    | wc -l: Secilenleri sayar

    SORU:
    John,Doe,120 jefferson st.,Riverside, NJ, 08075
    Jack,McGinnis,220 hobo Av.,Phila, PA,09119
    "John ""Da Man""",Repici,120 Jefferson St.,Riverside, NJ,08075
    Stephen,Tyler,"7452 Terrace ""At the Plaza"" road",SomeTown,SD, 91234
    ,Blankman,,SomeTown, SD, 00298
    "Joan ""the bone"", Anne",Jet,"9th, at Terrace plc",Desert City,C00123
    cevap:
    awk -F',' '{print $3}' dosya.csv
    yada
    cut -d, -f3 dosya.csv


    #  Linux Redirections & Pipes (Yonlendirme ve Borular)
*Hazirlayan: Gelecegin Cloud/DevOps Muhendisi*

## 1. Veri Kanallari (Streams) Nelerdir?
Linux'ta 3 ana kanal vardir:
- **0 (stdin):** Klavyeden girilen veri.
- **1 (stdout):** Basarili ve normal ciktilar (Ekrana basilir).
- **2 (stderr):** Hata mesajlari (Ekrana basilir).

## 2. Temel Yonlendirme Operatorleri
- `>` **(Overwrite - Ustune Yaz):** Ciktiyi dosyaya yazar, dosyada eski bir sey varsa ACIMAZ SILER.
  - *Ornek:* `echo "merhaba" > dosya.txt`
- `>>` **(Append - Sonuna Ekle):** Ciktiyi dosyanin EN ALT SATIRINA ekler. Log tutarken hep bu kullanilir!
  - *Ornek:* `echo "dunya" >> dosya.txt`
- `2>` **(Error Redirect - Hata Yonlendirme):** Sadece hatalari dosyaya yazar, basarili olanlari ekrana basar.
  - *Ornek:* `ls olmayan_klasor 2> hatalar.log`
- `/dev/null` **(Kara Delik):** Ciktiyi veya hatayi sonsuzluga (cope) yollar. Ekranda gormek istemedigin seyleri buraya atarsin.
  - *Ornek:* `ls root_klasoru 2> /dev/null`

## 3. Ileri Seviye (DevOps) Yonlendirmeler
- `> dosya.log 2>&1` **(Hepsini Birlestir):** Hem normal ciktilari hem de hatalari ayni dosyaya yazar.
- `|` **(Pipe - Boru):** Birinci komutun ciktisini, ikinci komutun girdisi yapar. Komutlari zincirler.
  - *Ornek:* `ls -l | grep "txt"` (Listele, ardindan icinden sadece txt olanlari filtrele)

< (Input Redirect - Iceri Al): Bir dosyadaki veriyi okuyup, komutun icine klavye girdisi gibi sokar. (Ornek: sort < liste.txt)



### 16. Kullanicilar ve Gruplar (Users & Groups)

Linux cok kullanicili (multi-user) bir sistemdir. Guvenlik ve yetki yonetimi bu temel uzerine kuruludur.

#### A) Kullanici Tipleri:
1. **Root (Super User):** Sistemin tek patronudur. UID puani `0`'dir. Her seyi silebilir veya degistirebilir.
2. **Normal Kullanicilar:** Bizim gibi sisteme giren kisiler. Genelde UID puanlari `1000`'den baslar.
3. **Sistem Kullanicilari:** Insan degildir. Arka planda calisan servislerdir (nginx, mysql gibi).

#### B) Kritik Dosyalar (Kullanici Bilgileri Nerede?):
1. `/etc/passwd` -> Kullanici adlari, ev dizinleri ve UID bilgilerini tutar.
2. `/etc/group` -> Gruplari ve icindeki kullanicilari listeler.
3. `/etc/shadow` -> Sifrelerin gizli (hashlenmis) hallerini saklar.

#### C) Temel Kullanici Komutlari:
1. **Yeni Kullanici Ekleme:**
   * `sudo useradd -m [kullanici_adi]` -> Kullaniciyi olusturur ve ev dizinini hazirlar.
2. **Sifre Belirleme:**
   * `sudo passwd [kullanici_adi]` -> Olusturulan kullaniciya giris sifresi verir.
3. **Kullanici Silme:**
   * `sudo userdel -r [kullanici_adi]` -> Kullaniciyi ve dosyalarini tamamen ucurur.

#### D) Grup Yonetimi (Departman Kurma):
1. **Yeni Grup Olusturma:**
   * `sudo groupadd [grup_adi]` -> Ornegin: `yazilimcilar` adinda bir grup acar.
2. **Kullaniciyi Gruba Ekleme (Terfi):**
   * `sudo usermod -aG [grup_adi] [kullanici_adi]`
   * **NOT:** `-aG` (Append Group) kullanilir. Boylece kullanici eski gruplarindan cikmadan yeni gruba girer.

#### E) Kimlik Kontrolu:
1. `id` -> O anki UID, GID ve dahil oldugun tum gruplari listeler.
2. `whoami` -> Sistemi o an hangi isimle kullandigini gosterir.

---
### Mudur Stratejisi:
Sirketinde bir stajyer ise basladiginda ona Root sifresini vermezsin. Once `useradd` ile hesabini acar, sonra sadece yetkili oldugu projelerin grubuna (`usermod -aG`) dahil edersin. Boylece stajyer sadece kendi dairesinde calisabilir, tum binayi (sunucuyu) yakamaz.


### 17. lsof -u [kullanici] (Dosya Casusu)

Linux'ta "Her sey bir dosyadir". Bu komut, bir kullanicinin sistemde o an actigi tum kapilari (dosya, internet, servis) listeler.

* **Amac:** Kullanicinin neyi kurcaladigini canli olarak gormek.
* **Kritik Kullanimlar:**
  * `sudo lsof -u stajyer`: Stajyerin actigi tum dosyalari doker.
  * `lsof /home/doganay/sirket.txt`: "Bu dosyayi su an kimler okuyor?" sorusunun cevabini verir.

* **Tablo Basliklari:**
  * **PID:** Islemin kimlik numarasi.
  * **TYPE:** Dosya tipi (REG: Normal dosya, DIR: Klasor).
  * **NAME:** Acik olan dosyanin tam yolu.


  ### 19. Kullanicilar Arasi Gecis (su Komutu)

Terminalde bir hesaptan digerine atlamak icin kullanilir.

* **su [kullanici]:** Kullanici degistirir ama mevcut dizinde kalir.
* **su - [kullanici]:** Kullaniciyi tum profil ayarlari ve ana diziniyle beraber yukler. (En sagliklisi budur).
* **sudo su - [kullanici]:** Sifre sormadan (yetkin varsa) baska kullaniciya gecer.
* **exit:** Bir onceki kullaniciya geri doner (Oturumu kapatir).

**Mantik:** `su` komutu "Switch User" (Kullanici Degistir) anlamina gelir. Basindaki `sudo` ise bu islemi yetkili yapmani saglar.