#### Windows Altyapısından kaynaklanan Zayıflıklar:
LM ve NTLM kullanıcı doğrulama protokollerindeki zayıflıklar:
 - Windows Authentication Protokolleri ile ilgili temel konular:
	 - Parola hash'leri 		
	 - Doğrulama protokolleri
 - Hash problemleri: LM Hash'lerinin Zayıflığı
	 - Kullanıcı parolası max 14 karakter  		
	 - Girilen kullanıcı parolaları büyük karaktere çevriliyor 		
	 - Parola gücü 7 karakter ile sınırlanıyor. 7 şer karakter hashleniyor.
 - Protokol Problemleri: 		
	 - Karşılıklı kullanıcı doğrulama Olmaması(Sahte
	   Sunucu) 		
	-   Reflective ve Relay Saldırıları

	Önerilen çözüm (elbette Domain ortamları için) Kerberos kullanıcı doğrulama protokolüdür. Ancak bu protokolün de içsel problemleri olduğunu göreceğiz.

- Pss The Hash(PTH) Saldırıları: 
	-	SAM Dosyasından ve bellekten parola hash'lerinin elde edilmesi:
	
		SAM dosyası Windows işletim sistemlerinde local kullanıcıların parola hashlerinin olduğu dosyadır. 
		Bu dosyaya çalışma anında erişim izni verilmez. Ancak DLL injection ve disk'e raw erişim sayesinde bu engeller atlatılabilir.  Ayrıca bilgisayar diski kriptolu değilse bilgisayar farklı bir işletim sistemi'ne (ör: Linux) boot edilerek veya disk farklı bir bilgisayara takılarak SAM dosyası elde edilebilir.
		SAM dosyasındaki hash'ler kriptoludur, ancak kripto anahtarı da SYSTEM dosyası içindedir. Dolayısıyla bu dosyaya erişilmesi halinde parola hash'leri elde edilebilir.
		
	-	Bellekten hash ve cleartext parolaların elde edilmesi: 
		Parola hash'lerinin ve dahası çeşitli güvenlik alt sistemleri tarafından ihtiyaç duyulan kriptolu (yani decrypte de edilebilen) normal parolaların bellekten elde edilmesi "Mimikatz" aracı ile mümkün olmuştur.
	-	Bu aracın yöntemlerini uygulayan diğer araçlar da mevcuttur: 
		-	Invoke-Mimikatz(powershell)
		-	Windows Credential Editor(WCE)
	-	Decrypt edilebilen paroları bellekte saklayan güvenlik alt sistemlerinden bazıları aşağıdaki gibidir:
		- **TsPkg**: Security Service Provider for Terminal Services: Terminal sunucularına Single Sign On fonksiyonalitesi kazandırır.
			**Wdigest**:  Digest SSP Internet Explorer ve IIS erişimlerinde erişim bilgilerinin MD5 hash'i veya message digest olarak iletilmesi sağlanır.
			**CresSSP**: Uygulamanın kullanıcısının erişim yetkilerini uzaktaki servislere delege etmesi için kullanılır.

		Parola hash ve cleartext hallerinin bellekte bulunması için interaktif logon gerçekleştirilmesi gerekmektedir.
	- Interaktif Logon Türleri:
		- Konsoldan(fiziksel olarak) logon olma 
		- Terminal servisi veya VNC gibi arayüzlerden logon olma 
		- Runas komutu ile farklı bir kullanıcı olarak komut satırından komut çalıştırma
		- PSExec aracını kullanırken -u seçeneği ile farkı bir kullanıcı olarak diğer bilgisayara erişme
	- Network Logon tipi erişimler de bellekte parola hash ve açık halleri görülmemektedir. Bunlara örnek olarak ağ paylaşımlarına bağlanma ve "-u" opsiyonu kullanmadan **PSExec** kullanımı verilebilir.
	- Antivirus yazılımları tarafından iyi bilinen Mimikatz'in kullanılmasından kaçınmak için "procdump" adlı ve Microsoft imzalı Sysinternals aracı ile LSASS.EXE prosesinin adres alanı indirilebilir. Daha sonra dump edilen bellek verisi Mimikatz veya Volatility ile analiz edilerek parola hash ve açık değerlerine ulaşılabilir.
		Parola hashlerini dump edebilen ve başka işlevleri de olan çok sayıda araç mevcuttur:
		-	Mimikatz(exe)
		-	Invoke-Mimikatz(powershell)
		-	Meterpreter payload'u "hashdump" fonksiyonu
		-	pwdump ve benzerleri

LM, NTLM ve domain yapılarındaki Kerberos protokollerinde anahtar olarak kullanıcı parolası değil de kullanıcının parola hash'i kullanıldığından hash bilgisi elde edilen bir kullanıcının parolası offline olarak kırılamasa bile hesabına erişilebilmektedir. Örneğin metasploit'in PSExec modülü kullanıcı parolası yerine PTH yöntemi ile kullanıcı parola hash'i kullanılarak erişimi desteklenmektedir.

- (Impersonation) Delegation Tokenların Çalınması
		2 tür Access Token vardır:
		
	- **Primary Access Token**: Bir process'i çalıştıran kullanıcının haklarını taşıyan tokendır.
		
	- **Impersonation Access token**: bu token ile istemci sunucu mimarisinde çalışan servislerde sunucu istemci proses'in erişim haklarını taşır.
		Delegation Token'lar impersonation token'ların sunucusunun farklı bir bilgisayarda olduğu durumlarda kullanılan özel bir türüdür.

#### Token çalınması ne demektir?

Hedef sistem üzerinde System kullanıcı haklarına ulaşan bir saldırgan sistemdeki diğer kullanıcılara ait olan token'ları çalabilir.
		
Bu token sayesinde domain admin yetkilerine sahip bir kullanıcının yerine geçilebilir.
Bu işlem için  "incognito.exe" veya Meterpreter'in "incognito" uzantısı kullanılabilir.

#### Token'ın Çalınması Nasıl Engellenir? 
msad2 responder1 Properties--> Account is sensitive and cannot be delegated

#### Windows Kerberos uygulamasının sağladığı imkanlar:
	
####  Golden Ticket/Silver Ticket(Pass The Ticket-PTT)

<img src="https://github.com/elifnurkarakoc/notes-and-blog/blob/master/Siber%20Olay%20Tespit%20ve%20M%C3%BCdahale/golden-ticket.PNG" width="40%">

Logon olmak isteyen kullanıcı var. Kullanıcı adı,Domain Controller üzerinde çalışan KDC alt servisi olan Authentication Service'ne gönderilir( yani bilgi güvenliğindeki karşılığı Identification. Authentication değil.)
	Authentication servisi, böyle bir kullanıcı benim sistemimde var mı? var ise karşıdaki kullanıcının bilgisayarına erişmek isteyen kullanıcı parola hashi ile kriptolanmış olan bir TGT gönderiyor. Kullanıcının bilgisayarında kullanıcının girmiş olduğu parolanın hesaplanmış parola hash'i ile bu TGT'yi açabiliyor ise kullanıcı parolasını biliyor. Bu Authentication mekanizmasının gerçekleşmesi için Salt kullanılmıyor. Salt olması için client bilgisayarında bunu bilmesi gerekiyor.Bu da mümkün değil.
	Kullanıcı Windows network'teki başka bir servise erişmek isterse:
	İstemci Ticket Granting Service gidiyor. Giderken de TGT'yi gönderiyor. Eğer TGT geçerli ise Domain controller TGS ile bir servis ticket'ı gönderiyor. Service Ticket erişilmek istenen sunucunun servisinin arkasındaki sunucunun parola hash'i ile Ticket'ı kriptolayarak istemciye gönderiyor.


Domain Parola Hash'lerinin Elde edilme yollar:
- vssadmin araı ile Volume Shadow Copy alarak.
- PowerSploit NinjaCopy powershell script'i ile disk'e raw formatta erişerek(bu şekilde NTDS.dit dosyasına erişim kontrolleri aşılmaktadır.)
- Mimikatz'in DCSync özelliği kullanılmak suretiyle Backup Domain Controller gibi davranılarak(bu şekilde reversible tutulan parolaların cleartext formatta da ele geçirilmesi mümkün olmaktadır.)

Tüm bu işlemler için doğal olarak domain admin kullanıcılarından birisinin parolası çalınmış olmalıdır.

NTDS.dit'in çalınmasının diğer sonuçları:
NTDS.dit dosyası herhangi bir şekilde elde edilmiş bir doman'de olabilecek diğer risklere örnekler aşağıdaki gibidir:
- PC vd disklerin kriptolanması için kullanılmış ve Domai Controller'da yedeklenmiş Bitlocker anahtarları
- LAPS(Local Administrator Password Solution) local administrator kullanıcı parolaları(değiştirme aralıkları kısa ise kısa bir süre kullanılabilecektir)

#### Golden Ticket:
Domain admin olmuş bir saldırganın domain parola hash'lerini elde etmek istemesinin en önemli nedenlerinden birisi KRBTGT kullanıcısının parola hash'ini elde edebilecek olmasıdır.
Bu kullanıcı tüm TGT'leri imzalayan kullanıcı olduğundan saldırgan kendisine uzun süreli(ör:10 yıl) bir TGT üretebilir.
	Bu kullanıcının gerçekte var olması bile gerekmez, Domain Admins grubuna(RID-512) dahil olması yeterli olacaktır. Pek çok sistem log'un da (ör:MSSQL Sunucusunda) kullanıcı adı olarak da verilen kullanıcı adı görünecektir.
#### Golden Tickettan nasıl kurtulunur? 

Saldırganın ürettiği TGT2nin geçersiz olması için KRBTGT kullanısıcının parolasının 2 defa sıfırlanması gerekir. 1 defa sıfırlandığından eski parola ile ticket almış kullanıcıların kesintiye uğramaması için eski parola sistem tarafından hatırlanır.

Ön tanımlı olarak TGT geçerlilik süresi 10 saattir. Dolayısıyla sistemde bir aksama olmaması için 2 sıfırlama arasında 10 saat beklenebilir.
	
#### Silver Ticket:
Bu yöntemde hedeflenen servise yönelik sahte bir Service Ticket üretilmesi ve servise yetkisiz erişim sağlanması hedeflenir. Bunun için hedef servis kullanıcısnın parola hash2ini elde edilmiş olması gereklidir.
Mimikatz ile şu bilgiler kullanılarak Silver Ticket üretilebilir:
- Domain SID
- Target
-	Service
-	User
-	Group

#### Kerberoasting :

Bu yöntemde servis kullanıcılarının parolalarının kırılmasının yanı sıra Silver Ticket üretmede olduğu gibi ilgili servise yönelik alınan service Ticket'ın ST içindeki kullanıcı bilgilerinin değiştirilmesi de hedeflenebilir.

Kerberoasting yöntemi ile Silver Ticket üretebilmek için Domain admin haklarına sahip olmak da gerekmez. Ancak servis hesabının parolasının kırılabilecek kadar,yani bir sözlük saldırısıyla tespit edilebilecek kadar zayıf olması gerekir 
Kerberoasting için SPN bilgilerini ve Service Ticker elde etmek için çeşitli VBS,Python(ör: Impacket) ve powershell(ör:Empire) scriptleri mevcuttur. Daha sonra servis parolasının kırılması gerekecektir.

#### Kerberoasting Handikap'ı nedir?

Üretilen Service Ticket içindeki PAC(Privileged access Certificate) imzalarından KRBTGT tarafından imzalanan veri doğru olmayacaktır(diğer imza servis hesabının parola hash'i ile imzalandığından ve bu bilgiye sahip olduğumuzdan doğru olacaktır.)

Ancak performans gerekçesiyle KRBTGT kullanıcısının imzası genellikle kontrol edilmez. Bu nedenle önemli bir engel olmayacaktır.

