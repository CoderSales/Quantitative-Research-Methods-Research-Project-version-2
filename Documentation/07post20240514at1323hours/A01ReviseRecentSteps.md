# Revise Recent Steps

____

- Note: was stuck on trying to reproduce the legend at the end of paper

____

```r
> library(fmri)
> t <- seq(0, 30, 0.1) # from 0 to 30 secs, in increments of 100ms
> h <- fmri.stimulus(301, durations = c(0), onsets = c(1), TR = 0.1)
> plot(t, h, type = "l", lwd = 2, col = "red", xlab = "Time (secs)", ylab = "h(t)", main = "Hemodynamic Response Function")
> library(oro.nifti)
> temp <- file.path(tempdir(), "mni_colin27_1998_nifti.zip")
> colin.url <-
+     "http://packages.bic.mni.mcgill.ca/mni-models/colin27/mni_colin27_1998_nifti.zip"
> download.file(colin.url, dest = temp)
trying URL 'http://packages.bic.mni.mcgill.ca/mni-models/colin27/mni_colin27_1998_nifti.zip'
Error in download.file(colin.url, dest = temp) : 
  cannot open URL 'http://packages.bic.mni.mcgill.ca/mni-models/colin27/mni_colin27_1998_nifti.zip'
In addition: Warning messages:
1: In download.file(colin.url, dest = temp) :
  downloaded length 0 != reported length 0
2: In download.file(colin.url, dest = temp) :
  cannot open URL 'https://packages.bic.mni.mcgill.ca/mni-models/colin27/mni_colin27_1998_nifti.zip': HTTP status was '403 Forbidden'
> unzip(temp, exdir = tempdir())
Warning message:
In unzip(temp, exdir = tempdir()) : error 1 in extracting from zip file
> colin <- readNIfTI(file.path(tempdir(), "colin27_t1_tal_lin.nii"))
Error in readNIfTI(file.path(tempdir(), "colin27_t1_tal_lin.nii")) : 
  File(s) not found!
> mask <- readNIfTI(file.path(tempdir(), "colin27_t1_tal_lin_mask.nii"))
Error in readNIfTI(file.path(tempdir(), "colin27_t1_tal_lin_mask.nii")) : 
  File(s) not found!
> colin <- colin * mask
> origin <- c(x = 91, y = 126, z = 72)
> mni2xyz <- function(x) sweep(x, 2, as.double(origin), "+")
> 
> xyz2mni <- function(x) sweep(x, 2, as.double(origin), "-")
> layout(matrix(1:4, ncol = 2, byrow = TRUE),
+        heights = c(181, 217),
+        widths = c(181, 217))
> layout.show(4)
> center <- origin
> greys <- grey(1:max(colin) / max(colin))
> par(mar = c(2, 2, 2, 2))
> image(colin[, center["x"], ], col = greys) # Coronal
> image(colin[center["y"], , ], col = greys) # Sagittal
> image(colin[, , center["z"]], col = greys) # Axial
> plot.new() # Empty quadrant
```

____

Some issues in above code, but, 

at the end there are

the plots shown on page 8 of the paper

albeit without labels.

____

Reviewing this paper:

[Coordinate-Based Meta-Analysis of fMRI | Studies with R | by Andrea Stocco](https://journal.r-project.org/archive/2014/RJ-2014-020/RJ-2014-020.pdf)

____

![partiallyReproducedThreePlanesFromPageEight](/src/images/partiallyReproducedThreePlanesFromPageEight.png)

Figure above shows

a screenshot 

from RStudio of

partially Reproduced Three Planes From Page Eight

of paper.

____

Plotting the foci

p. 10 of paper

copy and paste this into Excel:

```Excel
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

____

Copy and paste from Excel:

```Excel
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

```r
> df<-read.delim("clipboard")
```

following paper combined with previous review documented here: [Documentation / ... / A01ReviewPaper.md](/Documentation/05post20240510at1748hours/A01ReviewPaper.md)


