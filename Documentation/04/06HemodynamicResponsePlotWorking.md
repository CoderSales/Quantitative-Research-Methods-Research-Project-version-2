# Hemodynamic Response Plot Working

## Code

```r
> h <- fmri.stimulus(301, durations = c(0), # h(t) for instantaneous event at t=0, onsets = c(1), rt = 0.1)
+ onsets = c(1))
> plot(t, h, type = "l", lwd = 2, col = "red",
+      xlab = "Time (secs)", ylab = "h(t)", main = "Hemodynamic Response Function")
```

Note: line 2 of above is missing `rt = 0.1` from paper due to technical issue previously outlined.

## Screenshot (RStudio)

![Screenshot of HemodynamicResponse](/src/images/Screenshot-2024-04-22-131522-HemodynamicResponse.png)

____

Note: On repetition time, TR

Relevance: workaround outlined in this and previous document.

Quote from [Stocco 2014](https://journal.r-project.org/archive/2014/RJ-2014-020/RJ-2014-020.pdf) Paper (I added emphasis here and generally): "The interval between image acquisitions is known as **repetition time** or **TR**, and is typically 2
seconds."

____

Note: 

Quote: "Each image is made of thousands of almost-cubic elements called **voxels**."

Quote: "The size of a **voxel** (typically on the order of 3 × 3 × 3 mm) represents the *lower limit of the spatial resolution of an image*."

____

Quote: 

"the **BOLD response** 

*to an increase of neural activity at time t = 0* 

follows a specific time course, 

which is known as 

the **hemodynamic response function** `h(t)`"

____

Quote: (out of order with paper)

"The MRI scanner 

captures brain “activity” only indirectly, 

by measuring the so-called 

**Blood Oxygen-Level Dependent (BOLD) signal**

—that is, 

the amount of *oxygenated blood* 

*present* 

*in every position in space.*"

____

"The BOLD signal is known to vary as a function of neural activity."

____

## Issue: Plot not matching with paper on time axis

![Paper Hemodynamic Response Plot](/src/images/Screenshot-2024-04-22-133944-PaperHemodynamicResponsePlot.png)

____

### Potential Cause:

Workaround (previously stated), of:

removing `rt=0.1` in command.

____

#### References for fmri r documentation

Google Search String: [fmri r documentation](https://www.google.com/search?q=fmri+r+documentation&newwindow=1&sca_esv=6ab47ddd9796bc0d&sca_upv=1&sxsrf=ACQVn0_l_xD949yxjheWmqk9f-7tIpEz1w%3A1713790269641&ei=PV0mZufcJr-shbIPh_CkqA8&ved=0ahUKEwin7_ah7tWFAxU_VkEAHQc4CfUQ4dUDCBE&uact=5&oq=fmri+r+documentation&gs_lp=Egxnd3Mtd2l6LXNlcnAiFGZtcmkgciBkb2N1bWVudGF0aW9uMgQQABhHMgQQABhHMgQQABhHMgQQABhHMgQQABhHMgQQABhHMgQQABhHMgQQABhHSJkdUN0VWK4WcAB4ApABAJgBAKABAKoBALgBA8gBAPgBAZgCAaACDZgDAIgGAZAGCJIHATGgBwA&sclient=gws-wiz-serp)

[fmri: Analysis of fMRI Experiments](https://cran.r-project.org/web/packages/fmri/index.html)

[WIAS R-packages for imaging / neuroscience](https://www.wias-berlin.de/software/imaging/)

[WIAS-BERLIN](https://github.com/WIAS-BERLIN)

[WIAS-BERLIN/fmri](https://github.com/WIAS-BERLIN/fmri)

____

from last reference above (GitHub Repository README):

```r
install.packages("fmri")
```

prompted to Restart RStudio

RTools Warning Reemerges:

```r
WARNING: Rtools is required to build R packages but is not currently installed. Please download and install the appropriate version of Rtools before proceeding:
```

____

Issue:

```r
# install.packages("devtools")
devtools::install_github("muschellij2/fmri")
```

gives:

```r
Error in loadNamespace(x) : there is no package called ‘devtools’
```

____

This works (uncomment devtools installl line.) :

```r
install.packages("devtools")
```

Then can do:

```r
devtools::install_github("muschellij2/fmri")
```

____

but first:

TODO: try to do install with dependencies command from ealier.

____

#### Plan

(Try to)

Use the *format* of *this* command:

```r
install.packages('fmri', dependencies = TRUE, repos='http://cran.rstudio.com/')
```

from:

[01Plan.md](/Documentation/04/01Plan.md)

with *this* command:

```r
devtools::install_github("muschellij2/fmri")
```

to get *this* command:

```r
devtools::install_github("muschellij2/fmri", dependencies = TRUE, repos='https://github.com/WIAS-BERLIN/fmri')
```

Run that last command and see what happens.

____

Result of last command:

Downloads GitHub Repository:

![Downloading From GitHub](/src/images/Screenshot-2024-04-22-141030-DownloadingFromGitHub.png)

I stopped installation after download.

Reason: Uses Rtools 4 3 

versus 

RTools44 installed

____

Revert to previous command:

```r
install.packages("devtools")
```

gives Output:

```r
Error in install.packages : Updating loaded packages

Restarting R session...
```

system re runs the following automatically:

```r
install.packages("devtools")
```

resulting in:

```r
WARNING: Rtools is required to build R packages but is not currently installed. Please download and install the appropriate version of Rtools before proceeding:
```

gives location of devtools

____

Extract all

____

Back to paper:

retry:

```r
library(fmri)

t <- seq(0, 30, 0.1) # from 0 to 30 secs, in increments of 100ms
```

```r
h <- fmri.stimulus(301, durations = c(0), # h(t) for instantaneous event at t=0,
onsets = c(1), rt = 0.1), # Sampled at TR = 0.1 secs
plot(t, h, type = "l", lwd = 2, col = "red",
xlab = "Time (secs)", ylab = "h(t)", main = "Hemodynamic Response Function")
```

```r
System only takes:

> h <- fmri.stimulus(301, durations = c(0), # h(t) for instantaneous event at t=0,
+                    onsets = c(1), rt = 0.1), # Sampled at TR = 0.1 secs
```

and gives Error:

```r
Error: unexpected ',' in:
"h <- fmri.stimulus(301, durations = c(0), # h(t) for instantaneous event at t=0,
                   onsets = c(1), rt = 0.1),"
```

____

from 

[WIAS-BERLIN/fmri](https://github.com/WIAS-BERLIN/fmri)

run:

```r
devtools::install_github("muschellij2/fmri")
```

____

![DownloadingSecondTime](/src/images/Screenshot-2024-04-22-142518-DownloadingSecondTime.png)

____

![Installing-Rtools4-3](/src/images/Screenshot-2024-04-22-142839-Installing-Rtools4-3.png)

____

As before (not documented last time):

#### Error

```r
Error: Failed to install 'fmri' from GitHub:
  Could not find tools necessary to compile a package
Call `pkgbuild::check_build_tools(debug = TRUE)` to diagnose the problem.
```

```r
pkgbuild::check_build_tools(debug = TRUE)
```

Output:

```r
Your system is ready to build packages!
```

____

copied in from [A06UpdateR.md](/Documentation/01pre20240422at0941hours/A06UpdateR.md) (accidentally entered there)

____

Quit RStudio

From: [A06UpdateR.md](/Documentation/01pre20240422at0941hours/A06UpdateR.md)

Add or Remove Programs 

Uninstall R 4.3.3

Are you sure 

Yes

Successful > OK

____

Uninstall R Tools 4.3

____

Ok

____

Still installed are:

RTools 4.4 and RStudio

left alone for now.

____

Next step:

Reinstall R

____

from:

[r-project](https://cloud.r-project.org/)

per [update-r-using-rstudio | StackOverflow](https://stackoverflow.com/questions/13656699/update-r-using-rstudio)

referenced here [A06UpdateR.md](/Documentation/01pre20240422at0941hours/A06UpdateR.md) (second from last reference)

____

Currently installed:

R for Windows 4.3.3

RStudio

R Tools 4.4

____

Note: 

Possibly needed to add

RTools 43 to path when this was installed

from GitHub earlier

____

Google Search String: [Error: unexpected ',' in:](https://www.google.com/search?q=Error%3A+unexpected+%27%2C%27+in%3A&newwindow=1&sca_esv=f65ab4fb82876b19&sca_upv=1&sxsrf=ACQVn09fLS1xy8hUrahQzWxgI4jTGExF_Q%3A1713794410054&ei=am0mZu70ArCthbIPrbC40A0&ved=0ahUKEwju0Z3Y_dWFAxWwVkEAHS0YDtoQ4dUDCBE&uact=5&oq=Error%3A+unexpected+%27%2C%27+in%3A&gs_lp=Egxnd3Mtd2l6LXNlcnAiGUVycm9yOiB1bmV4cGVjdGVkICcsJyBpbjpIvARQAFgAcAB4AJABAJgBAKABAKoBALgBA8gBAPgBAZgCAKACAJgDAJIHAKAHAA&sclient=gws-wiz-serp)

_# # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # #

"These errors mean that the R code you are trying to run or source is not syntactically correct. That is, you have a typo."

"You can also use the formatR package to automatically format your code into something more readable. In RStudio, the keyboard shortcut <kbd>CTRL</kbd> + <kbd>SHIFT</kbd> + 
<kbd>A</kbd> will reformat your code."

[Error: unexpected symbol/input/string constant/numeric constant/SPECIAL in my code | StackOverflow](https://stackoverflow.com/questions/25889234/error-unexpected-symbol-input-string-constant-numeric-constant-special-in-my-co)

____

RStudio Screenshot:

![ReformatCurrentSelection](/src/images/Screenshot-2024-04-22-150918-ReformatCurrentSelection.png)

from above screenshot:

<kbd>Ctrl</kbd> <kbd>Shift</kbd> <kbd>P</kbd> - Show Command Palette

<kbd>Ctrl</kbd> <kbd>Shift</kbd> <kbd>A</kbd> - Reformat Current Selection

____

Google Search String: [r code parser](https://www.google.com/search?q=r+code+parser&oq=r+code+parser&gs_lcrp=EgZjaHJvbWUyBggAEEUYOTIGCAEQRRhAMgYIAhBFGEDSAQgyMjYxajBqN6gCALACAA&sourceid=chrome&ie=UTF-8)

[Chapter 10 Parser | r language definition](https://colinfay.me/r-language-definition/parser.html)

____

```blurb
by K Tabelow · Cited by 104 — Description. Return a design matrix for a linear model with given stimuli and possible polynomial drift terms. Usage fmri.design(stimulus, order ...
```

Google Search String: [h <- fmri.stimulus](https://www.google.com/search?q=h+%3C-+fmri.stimulus&oq=h+%3C-+fmri.stimulus&gs_lcrp=EgZjaHJvbWUyBggAEEUYOTIGCAEQRRhA0gEHOTM5ajBqN6gCALACAA&sourceid=chrome&ie=UTF-8)

[Package ‘fmri’](https://cran.r-project.org/web/packages/fmri/fmri.pdf)

From above blurb given by Google Search:

<kbd>Ctrl</kbd> <kbd>F</kbd> 

for: fmri.design(stimulus

gives: 

![Ctrl-f-for-fmri-dot-design](/src/images/Screenshot-2024-04-22-152513-Ctrl-f-for-fmri-dot-design.png)

____

![Issue-with-rt](/src/images/Screenshot-2024-04-22-160506-Issue-with-rt.png)

____

![Focused-Image-of-Docs-BOLD-response](/src/images/Screenshot-2024-04-22-161306-Focused-Image-of-Docs-BOLD-response.png)

____

From above:

```r
..., TR = 2, ....
```

is an example of the correct syntax for the TR argument (apart from the leading and trailing dots).

____

**Fix**: change `rt` or `RT` to **`TR`**:

```r
> h <- fmri.stimulus(301, durations = c(0), onsets = c(1), RT = 0.1)
Error in fmri.stimulus(301, durations = c(0), onsets = c(1), RT = 0.1) : 
  unused argument (RT = 0.1)
> h <- fmri.stimulus(301, durations = c(0), onsets = c(1), TR = 0.1)
> 
```

____


```r
> plot(t, h, type = "l", lwd = 2, col = "red",
+      xlab = "Time (secs)", ylab = "h(t)", main = "Hemodynamic Response Function")
> 
[WARNING] Deprecated: --self-contained. use --embed-resources --standalone
```


focus:

```r
--self-contained. use --embed-resources --standalone
```

where is `--self-contained` used?

____

![Better-Hemodynamic-Response-Function](/src/images/Screenshot-2024-04-22-162933-Better-Hemodynamic-Response-Function.png)

____

Google Search String: [r fmri [WARNING] Deprecated: --self-contained. use --embed-resources --standalone](https://www.google.com/search?q=r+fmri+%5BWARNING%5D+Deprecated%3A+--self-contained.+use+--embed-resources+--standalone&newwindow=1&sca_esv=f4839f9b938815d2&sca_upv=1&sxsrf=ACQVn0-LnfrBTPbPmdM2mclSdpkH17LElQ%3A1713800000436&ei=QIMmZqWeGqinhbIPkI200A0&ved=0ahUKEwilvvfBktaFAxWoU0EAHZAGDdoQ4dUDCBE&uact=5&oq=r+fmri+%5BWARNING%5D+Deprecated%3A+--self-contained.+use+--embed-resources+--standalone&gs_lp=Egxnd3Mtd2l6LXNlcnAiUXIgZm1yaSBbV0FSTklOR10gRGVwcmVjYXRlZDogLS1zZWxmLWNvbnRhaW5lZC4gdXNlIC0tZW1iZWQtcmVzb3VyY2VzIC0tc3RhbmRhbG9uZUgAUABYAHAAeAGQAQCYAQCgAQCqAQC4AQPIAQD4AQGYAgCgAgCYAwCSBwCgBwA&sclient=gws-wiz-serp)

[Warning in R Console about deprecated --self-contained option #12808 | rstudio / rstudio | GitHub.com](https://github.com/rstudio/rstudio/issues/12808)

[R Error when saving gt table in R Studio from the viewer | StackOverflow](https://stackoverflow.com/questions/77553242/r-error-when-saving-gt-table-in-r-studio-from-the-viewer)

above lists the following in `Related questions`:

[Shiny App to render Rmd with Flexdashboard Output Format shows pandoc document conversion failed with error 1 | StackOverflow](https://stackoverflow.com/questions/67702543/shiny-app-to-render-rmd-with-flexdashboard-output-format-shows-pandoc-document-c?rq=2)

which links to the answer here:

[R knit to HTML and this is error Error: pandoc.exe: [closed] | StackOverflow](https://stackoverflow.com/questions/66383067/r-knit-to-html-and-this-is-error-error-pandoc-exe/66387092#66387092)

Summary Note after the above Search and Results:

pandoc is used by Shiny

pandoc seems to be the source of this Warning.

____

## Continuing with the Paper

![library-oro-nifti](/src/images/Screenshot-2024-04-22-165413-library-oro-nifti.png)

____

![Add images with code](/src/images/Screenshot-2024-04-22-170358-Add-images-with-code.png)

____

From Paper:

"

Plotting the foci

Because each image in the orthographic view is a figure in itself, the individual foci can be visualized
by plotting points on top of each image with R’s points function, before proceeding to the next image.
In the example of Figure 2, **the individual foci of activation were stored in a ‘data.frame’ object called
foci.**

```r
> foci
x y z Study Type
1 -30 35 8 Cole Words
2 -46 7 21 Harstra Objects
3 -40 8 36 Ruge Shapes
4 36 12 54 Ruge Shapes
5 -48 28 32 Ruge Shapes
6 44 32 32 Ruge Shapes
7 -40 32 16 Ruge Shapes
8 -40 44 8 Ruge Shapes
9 40 40 16 Ruge Shapes
10 -32 20 -4 Ruge Shapes
11 32 28 -4 Ruge Shapes
12 -44 48 -8 Stocco Numbers
```

"

From RStudio:

```r
> foci
Error: object 'foci' not found
```

____

From Docs:

![data.frame](/src/images/Screenshot-2024-04-22-170936-data-frame.png)

____

### Code

Rerun code from earlier: `h <- fmri.stimulus(301, durations = c(0), onsets = c(1), TR = 0.1)`

```r
foci <- fmri.design(h, 2)
```

```r
foci
```

#### Screenshot

![Create foci](/src/images/Screenshot-2024-04-22-174008-Create-foci.png)

____

##### Pseudocode

Used:

```r
hrf <- fmri.stimulus(107, c(18, 48, 78), 15, 2)
z <- fmri.design(hrf, 2)
```

from: [Package ‘fmri’ | fmri | Documentation](https://cran.r-project.org/web/packages/fmri/fmri.pdf)

_# # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # 

modifying line 2 to the following pseudocode which is a hybrid between

what is in the [documentation](https://cran.r-project.org/web/packages/fmri/fmri.pdf) and

what is in the [paper](https://journal.r-project.org/archive/2014/RJ-2014-020/RJ-2014-020.pdf):

```r
h <- fmri.stimulus(107, c(18, 48, 78), 15, 2)
foci <- fmri.design(h, 2)
```

____

##### Code

```r
h <- fmri.stimulus(301, durations = c(0), onsets = c(1), TR = 0.1)`
```

```r
foci <- fmri.design(h, 2)
```

```r
foci
```

____

## New Search

[fMRI Paper | Coordinate-Based Meta-Analysis of fMRI | Studies with R | by Andrea Stocco](https://journal.r-project.org/archive/2014/RJ-2014-020/RJ-2014-020.pdf)

[CRAN Task View: Medical Image Analysis](https://cran.r-project.org/web/views/MedicalImaging.html)

Google Search String: [Brandon Whitcher, Jon Clayden, John Muschelli](https://www.google.com/search?q=Brandon+Whitcher%2C+Jon+Clayden%2C+John+Muschelli&oq=Brandon+Whitcher%2C+Jon+Clayden%2C+John+Muschelli&gs_lcrp=EgZjaHJvbWUyBggAEEUYOdIBBzQxN2owajeoAgCwAgA&sourceid=chrome&ie=UTF-8)

Result: [Neuroconductor: an R platform for medical imaging analysis ](https://academic.oup.com/biostatistics/article/20/2/218/4791943)

pdf of Paper: [Neuroconductor: an R platform for medical imaging analysis | Biostatistics (2019) 20, 2, pp. 218–239 | doi:10.1093/biostatistics/kxx068 | Advance Access publication on January 6, 2018 | JOHN MUSCHELLI∗, ADRIAN GHERMAN | JEAN-PHILIPPE FORTIN, BRIAN AVANTS | BRANDON WHITCHER | JONATHAN D. CLAYDEN | BRIAN S. CAFFO, CIPRIAN M. CRAINICEANU](https://watermark.silverchair.com/kxx068.pdf?token=AQECAHi208BE49Ooan9kkhW_Ercy7Dm3ZL_9Cf3qfKAc485ysgAAA3wwggN4BgkqhkiG9w0BBwagggNpMIIDZQIBADCCA14GCSqGSIb3DQEHATAeBglghkgBZQMEAS4wEQQMAkI_fX-cSBFRGECyAgEQgIIDL32NUwvNyI_r_iSVsohchOBIRdffvUnwQRX-UbPVQ0Gq707GnKlJ36j5N24DL5h2u0jegLGnH0JlQOrz9BcSj4rEgHfDOF6w2QPKTZwTj67NHwwRYxvPCr0-26rs-runu4W6IcHRaac-zV0UEFlETCq3agkV3hCpe83IHJ4n9RLBjrcGjNRVnLXN8nQtz72ckIFNmISd9w94EFHxlFrCfBxlgvzgnVKTnh7EZuYmT3Dnc9SvAKe0EjlE6zRxbzL09IgDRHHgUqPLKGb7sqxUmnt_vZlM_KxiBZK4X7BTByVe72a_ieDnAfxUu5ov-K0sc_EXfdHEUg-wIBP9V1iigzT4FG-DCmKAtrEzzPxxFs8QikC1i12Hpl0Kw8SKxrE4I4Ds2m9KzXdYBV8bzuwyjPJZ8KbTNWMwyw3GYcIu48S_O2lcmgwWBG1kC2yy1OOFk36h5CARNu9WegX-_1vDwb2JhVFYKKaKnf1wdoedPK7lbS-Dcp72sa8098NC0k-yQXY5hG_smaxIZ67pa72VHyteEAsW6gJSr4XqzEcDFDVwhLbZXZoLcNVJYTqngEaKzGLbKg7rh2dZA_u52mL4T4nRQbyDSI3IdehSh6PrhwpK-XFIEFI8l5yrQF6RM3QVGJV8HDO_KmTxmwsSN9juH0kzTuKZsKwSgL6Wdtskpj991vYBxoQ7t0Jf_BLJ_peqwceV4EWEG4br1atk-3DY07bI9AwYlXRjdy71V9YlgKhRWm1fuKVJjlNHM0I2crjfU_y37M9g3szgJQhpzXuNB3fivNow2byE5PBQFgRdru_G7MjZ7WDtUcCBf4R7sa91kCdGMVjRzTDoYkp_bveUvZO5WCvnHw8OqfOL_mFEsrs8gJIS1NhdElIkC8U-qB_lgpVz86_cMUCAHE89jP5kDwkMxlW3gD9Ar5f7KiD7IczqYqmmZtcHJeKVaePg2XmnrCzxM2gYMSivR-xsSjTAodP3XGo8R5Yh12ubyck0436tDtU9D38ba1fyiML4UGOY9WSM2BCQihs80SCwaZ7O8TL8_gY5OBiInY7K0gs5on-ujc-RKMbqDJSW8Kf3-dtf)

____

### Start trying to run paper R Code

```r
> library(neurohcp)
Error in library(neurohcp) : there is no package called ‘neurohcp’
```

____

from earlier:

```r
install.packages('fmri', dependencies = TRUE, repos='http://cran.rstudio.com/')
```

modifying above to below input:

```r
install.packages('neurohcp', dependencies = TRUE, repos='http://cran.rstudio.com/')
```

output:

```r
WARNING: Rtools is required to build R packages but is not currently installed. Please download and install the appropriate version of Rtools before proceeding:
```

____

#### TODO: Add / Check if where RTools installed, if path is correct


