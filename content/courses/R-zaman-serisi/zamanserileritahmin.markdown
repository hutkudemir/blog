---
title: "Zaman Serileri Wooldridge 18. Bölüm"
author: "Dr. Hüseyin Utku Demir"
date: 2022-12-03T21:13:14-05:00
categories: ["R"]
tags: ["R Markdown", "Zaman Serileri", "Tahmin"]
type: book
weight: 140
---
<link href="/rmarkdown-libs/pagedtable/css/pagedtable.css" rel="stylesheet" />
<script src="/rmarkdown-libs/pagedtable/js/pagedtable.js"></script>



Bu bölümde ileriye yönelik zaman serisi tahminleri yöntemlerinden bahsedeceğiz

<!--more-->

## İleriye Yönelik Tahmin Etme?

Hepinizin bildiği gibi iktisat biliminin bazı dalarında ileriye yönelik tahmin çok önemli bir yer tutar.Biz şimdilik regresyona bağlı bir tahmin yöntemi kullanacağız. Bu bölümde kullanacağımız örnekler Wooldridge ders kitabınızda bulunan örneklerden oluşacak. Bir veri setinin t zamanına kadar değerlerini bildiğimizi varsayalım. Bu zaman serisinin t+1 zamanında nasıl bir değer alacağını tahmin etmek ileriye yönelik tahmin etme olarak adlandırılır. Bu t+1 zamanının tahmini, veri setimizin yapısına göre değişkenlik gösterir. Eğer bir hisse senedi veya döviz kuru tahmini yapıyorsak, bu sürec bir günlük tahmin olabilir. Eğer GSYH'yı tahmin etmek istiyorsak, 3 ay veya 1 yıl sonrayı tahmin etmeye çalışabilirsiniz. Bazı veri setleri aylık verilerden oluşur ve bir ay sonrayı tahmin etmek isteyebilirsiniz.

Peki elde ettiğimiz tahminin, iyi bir thamin olup olmadığını nasıl anlayabiliriz. Wooldridge, yapmış olduğumuz tahmine $f$ (forecast) notasyonunu kullanmış. Eğer tahmin etmeye çalıştığımız $y_{t+1}$, $f$ değerinden farklı oluşursa. Tahminimiz bir hata payına sahip olur. İleriye yönelik tahmin hatası dediğimiz bu hataya $e$ diyelim. O zaman hata

$$
e_{t+1} = y_{t+1} - f_t
$$

olacaktır. $f_{t}$, $y_{t+1}$ için t zamanında yapmış olduğumuz tahmindir. $y_{t+1}$ ancak tahmin yapıldıktan sonra gözlemlenebilir ve biz hatamızın ne kadar olduğunu anlayabiliriz. Tahmin edebileceğiniz gibi hata payları negatif ve pozitif olacağından, toplam hata payı kareler alınarak bulunur. Bu yöntemi daha önce regresyon ve varyans için de kullanmıştık. $e_{t+1}^2$

## Kullanılan Regresyon Modelleri

Tahmin etmek istediğimi bir y değişkeni olduğunu varsayalım. Regresyon modelimiz

$$
y_t = \beta_0 + \beta_1 z_t + u_t 
$$

Bu regresyon modelini tahmin ederek $\beta_0$ ve $\beta_1$ parametrelerini tahmin edebiliriz ve aynı denklemi bir adım ilerisi için yazarsak

$$
y_{t+1} = \beta_0 + \beta_1 z_{t+1} + u_t 
$$

eğer $z_{t+1}$' ı biliyorsak $y_{t+1}$'ı tahmin edebiliriz. Ancak bir zaman serisinde geleceğe yönelik veriler çoğunlukla bilinemez. 

eğer $z_{t+1}$'ı bilmiyorsak veya tahmin edemiyorsak şu şekilde bir denklem yazmamız daha yararlı olacaktır.


$$
y_t = \beta_0 + \beta_1 y_{t-1} + \beta_2 z_{t-1} + u_t 
$$
Bu tür modellerde, tahmin için z değişkeni kaldırılabilir veya daha fazla gecikme değerleri alınabilir.

## Wooldridge Tahmin


```r
library(wooldridge)
library(stargazer)
```

```
## 
## Please cite as:
```

```
##  Hlavac, Marek (2018). stargazer: Well-Formatted Regression and Summary Statistics Tables.
```

```
##  R package version 5.2.2. https://CRAN.R-project.org/package=stargazer
```

```r
library(rmarkdown)
library(dynlm)
```

```
## Loading required package: zoo
```

```
## 
## Attaching package: 'zoo'
```

```
## The following objects are masked from 'package:base':
## 
##     as.Date, as.Date.numeric
```


```r
data(phillips, package = "wooldridge")
paged_table(phillips)
```

<div data-pagedtable="false">
  <script data-pagedtable-source type="application/json">
{"columns":[{"label":[""],"name":["_rn_"],"type":[""],"align":["left"]},{"label":["year"],"name":[1],"type":["int"],"align":["right"]},{"label":["unem"],"name":[2],"type":["dbl"],"align":["right"]},{"label":["inf"],"name":[3],"type":["dbl"],"align":["right"]},{"label":["inf_1"],"name":[4],"type":["dbl"],"align":["right"]},{"label":["unem_1"],"name":[5],"type":["dbl"],"align":["right"]},{"label":["cinf"],"name":[6],"type":["dbl"],"align":["right"]},{"label":["cunem"],"name":[7],"type":["dbl"],"align":["right"]}],"data":[{"1":"1948","2":"3.8","3":"8.1","4":"NA","5":"NA","6":"NA","7":"NA","_rn_":"1"},{"1":"1949","2":"5.9","3":"-1.2","4":"8.1","5":"3.8","6":"-9.3000002","7":"2.10000014","_rn_":"2"},{"1":"1950","2":"5.3","3":"1.3","4":"-1.2","5":"5.9","6":"2.5000000","7":"-0.59999990","_rn_":"3"},{"1":"1951","2":"3.3","3":"7.9","4":"1.3","5":"5.3","6":"6.6000004","7":"-2.00000024","_rn_":"4"},{"1":"1952","2":"3.0","3":"1.9","4":"7.9","5":"3.3","6":"-6.0000000","7":"-0.29999995","_rn_":"5"},{"1":"1953","2":"2.9","3":"0.8","4":"1.9","5":"3.0","6":"-1.0999999","7":"-0.09999990","_rn_":"6"},{"1":"1954","2":"5.5","3":"0.7","4":"0.8","5":"2.9","6":"-0.1000000","7":"2.59999990","_rn_":"7"},{"1":"1955","2":"4.4","3":"-0.4","4":"0.7","5":"5.5","6":"-1.1000000","7":"-1.09999990","_rn_":"8"},{"1":"1956","2":"4.1","3":"1.5","4":"-0.4","5":"4.4","6":"1.9000000","7":"-0.30000019","_rn_":"9"},{"1":"1957","2":"4.3","3":"3.3","4":"1.5","5":"4.1","6":"1.8000000","7":"0.20000029","_rn_":"10"},{"1":"1958","2":"6.8","3":"2.8","4":"3.3","5":"4.3","6":"-0.5000000","7":"2.50000000","_rn_":"11"},{"1":"1959","2":"5.5","3":"0.7","4":"2.8","5":"6.8","6":"-2.0999999","7":"-1.30000019","_rn_":"12"},{"1":"1960","2":"5.5","3":"1.7","4":"0.7","5":"5.5","6":"1.0000000","7":"0.00000000","_rn_":"13"},{"1":"1961","2":"6.7","3":"1.0","4":"1.7","5":"5.5","6":"-0.7000000","7":"1.19999981","_rn_":"14"},{"1":"1962","2":"5.5","3":"1.0","4":"1.0","5":"6.7","6":"0.0000000","7":"-1.19999981","_rn_":"15"},{"1":"1963","2":"5.7","3":"1.3","4":"1.0","5":"5.5","6":"0.3000000","7":"0.19999981","_rn_":"16"},{"1":"1964","2":"5.2","3":"1.3","4":"1.3","5":"5.7","6":"0.0000000","7":"-0.50000000","_rn_":"17"},{"1":"1965","2":"4.5","3":"1.6","4":"1.3","5":"5.2","6":"0.3000001","7":"-0.69999981","_rn_":"18"},{"1":"1966","2":"3.8","3":"2.9","4":"1.6","5":"4.5","6":"1.3000001","7":"-0.70000005","_rn_":"19"},{"1":"1967","2":"3.8","3":"3.1","4":"2.9","5":"3.8","6":"0.1999998","7":"0.00000000","_rn_":"20"},{"1":"1968","2":"3.6","3":"4.2","4":"3.1","5":"3.8","6":"1.0999999","7":"-0.20000005","_rn_":"21"},{"1":"1969","2":"3.5","3":"5.5","4":"4.2","5":"3.6","6":"1.3000002","7":"-0.09999990","_rn_":"22"},{"1":"1970","2":"4.9","3":"5.7","4":"5.5","5":"3.5","6":"0.1999998","7":"1.40000010","_rn_":"23"},{"1":"1971","2":"5.9","3":"4.4","4":"5.7","5":"4.9","6":"-1.2999997","7":"1.00000000","_rn_":"24"},{"1":"1972","2":"5.6","3":"3.2","4":"4.4","5":"5.9","6":"-1.2000000","7":"-0.30000019","_rn_":"25"},{"1":"1973","2":"4.9","3":"6.2","4":"3.2","5":"5.6","6":"2.9999998","7":"-0.69999981","_rn_":"26"},{"1":"1974","2":"5.6","3":"11.0","4":"6.2","5":"4.9","6":"4.8000002","7":"0.69999981","_rn_":"27"},{"1":"1975","2":"8.5","3":"9.1","4":"11.0","5":"5.6","6":"-1.8999996","7":"2.90000010","_rn_":"28"},{"1":"1976","2":"7.7","3":"5.8","4":"9.1","5":"8.5","6":"-3.3000002","7":"-0.80000019","_rn_":"29"},{"1":"1977","2":"7.1","3":"6.5","4":"5.8","5":"7.7","6":"0.6999998","7":"-0.59999990","_rn_":"30"},{"1":"1978","2":"6.1","3":"7.6","4":"6.5","5":"7.1","6":"1.0999999","7":"-1.00000000","_rn_":"31"},{"1":"1979","2":"5.8","3":"11.3","4":"7.6","5":"6.1","6":"3.7000003","7":"-0.29999971","_rn_":"32"},{"1":"1980","2":"7.1","3":"13.5","4":"11.3","5":"5.8","6":"2.1999998","7":"1.29999971","_rn_":"33"},{"1":"1981","2":"7.6","3":"10.3","4":"13.5","5":"7.1","6":"-3.1999998","7":"0.50000000","_rn_":"34"},{"1":"1982","2":"9.7","3":"6.2","4":"10.3","5":"7.6","6":"-4.1000004","7":"2.09999990","_rn_":"35"},{"1":"1983","2":"9.6","3":"3.2","4":"6.2","5":"9.7","6":"-2.9999998","7":"-0.09999943","_rn_":"36"},{"1":"1984","2":"7.5","3":"4.3","4":"3.2","5":"9.6","6":"1.1000001","7":"-2.10000038","_rn_":"37"},{"1":"1985","2":"7.2","3":"3.6","4":"4.3","5":"7.5","6":"-0.7000003","7":"-0.30000019","_rn_":"38"},{"1":"1986","2":"7.0","3":"1.9","4":"3.6","5":"7.2","6":"-1.6999999","7":"-0.19999981","_rn_":"39"},{"1":"1987","2":"6.2","3":"3.6","4":"1.9","5":"7.0","6":"1.6999999","7":"-0.80000019","_rn_":"40"},{"1":"1988","2":"5.5","3":"4.1","4":"3.6","5":"6.2","6":"0.5000000","7":"-0.69999981","_rn_":"41"},{"1":"1989","2":"5.3","3":"4.8","4":"4.1","5":"5.5","6":"0.7000003","7":"-0.19999981","_rn_":"42"},{"1":"1990","2":"5.6","3":"5.4","4":"4.8","5":"5.3","6":"0.5999999","7":"0.29999971","_rn_":"43"},{"1":"1991","2":"6.8","3":"4.2","4":"5.4","5":"5.6","6":"-1.2000003","7":"1.20000029","_rn_":"44"},{"1":"1992","2":"7.5","3":"3.0","4":"4.2","5":"6.8","6":"-1.1999998","7":"0.69999981","_rn_":"45"},{"1":"1993","2":"6.9","3":"3.0","4":"3.0","5":"7.5","6":"0.0000000","7":"-0.59999990","_rn_":"46"},{"1":"1994","2":"6.1","3":"2.6","4":"3.0","5":"6.9","6":"-0.4000001","7":"-0.80000019","_rn_":"47"},{"1":"1995","2":"5.6","3":"2.8","4":"2.6","5":"6.1","6":"0.2000000","7":"-0.50000000","_rn_":"48"},{"1":"1996","2":"5.4","3":"3.0","4":"2.8","5":"5.6","6":"0.2000000","7":"-0.19999981","_rn_":"49"},{"1":"1997","2":"4.9","3":"2.3","4":"3.0","5":"5.4","6":"-0.7000000","7":"-0.50000000","_rn_":"50"},{"1":"1998","2":"4.5","3":"1.6","4":"2.3","5":"4.9","6":"-0.6999999","7":"-0.40000010","_rn_":"51"},{"1":"1999","2":"4.2","3":"2.2","4":"1.6","5":"4.5","6":"0.6000000","7":"-0.30000019","_rn_":"52"},{"1":"2000","2":"4.0","3":"3.4","4":"2.2","5":"4.2","6":"1.2000000","7":"-0.19999981","_rn_":"53"},{"1":"2001","2":"4.8","3":"2.8","4":"3.4","5":"4.0","6":"-0.6000001","7":"0.80000019","_rn_":"54"},{"1":"2002","2":"5.8","3":"1.6","4":"2.8","5":"4.8","6":"-1.1999999","7":"1.00000000","_rn_":"55"},{"1":"2003","2":"6.0","3":"2.3","4":"1.6","5":"5.8","6":"0.6999999","7":"0.19999981","_rn_":"56"}],"options":{"columns":{"min":{},"max":[10]},"rows":{"min":[10],"max":[10]},"pages":{}}}
  </script>
</div>

```r
tsph<-ts(phillips, start = 1948)
plot(tsph[,"unem"],lty=1, lwd=1, ylim=c(0,15), ylab=("işz ve enf"))
lines(tsph[,"inf"],lty=2, lwd=2)
legend("topright", c("işsizlik","enflasyon"), lty=c(1,2), lwd = c(1,2))
```

<img src="/courses/R-zaman-serisi/zamanserileritahmin_files/figure-html/unnamed-chunk-3-1.png" width="672" />


```r
model1<-dynlm(unem~L(unem),data=tsph, end=1996)
model2<-dynlm(unem~L(unem) + L(inf),data=tsph, end=1996)
```


```r
stargazer(model1,model2,type ="text" )
```

```
## 
## =================================================================
##                                  Dependent variable:             
##                     ---------------------------------------------
##                                         unem                     
##                              (1)                    (2)          
## -----------------------------------------------------------------
## L(unem)                    0.732***               0.647***       
##                            (0.097)                (0.084)        
##                                                                  
## L(inf)                                            0.184***       
##                                                   (0.041)        
##                                                                  
## Constant                   1.572***               1.304**        
##                            (0.577)                (0.490)        
##                                                                  
## -----------------------------------------------------------------
## Observations                  48                     48          
## R2                          0.554                  0.691         
## Adjusted R2                 0.544                  0.677         
## Residual Std. Error    1.049 (df = 46)        0.883 (df = 45)    
## F Statistic         57.132*** (df = 1; 46) 50.219*** (df = 2; 45)
## =================================================================
## Note:                                 *p<0.1; **p<0.05; ***p<0.01
```


```r
f1<-predict(model1,newdata = window(tsph,start=1997))
```


```r
f2<-predict(model2,newdata = window(tsph,start=1997))
```


```r
y<-window(tsph,start=1997)[,"unem"]
```



```r
time=c(1997:2003)
matplot(time,cbind(y,f1,f2),type = "l",lwd=2,lty=1:3, ylim = c(4,7))
legend("topleft", c("işsizlik","tahmin1","tahmin2"),lwd=2,lty = 1:3)
```

<img src="/courses/R-zaman-serisi/zamanserileritahmin_files/figure-html/unnamed-chunk-9-1.png" width="672" />


```r
e1<-y-f1
e2<-y-f2
rmse<-sqrt(mean(e1^2))
mae<-mean(abs(e1))
<<<<<<< HEAD
```

```r
rmse2<-sqrt(mean(e2^2))
mae2<-mean(abs(e2))
```


```r
=======
>>>>>>> origin
rmse
```

```
## [1] 0.3247281
```

```r
mae
```

```
## [1] 0.2738516
```

```r
<<<<<<< HEAD
=======
rmse2<-sqrt(mean(e2^2))
mae2<-mean(abs(e2))
>>>>>>> origin
rmse2
```

```
## [1] 0.3135421
```

```r
mae2
```

```
## [1] 0.2455728
```

<<<<<<< HEAD



=======
>>>>>>> origin
