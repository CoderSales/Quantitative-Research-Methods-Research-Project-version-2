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

Code from page 7 of above package docs:

```r
hcp_ids(group = c("HCP", "HCP_900", "HCP_1200", "HCP_Retest"))
```

Error:

```r
Error in hcp_list_files(prefix = prefix, delimiter = "/") : 
  Forbidden (HTTP 403).
```

____

Docs | neurohcp [neurohcp: Human 'Connectome' Project Interface](https://rdrr.io/cran/neurohcp/)

allows neruohcp to run in browser

____

[API for neurohcp](https://rdrr.io/cran/neurohcp/api/)

____

Docs for neurohcp: [files](https://rdrr.io/cran/neurohcp/f/)

____

README for hcp: [hcp.Rmd](https://rdrr.io/cran/neurohcp/f/inst/doc/hcp.Rmd)

Code from README previously stated on line above:

```r
library(neurohcp)
library(dplyr)
knitr::opts_chunk$set(echo = TRUE, cache = FALSE, comment = "")

source("http://neuroconductor.org/neurocLite.R")

neuro_install("neurohcp", release = "stable")

```

Set key.

```r
if (have_aws_key()) {
  neurohcp::bucketlist()
}

if (have_aws_key()) {
  neurohcp::bucketlist(verbose = FALSE)
}

ids_with_dwi = hcp_900_scanning_info %>% 
  filter(scan_type %in% "dMRI") %>% 
  select(id) %>% 
  unique


head(ids_with_dwi)
```

```r
r = download_hcp_dir("HCP/100307/T1w/Diffusion", verbose = FALSE)
```

Error:

```r
Error in hcp_list_files(prefix = prefix, delimiter = delimiter, ...) : 
  Forbidden (HTTP 403).
```

____


Google Search: [Error in hcp_list_files(prefix = prefix, delimiter = delimiter, ...) : Forbidden (HTTP 403).](https://www.google.com/search?q=Error+in+hcp_list_files(prefix+%3D+prefix%2C+delimiter+%3D+delimiter%2C+...)+%3A+Forbidden+(HTTP+403).&oq=Error+in+hcp_list_files(prefix+%3D+prefix%2C+delimiter+%3D+delimiter%2C+...)+%3A+Forbidden+(HTTP+403).&gs_lcrp=EgZjaHJvbWUyBggAEEUYOdIBBzk3NGowajeoAgCwAgA&sourceid=chrome&ie=UTF-8)

result: stackoverflow [Trouble downloading S3 bucket objects through boto3. Error 403 HeadObject: Forbidden](https://stackoverflow.com/questions/59615713/trouble-downloading-s3-bucket-objects-through-boto3-error-403-headobject-forbi)

____

Document earlier search:

Google Search: [download_hcp_dir](https://www.google.com/search?q=download_hcp_dir&oq=download_hcp_dir&gs_lcrp=EgZjaHJvbWUyBggAEEUYOTIKCAEQABiABBiiBDIKCAIQABiABBiiBNIBBzU4MmowajeoAgCwAgA&sourceid=chrome&ie=UTF-8)

[download_hcp_dir: Download an entire directory from HCP](https://www.rdocumentation.org/packages/neurohcp/versions/0.9.0/topics/download_hcp_dir)

____

aws keys

____

Fix error

____

```r
r = download_hcp_dir("HCP/100307/T1w/Diffusion", verbose = FALSE)
```

```r
print(basename(r$output_files))
```

```r
r = list(output_files = c("bvals", "bvecs", "data.nii.gz", "grad_dev.nii.gz", "nodif_brain_mask.nii.gz")
)
```

```r
r$output_files
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

End of webpage code.

____

Another package:

[Installing Neuroconductor Packages](https://neuroconductor.org/tutorials/install)

____

Google Search: [Neuroconductor](https://www.google.com/search?q=Neuroconductor&sourceid=chrome&ie=UTF-8)

Result: [About Neuroconductor](https://neuroconductor.org/)

Citations given:

- [Neuroconductor Citation](https://neuroconductor.org/cite)

    - Biostatistics paper: [Neuroconductor: an R platform for medical imaging analysis ](https://academic.oup.com/biostatistics/article/20/2/218/4791943?login=false)

    - Pubmed link: [Neuroconductor: an R platform for medical imaging analysis](https://pubmed.ncbi.nlm.nih.gov/29325029/)

    - BibTex:
      ```BibTex
      @Article{pmid29325029,
        Author={Muschelli, J. and Gherman, A. and Fortin, J. P. and Avants, B. and Whitcher, B. and Clayden, J. D. and Caffo, B. S. and Crainiceanu, C. M. },
        Title={{N}euroconductor: an {R} platform for medical imaging analysis},
        Journal={Biostatistics},
        Year={2018},
        Month={Jan}
        }
      ```

____

