## Geoduck growth stats 

Levene's Test for Homogeneity of Variance (center = median)
       Df F value  Pr(>F)  
group   9  2.2106 0.02709 
      102                  
---
> summary(growth.aov)
            Df Sum Sq Mean Sq F value   Pr(>F)    
Site         3 0.7575 0.25249  19.844 5.56e-10  <---YES
Habitat      1 0.0019 0.00193   0.152    0.698  <---NOT
Both         3 0.0602 0.02006   1.576    0.201  <---NOT
Residuals   91 1.1579 0.01272

---
> TukeyHSD(growth.aov)
  Tukey multiple comparisons of means
    95% family-wise confidence level

Fit: aov(formula = Perc.Growth ~ Site * Habitat * Both, data = subset(Growth, Site != "SK"))

$Site
             diff          lwr         upr     p adj
FB-CI  0.20319048  0.113339762  0.29304120 0.0000003
PG-CI  0.22368490  0.134583441  0.31278636 0.0000000
WB-CI  0.07904957 -0.008084267  0.16618341 0.0893750 <-----NOT
PG-FB  0.02049442 -0.062198904  0.10318774 0.9157751 <-----NOT
WB-FB -0.12414091 -0.204710267 -0.04357155 0.0006531
WB-PG -0.14463533 -0.224368252 -0.06490240 0.0000447

$Habitat
           diff         lwr        upr     p adj
E-B 0.008818606 -0.03622265 0.05385986 0.6982499 <----NOT

$Both
                  diff         lwr        upr     p adj
CI-E-CI-B  0.031050427 -0.12975322 0.19185407 0.9988132
FB-B-CI-B  0.057843886 -0.09648176 0.21216954 0.9402385
FB-E-CI-B -0.021966799 -0.17372730 0.12979370 0.9998219
PG-B-CI-B  0.015462539 -0.13406425 0.16498932 0.9999817
PG-E-CI-B  0.017368753 -0.13695690 0.17169440 0.9999675
WB-B-CI-B -0.006232379 -0.15379592 0.14133117 1.0000000
WB-E-CI-B  0.040529518 -0.10899727 0.19005630 0.9901820
FB-B-CI-E  0.026793459 -0.12305803 0.17664495 0.9992797
FB-E-CI-E -0.053017226 -0.20022562 0.09419117 0.9513999
PG-B-CI-E -0.015587888 -0.16049241 0.12931664 0.9999761
PG-E-CI-E -0.013681674 -0.16353316 0.13616982 0.9999922
WB-B-CI-E -0.037282805 -0.18016059 0.10559498 0.9921821
WB-E-CI-E  0.009479091 -0.13542543 0.15438362 0.9999992
FB-E-FB-B -0.079810685 -0.21991388 0.06029251 0.6433318
PG-B-FB-B -0.042381347 -0.18006183 0.09529914 0.9794079
PG-E-FB-B -0.040475133 -0.18335292 0.10240266 0.9872543
WB-B-FB-B -0.064076265 -0.19962204 0.07146951 0.8228316
WB-E-FB-B -0.017314368 -0.15499485 0.12036611 0.9999309
PG-B-FB-E  0.037429338 -0.09736962 0.17222830 0.9886720
PG-E-FB-E  0.039335552 -0.10076765 0.17943875 0.9879072
WB-B-FB-E  0.015734420 -0.11688345 0.14835229 0.9999534
WB-E-FB-E  0.062496316 -0.07230264 0.19729527 0.8368737
PG-E-PG-B  0.001906214 -0.13577427 0.13958670 1.0000000
WB-B-PG-B -0.021694917 -0.15175071 0.10836087 0.9995431
WB-E-PG-B  0.025066979 -0.10721215 0.15734611 0.9989489
WB-B-PG-E -0.023601131 -0.15914690 0.11194464 0.9993945
WB-E-PG-E  0.023160765 -0.11451972 0.16084125 0.9995171
WB-E-WB-B  0.046761896 -0.08329390 0.17681769 0.9518219

> tapply(Growth$Perc.Growth, Growth$Both, mean)
       CI-B        CI-E        FB-B        FB-E        PG-B        PG-E        SK-B        SK-E        WB-B 
-0.02835626  0.01153696  0.23273395  0.16176607  0.21136399  0.22211300  0.09607143  0.15707436  0.04484610 
       WB-E 
 0.10045079 
 
 > tapply(Growth$Perc.Growth, Growth$Both, sd)
      CI-B       CI-E       FB-B       FB-E       PG-B       PG-E       SK-B       SK-E       WB-B       WB-E 
0.05346331 0.08259484 0.12514991 0.07258642 0.13285254 0.12531655 0.11061170 0.09539685 0.08260959 0.16181310 
