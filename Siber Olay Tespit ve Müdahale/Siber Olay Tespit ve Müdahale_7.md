
#### Temel Yetkinlik ve Araçlar 
- Temel işletim sistemleri ve sunucuların güvenlik ihtiyaç ve imkanlarına hakimiyet
-	Ağ ve uygulama sızma testi ve temel saldırı teknikleri bilgileri 
-	Temel TCP/IP ve çok kullanılan protokol bilgileri 
-	Tersine mühendislik becerileri(PE dosya formatı,decompile ve disassemble edebilme ve assembly analiz yetkinlikleri)
-	Adli bilişim temel teknik bilgileri
-	Lateral Movement tekniklerine ve bıraktıkları izlere hakimiyet
-	SIEM ve log yönetim araçları ile bunların kullandıkları altyapılara hakimiyet
-	İzleme ve uzaktan müdahale araçları üzerinde entegrasyon ve geliştirme yapabilme,ihtiyaca göre özel yazılımlar ve betikler geliştirebilme
-	Siber saldırılarda uygulanan yeni tekniklere ve yine siber olay tespit ve müdahale kavram va araçlarına sürekli merak duyma 
#### Temel Araçlar
- Alarm Üreten Araçlar
	-	Anti malware ve davranış tabanlı zararlı yazılım tespit çözümleri(Örn: Bir uygulamanın çalışma anında dışarıya sıradışı porttan bağlantı kurmak istemesi)
	-	Endpoint Detection and Response-EDR çözümleri 
	-	SIEM ve log yönetim çözümleri
	-	IPS/IDS çözümleri
	-	Web Application Firewall-WAF çözümleri
-	Log ve Oturum Verisi Üreten Araçlar
	-	Route ve Firewall'lar
	-	AAA sunucuları
	-	İşletim sistemi sunucuları
	-	Uygulama, veritabanı ve diğer servis sunucuları(DNS,DHCP,veritabanı,vd.)

Görünürlük Kavramı
-	Windows için:
	-	Endpoint Detection &Response(EDR) çözümleri
	-	Sysmon[Application and Services Logs>Microsoft> Windows >Sysmon>Operational]
	-	Powershell Script Block Logging(Group Policy ile aktifleştirilebilir)[Applications and services Logs>Microsoft>Wİndows>Powershell>Operational]
-	Linux için:
	-	auditd paketi

Konfigürasyon denetim ve zafiyet tarama araçları
Honeypot kullanımı ve darknet izleme
Decompiler'lar ve disassembler'lar
Zararlı yazılım dinamik analizi için sandbox ortamları
Siber istihbarat bilgileri


Siber İstihbarat Hizmetleri(ve Güvenlik Araçları ile Entegrasyonu)
-	Veri sızıntıları(kredi kartı,müşteri verileri.)
-	Benzer alan adları
-	Sızan kullanıcı hesapları
-	Güncel sosyal mühendislik ve dolandırıcılık senaryoları
-	IP kara listeleri

Büyük veri kavramları ve Log yönetimi ile ilgileri
-	Hacim,hız,çeşitlilik
-	Cluster mimarisi-kaynak havuzu(resource pooling),yüksek erişilebilirlik(high availability),kolay ölçeklenebilirlik(easy scability) ihtiyaçları
-	Veriyi alma ve işleme(ingesting),verinin saklama ortamında erişilebilir biçimde tutulması(persisting the data in storage),verinin işlenmesi ve analizi(computing and analyzing data),sonuçların görselleştirilmesi(visualizing the results)
-	NoSQL,JSON
-	Stream processing, in memory computing kavramları


