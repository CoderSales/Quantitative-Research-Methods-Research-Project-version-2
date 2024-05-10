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

```
h <- fmri.stimulus(301, durations = c(0), onsets = c(1), TR = 0.1)

plot(t, h, type = "l", lwd = 2, col = "red", xlab = "Time (secs)", ylab = "h(t)", main = "Hemodynamic Response Function")
```

____

