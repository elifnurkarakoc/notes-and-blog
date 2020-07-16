
### Siber Olay Tespit ve Müdahale 

#### Siber Olay Tespit ve Müdahalesinin önemi 

**Equifax**, ABD,Kanada ve İngiltere'de faliyet gösteren bir firma. 140 milyon civarı kişisel veri ile kredi kartı bilgisi sızması ile karşı karşıya kalıyor. Peki nasıl gerçekleşiyor? Equifax'ın Şikayet kabul uygulaması var ve bu uygulama Apache Struts framework üzerinde geliştirilmiş. Olaydan 2 ay önce Amerika'nın Homeland Security departmanı tarafından zafiyet açıklanıyor. Saldırganlar bu iki aylık süre zarfında 140 milyon civarı kişinin kişisel verilerini ve kredi kartı bilgilerini çalıyorlar.

#### Saldırı Metodolojisi
##### The Cyber Kill Chain
<img src="https://github.com/elifnurkarakoc/notes-and-blog/blob/master/Siber%20Olay%20Tespit%20ve%20M%C3%BCdahale/cyberkillchain.png" width="40%">

Herhangi bir saldırı öncelikle **Reconnaissance** ile başlar. Saldırgan hedef tehdit yüzeyini ve kırılgan noktalarını belirlemek için öncelikle bu aşamada zaman harcar.

**Weaponization**: gerekli toolları geliştirme aşamasıdır. Defans araçlarını bildikleri için anormal görünmeyecek yöntem ve araçlar geliştirirler. Zeroday exploitleri geliştirebiliyorlar.

**Delivery**: saldırı araçlarının taktiğinin işletilmesi. Payloadların hedef sistem üzerinde çalıştırılma aşamasıdır.

**Exploitation**: sisteme bir şekilde adım atılmış olması gerekmektedir. Kod çalıştırıldıktan sonra dışarıya shell alınması ve yeni bir kullanıcı tanımlanması örnek verilebilir.

**Installation**: Gerekli toolların karşı tarafa aktarılması aşamasıdır.

**Command&Control**: Komuta kontrol sunucularına bağlantı sağlanması aşamasıdır. tamamen automatize edilmiş bir şey ise ele geçirilmiş varlık sürekli bana bir emrin var mı? sorgulama aşamasına geçmiş olur.

**Actions on objectives**: Saldırganın hedefi bu adımda genel olarak belirtilmektedir. DDoS mu olacak? Lateral Movement mı olacak ? Zombi olarak mı kullanılacak ?


#### Saldırı Metodolojisi
**MITRE ATT&CK** : saldırı yöntemlerini somutlaştırma teknik olarak ne yaptıklarını açıklamak için önemli bir kaynaktır.

**Advanced Persistent Threat**: Kalıcı ileri seviye saldırılar

Ağa sızmak için genellikle sosyal mühendislik ve fiziksel sızma yöntemleri tercih edilir. Ağa ilk adım genellikle son kullanıcı bilgisayarı üzerinden atılır.
Hedefe özel geliştirilmiş zararlı yazılım kullanılır. Hedef bilgisayar üzerindeki koruma önlemlerini minimize eder, genellikle key logger ve screen capture özelliklerini barındırır.
Ele geçirilen sistem erişimin sürekliliği için dışarı yönlü tünel açılabilmesi gereklidir. Bu nedenle bu tür saldırıların engellenebilmesi ve tespiti için en etkili kontrollerden birisi dışarı yönlü filtreleme (**egress filtering**) ve siber istihbarat desteği de bulunan ağ izleme sistemleridir.
Saldırgan hedefine ulaşmak için ağ içinde sızma testi tekniklerini uygulayarak diğer sistemlere de sızmaya çalışır (**Lateral movement**)
Saldırgan kritik sistemlerle ilgili yeterince bilgi topladıktan sonra geçerli ve yetkili bir erişime benzer şekilde erişir, bu sayede izlenen sistemler üzerinde şüpheli aktiviteyi minimize eder.



#### Sosyal Mühendislik 
##### Drive by Downloads:
Kurban sadece bir web sitesini ziyaret ettiğinde bilgisayarına zararlı yazılım indirilmekte ve çalıştırılmaktadır.  Bu saldırı şu şekilde geliştirilmektedir.

**Kurbanın Zaralı Siteyi Ziyareti**: Saldırgan kurbanı kendi kontrol ettiği bir siteye sosyal mühendislik yöntemiyle yönlendirir. Ya da normal bir web sitesinin HTML injection açıklığını kullanarak bu siteye görünmeyen bir iframe ekler, bu frame kendi kontrol ettiği bir sitenin içeriğini barındırır. Ya da reklam altyapısını kullanarak yayınladığı reklam içeriği ile sonraki adımları gerçekleştirir.

**Exploit Kit**: Saldırganın kontrol ettiği sitenin içeriğine "exploit kit" adı verilen obfuscate edilmiş JavaScript kodlarını ekler. Exploit kit'ler 20$ $-2500$$ fiyat aralığında satın alınabilirler. exploit kit, çok kullanılan browser plugin'lerinin (ör:Flash,Java,PDF Reader v.d.) versiyonlarını inceledikten sonra uygun olan exploiti kullanır.

**Downoad ve Ele geçirme**: Tespit edilen açıklığa yönelik kullanılan exploit shellcode'u saldırganın istediği herhangi bir malware'i kurbanın bilgisayarına indirir ve çalıştırır. Saldırgan bir Exploit Kit Panel üzerinden kurduğu altyapının performansını izleyebilir.

**Zararlı Yazılım içeren dosyalar**: zararlı macro içeren ofis dokümanları, powershell,exe vd çalıştırılabilir kodları çalıştırabilir, internet'den dosya, script vb indirip çalıştırabilir. 
Right to Left Order(RTLO) isimlendirme kullanarak çalıştırılabilir dosyaya ofis dokümanı görüntüsü verme(ör:finans_tlexe.xls).
Renderer uygulama açıklıklarını kullanan dosyalar(ör:PDF,MSWord,Flash,vd).
Icon'u değiştirilmiş(ofis dokümanına, PDF dokümanına benzetilmiş) çalıştırılabilir zararlı uygulama dosyaları(Windows'un ön tanımlı olarak biline dosya uzantılarını gizleme özelliğinden faydalanılması)


