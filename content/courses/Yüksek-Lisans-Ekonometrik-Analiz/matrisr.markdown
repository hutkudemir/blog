---
title: "R ile Matris Örnekleri"
author: "Dr. Hüseyin Utku Demir"
date: 2020-12-01T21:13:14-05:00
categories: ["R"]
tags: ["R Markdown", "plot", "regression"]
type: book
weight: 40
---



Bu bölümde, R yardımıyla matris alıştırmaları bulacaksınız 

<!--more-->

İlk olarak 6x2 yani 6 satırlı ve 3 sütunlu bir matris oluşturalım ve A matrisi diyelim.


```r
A <- matrix(c(3,4,2,16,5,9,4,7,33,8,9,48),nrow=6)
A
```

```
##      [,1] [,2]
## [1,]    3    4
## [2,]    4    7
## [3,]    2   33
## [4,]   16    8
## [5,]    5    9
## [6,]    9   48
```

Gördüğünüz gibi R, yazmış olduğunuz her rakamı yukardam aşağıya doğru sütunlara göre yazdı ve 6 tane nrow (satır) belirledi. Eğer nrow değilde ncol (sütun) belirtseydik de aynı sonuca ulaşırdır.


```r
B<- matrix(c(3,4,2,16,5,9,4,7,33,8,9,48),ncol=2)
B
```

```
##      [,1] [,2]
## [1,]    3    4
## [2,]    4    7
## [3,]    2   33
## [4,]   16    8
## [5,]    5    9
## [6,]    9   48
```

Saıyların yazılışını, satırlara göre sıralamak istersek byrow seçeneğini eklemeliyiz.


```r
C<- matrix(c(3,4,2,16,5,9,4,7,33,8,9,48),ncol=2, byrow = T)
C
```

```
##      [,1] [,2]
## [1,]    3    4
## [2,]    2   16
## [3,]    5    9
## [4,]    4    7
## [5,]   33    8
## [6,]    9   48
```

dim komutuyla matrisin boyutunu daha sonra değiştirebiliriz. Örneğin 6x2'lik A matrisini, 4x3 matrise çevirmek istersek


```r
dim(A) <- c(4,3)
A
```

```
##      [,1] [,2] [,3]
## [1,]    3    5   33
## [2,]    4    9    8
## [3,]    2    4    9
## [4,]   16    7   48
```

komutunu kullanabiliriz.

Bazen kullandığımız matrislerde çok fazla gözlem olabilir. Bu durumda matrisin boyutunu yine dim yardımıyla öğrenebiliriz.


```r
dim(A)
```

```
## [1] 4 3
```


```r
dim(B)
```

```
## [1] 6 2
```

Bir matrisin transpose'u t() yardımıyla alınır.


```r
t(C)
```

```
##      [,1] [,2] [,3] [,4] [,5] [,6]
## [1,]    3    2    5    4   33    9
## [2,]    4   16    9    7    8   48
```

Diyelim ki bir matriste sadece bir sütuna veya bir satıra ihtiyacınız var, bu durumda kareli parantez kullanırız. kareli parantezin virgülden önce yazılan kısmı satırlar, sonrası sütunlar içindir.

Mesala, A matrisinin ikinci sütununu kullunmak isterseniz


```r
A[2,]
```

```
## [1] 4 9 8
```

yazarsınız.

Eğer A matrisinin 3'ncü sütununu kullanmak isterseniz


```r
A[,3]
```

```
## [1] 33  8  9 48
```

yazarsınız.

Diyelim ki matrisin sadece bir öğesini görmek istiyorsunuz, 2'nci satırı ve 3'ncü sütunu


```r
A[2,3]
```

```
## [1] 8
```

sonucunu verecektir.

Örneğin bu rakamın 8 değilde 15 olması lazım, o zaman


```r
A[2,3]<- 15
A
```

```
##      [,1] [,2] [,3]
## [1,]    3    5   33
## [2,]    4    9   15
## [3,]    2    4    9
## [4,]   16    7   48
```

yazabilirsiniz.

Diyelim ki üç ayrı vektörünüz var


```r
a<- c(3,2,3)
a
```

```
## [1] 3 2 3
```


```r
b<- c(5,2,1)
b
```

```
## [1] 5 2 1
```


```r
c<- c(2,2,4)
c
```

```
## [1] 2 2 4
```

Bu vektörlerden 3x3 bir matris oluşturabilirsiniz. Öncelikle bu matrisleri, bir matrisin sütunları yapmak isterseniz cbind fonksiyonu, satırları yapmak isterseniz rbind fonksiyonunu kullanabilirsiniz.


```r
Sutunlu<- cbind(a,b,c)
Sutunlu
```

```
##      a b c
## [1,] 3 5 2
## [2,] 2 2 2
## [3,] 3 1 4
```


```r
Satirli<- rbind(a,b,c)
Satirli
```

```
##   [,1] [,2] [,3]
## a    3    2    3
## b    5    2    1
## c    2    2    4
```

Bu iki matrisin determinantını det() yardımıyla bulabiliriz.


```r
det(Sutunlu)
```

```
## [1] 2.664535e-15
```



```r
det(Satirli)
```

```
## [1] 2.664535e-15
```

Satirli ve Sutunlu matrisler birbirlerinin transpose'u oldukları için determinantları da eşit.

Kare matrisin tersi solve() fonksiyonu ile bulunabilir.


```r
B <- matrix( c(2, 4, 6, 0, 1, 12, 10, 12,0), nrow=3)
B
```

```
##      [,1] [,2] [,3]
## [1,]    2    0   10
## [2,]    4    1   12
## [3,]    6   12    0
```


```r
solve(B)
```

```
##            [,1]       [,2]        [,3]
## [1,] -1.0909091  0.9090909 -0.07575758
## [2,]  0.5454545 -0.4545455  0.12121212
## [3,]  0.3181818 -0.1818182  0.01515152
```

3x3 bir birim matris oluşturmak için 


```r
C <- diag(1,nrow=3)
C
```

```
##      [,1] [,2] [,3]
## [1,]    1    0    0
## [2,]    0    1    0
## [3,]    0    0    1
```

kullanılabilir.

İki matrisi çarpmak için ilk matrisin sütun sayısıyla, ikinci matrisin satır sayısı eşit olmak zorundadır. B matrisiyle 3 satırlı herhangi bir D matrisi çarpılabilir. A 4x3 lük bir matris olmasına rağmen, A'nın transposu 3x4'lük bir matristir. 


```r
D<-t(A)
B %*% D
```

```
##      [,1] [,2] [,3] [,4]
## [1,]  336  158   94  512
## [2,]  413  205  120  647
## [3,]   78  132   60  180
```

ilk dersin ödevini çözmek için aşağıdaki formülü kullanabilirsiniz.




```r
K<-matrix(c(3,2,0,1,0,1,2,1,3),nrow=3)
L<-matrix(c(11,5,11),nrow=3)
solve(K,L)
```

```
##      [,1]
## [1,]    1
## [2,]    2
## [3,]    3
```


## Matrislerle işlem yapma

sadece birlerden oluşmuş bir vektöre ihtiyacımız var. Bu vektöre i diyoruz.


```r
Veci <- c(rep(1, 12))
Veci
```

```
##  [1] 1 1 1 1 1 1 1 1 1 1 1 1
```

rep kaç tane 1'e ihtiyacımız varsa o kadar tekrarlayıp bize bir satırlık vektör oluşturacaktır. 12 tane birden oluşan bir vektör yarattık. 1 yerine istediğiniz rakamı da yazabilirsiniz.

Biz şimdilik işlemleri anlayabilmek için 3x3 matrislerle işlem yapıyoruz ve 3 satırlık bir vektöre ihtiyacımız var.


```r
veci <- c(rep(1, 3))
i <- matrix(veci, nrow = 3)
i
```

```
##      [,1]
## [1,]    1
## [2,]    1
## [3,]    1
```

i vektörü işlemlerde bize bazı kolaylıklar sağlar. Örneğin elimizde başka bir 3 satırlı 1 sütunlu vektör varsa,

Örneğin


```r
k <- matrix( c(7, 9, 26), nrow = 3)
k
```

```
##      [,1]
## [1,]    7
## [2,]    9
## [3,]   26
```

t(i) ve k'nın çarpımı bize k vektörünün elementlerinin toplamını (7 + 9 + 26 = 42) verir. i vektörü 3x1 bir matristir. i'nin transpozu 1x3 matris olur. k 3x1 bir matristir. $i^T k$ b'ze 1x1 bir sonuç verecektir. Arada kalan 3 sütun ve 3 satır çarpım koşuludur.


```r
t(i) %*% k
```

```
##      [,1]
## [1,]   42
```


i matrisi daha büyük boyutlu matrislerde de işimize yarayacaktır.

Burdan da anlaşılacağı üzere $i^T i$ toplam kaç tane satır bulunduğunu söyler. Bizim örneğimizde satır sayısı üçtür.


```r
t(i) %*% i
```

```
##      [,1]
## [1,]    3
```

$(i^T i)^{-1}$ bize $1/n$'i verecektir.


```r
solve(t(i) %*% i)
```

```
##           [,1]
## [1,] 0.3333333
```

$i^T k$ sütunun toplamını veriyor, $(i^T i)^{-1}$ ise $1/n$'i veriyor. Buna göre $(i^T i)^{-1}i^T k$ bize bu sütunun ortalamasını verecektir.


```r
solve(t(i) %*% i)  %*%  t(i) %*% k
```

```
##      [,1]
## [1,]   14
```

Biliyorsunuz ki varyansı veya kovaryansı bulmak için her bir öğeyi ortalamasından çıkartmamız gerekebilir. Bizim örneğimizde bu ortalamayı 3x1 matris şekinde yazmak istersek i matrisiyle çarpmamız yetecektir.


```r
i %*%  solve(t(i) %*% i)  %*%  t(i) %*% k
```

```
##      [,1]
## [1,]   14
## [2,]   14
## [3,]   14
```

Bu matrisi k matrisimizden çıkarırsak $k - \bar{k}$'yı her bir öğe için bulmuş oluruz. 


```r
k - i %*%  solve(t(i) %*% i)  %*%  t(i) %*% k
```

```
##      [,1]
## [1,]   -7
## [2,]   -5
## [3,]   12
```

Ama biliyoruz ki ortalamaların toplamı sıfırı verir. Bu matrisi $t(i)$ ile çarparsak bütün sütunun öğelerinin toplayacağı için sonucu 0 olarak verecektir.


```r
t(i) %*% (k - i %*%  solve(t(i) %*% i)  %*%  t(i) %*% k)
```

```
##      [,1]
## [1,]    0
```

Bu özellik bize birşeyler daha öğretecek.

$$
i^T(k - i(i^T i)^{-1}i^T k) = 0
$$
$$
i^T(I_n - i(i^T i)^{-1}i^T) k= 0
$$
$i^T$'u parantez içine dağıtalım.

$$
(i^T - i^Ti(i^T i)^{-1}i^T) k= 0
$$
$i^Ti(i^T i)^{-1}$ birbirleribi götüreceklerdir.

$$
(i^T - i^T) k= 0
$$
$$
(0) k= 0
$$

Bu parantez içinde kalan matrise özel bir isim verelim.

$$
M_0 = I_n - i(i^T i)^{-1}i^T
$$
$M_0$ matrisi simetrik bir matrisdir.


$$
M_0 = M_0^T =  I_n - i(i^T i)^{-1}i^T =  (I_n - i(i^T i)^{-1}i^T)^T
$$
$M_0$'yu $M_0$ ile çarparsak $M_0$ buluruz. Dolayısıyla $M_0$ idempotent'dir.


$$
M_0 M_0 = (I_n - i(i^T i)^{-1}i^T)  (I_n - i(i^T i)^{-1}i^T)
$$
$$
= I_n - i(i^T i)^{-1}i^T - i(i^T i)^{-1}i^T) + i(i^T i)^{-1}i^Ti(i^T i)^{-1}i^T
$$
$$
= I_n - i(i^T i)^{-1}i^T - i(i^T i)^{-1}i^T) + i(i^T i)^{-1}i^T
$$
$$
= I_n - i(i^T i)^{-1}i^T = M_0
$$



