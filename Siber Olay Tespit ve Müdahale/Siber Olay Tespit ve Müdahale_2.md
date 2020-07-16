
#### Bilgi Toplama - Windows

**whoami**: kullanıcı domain ve adı

**hostname**: sunucu adı

**systeminfo**: işletim sistemi adı ve versiyonu yüklü hotfixler

**whoami /groups**: kullanıcının üyesi olduğu grupları

**net users**: kullanıcı listesi

**net localgroup Administrators**: Administrators grubunun üyeleri 

**net localgroup**: kullanıcı grupları

**tasklist /SVC**: çalışan prosesler ve ilgili servis bilgileri

**ipconfig /all**: ağ arayüz bilgileri

**netstat -ano**: dinleyen ağ servisleri 

**net start**: çalışan servisler

**quser**: sisteme bağlı kullanıcılar

**qprocess**: çalışan uygulamalar ve uygulamaları başlatan kullanıcılar

**driverquery**: driver'lar

**net share**: paylaşımlar

**more %WINDIR%\System32\drivers\etc\hosts**: hosts dosyası

**more %WINDIR%\System32\drivers\etc\networks**: networks dosyası

**gpresult /R**: Group policy

**dsquery group**: domain grup listesi

**dsquery user**: domain kullanıcılarının listesi

**dsquery compute**: domaine'e bağlı bilgisayarların listesi

#### Yetki Yükseltme İmkanları
İki temel alandan kaynaklanır: 

 - Konfigürasyon hataları ve erişim bilgilerinin sızması
 
 - Local Exploit imkanları

Belli bir dönem çok sık kullanılmış olan local exploitlere örnek olarak MS14-058 açıklığı ile local system kullanıcı haklarına yükseltme ve DC sunucusuna eriştikten sonra MS14-068 açıklığı ile Domain Admin kullanıcı haklarına yükseltme imkanları verilebilir.

Domain ve erişilen sistem hakkında bilgi toplama amacıyla kullanılan komutların pek çoğu sıradan kullanıcılar tarafından kullanılmayacağından bu proseslerin başlatılmasının izlenmesinde fayda vardır.
Ayrıca lateral movement için kullanılabilen ancak sıradan kullanıcılar tarafından sık kullanılmayan komutların da izlenmesinde fayda vardır.

#### İzlenmesinde fayda olabilecek bazı komutlar:
**cscript**: vbscript çalıştırmak için

**del**: parametre olarak bir exe,bat,ps1 dosyası kullanılmışsa

**Sysinternals araçları**: procdump--> bellek dump etmek, accesschk-->erişim hakları sorgulama, psexece--> uzakta komut çalıştırma

**powershell**: powershell fonksiyonalitesini kullanma

**regsvr32**: Applocker kontrolünü aşmak için

**vssadmin**: NTDS.DIT dosyasını çalmak için Volume Shadow Copy alma

**wmic**: WMI fonksiyonalitesini kullanma

**schtasks**: Scheduled iş oluşturmak için

**netsh**: Firewall konfigürasyonunu yönetmek için

**procdump.exe -accepteula -ma lsass.exe lssas.dmp--> lsass.exe** process'inin bellekteki adres alanındaki tüm verilere erişip dump etmek mümkün. O anda veya kısa bir süre önce sisteme erişmiş olan kullanıcıların bilgilerin dump etmiş olunur.

**minidump lsass.dmp** -->yakın zamanda bağlanmış olan kullanıcıların password'leri clean text olarak elde ediliyor.

#### Yetki yükseltme ve sonraki adımlar:
Bilgi toplama script ve araçlarını ele geçirilen platforma yükleme ve çalıştırma

 - Local exploit çalıştırarak yetki yükseltme 
 - Bir konfigürasyon zaafından faydalanarak yetki yükseltme  
 - Elde edilen arka kapının sürekliliğini sağlama
 - İşlemci gücünü kullanma amacıyla sisteme erişildiyse:
  -- DDOS amaçlı ise gerekli araçları yükleme ve emirler için Command&Control sunucusuna bağlanmaya başlama
--Crypto Mining amaçlı ise gerekli araçları yükleme ve yine komuta kontrol sunucuna bağlanmaya başlama
 - Parola hashlerini ele geçirme
 -  Bellekten parola çalma Registry'den VNC parolası, browser'lar tarafından saklanan erişim bilgileri, WinScp tarafından saklanan erişim bilgileri gibi pek çok erişim bilgisini ele geçirme 
   - Domain ve diğer sistemlerle ilgili bilgi toplama 
   - Diğer dosyaları inceleme 
   - Diğer sistemlere yönelik taramalara başlama

#### Bilgi Toplama-Linux
**whoami**: kullanıcı adı

**id**: kullanıcı id'si ve grupları

**hostname**: sunucu adı

**uname -a** :sistem ve kernel bilgisi

**cat /etc/*-release**: işletim sistemi bilgisi

**lscpu**: işlemci mimari bilgisi

**/sbin/ifconfig -a** : tüm ağ ara yüzlerinin listesi

**echo $HOME**: home dizinimiz

**ls -ahl ~**: home dizin içeriğimiz ve erişim hakları 

**printenv**: Environmental variable değerleri

**last**: son kullanıcı aktiviteleri

**netstat -antp**: TCP servislerin ve ilgili proseslerin listesi

**netstat -anup**: UDP servislerin ve ilgili proseslerin listesi

**cat /etc/passwd**: passwd dosyası(tüm kullanıcılar kullanıcıların kimler olduğunu görebilir)

**cat /etc/group**:group dosyası

**cat /etc/shadow**: shadow dosyası(okuma hakkımız var ise)

**cat /etc/sudoers**


#### Yanal Hareket:

**PSExec**: Sysinternal da bulunan, uzaktaki bilgisayarda komut çalıştırmamızı sağlayan bir yazılımdır.Bu normal bir davranış değildir. karşı tarafta yeni bir servis başlatılmış oluyor.

**WMI**: Uzaktan kod çalıştırmada, log toplamada vb. oldukça yetenekli. 

**Powershell-WinRM**

**Terminal servisi,ssh** vb.

Ele geçirilen sistem kullanıcı adı ve parola bilgileri ile:

 - CrackMapExec(CME)
 - Nmap PSExec spray: nmap -p139,445 --script=smb-psexec
   --script-args=smbuser=kullanici,smbpass=par01a target
 - spraywmi.py Python script'i

gibi araçlarla elde ettikleri bilgilerle daha fazla sisteme erişmeye çalışabilirler.
Elbette böyle bir tarama izlenen bir ortamda dikkat çekecektir.


