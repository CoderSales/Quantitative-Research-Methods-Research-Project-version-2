# A04PostMeeting

## Update R

[HOW TO UPDATE R ON RSTUDIO](https://www.listendata.com/2015/08/how-to-update-r-software.html)

```r
install.packages("installr")
library(installr)
updateR() 
```

____

`updateR()` is not progressing

____

[Upgrading R](https://www.r-statistics.com/tag/installr/#:~:text=There%20is%20also%20a%20step,the%20latest%20version%20of%20R).)

____

```r
install.packages("installr") # install 
setInternet2(TRUE) # only for R versions older than 3.3.0
installr::updateR() # updating R.
# If you wish it to go faster, run: installr::updateR(T)
```

____
