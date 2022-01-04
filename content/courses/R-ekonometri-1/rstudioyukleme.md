---
date: "2021-01-01"
title: R ve R-Studio yükleme ve kullanma
type: book
weight: 20
---

R ve R-studio yükleyin ve kullanmaya başlayın.

<!--more-->

{{< icon name="clock" pack="fas" >}} Haftada 1-2 saat, 2 hafta için.

## R ve R-Studio Yükleme

Bu dersi almak için R ve R-studio programlarını bilgisayarınıza kurmanız gereklidir. Aşağıdaki video R ve R-studio programlarını bilgisayarınıza yüklemenize yardımcı olacaktır.

{{< youtube j252S7XZjI0 >}}

## R-Studio

Artık R programını R-Studio üzerinden kullanacağız ve birdaha R'ı açmanıza gerek kalmayacak. R-Studio programını bilgisayarınızda açtıktan sonra aşağıdaki fotoğrafı göreceksiniz.

{{< figure library="true" src="r.png" >}}

Fotoğrafta gördünüz üzere R-Studio 4 ana kutucuk şeklinde açılıyor. İlk bahsedeceğimiz sol altta bulunan ve üstünde Console, Terminal ve Jobs sekmeleri bulunan kutucuk olacak.

{{< figure library="true" src="r1.png" >}}

Bu kutucukta en çok kullanılan sekme Console sekmesidir. Console sekmesine, r-studio'da kullanağımız kodları yazarız. Bu kodları en basitten en zora doğru yavaş yavaş öğreneceğiz. Console sekmesinde yapabileceğiniz en basit işlem basit matematiksel işlemlerdir. Mesela consola 4 + 2 yazıp enter tuşuna bastığınızda console size bu işlemin sonucunu verecektir.

{{< figure library="true" src="r2.png" >}}

Zor bir işlem yapıp sonucunu R-studio'ya kaydetmek ve daha sonra kullanmak isterseniz işleminize bir isim verebilir ve daha sonra bu sonucu başka bir işlemde kullanabilirsiniz. Mesela 4 + 2 işleminin sonucunu a olarak kaydedelim ve a'yı başka bir işlemde kullanalım. 

```{r}
a <- 4 + 2
b<- a + 15
c<- b/a
d<- b*c
a
b
c
d
```

{{< figure library="true" src="r14.png" >}}

Burada dikkat etmeniz gereken R-studio'nun eşittir olarak <- (küçüktür tire) işaretini kullanıyor olması. Bizde eşitlik yazmak istediğimizde bu <- işaretini kullanacağız.

Sol üste bulunan kutucuk script sekmesi olarak adlandırılır. Scriptler yazdığımız kodları kaydetmek ve daha sonra kullanmamızda işimize yarar. İçine yazacağınız herşey kod olmalıdır. Bir çok araştırmacı console kullanmadan bütün kodlarını script'e yazar ve kodları ordan çalıştırır. Görmüş olduğunuz run butonu kodları çalıştırmaya yarar. Script'e düz yazı yazığ ne yaptığınızı yazmak isterseniz paund (numara) işaretini kullanıp onun arkasına yazmalısınız. Biz script yerine düz yazı yazabildiğimiz Rmarkdown kullanacağız. Rmarkdown'ın ne olduğunu ileriki bölümlerde anlatacağım. Zaman serisi dersi için script kullanmayacağız.

Sağ üst köşede bulunan kutucuk üzerinde beş sekme bulunuyor. Bunlar Environment, history, connections, build, git ve tutorial. Bu sekmelerin hepsini hemen öğrenmenize gerek yok. İhtiyacımız olursa bu konuya geri döneriz. Environment sekmesinden inceleme yapacağımız veri setlerini yükleyebilmekteyiz. İmport Dataset bu konuda bize yardımcı olacaktır. Veri setimiz hangi tür olursa olsun (excel, text ...) Rstudio bu verileri yüklememize yardımcı olur. Environment sekmesi sadece yüklediğimiz dataları görmemizi sağlamaz, aynı zamanda fotoğraftan da görebileceğiniz üzere console'da yarattığımız objeleride gözlememizi sağlar.

{{< figure library="true" src="r3.png" >}}

## R ve R-Studio Paket Yükleme

Son kutucuk sağ alt köşede bulununan ve Files, plots, packages, help, viewer sekmeleri bulunan kutucuk. Bu kutucukta Files bize R'ın bilgisayarınızda hangi bölümde çalıştığınızı gösterir. Örneğin benim bilgisayarımda R masaüstünde (desktop) bulunan uygulamaliekonometri dosyasının içinde bulunan content dosyasının içinde bulunuyor.

{{< figure library="true" src="r4.png" >}}

Sizin bilgisayarınızda nerde çalıştığını new folder yazan yerin altında takip edebilirsiniz. Bu dosyayı değiştirmek isterseniz daha sonra değiştirilebilir. R burayı working directory (çalışma alanı) olarak algılar. İstediğiniz dosyaları ve dataları bu dosyanın içine yükleyip, R ortamına rahatça atabilirsiniz. Biz şimdilik bu sekmeylede ilgilenmeyeceğiz. Plots sekmesi R'da çizdiğimiz grafikleri otomatik olarak gösterecektir. 

Packages sekmesi en çok kullanacağımız sekmelerden biri.

{{< figure library="true" src="r5.png" >}}

Bu sekmede R'ın kendi yüklemiş olduğu ve sizin daha sonra yükleyeceğiniz bütün paketleri görebilirsiniz. Zaman serisi analizlerini yapmak için bizde bir çok paket yükleyeceğiz. Siz bu paketleri bu sekmeden yükleyeceksiniz. Paket yüklemek bir kerelik bir iş olup, paketi yükledikten sonra tekrar yüklemenize gerek kalmayacak. 

Mesela ilk yükleyeceğimiz paket wooldridge paketi. Wooldridge, ekonometri 1 kitaplarınızdan birinin yazarı ve kitapta kullandığımız analizleri bizim de tekrarlayabilmemiz ve veri setlerine ulaşabilmemiz için bir paket yazmış ve R'a entegre etmiş. Bu veri setlerine ulaşmak için wooldridge paketini yüklemeliyiz.

Paket yüklemenin en çok kullanılan iki yönteminden biri Packages sekmesinde bulunan Install tuşudur bu tuşa bastığınızda karşınıza bir sihirbaz çıkacak.

{{< figure library="true" src="r6.png" >}}

Packages yazan yerin altına yüklemek istediğimiz paketi yazıyoruz. İlk üç harfi yazdıktan sonra zaten sihirbaz bize olası seçenekleri sunuyor ve biz istediğimizi seçiyoruz ya da kendimiz yazıyoruz.

{{< figure library="true" src="r7.png" >}}

Sonra Install tuşuna basıyoruz ve yüklüyor. Paketleri yüklemenin ikinci yolu ise Console'a bu işlemle ilgili kodu yazmak. Bu işlem için install.packages() kodunu kullanacağız, install yüklemek, packages paket anlamına gelmektedir. install.packages("wooldridge") kodunu konsola yazarak, R kodlarının nasıl çalıştığını anlamaya başlayabilirsiniz. Ne yapmak istediğimizle ilgili kodu yazıyoruz, bu örnekte paket yüklemek ve parantez içine de bunu neye yapmak istediğimizi yazıyoruz, bu örnekte wooldridge paketi.

Bu iki işlemden her hangi biriyle istediğiniz paketi yükledikten bir daha bu işlemi tekrarlamanıza gerek kalmayacak. Bundan sonra wooldridge veri setlerinden herhangi birini kullanmak istediğimizde R bizim bu paketi yüklediğimizi anlayacak ancak eğer bu paketi kullanacaksak her Rstudio'yu açtığımızda R'a bu paketi kullanmak istediğimizi hatırlamamız gerecek. Her dersin başında ve ödevlerinizde hangi paketleri yüklemeniz ve kullanmanız gerektiğini söyleyeceğim. Bu hatırlatma işlemi library() fonksiyonuyla yapılacaktır.

Örneğin sizden wooldridge'in intdef isimli veri setinizi kullanmanızı istedim. Bu durumda intdef datasını yüklemek için console'a aşağıdaki kodları yazmanız lazım.

```{r}
library(wooldridge)
data(intdef)
```

Anlatacağım örneklere başlamadan önce bir çok library fonksiyonu görebilirsiniz. Bu library() fonksiyonunda parantez içine yazmış olduğum paketin R'a yüklemiş olması gerektiğini söyler. Eğer yüklememişseniz  install.packages() fonksiyonuyla önce yüklemeniz gereklidir. Yükledikten sonra library() fonksiyonuyla bir kez R'a hatırlatmanız yeterli olacaktır. Artık veri çağırmak için data() fonksiyonunu istediğiniz kadar kullanabilirsiniz. Unutmayın Eğer R'ı kapatırsanız ve tekrar bu paketi kullanmak isterseniz, artık tekrar aynı paketi yüklemenize gerek yoktur. library() fonksiyonu paketi kullanmak için yeterli olacaktır.

## Veri Seti

data() fonksiyonunu Console'a yazdıktan sonra, wooldridge veri setlerinden istediğimiz veri setini parentez içine yazarsak o veri setini, sağ üst köşede bulunan Environment sekmesinden gözlemleyebilirsiniz. intdef veri seti ilk olarak Promise olarak görülecektir. Bu data'yı daha kullanmaya başlamadığımız anlamına gelir.

{{< figure library="true" src="r8.png" >}}

Promise yazısına tıkladığınızda artık veri setimiz kullanıma hazırdır. Aslında tıklamanıza gerek yok, veri setini ilk Console'da kulandığımızda otomatik olarak promise kaybolur ve veri seti kullanıma hazır olur.

{{< figure library="true" src="r9.png" >}}

Gördüğünüz gibi veri seti Environment'da artık data grubunun altında yer almaktadır. Yanında veri setinde kaç gözlem olduğu ve kaç değişken olduğu yazar. Bu veri setinde 56 gözlem (observation), 13 değişken (variables) bulunmaktadır. Bu veri setini açmak ve gözlemlemek istersek yüne iki yol izleyebiliriz. Birinci yol, Console'a view(intdef) yazmak, ikinci yol Environment'da intdef veri setinin üzerine tıklamaktır.

{{< figure library="true" src="r10.png" >}}

Görüleceği üzere, artık script kutusunun yerini veri setimiz almış bulunuyor. Bu veri setini istediğinizde sekmenin üzerinde bulunan x işaretini kullanarak kapatıp, script'e geri dönebilirsiniz.

Veri setini incelemek istersek, ilk sütünda year (yıl) değişkeninin olduğunu göreceğiz. Bu zaman serileri için en önemli değişkendir. Ve diğer 12 değişkenin hangi yılda ne olduğunu gösterir. Örneğin üçüncü sütunda bulunan inf (enflasyon) değişkenine bakarsanız, 1952 yılında enflasyonun 1.9 olduğunu söyleyebilirsiniz.

Bu veri setini bu şekide açmadan içinde bulunan ilk 6 yılı Console üzerinden gözlemlemek istersek head komutu işimize yarayacaktır.

```{r}
head(intdef)
```

{{< figure library="true" src="r15.png" >}}


Aynı şekilde tail komutu son 6 gözlemi gösterir.

```{r}
tail(intdef)
```

{{< figure library="true" src="r16.png" >}}

Wooldride veri setleri ve sizin ulşabileceğiniz bir çok veri seti değişkenleri kısaltma adlara sahip, örneğin out, örneğin rec. Analizi yapmadan önce bütün bu değişkenlerin anlamlarını öğrenmemiz gerekir. R'a yazdığımız bütün kodlar ve bütün paketler için konsola ? veya help yazabiliriz. Bu komut bize sağ alt köşede bulunan kutucukta, help sekmesinde o konuyla ilgili yardım getirecektir. Biz veri setimiz için yardım istediğimizden konsola ?intdef yazmalıyız.

```{r}
?intdef
```

Bu komut ya da help(intdef) komutu veri setimizle ilgili yardımı getirecektir.

{{< figure library="true" src="r11.png" >}}

Ancak tabi ki yardım ingilizce. Bu yüzden google'a gidip google translate yazmanızı ve açmanızı bekliyorum.

{{< figure library="true" src="r12.png" >}}

Google'da bu sayfa karşınıza açılacak. Biz çevirimizi ingilizceden türkçeye çevireceğimiz için ortada bulunan işarate basıp, çeviriyi English Turkish yapmayı unutmayın.

Help sayfanızda bulunan değişkenlerinizin açıklamalarını kopyalayıp buraya yapıştırın.

{{< figure library="true" src="r13.png" >}}

gördünüz gibi artık kullanacağımız değişkenlerin tanımlarını yapabiliriz.

veri setimiz 1948'den 2003'e kadar olan dönemi kapsar, inf, TÜFE (Tüketici fiyat endeksi enflasyon oranıdır... gibi.

Diyelim ki enflasyon oranını, yıllara göre göstermek istedik. Şimdilik plot fonksiyonu işimizi görecektir.

```{r}
plot(inf~year, data = intdef)
```
{{< figure library="true" src="r17.png" >}}

Enflasyonun 1950'lere girerken biraz yüksek olduğunu, daha sonra 1960'ların ortalarına kadar düşük seyrettiğini ve artışa geçtiğini, 1980'lerin sonundan sonra tekrar düştüğünü gözlemleyebiliyoruz.

Gördüğünüz gibi plot fonksiyonunda önce inf değişkenini kullandık, bu bize önce y eksenine koymak istediğimiz değişkeni yazmamız gerektiğini söyler. Daha sonra ~ işaretini kullandık ve x-ekseninde hangi değişkeni kullanmak istiyorsak onu yazdık. Örneğizde, yıllara göre değişimi görmek istediğimiz için year değişkenini kullandık. Ancak bu yeterli değildi, çünkü R ne inf değişkenini, ne de year değişkenini tanımıyor, Environment'a bakarsanız, ne year ne de inf değişkenini görebilirsiniz. Bu iki değişkende intdef datasının içinde bu yüzden data eşittir komutunu kullanarak bu iki değişkenin intdef datasının içinde olduğunu belirttik. Aynı grafiği çizmenin ve bizimde sıklıkla kullanacağımız ikinci yöntemi dolar işareti kullanmaktır.

```{r}
plot( intdef$inf ~ intdef$year)
```

{{< figure library="true" src="r18.png" >}}

Gördüğünüz gibi bu tür kullanımda datayı ayrı olarak belirtmeye gerek yok. Çünkü dolar işaretiyle verileri hangi veri setinin içinde bulabileceğini R'a söylüyoruz. Veri setinin içindeki değişkenleri kullanmanın bir diğer yolu veri setini R'a bağlamaktır. attach komutuyla veri setini R environment'ına tuttururuz ve değişkenleri algılamasını sağlayabiliriz. Böyle bir durumda ne data belirtmemize ne de dolar işareti kullanmamıza gerek kalır.

```{r}
attach(intdef)
plot(inf ~ year)
```

{{< figure library="true" src="r19.png" >}}

Bu durumda R değişkenleri aynı Environment'da gibi okuyabilecektir. Ancak R ortamında bir çok veri setiyle çalışabileceğinizden ve bu veri setlerinin içinde aynı isimde olabilecek bir çok değişken olduğundan analizlerizde yanılmamanız için ikinci yöntemi öneriyorum. Tutturmayı R'dan kaldırmak için detach komutunu kullanıyoruz.

```{r}
detach(intdef)
```

artık plot(inf ~ year) kodunu Console'a yazarsanız, inf ve year verisini Environment'da göremeyecektir ve grafiği çizemeyecektir.

Zaman serisi dışında regresyon yapmak için lm (linear model, doğrusal model fonksiyonunu kullanıyoruz. mesela yanlış bir analizle enflasyon ve faiz oranları arasında ilişkiye doğrusal regresyon modeliyle bakarsak sonuçları şu şekide bulabiliriz.

```{r}
ilkmodel<- lm(intdef$i3 ~ intdef$inf)
summary(ilkmodel)
```
{{< figure library="true" src="r20.png" >}}

Görüleceği üzere inf önündeki katsayıyı 0.64 olarak tahmin ettik ve yüzde 99'un üzerinde anlamlılık düzeyi var. Ancak analizimiz çok naif ve henüz enflasyon 1 birim artarsa faizler 0.64 birim artar diyemiyoruz. Doğrusal modeller için önceki dersleri sitede bulabilirsiniz. Ancak analizi anlamadıysanız endişelenmeyin çünkü henüz örneklere başlamadık.

Diğer derste Rmarkdown'ı nasıl kullanacağımızı ve bundan sonra R işlemlerimizi Rmarkdown üzerinden nasıl sürdüreceğimizi ve ödevlerinizi Rmarkdown siteleriyle nasıl paylaşacağınızı anlatacağım.





