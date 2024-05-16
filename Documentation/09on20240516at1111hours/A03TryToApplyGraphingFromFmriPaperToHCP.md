# Try to Apply Graphing from fMRI Paper to HCP

[Back to README](/)

____

Update:

Try applying HCP progress to:

AWS S3 Client Package [README](https://cran.r-project.org/web/packages/aws.s3/readme/README.html)

____

```r
library("aws.s3")
```

Output:

```r
Attaching package: ‘aws.s3’

The following object is masked from ‘package:neurohcp’:

    bucketlist
```

```r
bucketlist()
```

____

Setup AWS

____

```r
get_bucket(bucket = '1000genomes')
```

____
