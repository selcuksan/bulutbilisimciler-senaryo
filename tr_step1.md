# Arşivleme ve Çıkarma
Paket kurulumuna ve farklı paket yöneticilerine girmeden önce dosyaları arşivleme ve sıkıştırmayı tartışmamız gerekiyor çünkü internette yazılım ararken bunlarla büyük olasılıkla karşılaşacaksınız. 
Muhtemelen bir dosya arşivinin ne olduğunu zaten biliyorsunuzdur, büyük olasılıkla .rar ve .zip gibi dosya türleriyle karşılaşmışsınızdır. 
Bunlar bir dosya arşividir, içlerinde birçok dosya içerirler, ancak arşiv olarak bilinen tek dosyada gelirler.

## tar
tar, Linux'ta dosyaları sıkıştırmak için kullanılan bir programdır.
Sıkıştırılacak dosyalar oluşturmak için: ```touch d1 d2 d3 d4 d5```

Dosyaları sıkıştırmak için: ```tar -cvf arsiv.tar d1 d2 d3 d4 d5```
-   **-c** Create: tar dosyasının yaratılacağını belirtir.
-   **-v** Verbose: bir tar dosyasının yaratılırken ya da açılırken elden geçen dosyaların isimlerini ekrana listelemek icin kullanılır.
-   **-f** File: yaratılacak,açılacak ya da içindekiler tablosu listelenecek tar dosyasının adının komut satırında verileceğini belirtir.

Sıkıştırılmış dosyayı açmak için: ```tar xvf arsiv.tar```
-   -x Extract: bir tar dosyasının açılacağını belirtir.

Linux yolculuğunuz boyunca bzip2, compress, zip, unzip gibi diğer arşiv ve sıkıştırma türleriyle karşılaşacaksınız. Bunlar biraz daha az yaygın, ancak farklı yardımcı programların farklı komutlar gerektireceğini unutmayın.

