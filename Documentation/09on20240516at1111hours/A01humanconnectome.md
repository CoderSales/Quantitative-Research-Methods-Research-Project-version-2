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

Command:

```r
ids_with_dwi = hcp_900_scanning_info %>% 
+ filter(scan_type %in% "dMRI") %>%
+ select(id) %>%
+ unique
```

Error:

```r
  could not find function "%>%"
```

Google Search: [could not find function "%>%"](https://www.google.com/search?q=could+not+find+function+%22%25%3E%25%22&oq=could+not+find+function+%22%25%3E%25%22&gs_lcrp=EgZjaHJvbWUyBggAEEUYOTIHCAEQABiABDIHCAIQABiABDIHCAMQABiABDIHCAQQABiABDIHCAUQABiABDIHCAYQABiABDIHCAcQABiABDIHCAgQABiABDIHCAkQABiABNIBBzg5MmowajeoAgCwAgA&sourceid=chrome&ie=UTF-8)

Result: stackoverflow: [Error: could not find function "%>%"](https://stackoverflow.com/questions/30248583/error-could-not-find-function)
