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


____

Retry:

Plan:

Without `rt = 0.1`:

```r
h <- fmri.stimulus(301, durations = c(0), # h(t) for instantaneous event at t=0, onsets = c(1), rt = 0.1)
```

```r
onsets = c(1))
```

____

Workaround of excluding onsets = c(1) worked.

Worked:

```r
> h <- fmri.stimulus(301, durations = c(0), # h(t) for instantaneous event at t=0, onsets = c(1), rt = 0.1)
+ onsets = c(1))
```

Note:

entered into RStudio as 2 separate lines:

the following prompted by `>`:

```r
h <- fmri.stimulus(301, durations = c(0), # h(t) for instantaneous event at t=0, onsets = c(1), rt = 0.1)
```

the following prompted by `+`, to complete the above command (assumed):

```r
onsets = c(1))
```
