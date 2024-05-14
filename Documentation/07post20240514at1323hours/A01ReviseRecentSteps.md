# Revise Recent Steps

____

- Note: was stuck on trying to reproduce the legend at the end of paper

____

```r
library(fmri)
t <- seq(0, 30, 0.1) # from 0 to 30 secs, in increments of 100ms
h <- fmri.stimulus(301, durations = c(0), onsets = c(1), TR = 0.1)
plot(t, h, type = "l", lwd = 2, col = "red", xlab = "Time (secs)", ylab = "h(t)", main = "Hemodynamic Response Function")
library(oro.nifti)
temp <- file.path(tempdir(), "mni_colin27_1998_nifti.zip")
colin.url <-
+     "https://packages.bic.mni.mcgill.ca/mni-models/colin27/mni_colin27_1998_nifti.zip"
download.file(colin.url, dest = temp)
```

Note:

editted from this:

http://packages.bic.mni.mcgill.ca/mni-models/colin27/mni_colin27_1998_nifti.zip

to this:

https://packages.bic.mni.mcgill.ca/mni-models/colin27/mni_colin27_1998_nifti.zip

output:

ignore thanks to correction above:

```r
trying URL 'http://packages.bic.mni.mcgill.ca/mni-models/colin27/mni_colin27_1998_nifti.zip'
Error in download.file(colin.url, dest = temp) : 
  cannot open URL 'http://packages.bic.mni.mcgill.ca/mni-models/colin27/mni_colin27_1998_nifti.zip'
In addition: Warning messages:
1: In download.file(colin.url, dest = temp) :
  downloaded length 0 != reported length 0
2: In download.file(colin.url, dest = temp) :
  cannot open URL 'https://packages.bic.mni.mcgill.ca/mni-models/colin27/mni_colin27_1998_nifti.zip': HTTP status was '403 Forbidden'
```

Correction:

```r
colin.url <- "https://packages.bic.mni.mcgill.ca/mni-models/colin27/mni_colin27_1998_nifti.zip"
```


```r
unzip(temp, exdir = tempdir())
```

corrections mean the following Warning message no longer applies:

output:

```r
Warning message:
In unzip(temp, exdir = tempdir()) : error 1 in extracting from zip file
```

colin <- readNIfTI(file.path(tempdir(), "colin27_t1_tal_lin.nii"))

output:

```r
Error in readNIfTI(file.path(tempdir(), "colin27_t1_tal_lin.nii")) : 
  File(s) not found!
```

correction of above:

once downloaded

manually unzip and save to a folder called temp.

____

Then to correct next issue:

create pathToFile variable

pathToFile <- and put path to file in ""

then run the following

replacing `file.path(tempdir()`....

with: `file.path(pathToFile`....

```r
mask <- readNIfTI(file.path(tempdir(), "colin27_t1_tal_lin_mask.nii"))
```

like this:

```r
mask <- readNIfTI(file.path(pathToFile, "colin27_t1_tal_lin_mask.nii"))
```

fixes the following:

output:

```r
Error in readNIfTI(file.path(tempdir(), "colin27_t1_tal_lin_mask.nii")) : 
  File(s) not found!
```

```r
colin <- colin * mask
origin <- c(x = 91, y = 126, z = 72)
mni2xyz <- function(x) sweep(x, 2, as.double(origin), "+")

xyz2mni <- function(x) sweep(x, 2, as.double(origin), "-")
layout(matrix(1:4, ncol = 2, byrow = TRUE),
+        heights = c(181, 217),
+        widths = c(181, 217))
layout.show(4)
center <- origin
greys <- grey(1:max(colin) / max(colin))
par(mar = c(2, 2, 2, 2))
image(colin[, center["x"], ], col = greys) # Coronal
image(colin[center["y"], , ], col = greys) # Sagittal
image(colin[, , center["z"]], col = greys) # Axial
plot.new() # Empty quadrant
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

____

Some data wrangling / iterative attempts required here.

```r
> df<-read.delim("clipboard")
> foci <- df
> head(foci)
[1] x.y.z.Study.Type.1..30.35.8.Cole.Words.2..46.7.21.Harstra.Objects.3..40.8.36.Ruge.Shapes.4.36.12.54.Ruge.Shapes.5..48.28.32.Ruge.Shapes.6.44.32.32.Ruge.Shapes.7..40.32.16.Ruge.Shapes.8..40.44.8.Ruge.Shapes.9.40.40.16.Ruge.Shapes.10..32.20..4.Ruge.Shapes.11.32.28..4.Ruge.Shapes.12..44.48..8.Stocco.Numbers
<0 rows> (or 0-length row.names)
> df1 <- read.delim("clipboard", sep = " ")
> foci <- df1
> head(foci)
 [1] x        y        z        Study    Type     X1       X.30     X35      X8       Cole     Words    X2       X.46     X7       X21      Harstra  Objects 
[18] X3       X.40     X8.1     X36      Ruge     Shapes   X4       X36.1    X12      X54      Ruge.1   Shapes.1 X5       X.48     X28      X32      Ruge.2  
[35] Shapes.2 X6       X44      X32.1    X32.2    Ruge.3   Shapes.3 X7.1     X.40.1   X32.3    X16      Ruge.4   Shapes.4 X8.2     X.40.2   X44.1    X8.3    
[52] Ruge.5   Shapes.5 X9       X40      X40.1    X16.1    Ruge.6   Shapes.6 X10      X.32     X20      X.4      Ruge.7   Shapes.7 X11      X32.4    X28.1   
[69] X.4.1    Ruge.8   Shapes.8 X12.1    X.44     X48      X.8      Stocco   Numbers 
<0 rows> (or 0-length row.names)
```


```r
# Transforms the coordinates
im.foci <- mni2xyz(foci[1:3])

# Normalizes
im.foci <- sweep(im.foci, 2, dim(colin), "/")
image(colin[, center["y"], ], col = greys) # Coronal
points(x = im.foci[,"x"], y = im.foci[,"z"], lwd = 2, col = "red")
```

Assume errors no longer a factor from here on (since sorted folder file and dataframe)

```r
Error in `[.data.frame`(im.foci, , "x") : undefined columns selected
```

```r
image(colin[center["x"], , ], col = greys) # Sagittal
points(x = im.foci[,"y"], y = im.foci[,"z"], lwd = 2, col = "red")
```

```r
Error in `[.data.frame`(im.foci, , "y") : undefined columns selected
```

```r
image(colin[, , center["z"]], col = greys) # Axial
points(x = im.foci[,"x"], y = im.foci[,"y"], lwd = 2, col = "red")
```


```r
Error in `[.data.frame`(im.foci, , "x") : undefined columns selected
```

```r
im.foci <- mni2xyz(foci[1:3])
center <- round(colMeans(im.foci), 0)
# Normalizes
im.foci <- sweep(im.foci, 2, dim(colin), "/")
CF <- colMeans(im.foci)
```

____

![Screenshot-2024-05-14-200900-Redo-plots-from-clipboard](/src/images/Screenshot-2024-05-14-200900-Redo-plots-from-clipboard.png)

Figure above has Redo plots from clipboard Screenshot

____

Redo plots

with sorted

folder files and dataframe (foci)

____

gives:

____

![Screenshot-2024-05-14-at-210400-approximately-dotted-plots.png](/src/images/Screenshot-2024-05-14-at-210400-approximately-dotted-plots.png)

____

Redo plot 

with correct order:

![Screenshot-2024-05-14-at-210900-approximately-Redo-image-in-correct-order.png](/src/images/Screenshot-2024-05-14-at-210900-approximately-Redo-image-in-correct-order.png)

Figure above shows 3 planes with points

____

![Screenshot-2024-05-14-211500-approximately-Screenshot-with-3-planes-and-paper](/src/images/Screenshot-2024-05-14-211500-approximately-Screenshot-with-3-planes-and-paper.png)

Figure above shows 3 planes with later code in paper including the paper itself