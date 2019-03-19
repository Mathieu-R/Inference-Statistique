### 1. Statistique descriptive    
1.1 Moyenne empirique    
> Moyenne arithmétique des observations
```r
$ mean(x)
```

1.2 Médiane empirique
> Nombre juste au milieu des observations ($q_{0.5}$)    
> S'il y a un nombre pair d'observations, alors $q_{0.5}$ est la moynne des 2 points les plus proches du milieu.   
```r
$ median(x)
```

- Si **_mean = median_** alors la distribution est symmétrique    

1.3 Quantile empririque
> Soit n, le nombre d'observations.    
> $q_p$ avec $p\in ]0, 1[$ est la valeur qui partage l'échantillon en 2.    
> $q_p = 1 + [(n - 1)p]$

_Par exemple pour $q_{0.3}$_ :
```r
$ x <- c(22.3, 17.9, 20.4, 24.6, 19.5, 26.2, 18.7)
$ quantile(x, p = 0.3)

30%
19.3
```

1.4 Le résumé à 5 nombres
> $x_1$ : la plus petite observation.    
> $q_{0.25}$ : le premier quartile.    
> $q_{0.50}$ : le deuxième quartile (**median**).    
> $q_{0.75}$ : le troisième quartile.     
> $x_n$ : la dernière observation. 

> $q_{0.25}, q_{0.50}, q_{0.75}$ = écart interquantile (**IQR**).

```r
$ quantile(x)
$ summary(x)
$ summary (mon.dataframe)
```

Soit un dataframe nommé _AirQuality_ contenant les colonne _Ozone_ et _Month_.   
On peut obtenir un **summary** de la variable _Ozone_ pour _chaque mois_
```r
$ aggregate(Ozone ~ Month, data = AirQuality, FUN = summary)
```

1.5 Diagramme en boite
> Représentation graphique du résumé à 5 chiffres.    
> Une boite du 1er au 3ème quartille.    
> Une ligne à hauteur de la _médiane_ $(q_{0.25})$.   
> Les lignes (moustaches) qui partent des extrémités de la boite jusqu'au points extrêmes se trouvant dans l'intervalle : $[q_{0.25} - (1.5 \times IQR), q_{0.75} + (1.5 \times IQR)]$

> On observe les **observation atypiques** en dehors des moustaches.

```r
$ ggplot(AirQuality) +
  aes(x = "", y = Temp) +
  geom_boxplot()
```

Une boite à moustache par mois :
```r
$ ggplot(AirQuality) +
  aes(x = Month, y = Temp) +
  geom_boxplot()
```

1.6 Etendue d'un échantillon
> Ecart entre ces valeurs extrêmes


```r
$ max(x) - min(x)
```

1.7 L'écart interquantile (IQR) 
> Ecart entre le 3ème  et le 1er quartile ($q_{0.75} - q_{0.25}$).

```r
$ IQR(x)
```

1.8 Variance 
> Soit n le nombre d'observations.     
> Somme des carrés des écarts à la moyenne divisée par $(n-1)$.   
> $s_n^2 = \frac{1}{n-1} \sum\limits_{i=1}^{n} (x_i - \bar{x})^2$

```r
$ var(x)
```

1.9 Ecart-type
> Mesure la dispersion des données autour de leur moyenne.    
> $s_n = \sqrt{s_n^2}$

```r
$ sd(x)
```

1.10 Règle empirique
> La majorité (95%) des données d'une observation sont éloignées de moins de 2 écarts-types de la moyenne.

Pour une distribution symétrique et sans valeurs aberrantes : 
- Environ **68%** des valeurs sont situées
à moins d'un écart type de la
moyenne (entre $\bar{x} - s_n$ et 	$\bar{x} + s_n$). 

- Environ **95%** des valeurs sont situées
à moins de 2 écarts types de la
moyenne (entre $\bar{x} - 2s_n$ et 	$\bar{x} + 2s_n$).

- Environ **99.7%** des valeurs sont
situées à moins de 3 écarts types
de la moyenne (entre $\bar{x} - 3s_n$ et 	$\bar{x} + 3s_n$).

