
### Süreç ve Organizayonel Tanımlar
####	Incident Response Life Cycle
<img src="https://github.com/elifnurkarakoc/notes-and-blog/blob/master/Siber%20Olay%20Tespit%20ve%20M%C3%BCdahale/1-Incident-Response-Life-Cycle.png" width="40%">

**Preparation**:hazırlık, olay olduktan sonra ne yapabilirizi düşünmekten ziyada olayın ihtimalini düşürebileceğimiz çalışmalarda bu kapsamın içerisinde. 
	**Detection & Analysis**: olayın tespiti ve analizi
	**Containment Eradication & Recovery**:saldırganın etki alanını sınırlandırma,saldırganın yaptığı etkinin olumsuz sonuçlarını temizleme yani normal operasyona geri döndürebilme, müdahale sırasında yaptığımız ve fonksiyoneliteyi etkileyen durumları temizleme.
	**Post-Incident Activity**: olay sonrası değerlendirme, neyi yanlış yaptık karşı taraf neyi yanlış yaptı?

**SOC**: Security Operations Center
- Ana Tema: İzleme
		
	7/24 telekom altyapılarını izleyen NOC konseptinin siber güvenlik alanında uygulamasıdır.
	
**CERT**: Computer Emergancy Response Team 
- Ana Tema:Koordinasyon ve Bilgilendirme

**USOM**: Ulusal Siber Olaylara Müdahale Merkezi(TR-CERT)
- Sadece izleme ve müdahale yapan ekipleri kapsamıyor. Bütün Bilgi güvenliği ve yönetimini kapsıyor.

 **CSIRT**: Computer Security Incident Response Team
   - Ana Tema: Olay müdahalesi
    	
    	Olay gerçekleştikten sonra müdahale sürecini yöneten ve gerçekleştiren çok disiplinli ekiplere verilen addır. 

**Güvenlik Yönetiminin Ana Parçaları:**
	**Yönetişim**: Yönetimden bağımsız, yönetimi denetleyen yapı.
	**Güvence**
	**Operasyon**
	
**Yönetişim kavramanın ve güvenlik organizasyonu içindeki iletişimin önemi**

Mimari değişiklikler ve dönüşüm projeleri hakkında olay tespit ve müdahale ekibinin bilgilendirilmesi,görüşlerinin alınması
		
Denetim ve sızma testi sonuçlarına olay tespit ve müdahale ekibinin de erişmesi ve incelemesi

Tespit edilen olaylar sonrasında post-mortem analiz raporlarının disiplinli bir biçimde hazırlanması ve yönetişim ekibi tarafından risk analizi,düzeltici faaliyet planlama vd. aktiviteler de ciddiyetle ele alınması

Güvenlik anahtar performans göstergelerinin yönetimi

Olay tespit ve müdahale ekibine çok kullanılan lokal exploit açıklıkları ve remote açıklıklarla ilgili bilgi sahibi olabilmeleri için yama geçilme bilgilerinin sağlanması(veya bu bilgileri çekecek mekanizmaları kurabilmelerine imkan verilmesi)

Kırmızı takım tabikat ve çalışmalarının yürütülmesi, izleme ekiplerinin bu çalışmalara hem(ofansif tarafta) katılımı hem de izleme faaliyetlerinin etkinliklerinin ölçülmesi 

Ofansif görevlerde çalışmış uzmanların(sızma testi uzmanları) izleme ekiplerine geçişlerne imkan verilmesi

Tespit ve müdahale ekibinin Tehdit İstihbaratı ile desteklenmesi

**Süreçsel Hazırlık Aşaması:**

Playbook'lar(Oyun Taktik Planları): belli türde çok sık rastlanan olaylarda izlenecek sürecin ve yapılacak aktivitelerin önceden planlanması 

 - Oltalama sosyal mühendislik saldırısı 
 - Zararlı yazılım bulaşması 
 - DDOS saldırısı 
 - Web Uygulama Saldırısı 
 - Personelin veri sızdırması

**Süreçsel Hazırlık aşaması:**

<img src="https://github.com/elifnurkarakoc/notes-and-blog/blob/master/Siber%20Olay%20Tespit%20ve%20M%C3%BCdahale/phishing.PNG" width="40%">


<img src="https://github.com/elifnurkarakoc/notes-and-blog/blob/master/Siber%20Olay%20Tespit%20ve%20M%C3%BCdahale/phishing-2.PNG" width="40%">


<img src="https://github.com/elifnurkarakoc/notes-and-blog/blob/master/Siber%20Olay%20Tespit%20ve%20M%C3%BCdahale/phishing-3.PNG" width="40%">


<img src="https://github.com/elifnurkarakoc/notes-and-blog/blob/master/Siber%20Olay%20Tespit%20ve%20M%C3%BCdahale/phishing-4.PNG" width="40%">


<img src="https://github.com/elifnurkarakoc/notes-and-blog/blob/master/Siber%20Olay%20Tespit%20ve%20M%C3%BCdahale/phishing-5.PNG" width="40%">


Tehdit göstergelerinin belirlenmesi **-->** Risk fAktörlernin belirlenmesi **-->** Veri Toplama **-->** Kategorize Etme **-->** Önceliklendirme
	Önceliklendirme **-->** Doğrula **-->** IOC'leri belirle **-->** Kurum Sistmelerinin Taranması **-->** Kapsmaın güncellenmesi **-->** Etkilenen tüm noktaları belirle

**IOC**: Indicator of Compromise(İhlal belirteci) 
IOC'ler ile olayın analizi ile yeni kapılar açılabilir.

