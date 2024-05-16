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
