
#### Sistem Log Altyapıları
-	Windows Log Altyapısı
	-	Windows Event Logları
		-	Windows	4624	An account was successfully logged on
		-	Windows	4625	An account failed to log on
		-	Windows	4720	A user account was created
		-	Windows	4722	A user account was enabled
		-	Windows	4740	A user account was locked out
		-	Windows	4946	A change has been made to Windows Firewall exception list. A rule was added
			-	Kaynak Link: https://www.ultimatewindowssecurity.com/securitylog/encyclopedia/default.aspx
	-	Sysmon Logları
		Ürettiği loglar Lateral Movement gibi tekniklere dayanarak bir analistin görmek istediği verileri içeriyor.
		Sysmon logları Applications and Services Logs/Microsoft/Windows/Sysmon/Operational dosyasında saklanır.
			-	Event ID 1: Process creation
			-	Event ID 2: A process changed a file creation time
			-	Event ID 3: Network connection
			-	Event ID 4: Sysmon service state changed
			-	Event ID 5: Process terminated
			-	Event ID 6: Driver loaded
			-	Event ID 7: Image loaded
			-	Event ID 8: CreateRemoteThread
			-	Event ID 9: RawAccessRead
				-	Kaynak Link: https://docs.microsoft.com/en-us/sysinternals/downloads/sysmon

	-	Sysmon Konfigürasyon dosyası örneği:
	
         <img src="https://github.com/elifnurkarakoc/notes-and-blog/blob/master/Siber%20Olay%20Tespit%20ve%20M%C3%BCdahale/sysmon-log-1.PNG" width="40%">
		
		

		-	DriverLoad kısmında eğer imzalayan kurum içerisinde microsoft geçiyor ise bunu loglama.
		-	ProcessTerminate kısmında include demesi ve hiç bir şey tanımlamamış dolayısıyla hiç bir şey tanımlamamış oluyor.
			-	NetworkConnect kısmında sadece 443 ve 80 bağlantılarını logluyor.
	- Diğer Event Log Dosyalarına Örnekler
		-	Yanal hareket [Lateral Movement] açısından önemli olabilecek diğer event loglarına örnek olarak aşağıdakiler verilebilir:
			-	Remote Desktop bağlantıları için: 
			-	Applications and Services Logs **-->** Microsoft **-->** Windows **-->** TerminalServices-LocalSessionManager **-->** Operational
				Task Scheduler sistemi için:
					Applications and Services Logs **-->** Microsoft **-->** Windows **-->** TaskScheduler **-->** Operational

-	Unix&Linux Syslog Altyapısı
	-	Syslog 
-	Genel Log Altyapılarından bağımsız Log Kaynakları
	-	Dosya formatındaki loglar:
		-	DNS
		-	DHCP
		-	WEB
		-	Üçüncü taraf uygulamaların ürettiği log kayıt dosyaları

-	Genel Log Toplama Metodları
	-	WMI
	-	SSH
	-	SMB
	-	SYSLOG
	-	Veritabanı Erişimi 
	-	Diğer özel protokoller

Saldırı araçlarının bıraktığı izler:
-	Kaynak link:https://www.jpcert.or.jp/english/pub/sr/20170612ac-ir_research_en.pdf

	Zaman Çizgisi(Timeline) kavramı ve log kaynaklarının zaman senkronizasyonu
	Logların saklanma süresi(yasal ve inceleme süre gereksinimleri)
-	Logların değiştirilemezliğini güvence altına alınması(sayısal olarak imzalanması)
-	Structured threat Information Exchange[STIX] dili ve Trusted Automated Exchange of Intelligence Information[TAXII] protokolü

       <img src="https://github.com/elifnurkarakoc/notes-and-blog/blob/master/Siber%20Olay%20Tespit%20ve%20M%C3%BCdahale/stix-1.PNG" width="40%">
