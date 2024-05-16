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

#### Error: [Resolved]

```r
  could not find function "%>%"
```

____

[Fix]:

|Part 1: install 2 packages:|
|------------------------------------------------------------------------|

```r
install.packages("magrittr") # package installations are only needed the first time you use it
install.packages("dplyr")    # alternative installation of the %>%
library(magrittr) # needs to be run every time you start R and want to use %>%
library(dplyr)    # alternatively, this also loads %>%
```

|Part 2: Repaste original code correctly formatted (remove <kbd>+</kbd>):|
|------------------------------------------------------------------------|

```r
ids_with_dwi = hcp_900_scanning_info %>% 
    filter(scan_type %in% "dMRI") %>%
    select(id) %>%
    unique
```

##### Google Search: [could not find function "%>%"](https://www.google.com/search?q=could+not+find+function+%22%25%3E%25%22&oq=could+not+find+function+%22%25%3E%25%22&gs_lcrp=EgZjaHJvbWUyBggAEEUYOTIHCAEQABiABDIHCAIQABiABDIHCAMQABiABDIHCAQQABiABDIHCAUQABiABDIHCAYQABiABDIHCAcQABiABDIHCAgQABiABDIHCAkQABiABNIBBzg5MmowajeoAgCwAgA&sourceid=chrome&ie=UTF-8)

**Reference**: stackoverflow: [Error: could not find function "%>%"](https://stackoverflow.com/questions/30248583/error-could-not-find-function)

Bug Fixed [Resolved]

____

Continuing with: [Getting Data from the Human Connectome Project (HCP)](https://cran.r-project.org/web/packages/neurohcp/vignettes/hcp.html)

```r
head(ids_with_dwi)
```

Let us download the complete directory of diffusion data using download_hcp_dir:

```r
r = download_hcp_dir("HCP/100307/T1w/Diffusion", verbose = FALSE)
```

From above: "complete directory"

There is a wait here (minute(s)).

```r
print(basename(r$output_files))
```

```r
ids_with_dwi = ids_with_dwi %>% 
  mutate(id_dir = paste0("HCP/", id, "/T1w/Diffusion"))
```

```r
if (have_aws_key()) {
  ret = download_hcp_file("HCP/100307/T1w/Diffusion/bvals", verbose = FALSE)
}
```

End of webpage document.

____

Note: from start of webpage document:

All code for this document is located at [here](https://raw.githubusercontent.com/muschellij2/neuroc/master/neurohcp/index.R).

Note: This version untried as used the version in original webpage.

____
