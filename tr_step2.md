# Paket Yönetimi
Sisteminiz internet tarayıcıları, metin editörleri, medya oynatıcılar vb. birçok paketten oluşur. Peki paket nedir? 
Bunları Chrome, Photoshop, vb. olarak biliyor olabilirsiniz ve öyledirler; aslında bir dosyada derlenmiş çok sayıda dosyadan başka bir şey de değildirler.
Bu paketler, sisteminize yazılım yükleyen ve bakımını yapan paket yöneticileri aracılığıyla yönetilir ve çoğu zaman yazılım yüklemek için bir paket yöneticisi kullanacaksınız. En yaygın paket çeşitleri Debian (.deb) ve Red Hat (.rpm)'dir. 

Debian, Pardus, Ubuntu vb. dağıtımlarda Debian tarzı, Red Hat Enterprise Linux, Fedora, CentOS vb. dağıtımlarda ise Red Hat tarzı paketler kullanılır.
+ Debian dağıtımlarında manuel paketler dpkg aracı ile; repo paketleri apt aracı ile yüklenirler ve repolar **/etc/apt/sources.list** dosyasında bulunur.

Linux sistemleri, kullanıcının ihtiyacı olduğunda, programa kolayca ulaşabilmesini sağlayacak program paketlerini içinde bulunduran kendi paket depolarına(repository) sahiptirler. Farklı Linux dağıtımları için bu paketler farklılık gösterebildiği için farklı Linux dağıtımlarının da kendi paketleri üzerinde işlem yapabilmek için farklı komutları vardır.
+ CentOS dağıtımlarında manuel paketler `rpm` aracı ile; repo paketleri `yum` aracı ile yüklenirler ve repolar **/etc/yum.repos.d** dosyasında bulunur.
+ Debian dağıtımlarında manuel paketler `dpkg` aracı ile; repo paketleri `apt` aracı ile yüklenirler ve repolar **/etc/apt/sources.list** dosyasında bulunur.

## APT (Advanced Package Tool) 
APT Paket Yöneticisi, yani Gelişmiş Paketleme Aracı, Debian GNU/Linux ve Debian
tabanlı işletim sistemlerinin paket yönetim sistemidir. APT arayüz ile değil komut sistemi ile çalışmaktadır.
Synaptic gibi yeni yazılım paketleri yükleme, mevcut yazılım paketlerini yükseltme,
paket liste içeriklerini güncelleme ve tüm sistemi güncelleme gibi işlemleri yapan bir
terminal komutudur.
APT’nin terminal üzerinde komutlarla çalışmasına, arayüze sahip olmamasına rağmen
kullanımı oldukça kolaydır.

Komutları incelemeye başlamadan önce belirtmemiz gereken bir nokta var; APT ile
yapacağınız işlemler için terminal açıp komutları girdiğinizde;
```
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
```
şeklinde bir uyarı alıyorsanız bu APT’nin sisteminiz üzerinde değişiklik yapması nedeniyle sizden Root yetkisi istemesinden kaynaklanmaktadır. Bu durumu “Root” yetkisi alarak çözebilirsiniz. Sadece girdiğiniz komut için komutun başına `sudo` yazmanız yeterlidir: ```sudo apt-get update```.

### Paket Listelerinin Güncellenmesi
Sistemdeki paketlerin güncellenmesi için ```apt-get update``` komutunun girilmesi yeterli olacaktır. 
Bu komut ile /etc/apt/sources.list dosyasındaki arşivlerden güncel paket listelerinin indirilmesi sağlanır. Böylece depolardaki güncel paketler alınmış olur.
Bu işlem süresi depolardaki güncelleme miktarına ve İnternet bağlantınıza bağlı olarak değişebilir.

APT komutlarını kullanma esnasında en çok karşılaşılan sorun; komutlar girildiğinde
```
E: Could not get lock /var/lib/dpkg/lock – open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
```
uyarısının alınmasıdır. Bu uyarının sebebi, terminal açıkken APT komutlarını yazdığınızda başka bir paket yöneticisinin açık olmasıdır. 

### Paket Kurma
Çalışmalarımızı **vim** paketi üzerinden gerçekleştireceğiz.
Paket kurulumu yapmak için; ```apt-get install vim``` komutu girilmelidir. 
Buradaki paket adını girerken dikkat etmemiz gereken depolardaki paket adlarını doğru girmemizdir. 
Aksi takdirde depolarda bu paketi bulamayacağı için yüklemeyi gerçekleştiremeyecektir. 
Eğer paketin tam adını bilmiyorsak birkaç harfini girip `tab` tuşu ile otomatik tamamlamayı deneyebiliriz.

### Paket Kaldırma
Sisteminizden kaldırmak istediğiniz paketler için; ```apt-get remove vim``` komutunun girilmesi gerekir. 
APT ile paket kaldırma işleminde bağımlılıklar da kaldırılacak ancak konfigürasyon dosyaları kaldırılmayacaktır. Konfigürasyon dosyaları ile birlikte bir paket kaldırılmak isteniyorsa; ```apt-get --purge remove vim``` komutu kullanılmalıdır.

### Paketleri Yükseltme
Sistemdeki paketlerin tamamının yükseltilmesi için paket listelerini güncelledikten sonra; ```apt-get upgrade``` komutu kullanılabilir. 
Sadece tek bir paketin yükseltilmesi isteniyorsa;```apt-get upgrade vim``` komutu kullanılır. 
Ayrıca dağıtım yükseltmeleri için; ```apt-get dist-upgrade``` komutunun kullanılması gerekmektedir.

