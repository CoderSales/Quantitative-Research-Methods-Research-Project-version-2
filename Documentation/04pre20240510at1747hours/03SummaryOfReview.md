#  Summary of Review

## Done

- Reference: [Installing Rtools44](https://cran.r-project.org/bin/windows/Rtools/rtools44/rtools.html)

- Active Download Link: [[Active linked Download of the] Rtools44 installer](https://cran.r-project.org/bin/windows/Rtools/rtools44/files/rtools44-6104-6039.exe) already installed.

- Add

```bash
C:\rtools44
```

to `Windows > System Variables > Path`.

- Solved RTools Warning

____


## Next

```r
h <- fmri.stimulus(301, durations = c(0), # h(t) for instantaneous event at t=0,
onsets = c(1), rt = 0.1), # Sampled at TR = 0.1 secs
```
