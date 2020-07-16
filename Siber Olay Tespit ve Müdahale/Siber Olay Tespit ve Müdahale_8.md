
### Temel Log Yönetimi
-	Log verisini anlamlandırma ve zenginleştirme ihtiyacının nedeni
-	**Taxonomy**: Log türlerini ve kritiklerini sınıflandırma
-	**Zenginleştirme**: Log kaynaklarının rollerini belirtme,IP adreslerinden yola çıkarak coğrafi konum bilgisi ekleme
-	**Normalizasyon**: farklı log kaynaklarındaki benzer alan isimlerini standartlaştırma,aynı kullanıcıya ait farklı kullanıcı id'leri lookup listesi kullanarak tek isim olarak belirtme

**Örnek IDS Kuralı**
-	**Snort**
	-	iodine aracı ile yapılan DNS tünellemeyi tespit etme

		<img src="https://github.com/elifnurkarakoc/notes-and-blog/blob/master/Siber%20Olay%20Tespit%20ve%20M%C3%BCdahale/snort-kural-1.PNG" width="40%">
		
		- alert: alarm üreticek
		- udp: udp paketlerini incelicek 
		- any any: herhangi bir ip'nin herhangi bir kaynak portundan 
		- -> any 53 : herhangi bir hedef ip adresinin 53 portuna
	    -   içeriğinde binary olarak content kısmındaki veriyi barındıran ve hemen 2 bayt sonra ve 10 bayt derinliğinde content 2 deki veriyi barındıran palet var ise msg de bulunan mesaj ile alarm üretiyor. Belli bir zaman için de kaç tane alarm üreteceğide tanımlı.sid bilgisi kuralın numarası.

		     İkinci kuralda response tarafı kuralın.

**Örnek Zaralı Dosya Tespit Kuralı**
	**Yara**

<img src="https://github.com/elifnurkarakoc/notes-and-blog/blob/master/Siber%20Olay%20Tespit%20ve%20M%C3%BCdahale/yara-kural%C4%B1-1.PNG" width="40%">

-	Dosya taramaları sırasında zararlı yazılımları bulması için kullanılan bir yöntemdir.

	**strings**:zaralının içerisinde görülen stringler
	
	**condition**:kural olarak da zararlının 0. baytından başlayarak şu değerlerin olması gerekiyor ve dosya büyüklüğünün 70KB'den düşük olması gerekiyor ve strings kısmında olan iki string de barındırması gerektiği kural olarak verilmiş.

**Örnek Log alarm ve SIEM Korelasyon Kuralları**
	3 dk içinde aynı kullanıcı adı ile farklı sunuculara 10'dan fazla başarılı veya başarısız erişim denemeleri yapılması
	Port tarama yapan bir sunucudan bir başka sunucuya başarılı bir logon olayı gerçekleştirilmesi
	Aynı kaynak IP adresinden bir web sunucusuna yapılan istekelre karşılık 3 dk içinde 20 den fazla 404 statü kodlu yanıt döndürülmesi

**Tipik Zararlı Yazılım Özellikleri**
- **Dropper**: Resources bölümünden veya uygulama içine gömülmüş çalıştırılabilir kodları dosya sistemine yerleştirme
- **Registry oluşturma**: Sürekliliği(persistence) garanti altına almak zere belirli registry key'lerine değer yazma
- **Servis oluşturma**: Sürekliliği(persistence) garanti altına almak üzere drop ettiği veya sonradan dışarıdan çektiği bir çalıştırılabilir kod ile servis oluşturma	
- **Dışarı yönlü erişim**: HTTP(S),DNS,ICMP vd. protokoller içinden tünelleme yöntemi ile dışarı kapı açma veya komuta kontrol sunucusundan emir alma	
- **Kodlanmış veya paketlenmiş kod dosyası formatında olma**: Tersine mühendisliği zorlaştırmak için encoding ve packing metodları ile kendini gizlemeye çalışma

**Indicator Of Compromise(IOC) Örnekleri**
-	Dosya hash değeri
-	Proses adı
-	Servis adı
-	Kullanıcı adı
-	Url isteği DNS sorgusu
-	Registry kaydı
-	Belli bir string'i veya veriyi içeren dosyalar
-	Belli API fonksiyonlarını import eden PE dosyaları,vd.


**Saldırı Belirtileri**
-	Hazır saldırı araçlarını tanımanın faydaları
	-	Hazır araçlar ürettikleri trafikte belirli karakteristik izleri barındırırlar. Sıradan saldırganlar bu araçlar genellikle ön tanımlı ayarları ile kullandıklarından tespitleri daha da kolaydır. Bunlara örnek olarak şunları verebiliriz:
		-	Metasploit(ön tanımlı reverse bağlantı portu olarak 4444 portunun kullanımı)
			-  Psexec spray saldırılarında başarılı olanları tespit etmek için kullanılabilir
		-	Reverse lookup istekleri:
			-	Netcat
		-	Tarama araçlarının karakteristik davranışları
			-	Nmap'in ICMP echo request'e(ping'e) yanıt vermeyen sunucuların TCP 80 portuna bir de SYN paketi göndermesi
			-	Nikto'nun taramalar için kullandığı User Agent başlığında Nikto adının geçmesi
-	Sıradan kullanıcıların kullanmayacakları komutlara örnekler:
	-	Ben kimim ve grup üyeliklerim neler
	-	Sistem üzerindeki diğer kullanıcılar ve grup üyelikleri neler
	-	Dosyalar içinde komut satırında kelime arama
	-	Dosya dizin erişim haklarının komut satırından sorgulanması 
	-	Servis ve task'ların listelenmesi
	-	Sistem bilgileri ve geçilmiş yama bilgilerinin listelenmesi
	-	Domain kullanıcıları listelenmesi

**Adli Bilişim Temel Kavramları**
-	Yasal mevzuata uygun kanıt toplama
-	Forensic kopyasının alınması ve kanıt hash'inin hesaplanması
-	Kanıt orjinallerinin güvenli biçimde saklanması
-	Logların mahkemede kabul edilebilirliği
-	Disk mimarisi,silinen dosyalar,kullanılmayan disk alanları, dosya son cluster'ları,dosya kazıma kavramları
-	Güvenilen çalıştırılabilir dosyaların enfekte olmuş veya yabancı/üçüncü parti dosyalardan ayrıştırılması


