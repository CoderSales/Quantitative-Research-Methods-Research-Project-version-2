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

|Abstract to generalise and Refactor:|
|------------------------------------|

Google Search: [underline in markdown](https://www.google.com/search?q=underline+in+markdown&oq=underline+in+markdown&gs_lcrp=EgZjaHJvbWUyCQgAEEUYORiABDIHCAEQABiABDIHCAIQABiABDIHCAMQABiABDIICAQQABgWGB4yCAgFEAAYFhgeMgoIBhAAGA8YFhgeMggIBxAAGBYYHjIICAgQABgWGB4yCAgJEAAYFhge0gEIMzc4OWowajeoAgCwAgA&sourceid=chrome&ie=UTF-8)

[Reference for underline using heading](https://www.ionos.com/digitalguide/websites/web-development/markdown/#:~:text=Text%20can't%20be%20underlined,usually%20inadvisable%20to%20do%20so.)

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

|Application of Stackoverflow abstracted Generalisation (generalised abstraction / (<kbd>Ctrl</kbd> + <kbd>F</kbd>)"Abstract to generalise") to Bug:|
|---------------------------------------------|

Google Search: [underline in markdown](https://www.google.com/search?q=underline+in+markdown&oq=underline+in+markdown&gs_lcrp=EgZjaHJvbWUyCQgAEEUYORiABDIHCAEQABiABDIHCAIQABiABDIHCAMQABiABDIICAQQABgWGB4yCAgFEAAYFhgeMgoIBhAAGA8YFhgeMggIBxAAGBYYHjIICAgQABgWGB4yCAgJEAAYFhge0gEIMzc4OWowajeoAgCwAgA&sourceid=chrome&ie=UTF-8)

[Reference for underline using heading](https://www.ionos.com/digitalguide/websites/web-development/markdown/#:~:text=Text%20can't%20be%20underlined,usually%20inadvisable%20to%20do%20so.)

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

*Code with Bug*:

```r
ids_with_dwi = hcp_900_scanning_info %>% 
+ filter(scan_type %in% "dMRI") %>%
+ select(id) %>%
+ unique
```

*Trying to translate Code with Bug to Code with Fix*:

Note: here: Key:

variable = ids_with_dwi

argument = hcp_900_scanning_info

```r
ids_with_dwi <- filter(scan_type %in% "dMRI") %>%
ids_with_dwi <- ids_with_dwi[id] 
ids_with_dwi
```


_# # # # # # # # # # # # # # # # # # # # 

**Reference**: [Error: could not find function "%>%"](https://stackoverflow.com/questions/30248583/error-could-not-find-function)

____

Debug continued:

Tried:

```r
ids_with_dwi <- filter(scan_type %in% "dMRI") %>%
ids_with_dwi <- ids_with_dwi[id] 
ids_with_dwi
```

Error:

Error: object 'ids_with_dwi' not found

Google Search: [r programming Error: object '' not found](https://www.google.com/search?q=r+programming+Error%3A+object+%27%27+not+found&oq=r+programming+Error%3A+object+%27%27+not+found&gs_lcrp=EgZjaHJvbWUyBggAEEUYOTIGCAEQRRhAMgYIAhBFGEDSAQkxNDkxMmowajeoAgCwAgA&sourceid=chrome&ie=UTF-8)

Result:

If you forget to define an object or assign a value to it, R will not be able to find it and throw the 'Object Not Found' error. Always make sure to define and assign values to your objects before using them in your code. Incorrect Data Types: Attempting operations that are only applicable to specific data types.

Source:

[Fix It Insider](https://fixitinsider.com/how-to-fix-object-not-found-error-in-r/#:~:text=If%20you%20forget%20to%20define,applicable%20to%20specific%20data%20types.)

Attempted Application to Bug:

Convert <- to =

Reason:

to create variable

Assume:

<- operator only works

after = operator used previously to assign / declare / instantiate variable

