Noter om stratificeret sampling
================
PSL
September 27, 2018

### Kort resum? af SRS og HT-estimatoren

Antag at vi har en population med \(N\) enheder, og at enhederne har en
egenskab \(y\). Vi ?nsker at bestemme den totale sum af denne egenskab i
hele populationen: \[ t_y = \sum _{j=1}^N y_j\] Til dette form?l udtager
vi en stikpr?ve af st?rrelsen \(n\) ved simpel udv?lgelse (SRS, simple
random sample) hvorved sandsynligheden for udv?lgelse \(\pi\) for hver
enkelt enhed bliver \(n/N\). Herefter kan vi danne et estimat for
\(t_y\) med Horvitz-Thompson estimatoren, hvor hver enkelt observation
fra stikpr?ven v?gtes med \(\pi^{-1}\):
\[\hat{t}_y = \sum_{j=1}^n \frac{N}{n}y_j\]

> Nogle bryder sig ikke om at opskrive summationen for \(\hat{t}_y\) med
> samme index \(j\) som for \(t_y\), da det p? en m?de indikerer, at
> summen l?ber over de f?rste \(n\) enheder ud af \(N\). I stedet kan
> man betegne den udvalgte stikpr?ve med \(\mathcal{S}\) og skrive
> \[ \hat{t}_y = \sum_{j \in \mathcal{S}} \pi^{-1}y_j\] Som regel er der
> dog *ikke* tvivl om hvad der menes, og derfor foretr?kkes notationen
> med summation over \(j = 1, \ldots, n\).

Variansen for \(\hat{t}_y\) bestemmes ved
\[V(\hat{t}_y) = (1-\frac{n}{N}) N^2 \frac{\hat{s}^2}{n} \] hvor
\(\hat{s}^2\) er et estimat for variansen i populationen
\(V(y) = \sigma^2\). Vi estimerer \(s\) med stikpr?vestandardafvigelsen.
Som regel er det ikke variansen men derimod spredning p? estimatet, som
vi er interesserede i. Denne st?rrelses kaldes ogs? for *standardfejlen*
(s.e., standard error) og beregnes ved at uddrage kvadratroden af
variansen.

?nskede vi i stedet at estimere middelv?rdien \(\mu\) i populationen, da
s?ttes blot totalen mod populationsst?rrelsen hvorved vi f?r
\[\hat{\mu} = \bar{y} = \frac{1}{N} \hat{t}_y = \sum_{i=1}^n \frac{1}{n}y_i \]
Variansen for den estimerede middelv?rdi beregnes derfor som
\[V(\bar{y}) = V(\frac{1}{N}\hat{t}_y) = \frac{1}{N^2}V(\hat{t}_y) = (1-\frac{n}{N}) \frac{\hat{s}^2}{n}\]

### Kort resum? af STSI og HT-estimatoren

Vi ser nu p? tilf?ldet hvor populationen \(U\) deles op i \(L\)
disjunkte m?ngder, det vil sige
\(U = U_1 \cup U_2 \cup \ldots \cup U_L\) og
\(U_i \cap U_j = \emptyset\) for \(i \ne j\). Opdelingen kaldes en
*stratifikation*, og delm?ngderne kaldes *strata*. Ideen er at i stedet
for at tr?kke en stikpr?ve simpelt tilf?ldigt i hele \(U\), s? tr?kker
vi nu en stikpr?ve simpelt tilf?ldigt i hver af de \(L\) strata. Vi ved
allerede, hvordan vi beregner HT-estimat og tilh?rende standardfejl for
en SRS stikpr?ve, nu skal vi blot kombinere de \(L\) estimater og
standardfejl til et samlet estimat.

F?rst ser vi p? estimation af \(t_y\), hvor estimatet beregnes som
summen af de stratumvise estimater
\[\hat{t}_y^{st} = \sum_{h=1}^L \hat{t}_h = \sum_{h=1}^L \sum_{j=1}^{n_h} \frac{N_h}{n_h} y_{hj}\]
hvor \(y_{hj}\) er den \(j\)’te enhed i stikpr?ven i det \(h\)’te
stratum. Da stikpr?ven antages trukkes uafh?ngigt i de to strata (STSI,
stratified simpel random sampling) beregnes variansen som
\[V(\hat{t}_y^{st}) 
= V(\sum_{h=1}^L \hat{t}_h) 
= \sum_{h=1}^L V(\hat{t}_h) 
= \sum_{h=1}^L (1-\frac{n_h}{N_h}) N_h^2 \frac{\hat{s}_h^2}{n_h}\]

Hvis vi i stedet vil estimere middelv?rdien er det ikke helt s? simpelt,
da vi bliver n?dt til at tage hensyn til den relative st?rrelse af det
enkelte stratum (stratumv?gten) \[\bar{y}^{st}
= \frac{\sum_{h=1}^L N_h \bar{y}_h}{N}
= \sum_{h=1}^L \frac{N_h}{N} \bar{y}_h
= \sum_{h=1}^L W_h \bar{y}_h
\] Dette f?lger blandt andet af f?lgende omskrivning af udtrykket for
populationsgennemsnittet \[\mu = \frac{\sum_{i=1}^N y_i}{N}
= \frac{\sum_{h=1}^L \sum_{j=1}^{N_h} y_{hj}}{N}
= \frac{\sum_{h=1}^L N_h \mu_h}{N}
= \sum_{h=1}^L W_h \mu_h\]

Dermed kan vi ogs? opstille udtrykket for variansen af estimatet for
middelv?rdien baseret p? en stratificeret stikpr?ve \[V(\bar{y}^{st})
= V(\sum_{h=1}^L W_h \bar{y}_h)
= \sum_{h=1}^L W_h^2 V(\bar{y}_h)\]

### Simpelt eksperiment med stratificeret sampling

Lad os nu forestille os, at vi deler populationen \(U\) over i to
halvdele, \(U_1\) og \(U_2\). De to halvdele kan ogs? opfattes som
*strata* selvom opdelingen er sket helt tilf?ldigt. De to halvdele er
lige store, \(N_1 = N_2 = N/2\), og da opdelingen er sket tilf?ldigt er
middelv?rdi og varians af \(y\) den samme i de to halvdele, det vil sige
\(\mu_1 = \mu_2\) og \(\sigma_1^2 = \sigma_2^2\).

Lad os ogs? dele stikpr?ven over i to lige store dele,
\(n_1 = n_2 = n/2\). Det vil sige at i stedet for en stikpr?ve p? \(n\)
ud af \(N\), s? har vi nu to stikpr?ver af den halve st?rrelse. Hvad er
konsekvensen af dette i forhold til usikkerhed (standardfejl) p?
estimaterne for total og middelv?rdi?

F?rst total: \[\begin{aligned}
V(\hat{t}_y^{st}) &= \sum_{h=1}^2 (1-\frac{n_h}{N_h}) N_h^2 \frac{\hat{s}_h^2}{n_h} \\
&= \sum_{h=1}^2 (1-\frac{\frac{1}{2}n}{\frac{1}{2}N}) (\frac{1}{2}N)^2 \frac{\hat{s}_h^2}{\frac{1}{2}n} \\
&= \sum_{h=1}^2 \frac{1}{2} (1-\frac{n}{N}) N^2 \frac{\hat{s}_h^2}{n}\\
&= (1-\frac{n}{N}) N^2 \frac{\hat{s}_h^2}{n}\\
&=V(\hat{t}_y)
\end{aligned}\]

Det vil sige, at under de n?vnte foruds?tninger er der intet vundet
(eller tabt) ved at lave en stratifikation.

Vi kan gentage beregningen for estimatet for middelv?rdien:
\[\begin{aligned}
V(\bar{y}^{st}) &= \sum_{h=1}^2 W_h^2 V(\bar{y}_h) \\
&= \sum_{h=1}^2 (\frac{N_h}{N})^2 (1-\frac{n_h}{N_h}) \frac{\hat{s_h}^2}{n_h} \\
&= \sum_{h=1}^2 (\frac{\frac{1}{2}N}{N})^2 (1-\frac{\frac{1}{2}n}{\frac{1}{2}N}) \frac{\hat{s_h}^2}{\frac{1}{2}n}\\
&= \sum_{h=1}^2 \frac{1}{2} (1-\frac{n}{N}) \frac{\hat{s_h}^2}{n}\\
&= (1-\frac{n}{N}) \frac{\hat{s_h}^2}{n} \\
&= V(\bar{y})
\end{aligned}\] Resultatet bliver naturligvis det
samme.

<!-- ```{r cars} -->

<!-- summary(cars) -->

<!-- ``` -->

<!-- ## Including Plots -->

<!-- You can also embed plots, for example: -->

<!-- ```{r pressure, echo=FALSE} -->

<!-- plot(pressure) -->

<!-- ``` -->

<!-- Note that the `echo = FALSE` parameter was added to the code chunk to prevent printing of the R code that generated the plot. -->
