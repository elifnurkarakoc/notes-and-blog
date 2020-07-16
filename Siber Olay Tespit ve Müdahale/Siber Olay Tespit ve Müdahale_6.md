

### Teknik Hazırlık Aşaması:

Crime Prevention Through Environtmental Design-CPTED-Çevresel Tasarım Vasıtasıyla Suçu Engelleme

Tehdit yüzeyi analizi ve güvenlik alanlarının( domainlerinin tespiti)
-	Kurumsal veri analizi
	-	Kurumsal veri envanteri,yaşam döngüleri ve saklama alanlarının belirlenmesi
	-	Kurumsal veri sınıflandırma ve koruma ihtiyaçlarının belirlenmesi
-	Hizmet sürekliliği açısından kritik sistem, ağ altyapısı ve uygulamaların belirlenmesi
	-	Uygulama katmanında iş etki analizi gerçekleştirilerek kritik uygulamalar ve destekleyen sistemlerin belirlenmesi
	-	Belirlenen uygulamalar ve sistemlerle ilgili mevcut yedekleme altyapılarının tespiti

-	Ağ topolojisinin değerlendirilmesi
	-	Kablosuz ağ bağlantıları ve kullanıcı profilleri
	-	VPN bağlantıları ve kullanıcı profilleri
	-	Dışarıdan içeriye doğru extranet bağlantıları
	-	Şubeler ve zuak lokasyonlar
	-	İnternet'e açık servisler
	-	İnternet'e açık uygulamalar ve kullanıcı profilleri
	-	Sunucu ve kritik verilerin bulunduğu ağ segmenrleri, bu segmentlere erişim kontrolleri
	-	Felaket kurtarma merkezi bağlantıları
	-	Kullanıcı ağ segmentleri
	-	Yazıcı ağ segmentleri
	-	VOIP ağ segmentleri
	-	Kullanıcı bilgisayar, laptop ve akılı cihazları envanteri
	-	Yoğun ziyaretçi trafiği olan ve off-shore'da bulunan cihazlar(kurum dışı ve tek olan cihazlar,örn:ATM)
	-	Çeşitli katmanlarda kullanılan bulut hizmetleri ve hosting hizmeti alınan durumlar
-	Kurum dışı ile paylaşılan veriler ve üçüncü taraf güvenşiği ile ilgili endişelerin belirlenmesi
	-	İş birimlerinden ve BT operasyon birimlerinden veri paylaşılan üçüncü tarafların listesinin alınması
	-	Her bir üçüncü taraf ve paylaşım durumu için gerekli veri koruma ihtiyaçlarının belirlenmesi
-	Dışarıdan bakım hizmeti alınan, kiralanan ve yerinde veya uzaktan erişilen varlıkların belirlenmesi
	-	Sunucular
	-	Yazıcılar
	-	PC'ler
	-	Altyapı donanımları(UPS,telefon santrali vd)
-	Güvenli yazılım ve sistem geliştirme süreçlerinin yeterliliklerinin değerlendirilmesi
-	Yukarıdaki değerlendirmelerin periyodik(en az yılda 1 defa) olarak tekrar edilmesi

Tehdit yüzeyinin daraltılması ve saldırı ihtimalinin azaltılması
-	Erişen kullanıcı profiline uygun olarak ağ bölümlemesi mimarisinin kurulması,eksikliklerin giderilmesi için hemen uygulanabilecek kontrollerin uygulanması, diğerleri için proje planlarının oluştuurlması
-	HTTPS,DNS,Windows Update ve diğer servsiler için dışarı yönlü trafiğin belirli sunucularla kısıtlanması
-	İçeriden dışarıya tüm uç noktalar ve sunucular için filtreleme uygulanması
-	Uç noktalar ve geçit sunucular üzerinde(Web Proxy,SMTP) DLP çözümlerinin devreye alınması
-	Uç nokta ve kurum dışına çıkan cihazlar üzerinde uygulanabilecek donanımsal port kısıtlama ihtiyaç imkanlarının değerlendirilmesi
-	Kriptografik kontrol uygulama ihtiyaçlarının belirlenmesi(uç noktalar,akıllı cihazlar,veri iletim ve depolama ortamları için)
-	Kurum dışı ile veri paylaşılan durumları minimize etme,veriyi paylaşmak yerine uygulama üzerinden verilere erişim imkanı sağlama, gerekli durumlarda kurum verilerini veri paylaşılan taraflarda izole tutma imkanlarını araştırma
Sensör yeterliliklerinin değerlendirilmesi sensör yatırım ve geliştirme planlamasını yapılması
-	Sunucular
	-	Windows sunucular için güvenlik ve gerekli ise ek(ör:sysmon,dhcp,dns,veritabanı,kritik uygulama vd) log toplama ihtiyaç ve imkanlarının değerlendirilmesi
	-	Unix/Linux sunucular için güvenlik log toplama ihtiyaç ve imkanlarının değerlendirilmesi
	-	Veritabanı sunucuları için özel log toplama ihtiyaç ve imkanlarının değerlendirilmesi
	-	Kritik sistemler ile File Integrity Monitoring (FIM) ihtiyaç ve imkanlarının değerlendirilmesi
-	Network Cihazları
	-	Flow verisi toplama ihtiyaç ve imkanlarının değerlendirilmesi
	-	Netowrk cihazları üzerinde yapılan (AAA sunucu imkanları kullanılarak) loglama ihtiyaç ve imkanlarının değerlendirilmesi
-	Firewall'lar
	-	Ağ segment ihtiyaçlarına uygun olarak bölümleme gerçekleştirebilecek firewall ihtiyaç ve imkanlarının değerlendirilmesi
	-	Firewall'lar üzerindeki drop ve forward edilen paket loglama ihtiyaç ve imkanlarının değerlendirilmesi
-	VPN geçitleri
	-	VPN bağlantı loglama imkanlarının değerlendirilmesi
-	Uç noktalar ve güvenlik sunucuları
	-	Anti malware loglama imkanlarının değerlendirilmesi
	-	EDR çözümü ihtiyaç ve imkanlarının değerlendirilmesi
	-	DLP ihtiyaç ve imkanlarının değerlendirilmesi
-	Fiziksel erişim kontrol cihaz ve sunucuları 
	-	Dosya veya veritabanı bağlantısı ile fiziksel erişim loglama imkanlarının değerlendirilmesi

Durumsal Farkındalık
-	Güvenlik mimarisinin sürekliliği için proje yönetim sürecinin düzenlenmesi
	-	Kurumun mevcut genel ve BT proje yönetim süreçleri içine önleyici ve tespit edici gvenlik kontrol ihtiyaçlarının tespiti,uygulanmasının takibi ve izleme süreçlerine dahil edilmesi için gerekli düzenlemlerin yapılması
	-	Değişiklik yönetim sürecinde otorizasyona tabi olmadan herhangi bir değişikliğin yapılmasının,test v. amaçlarla yeterli güvenlik ve sıkılaştırma yapılmadan yeni bir sistemin ağa sokulmasının engellenmesi
-	Sistem sıkılaştırma prosedürleri
	-	Sunucu,PC,ağ cihazı vd. altyapılar bazında özellikle çok kurulumu yapılan sistemler için sıkılaştırma(gereksiz servislerşn kapatılması, parola, güncelleme ve loglama politikalarının uygulanması,güvenlik çözümlerinin-anti malware,DLP,EDR vd. kurulması)

-	Envanter ve güncelleme takibi
	-	Güvenilir envanter takip dosya,liste ve sistemlerinin belirlenmesi ve periyodik olarak gözden geçirilmesi
	-	Periyodik ağ taramaları(filtreleme kuralları gözde tutularak gerekli ağ segmentleri içinden) ve merkezi yönetim sunucularından alınacak listeler ile dokümante edilmiş envanter ile fiili envanterin karşılaştırılması
	-	Log kayıtlarından tespit edilebilecek ağa yeni cihaz vb bağlantı durumlarının periyodik olarak gözden geçirilmesi ve dökümante edilmiş envanter ile karşılaştırılması
-	Erişim kontrol matrisinin sürekli gözden geçirilmesi ve yüksek yetkili kullanıcı hesaplarının/gruplarının merkezi olarak izlenmesi
	-	Erişim kontrol matrislerinin kaynaklarının belirlenmesi
	-	Yüksek yetkili kullanıcı listesinin oluşturulması
	-	Yüksek yetkili kullanıcı erişim bilgileri log kaynaklarının belirlenmesi ve gerekli alarm durumlarının(yani anormal erişim durumlarının belirlenmesi)
	-	Yüksek yetkili kullanıcı grup listesinin oluşturulması
	-	Yüksek yetkili kullanıcı gruplarına ekleme loglarının kaynaklarının belirlenmesi ve alarm kurallarına eklenmesi
-	Denetim,zafiyet tarama ve pentest raporlarından faydalanma
	-	Denetim raporlarından tespit edile süreç bulgularının izlenmesi ve bunlara uygun olarak izleme stratejilerinin yeniden değerlendirilmesi
	-	Zafiyet tarama ve pentest rapor bulgularının izlenmesi ve bunlara uygun olarak izleme startejilerinin yeniden değerlendirilmesi
	-	Bulgu ve düzeltici faaliyet kayıtlarındaki ilerlemelerin izlenmesi ve geciken alanlarla ilgili endişelerin gerekli yöneticilere iletilmesi,gerekli ise izleme stratejilerinin yeniden değerlendirilmesi
-	Denetim izi(audit log) ayarlarının belirlenmesi ve izlenmesi
	-	Güvenlik izleme stratejisini destekleyecek log konfigürasyon ihtiyaçlarının belirlenmesi ve uygulanması
	-	Periyodik olarak(mümkünse) uzaktan ve yerinde log ayarlarının izlenmesi için gerekli yöntem ve süreçlerin geliştirilmesi ve uygulanması
	-	Periyodik olarak log optimizasyonu yapabilmek amacıyla konfigürasyonlarında iyileştirmeye gidilmesi,gerekli noktalarda filtreleme uygulanması
-	Öncü veya yan belirti olarak kapasite kullanım ve kesinti takibi
	-	Web taramalarında web sunucu CPU ve bellek kullanımlarındaki artış
	-	Yine web uygulama taramalarında gözlenen 400 ve 500 yanıt kodlu hatalarındaki artışlar
	-	Ağ trafiğindeki artış
	-	Servislere yönelik exploit denemeleri sonucunda yaşanabilecek servis kesintilerinin izlenmesi

