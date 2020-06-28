## Wifi Security - Kablosuz Ağ Hacking Tekniklerinin Temelleri

Erişim noktası ve istemci arasında geçen iletişim:

<img src="https://github.com/elifnurkarakoc/notes-and-blog/blob/master/Wifi%20Security/wifiSecurity101.png" width="40%">

İletişimin başlangıç noktası: erişim noktaları tarafından yayılan **beacon** paketleridir.  Bir erişim noktasına bağlanmak istediğimizde temel kural bu erişim noktasını görmemiz ya da bu erişim noktasının adını bilmemizdir. Erişim noktalarının kendini etrafa duyurabilmek ve etrafta görünür olabilmek için yaydıkları paketlerdir.

Wireshark da Beacon paket incelemesi için kullanılacak olan filtre:

> wlan.fc.type.subtype==0x0008

Source adres erişim noktamızın MAC adresi iken Destination adres Broadcast adresidir. Erişim noktaları etrafa kendilerini duyurabilmek için Destination adresini broadcast olarak set ediyorlar.

<img src="https://github.com/elifnurkarakoc/notes-and-blog/blob/master/Wifi%20Security/beaconpacket_1.PNG" width="50%">


Fixed Parameter/Capabilities Information /Privacy:AP/STA can support WEP —> erişim noktası bir şifreleme standardı destekliyorsa, ön parola koruması var ise 1 olarak set edilir. 0 ise ön parola koruması mevcut değil.

<img src="https://github.com/elifnurkarakoc/notes-and-blog/blob/master/Wifi%20Security/beaconpacket_2.PNG" width="50%">

Tagged Parameter: kısmından bir erişim noktası hakkında bir çok bilgi temin edilir. Örneğin:

SSID: kablosuz ağın adı.

DS Paramater: Current Channel:1 Erişim noktasının yayın yaptığı kanal numarası bulunmaktadır.

RSN Information/RSN Capabilities: Erişim noktasının sahip olduğu şifreleme standardına ait bilgileri görülmektedir.

**Airodumpng** gibi araçlar erişim noktaları tarafından yayılan paketleri alıp içerisindeki bilgileri parse edip sunuyor.

Erişim noktası beacon paketlerini yaydıktan sonra istemcinin bağlantı talebinde bulunması gerekir. Bu talebe **Probe request** denmektedir. 

> wlan.fc.type.subtype==0x0004

Probe request paketleri incelendiğinde çıkış kaynakları belli ama gideceği adres belli değil. Probe requestler genel olarak Broadcast paket olarak tanımlanıyor. Gideceği adresi bilmiyor etrafa yayılıyor.

Destination adreslerin broadcast olması sahte erişim noktalarının başarı oranını arttıran bir durum.Çünkü gidilecek adres belli değil sadece SSID değerini biliyoruz.

Gizli erişim noktaları, bir kişi ona bağlanmak istediği zaman tespit edilebilir. SSID değeri öğrenilir.

**Probe Response** paketi erişim noktasının ben buradayım dediği pakettir. Gelen bağlantı talebine verilen bağlantı cevabıdır. 

> wlan.fc.type.subtype==0x0005

Destination Adrese bakıldığında bu paketin kime gideceğinin belli olduğu görülmektedir.

Beacon paketinde olduğu gibi Probe response paket içeriğinde bir çok bilgi bulunmaktadır. Sebebi beacon paketi ile aynı nokta tarafından üretilmesi ve temel iletişimi sağlayan paketlerden olmasıdır.

Gizli erişim noktalarının tespiti için Probe response paketleri incelenmelidir.

El sıkışma aşamasında **Authentication Request** ve **Authentication Response** gerçekleşir.
Ağa dahil olma aşaması olarak nitelendirdiğimiz yani IP adresi alma kısmı ilişkilendirme talebi ve bu talebe karşılık bir cevap dönüyor. 

Bunların tamamı sağlandığında erişim noktasına bağlanmış olunur.

