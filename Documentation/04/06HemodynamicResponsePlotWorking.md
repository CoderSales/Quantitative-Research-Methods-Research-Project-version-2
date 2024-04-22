# Hemodynamic Response Plot Working

```r
> h <- fmri.stimulus(301, durations = c(0), # h(t) for instantaneous event at t=0, onsets = c(1), rt = 0.1)
+ onsets = c(1))
> plot(t, h, type = "l", lwd = 2, col = "red",
+      xlab = "Time (secs)", ylab = "h(t)", main = "Hemodynamic Response Function")
```

Note: line 2 of above is missing `rt = 0.1` from paper due to technical issue previously outlined.

![Screenshot of HemodynamicResponse](/src/images/Screenshot-2024-04-22-131522-HemodynamicResponse.png)
