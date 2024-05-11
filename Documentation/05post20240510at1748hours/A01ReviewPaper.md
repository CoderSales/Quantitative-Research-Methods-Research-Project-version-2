# A01 Review Paper

____

Review this paper:

[Coordinate-Based Meta-Analysis of fMRI | Studies with R | by Andrea Stocco](https://journal.r-project.org/archive/2014/RJ-2014-020/RJ-2014-020.pdf)

____

redo code from half way through: [ 04pre20240510at1747hours / 06HemodynamicResponsePlotWorking.md ](/Documentation/04pre20240510at1747hours/06HemodynamicResponsePlotWorking.md)

( <kbd>Ctrl</kbd> <kbd>F</kbd> search for this string: 

Fix: change rt or RT to TR:

)

Code:

```r
h <- fmri.stimulus(301, durations = c(0), onsets = c(1), TR = 0.1)

plot(t, h, type = "l", lwd = 2, col = "red", xlab = "Time (secs)", ylab = "h(t)", main = "Hemodynamic Response Function")
```

____

Let us take the following example where we have data in an Excel sheet that we want to import into RStudio:

Select and copy the required data using either the copy option or the shortcut CTRL+C to import the required data. Then, return to RStudio and use the following command to save and load data in R in a dataframe named “df”:

```r
df<-read.delim("clipboard")
```

After running this command, the data in the clipboard will be saved in the “df” dataframe. Let us verify the data by printing the first few rows using the “head” function:


```r
head(df)
```

```r
df1 <- read.delim("clipboard", sep = " ")
```

```r
head(df1)
```

[Top 3 Ways to Import Data into R using Copy and Paste](https://www.analyticsvidhya.com/blog/2023/03/top-3-ways-to-import-data-into-r-using-copy-and-paste/#:~:text=To%20paste%20data%20as%20a,shortcut%20ctrl%20%2B%20shift%20%2B%20t.)

____


Steps:

- Copy in dataframe from paper to Excel 

- Copy dataframe again

```r
df<-read.delim("clipboard")
```

```r
head(df)
```


```r
df1 <- read.delim("clipboard", sep = " ")
```

head(df1)

[how to paste  a data frame into r](https://www.google.com/search?q=how+to+paste++a+data+frame+into+r&newwindow=1&sca_esv=b2746cf197726f04&sca_upv=1&sxsrf=ADLYWIL-w_P6lD0H3ACbr3FO2jSYryvQng%3A1715372313629&ei=GYE-ZqP0JYvcxc8PmNaTgAI&ved=0ahUKEwjj5KTr84OGAxULbvEDHRjrBCAQ4dUDCBA&uact=5&oq=how+to+paste++a+data+frame+into+r&gs_lp=Egxnd3Mtd2l6LXNlcnAiIWhvdyB0byBwYXN0ZSAgYSBkYXRhIGZyYW1lIGludG8gcjIKECEYoAEYwwQYCkiuD1DXBFiKDXACeAGQAQCYAXmgAbgEqgEDNC4yuAEDyAEA-AEBmAIIoALeBMICChAAGLADGNYEGEfCAggQABiABBiiBJgDAIgGAZAGCJIHAzYuMqAH1RY&sclient=gws-wiz-serp)

[R – as.data.frame() Function Example](https://www.geeksforgeeks.org/convert-an-object-to-data-frame-in-r-programming-as-data-frame-function/)

[store to a data frame object in r](https://www.google.com/search?q=store+to+a+data+frame+object+in+r&oq=store+to+a+data+frame+object+in+r&gs_lcrp=EgZjaHJvbWUyBggAEEUYOTIHCAEQIRigAdIBCDc0MjZqMGo3qAIIsAIB&sourceid=chrome&ie=UTF-8)

[WIAS-BERLIN/fmri](https://github.com/WIAS-BERLIN/fmri)

They are the open tabs at the moment for making this part work.

[works to the top of page 7 of this paper now](https://journal.r-project.org/archive/2014/RJ-2014-020/RJ-2014-020.pdf)

____

Relevant code paste from RStudio:

```r
> df<-read.delim("clipboard")
> head(df)
            x.y.z.Study.Type
1      1 -30 35 8 Cole Words
2 2 -46 7 21 Harstra Objects
3     3 -40 8 36 Ruge Shapes
4     4 36 12 54 Ruge Shapes
5    5 -48 28 32 Ruge Shapes
6     6 44 32 32 Ruge Shapes
> df1 <- read.delim("clipboard", sep = " ")
> head(df1)
    x  y  z   Study    Type
1 -30 35  8    Cole   Words
2 -46  7 21 Harstra Objects
3 -40  8 36    Ruge  Shapes
4  36 12 54    Ruge  Shapes
5 -48 28 32    Ruge  Shapes
6  44 32 32    Ruge  Shapes
> foci <- df1
> head(foci)
    x  y  z   Study    Type
1 -30 35  8    Cole   Words
2 -46  7 21 Harstra Objects
3 -40  8 36    Ruge  Shapes
4  36 12 54    Ruge  Shapes
5 -48 28 32    Ruge  Shapes
6  44 32 32    Ruge  Shapes
> # Transforms the coordinates
> im.foci <- mni2xyz(foci[1:3])
> # Normalizes
> im.foci <- sweep(im.foci, 2, dim(colin), "/")
> image(colin[, center["y"], ], col = greys) # Coronal
> points(x = im.foci[,"x"], y = im.foci[,"z"], lwd = 2, col = "red")
> image(colin[center["x"], , ], col = greys) # Sagittal
> points(x = im.foci[,"y"], y = im.foci[,"z"], lwd = 2, col = "red")
> image(colin[, , center["z"]], col = greys) # Axial
> points(x = im.foci[,"x"], y = im.foci[,"y"], lwd = 2, col = "red")
> plot.new()
> 
> 
```
____

Legend workaround:

```r
legend(x = "center", legend = l.args, col = l.args$col, pch = l.args$pch)
```

[R - object not found error when it exists](https://stackoverflow.com/questions/58840141/r-object-not-found-error-when-it-exists)

Google Search: [Error: object 'xpd' not found r](https://www.google.com/search?q=Error%3A+object+%27xpd%27+not+found+r&newwindow=1&sca_esv=b2746cf197726f04&sca_upv=1&sxsrf=ADLYWII6jdUF1b8sx2M3NxVSd4VWbqa5LQ%3A1715386084178&ei=5LY-ZtXCCpqJ7NYPtYms2AU&ved=0ahUKEwjVxMyRp4SGAxWaBNsEHbUEC1sQ4dUDCBA&uact=5&oq=Error%3A+object+%27xpd%27+not+found+r&gs_lp=Egxnd3Mtd2l6LXNlcnAiH0Vycm9yOiBvYmplY3QgJ3hwZCcgbm90IGZvdW5kIHIyBRAhGKABMgUQIRigATIFECEYoAEyBRAhGKABSNoUUOsGWMQKcAF4AZABAJgBwAGgAbUCqgEDMC4yuAEDyAEA-AEBmAIDoALTAsICChAAGLADGNYEGEfCAgcQIxiwAhgnwgIHEAAYgAQYDcICCBAAGAgYDRgewgILEAAYgAQYhgMYigXCAggQABiABBiiBJgDAIgGAZAGCJIHBTEuMS4xoAe3Dg&sclient=gws-wiz-serp)

____

[legend {graphics} | R Documentation | Add Legends to Plots](https://stat.ethz.ch/R-manual/R-patched/library/graphics/html/legend.html)

____
