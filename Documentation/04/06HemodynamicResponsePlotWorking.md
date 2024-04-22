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
