# Try to Apply Graphing from fMRI Paper to HCP

[Back to README](/)

____

Update:

Try applying HCP progress to:

AWS S3 Client Package [README](https://cran.r-project.org/web/packages/aws.s3/readme/README.html)

____

Update:

Try to combine:

- `fmri` paper: [Coordinate-Based Meta-Analysis of fMRI | Studies with R | by Andrea Stocco](https://journal.r-project.org/archive/2014/RJ-2014-020/RJ-2014-020.pdf), documented in this repository here: [A01ReviewPaper.md](/Documentation/05post20240510at1748hours/A01ReviewPaper.md), 

- HCP webpage: [Getting Data from the Human Connectome Project (HCP)](https://cran.r-project.org/web/packages/neurohcp/vignettes/hcp.html), 

    -    ( which refers to: [Public Connectome Data](https://db.humanconnectome.org/) )

    , and

- [AWS S3 Client Package](https://cran.r-project.org/web/packages/aws.s3/readme/README.html)

____


## Next Step

Try to combine:

This Command:

```r
library(oro.nifti)
temp <- file.path(tempdir(), "mni_colin27_1998_nifti.zip")
colin.url <-
"http://packages.bic.mni.mcgill.ca/mni-models/colin27/mni_colin27_1998_nifti.zip"
```

on page 8. of:

`fmri` paper: [Coordinate-Based Meta-Analysis of fMRI | Studies with R | by Andrea Stocco](https://journal.r-project.org/archive/2014/RJ-2014-020/RJ-2014-020.pdf)


with:

[AWS S3 Client Package](https://cran.r-project.org/web/packages/aws.s3/readme/README.html)

and / or:

HCP webpage: [Getting Data from the Human Connectome Project (HCP) | John Muschelli | 2020-10-14](https://cran.r-project.org/web/packages/neurohcp/vignettes/hcp.html)

____

from:

page 8 of

`fmri` paper: [Coordinate-Based Meta-Analysis of fMRI | Studies with R | by Andrea Stocco](https://journal.r-project.org/archive/2014/RJ-2014-020/RJ-2014-020.pdf)

need to have MNI space coordinates

per oro.nifti R package;

and I want to apply this to / use analysis methods from / work on data from:

[AWS S3 Client Package](https://cran.r-project.org/web/packages/aws.s3/readme/README.html)

or

HCP webpage: [Getting Data from the Human Connectome Project (HCP) | John Muschelli | 2020-10-14](https://cran.r-project.org/web/packages/neurohcp/vignettes/hcp.html)

____

Note:

HCP webpage: [Getting Data from the Human Connectome Project (HCP) | John Muschelli | 2020-10-14](https://cran.r-project.org/web/packages/neurohcp/vignettes/hcp.html)

points to repository for neurohcp package:

[muschellij2/neurohcp](https://github.com/muschellij2/neurohcp)

____

from above repository:

```r
# install.packages("devtools")
devtools::install_github("muschellij2/hcp")
```

To update all packages:

```r
1
```

Warning:

```r
Warning: package ‘neurohcp’ is in use and will not be installed
```

____

Google Search: [neurohcp](https://www.google.com/search?q=neurohcp&oq=neurohcp&gs_lcrp=EgZjaHJvbWUyBggAEEUYOTIJCAEQABgNGIAEMgkIAhAAGA0YgAQyCQgDEAAYDRiABDIJCAQQABgNGIAEMgYIBRBFGDwyBggGEEUYPDIGCAcQRRg80gEIMTE2OGowajeoAgCwAgA&sourceid=chrome&ie=UTF-8)

[neurohcp: Human 'Connectome' Project Interface](https://cran.r-project.org/web/packages/neurohcp/index.html)

package url convention Requested on docs:

Please use the canonical form [https://CRAN.R-project.org/package=neurohcp](https://CRAN.R-project.org/package=neurohcp) to link to this page.

links to:

HCP webpage: [Getting Data from the Human Connectome Project (HCP) | John Muschelli | 2020-10-14](https://cran.r-project.org/web/packages/neurohcp/vignettes/hcp.html)

____

[Package ‘neurohcp’](https://cran.r-project.org/web/packages/neurohcp/neurohcp.pdf)
____

