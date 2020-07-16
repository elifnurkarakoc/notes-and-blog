### Windows Ağlarıyla Gelen Lateral Movemont İmkanları 

#### VMI-Windows Managment Instrumentation

WMI altyapısı uzaktan WMI provider nesnelerine ve bunların metotlarına erişim imkanı verir. Dolayısıyla bu metotların sağladığı hem bilgi toplama(enumeration) hem de işlem gerçekleştirme imkanlarına sisteme diğer şekillerde erişmeden sahip olabiliriz.
Ayrıca WMI'ın sağladığı Eventing imkanı ile belli durumlarda tetiklenen backdoor'lar kurulabilir. WMI'ın sağladığı bu imkan diske(dosya oluşturma anlamında) değmeden faaliyet gösterme imkanı vermektedir. Hacker'lar tarafından bu duruma LIVING OFF THE LAND adı verilmektedir.

##### Araçlar:
- Powershell:WMI erişimleri için en sık kullanılan araç powershell commandlet'leridir
- wmic.exe:Tüm Windows bilgisayrlarada mevcut olduğu için saldırgan açısından daha az dikkat çekmeye yardımcı olur.
- wmiexec.py:Impacket Python modülünün örnek WMI erişim aracı.
- Metasploit wmiexec modülü.
- Linux üzerinde çalışan wmic,pth-wmic,wmis(PTH yapabilen wmis) araçları


#### WMI Backdoor imkanı: 
WMI Eventing altyapısı sayesinde bir persistence(kalıcılık) imkanı kazanılabilir.
Kalıcı(**persistent**) bir event kaydı (subscription) için aşağıdaki üç faktöre ihtiyaç vardır:
- Event Filter:Bir kullanıcının logon olması, sistemin yeniden başlatılması veya farklı bir olay tarafından tetiklenecek tanım 
- Event Consumer: Filter tetiklendiğinde gerçekleştirilecek faaliyet
- Filter to Consumer Binding:Filter ve Consumer'ı birbirne bağlayan tanım

#### Event Consumer türleri:
- LogFileEventConsumer: Olay verisini belli bir log dosyasına yazar.
- 	**ActiveScriptEventConsumer**:Bir gömülü VBScript veya Jscript çalıştırır.
- 	NTEventLogEventConsumer: Olay verisini bir Windows event kaydı olarak yazar
- 	SMTPEventConsumer:Olay verisini e-posta ile gönderir.
- 	**CommandLineEventConsumer**: Bir komut satırı uygulaması çalıştırır.


Örnek her bir logon işleminde saldırgan WMI ile botnet ağına saldırganı dahil ediyor.


**WinRM-Windows Remote Managment**:
- WinRM Powershell Remoting(Powershell komutlarının uzaktaki bilgisayarın konsolundaymış gibi çalıştırma imkanı) ve CIM ile başlayan WMI provider sınıflarını çalıştırma amaçları ile kullanılabilir.
- HTTP(TCP 5985) veya HTTPS(TCP 5986) protokolleri ile SOAP mesajları ile erişilebilir.
- Açık olması halinde WMI gibi lateral movement amacıyla kullanılabilir,ancak genellikle ön tanımlı olarak kapalıdır. 
- Uzaktan psexec, wmiexec gibi bağlantılarla etkinleştirilebilir.


**DCOM-Distibuted Component Object Model**:

DCOM Microsoft'un dağıtık kod altyapısının bilgisayarlar arasında kullanılmasını destekleyen mimarisidir.

Bu altyapı kullanılarak bir bilgisayardaki bir process bir başka bilgisyardaki COM nesnesine(yapılan bazı registry tanımları sonrasında) erişerek kullanabilir.

Powershell veya farklı bir uygulama dili kullanılarak Excel.Application, MMC20.Application, ShellWindows,ShellBrowserWindow,Visio.Application,Visio.InvisibleApp, Outlook.Application,Word.Application gibi application idleri ile farklı bir bilgisayar üzerinde komut çalıştırılabilir.


**Named Pipe İmkanı**
Named Pipelar anonim pipelarda olduğu gibi okuma ve yazma imkanları verirler ve(Windows işletim sistemi için) SMB Protokolü üzerinden de eişilebilirler.

Uzaktan kötüye kullanım imkanı olma ihtimali düşük olsa da zararlı yazılımlar tarafından ve saldırganların lateral movement çabalarının bir parçası olan backdoor oluşturmak için sıklıkla kullanılırlar.

Yapılan erişimler SMB portlarına yapılacağından backdor zararlı yazılımı tarafından açılacak bir port kadar dikkat çekmezler.

Diğer bilgisayarlarda işlem yapma imkanı veren diğer komutlar

**schtasks**: Uzaktaki bilgisayar üzerinde iş tanımlama

**sc**: uzaktaki bilgisayar üzerinde servis tanımlama


