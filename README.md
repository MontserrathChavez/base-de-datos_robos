# base-de-datos_robos
Aqui se analizan datos de robos durante cierto periodo 
library(readxl)
> list.files()
[12] "Libro2.xlsx"                                                                                                                 
> datos <- read_excel("Libro2.xlsx")
> View(datos)
> summary(datos)
  Municipio         Robo tranporte Robo de negocio  Robo de vehiculo  Robo en casa    Robo con violencia
 Length:46          Min.   :0      Min.   : 0.000   Min.   : 0.000   Min.   : 0.000   Min.   : 0.00     
 Class :character   1st Qu.:0      1st Qu.: 0.000   1st Qu.: 4.621   1st Qu.: 2.395   1st Qu.:11.60     
 Mode  :character   Median :0      Median : 3.332   Median : 8.460   Median : 7.117   Median :19.40     
                    Mean   :0      Mean   : 6.681   Mean   :11.282   Mean   : 7.848   Mean   :24.66     
                    3rd Qu.:0      3rd Qu.: 9.430   3rd Qu.:14.055   3rd Qu.:12.099   3rd Qu.:31.39     
                    Max.   :0      Max.   :37.611   Max.   :44.514   Max.   :30.405   Max.   :77.42     
> library(tidyverse)
Error en library(tidyverse): no hay paquete llamado ‘tidyverse’

> install.packages("tidyverse")
WARNING: Rtools is required to build R packages but is not currently installed. Please download and install the appropriate version of Rtools before proceeding:

https://cran.rstudio.com/bin/windows/Rtools/
Installing package into ‘C:/Users/bodes/AppData/Local/R/win-library/4.5’
(as ‘lib’ is unspecified)
also installing the dependencies ‘fastmap’, ‘sys’, ‘ps’, ‘sass’, ‘digest’, ‘cachem’, ‘farver’, ‘labeling’, ‘RColorBrewer’, ‘viridisLite’, ‘rappdirs’, ‘askpass’, ‘base64enc’, ‘processx’, ‘evaluate’, ‘highr’, ‘xfun’, ‘yaml’, ‘bslib’, ‘fontawesome’, ‘htmltools’, ‘jquerylib’, ‘tinytex’, ‘backports’, ‘generics’, ‘memoise’, ‘blob’, ‘DBI’, ‘data.table’, ‘gtable’, ‘isoband’, ‘S7’, ‘scales’, ‘gargle’, ‘uuid’, ‘curl’, ‘ids’, ‘rematch2’, ‘mime’, ‘openssl’, ‘timechange’, ‘systemfonts’, ‘textshaping’, ‘callr’, ‘fs’, ‘knitr’, ‘rmarkdown’, ‘selectr’, ‘stringi’, ‘broom’, ‘conflicted’, ‘dbplyr’, ‘dplyr’, ‘dtplyr’, ‘forcats’, ‘ggplot2’, ‘googledrive’, ‘googlesheets4’, ‘haven’, ‘httr’, ‘jsonlite’, ‘lubridate’, ‘modelr’, ‘purrr’, ‘ragg’, ‘reprex’, ‘rstudioapi’, ‘rvest’, ‘stringr’, ‘tidyr’, ‘xml2’

The downloaded binary packages are in
	C:\Users\bodes\AppData\Local\Temp\RtmpQrpHkV\downloaded_packages
> library(tidyverse)
── Attaching core tidyverse packages ───────────────────────────────────────────────────────────────────────── tidyverse 2.0.0 ──
✔ dplyr     1.2.1     ✔ readr     2.2.0
✔ forcats   1.0.1     ✔ stringr   1.6.0
✔ ggplot2   4.0.3     ✔ tibble    3.3.1
✔ lubridate 1.9.5     ✔ tidyr     1.3.2
✔ purrr     1.2.2     
── Conflicts ─────────────────────────────────────────────────────────────────────────────────────────── tidyverse_conflicts() ──
✖ dplyr::filter() masks stats::filter()
✖ dplyr::lag()    masks stats::lag()
ℹ Use the conflicted package to force all conflicts to become errors
> glimpse(datos)
Rows: 46
Columns: 6
$ Municipio            <chr> "Abasolo", "Acambaro", "San Miguel De Allende", "Apaseo El Alto", "Apaseo El Grande", "Atarjea", "…
$ `Robo tranporte`     <dbl> 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0,…
$ `Robo de negocio`    <dbl> 3.020327, 0.000000, 11.021597, 5.352173, 10.644577, 0.000000, 34.837390, 0.000000, 3.329005, 0.000…
$ `Robo de vehiculo`   <dbl> 10.067756, 9.622555, 9.447083, 21.408691, 44.513688, 0.000000, 24.132149, 2.364290, 13.316022, 0.0…
$ `Robo en casa`       <dbl> 1.006776, 8.820675, 18.894167, 13.380432, 7.741511, 0.000000, 15.422803, 0.000000, 14.425691, 7.37…
$ `Robo con violencia` <dbl> 16.108410, 14.433833, 29.915764, 28.098907, 77.415112, 0.000000, 73.485117, 14.185739, 32.180387, …
> modelo<-lm( `Robo de negocio`~`Robo de vehiculo` +`Robo en casa` +`Robo con violencia`, data=datos)
> summary(modelo)

Call:
lm(formula = `Robo de negocio` ~ `Robo de vehiculo` + `Robo en casa` + 
    `Robo con violencia`, data = datos)

Residuals:
    Min      1Q  Median      3Q     Max 
-10.908  -3.063  -1.180   1.389  13.475 

Coefficients:
                     Estimate Std. Error t value Pr(>|t|)    
(Intercept)          -1.37461    1.58935  -0.865  0.39201    
`Robo de vehiculo`   -0.29943    0.11405  -2.625  0.01202 *  
`Robo en casa`        0.35261    0.13063   2.699  0.00997 ** 
`Robo con violencia`  0.35145    0.05808   6.051 3.36e-07 ***
---
Signif. codes:  0 ‘***’ 0.001 ‘**’ 0.01 ‘*’ 0.05 ‘.’ 0.1 ‘ ’ 1

Residual standard error: 5.952 on 42 degrees of freedom
Multiple R-squared:  0.5911,	Adjusted R-squared:  0.5619 
F-statistic: 20.24 on 3 and 42 DF,  p-value: 2.866e-08

> View(modelo)
> View(datos)
> summary(modelo)

Call:
lm(formula = `Robo de negocio` ~ `Robo de vehiculo` + `Robo en casa` + 
    `Robo con violencia`, data = datos)

Residuals:
    Min      1Q  Median      3Q     Max 
-10.908  -3.063  -1.180   1.389  13.475 

Coefficients:
                     Estimate Std. Error t value Pr(>|t|)    
(Intercept)          -1.37461    1.58935  -0.865  0.39201    
`Robo de vehiculo`   -0.29943    0.11405  -2.625  0.01202 *  
`Robo en casa`        0.35261    0.13063   2.699  0.00997 ** 
`Robo con violencia`  0.35145    0.05808   6.051 3.36e-07 ***
---
Signif. codes:  0 ‘***’ 0.001 ‘**’ 0.01 ‘*’ 0.05 ‘.’ 0.1 ‘ ’ 1

Residual standard error: 5.952 on 42 degrees of freedom
Multiple R-squared:  0.5911,	Adjusted R-squared:  0.5619 
F-statistic: 20.24 on 3 and 42 DF,  p-value: 2.866e-08

> 
