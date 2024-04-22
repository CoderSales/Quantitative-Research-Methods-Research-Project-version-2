# Retry Format Command

(From previously documented error, taking all of command before final comma: )

```r
h <- fmri.stimulus(301, durations = c(0), # h(t) for instantaneous event at t=0, onsets = c(1), rt = 0.1)
```

output:

```r
+
```

_# # # # # # # # # # # # # # # # # # # # # # # # # # # # #

Try adding:

```r
onsets = c(1), rt = 0.1)
```

Error:

```r
Error in fmri.stimulus(301, durations = c(0), onsets = c(1), rt = 0.1) : 
  unused argument (rt = 0.1)
```