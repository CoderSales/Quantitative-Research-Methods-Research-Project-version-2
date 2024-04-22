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

Workaround previously stated of:

removing `rt=0.1` in command.

____
