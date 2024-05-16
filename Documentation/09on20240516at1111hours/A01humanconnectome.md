# humanconnectome

[Getting Data from the Human Connectome Project (HCP)](https://cran.r-project.org/web/packages/neurohcp/vignettes/hcp.html)

[Public Connectome Data](https://db.humanconnectome.org/)

## Installing the neurohcp package

Command:

```r
source("http://neuroconductor.org/neurocLite.R")
```

Error:

```r
'getOption("repos")' replaces Bioconductor standard repositories, see 'help("repositories", package = "BiocManager")' for details.
Replacement repositories:
    CRAN: https://cran.rstudio.com/
Bioconductor version 3.18 (BiocManager 1.30.22), R 4.3.3 (2024-02-29 ucrt)
Using neurocLite version: # neurocInstall package version: 0.12.0
```

Refactor command per error:

```r
getOption("http://neuroconductor.org/neurocLite.R")
```

Output:

```r
NULL
```

____

Retry:

```r
source("http://neuroconductor.org/neurocLite.R")
'getOption("repos")' replaces Bioconductor standard repositories, see 'help("repositories", package = "BiocManager")' for details.
Replacement repositories:
    CRAN: https://cran.rstudio.com/
Bioconductor version 3.18 (BiocManager 1.30.22), R 4.3.3 (2024-02-29 ucrt)
Using neurocLite version: # neurocInstall package version: 0.12.0
```

```r
 neuro_install("neurohcp", release = "stable")
Installing package
(as ‘lib’ is unspecified)
Warning: unable to access index for repository https://neuroconductor.org/releases/2020/05/bin/windows/contrib/4.3:
  cannot open URL 'https://neuroconductor.org/releases/2020/05/bin/windows/contrib/4.3/PACKAGES'
trying URL 'https://cran.rstudio.com/bin/windows/contrib/4.3/neurohcp_0.9.0.zip'
Content type 'application/zip' length 624303 bytes (609 KB)
downloaded 609 KB

package ‘neurohcp’ successfully unpacked and MD5 sums checked
```

____

Note: following:

[Getting Data from the Human Connectome Project (HCP)](https://cran.r-project.org/web/packages/neurohcp/vignettes/hcp.html)

____

Note: added command:

```r
library(neurohcp)
```

____

```r
set_aws_api_key(access_key = "ACCESS_KEY", secret_key = "SECRET_KEY")
```

____


```r
if (have_aws_key()) {
  neurohcp::bucketlist()
}
```

____

### Command:

```r
ids_with_dwi = hcp_900_scanning_info %>% 
+ filter(scan_type %in% "dMRI") %>%
+ select(id) %>%
+ unique
```

#### Error:

```r
  could not find function "%>%"
```

##### Google Search: [could not find function "%>%"](https://www.google.com/search?q=could+not+find+function+%22%25%3E%25%22&oq=could+not+find+function+%22%25%3E%25%22&gs_lcrp=EgZjaHJvbWUyBggAEEUYOTIHCAEQABiABDIHCAIQABiABDIHCAMQABiABDIHCAQQABiABDIHCAUQABiABDIHCAYQABiABDIHCAcQABiABDIHCAgQABiABDIHCAkQABiABNIBBzg5MmowajeoAgCwAgA&sourceid=chrome&ie=UTF-8)

____

###### Result: stackoverflow: 

**Content**:

The pipe operator %>% was introduced to "decrease development time and to improve readability and maintainability of code."

But everybody has to decide for himself if it really fits his workflow and makes things easier. For more information on magrittr, click [here](http://cran.r-project.org/web/packages/magrittr/vignettes/magrittr.html).

Not using the pipe %>%, this code would return the same as your code:

```r
words <- colnames(as.matrix(dtm))
words <- words[nchar(words) < 20]
words
```

**Comparative Context (Code from Question)**:

```r
words <- dtm %>%
as.matrix %>%
colnames %>%
(function(x) x[nchar(x) < 20])
```

**Comparing Code from Content(Answer) with Code from Context(Question)**:

*Question Code*:

```r
words <- dtm %>%
as.matrix %>%
colnames %>%
(function(x) x[nchar(x) < 20])
```

*Answer Code*:

```r
words <- colnames(as.matrix(dtm))
words <- words[nchar(words) < 20]
words
```

_# # # # # # # # # # # # # # # # # # # # 

```html
<html>
    <head>
    </head>
    <body>
<u>Abstract to generalise and Refactor:</u>
    </body>
</html>
```

Note: here: Key:

- variable = words

- argument = dtm



*Question Code*:

```r
variable <- argument %>%
as.matrix %>%
colnames %>%
(function(x) x[nchar(x) < 20])
```

*Answer Code*:

```r
variable <- colnames(as.matrix(argument))
variable <- variable[nchar(variable) < 20]
variable
```

_# # # # # # # # # # # # # # # # # # # # 

```html
<html>
    <head>
    </head>
    <body>
<u>Application of Stackoverflow abstracted Generalisation (generalised abstraction / (<kbd>Ctrl</kbd> + <kbd>F</kbd>)"Abstract to generalise") to Bug:</u>
    </body>
</html>
```



_# # # # # # # # # # # # # # # # # # # # 

**Reference**: [Error: could not find function "%>%"](https://stackoverflow.com/questions/30248583/error-could-not-find-function)

____

