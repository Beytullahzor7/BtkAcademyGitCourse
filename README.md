## GIT Versiyon Kontrol Sistemi Nedir?
**GIT nedir?** diye sorduğunuzda versiyon kontrol sistemi cevabını almışsınızdır. İyi de versiyon kontrol sistemi nedir?

Projemi geliştirirken "proje", "projee", "projee_son", "projee_son_5" şeklinde klasörlesem olmaz mı? GIT öğrenmeden olmaz mı? - OLMAZ!

Son sorudan başlayayım. Eğer profesyonel işler yapacaksanız GIT öğrenmek zorundasınız. Klasör isminin sonuna fazladan harfler, rakamlar ekleyerek proje geliştirmek ilerleyen süreçlerde başa çıkılabilecek bir yöntem değildir.

Versiyon Kontrol Sistemi Nedir? sorusuna gelirsek; Bir döküman (yazılım projesi, ofis belgesi vb.) üzerinde yaptığınız degişiklikleri adım adım izleyen, istediğinizde kayıt eden ve isterseniz bunu internet üzerindeki bir bilgisayarda veya yerel bir cihazda (respository / repo / depo) saklamanızı ve yönetmenizi sağlayan bir sistemdir.

Versiyon Kontrol Sistemi yerine Kaynak Kod Yönetim Sistemi ifadesini de duymuş olabilirsiniz. İkisi de aynı şeyi ifade etmektedir.

**GIT Bize Ne Sağlar?** <br>
Birden fazla yerde (dağıtık olarak) dosyalarınızı ve versiyon kontrol bilgilerinizi depolayabilirsiniz. Böylelikle cihaz bağımsız olarak dosyalarınıza erişebilirsiniz.
"commit" yaparak SnapShot (anlık görüntü) özelliği ile istediğiniz zaman proje veya dosyaların o anki halini kayıt altına alabilirsiniz. Böylelikle ileride bir hata ile karşılaşırsanız herhangi bir zamandaki herhangi bir versiyona dönüş yapabilirsiniz.
SnapShot alındıktan sonra değişiklik yapılan dosyaları görebilirsiniz.
Takımların aynı projede beraber çalışmasına imkan verir. Kim neyi düzenledi? Ne ekledi? Ne çıkarttı? Son değişiklik ne zaman yapıldı? gibi bilgilere erişebilirsiniz. Bu sayede topluluk ile proje geliştirme süreçlerini kolaylaştırabilirisiniz.
Projede versiyonlanmasını istemediğiniz dosyaları belirtebilirsiniz. (node_modules, .mp4, .log, .env gibi)

```
$ls --> İçerisinde bulundugumuz klasörleri listeler ve gösterir
$ls -la --> Gizli klasörleri gösterir
$pwd --> Print Working Directory. Güncel olarak içerisinde bulunduğumuz dizini gösterir 
$cd --> Change Directory 
$cd .. --> Bir üst dizine git 
$clear --> Konsol ekranını temizler
$mkdir --> Make Directory
$touch not.txt --> not.txt adında bir dosya olusturduk
$rm not.txt --> Yukarıdaki satırda olusturdugumuz not.txt isimli dosyayı siler
$rm -rf --> Olusturulan bir klasörü siler
$git --> Git içerisindeki mevcut komutları açıklamaları ile beraber ekrana getirir
$git --version --> Git'in içerisindeki mevcut komutları açıklamaları ile beraber ekrana getirir
$git config --global user.name "Beytullah Zor" --> Global kullanıcı ismini belirleriz
$git config --global user.email beytullahzor7@gmail.com --> Global kullanıcı emailini belirleriz
$git status --> Git'in güncel durumunu gösterir
$git init -->Git'i başlatırız
$git add --> Dosya ekleme işlemi yaparız
$git add . -->Bütün dosyaları ekleriz
$git commit -m "message" --> Commit mesajı ekleriz
$git log --> Yapılan commitlerin geçmişini listeler
$git commit --amend --> Son commit üzerine yeni dosyalar ekleyerek aynı commitin içeriğini değiştirdik. Yeni bir commit oluşturmadık 
$git commit --amend -m "message" --> Commitin mesajını değiştirdik
$git branch --> Mevcut branchleri listeler
$git branch -M main --> Ana branchin adını main olarak değiştirir
$git branch feat --> Feat adında yeni bir branch olusturduk
$git branch -d branchname --> Branch silmek
$git branch -r --> Remote branchleri gösterir
$git checkout origin/master --> Remote branchlere gecerken switch degil checkout kullanırız
$git fetch origin master --> Uzak sunucudaki değişiklikleri locale getirerek bize gösterir
$git pull origin master --> ($git fetch + $git merge) Yani github üzerindeki değişiklikleri projeme ekle demektir
$git switch master --> Master branchine gecis yaptık
$git merge feat --> Feat branchi ile Master branchini birleştirdik
$git log -n 1 --> En son commiti getirir
$git log -n 2 --> En son 2 commiti getirir
$git checkout -b footer --> Şuan master branchi üzerindeyken footer adında yeni bir branch oluşturdum ve ona geçiş yaptım
```

* Her commitin kendine ait bir hashi olur ve uniquedir
* .gitignore adında bir dizin olusturup gözükmesini istemediğim dosyaları bu yapı içerisinde belirtirim


<br>

**HEAD**
```
Git içerisinde nerede olduğumuzu gösterir. Genellikle son commitimizi gösterir. Commit ve branch açısından benim güncel konumumu verir
```

<br>

**STASH**
```
Master brachinden farklı bir branch açıp, içerisine bir dosya oluşturup git add . dersek ve commit etmezsek,
tekrar master branchine dönüş yaptığımızda o dosya master branchi içerisinde gözükür.

Yaptığım işleri al, bir yerde sakla ve ben bu işlemleri şuan için görmeyeyim ama lazım olduğunda istediğim zaman kullanayım. İşte bu işleme stash adı verilir

$git stash --> Artık yaptığım işlemler ara bir katmanda yer alır
$git stash pop --> Stash işleminde ara bir katmana aldığım dosyaları, o an hangi branch üzerinde işlem yapmak istiyorsam ve dosyaları oraya getirmek istiyorsam geri getiren komuttur
$git stash list --> Saklı olan stashlerin listesini gösterir. Örneğin bu komutu calıstırdığımda 2 kısım olsun(stash@{0}, stash@{1}). İstersem bu stashleri tek tek ekleyebilirim
$git stash apply stash@{0} --> Teker teker stash eklemek istediğim durumda kullanırım
$git stash clear --> Bütün stashleri siler
$git stash apply --> Tek bir stash varsa, pop veya stash@{0} yapmak yerine direkt olarak apply komutu ile bu stashi geri getirebilirim
```

<br>

**CHECKOUT**
```
Attığımız commitler arasında geçis yapmak için $git checkout komutunu kullanırız.
Her commitin unique bir id si vardır. $git log yaptıgımızda commitlere ve id bilgilerine ulaşabiliriz.
Örnegin $git log komutunu calıstırdıgımızda karşımıza 3 commit çıkmış olsun:
    commit1, commit2, commit3

En son commitin id si 3 tür. Ancak ben commit2 ye gitmek istiyorum. Bunun için yazmam gereken komut
$git checkout 2 dir.
```

<br>

**RESET VE REVERT**
```
$git reset "gitmek istediğimiz commitin id si"

Bunu yaptığımızda id sini verdiğimiz commite gideriz ancak bu commitin sonrasındaki commitlerde yapılan değişikliklerde bizimle beraber gelir

Örneğin 3 commitimiz olsun:
    commit4, commit5, commit6
    
    $git reset 4 komutunu calıstırgımızda 4. commite geri dönerim ancak 5 ve 6. committe yapılan işlemlerde beraberinde gelir.
    $git log dediğimde ise 5 ve 6. commitler artık gözükmez.
    
$git reset --hard 4 komutunu calıstırdıgımda bu sefer yine reset işlemini gerçekleştirdim ancak diğerinde farklı olarak artık 5 ve 6. committeki işlemler
                    beraberinde gelmez ve $git log dediğimde 5 ve 6. commitler yine görünmez.
                    
5 ve 6. commiti beğenmedim ve 4. committen devam etmek istiyorum ve 5 ve 6. commitlerin silinmesini istemeyip aynı branch üzerinden devam etmek istiyorum
$git rever "commit id" komutu ile bunu yapabilirim. Örneğin

$git revert 6 komutunu calıstırdım. Bu komutun anlamı 6. committe yapılan değişiklikleri geri al demektir. Böylece yeni bir commit üzerinden
6. committe yapılan işlemler yapılmadan devam edilir. $git log dediğimde ise 6. commitin işlemi gözükmeye devam eder
```

<br>

**DIFF**
```
$git diff --> İstediğimiz yapılar arasındaki farkları gösterir
$git diff HEAD --> Son commite göre neleri değiştirdiğimi gösterir

$git diff id1 id2 --> 2 commit arasındaki farkı gösterir

$git diff master feat --> Master ve Feat branchi arasındaki farkı görmek
```

<br>

**REBASE**
```
Kelime anlamı yeniden temel atmaktır. Bir master branchi bir de feature branchi var. Ben şuan feature branchi üzerinde calısıyorum ancak master branchinde bazı degisiklikler
oldu ve masterı feature branchine merge ettim. Sonra feature üzerinde calısmaya devam ederken masterda tekrar degisiklikler oldu ve yine masterı feature üzerine merge ettim
Şuan projemde bir sürü merge commit oluştu. Aslında bu merge commitlerin olmasına gerek yok. Masterdaki commitleri alıp sonrasında da featuredeki esas commitleri
aynen sıra ile koyup aradaki merge commitlerden kurtulma işlemine rebase denir.
```
![rebase](https://user-images.githubusercontent.com/62347094/166682117-0574a41a-709c-49a4-83ef-dd113893e6ef.PNG)

**$git rebase master** --> Şuan feature branchi içerisindeyim. Bu komutu çalıştırdığımda önce commit sırasına göre master branchini, sonra commit sırasına göre feature branchini getirerek aradaki merge commitlerden kurtulmuş olduk.

<hr>

**$git remote add origin .git** --> Uzak sunucu eklemek <br>
**$git push -u origin master** --> Master branchini .git uzantılı uzak sunucuya pushlamak

<br>

**PULL REQUEST**
```
Farklı 2 branch arasında herhangi bir conflict yoksa bunları bir mesaj commitleyerek tek bir branch üzerinden ilerleyebilirim. Bu işleme pull request denir
```

<br>

**$git fetch VS $git pull**
```
Git fetch, pull a kıyasla daha güvenli bir komuttur. Local repomuza değişiklikleri getirir ama dosyalarımızı değiştirmez. Dosyaları değiştirmeden önce veya commitlerimizi
vs. değiştirmeden önce, merge etmeden önce dosyaları incelememize olanak sağlar.

Git pull ise direkt olarak github üzerindeki bütün değişiklikleri locale getirir ve dosyaları değiştirir
```
<br>

**$git clone .git** --> Uzantısını belirttiğim repoyu al ve benim için direkt bilgisayarıma kopyala

<br>

**FORK**
```
Projeyi çatallandırmaktır. Mevcut projeyi kendi hesabıma kopyalar ve o andan itibaren kendim o kısımdan devam edeceğimi belirtmiş olurum. Bir push yaptığımda
kendi hesabıma koyacağım, sizinle bir alakam kalmadı demektir
```
