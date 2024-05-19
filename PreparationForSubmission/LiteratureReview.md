# Literature Review

## Table of Contents

[Nomenclature](https://github.com/CoderSales/Quantitative-Research-Methods-Research-Project-version-1/blob/main/PreparationForSubmission/LiteratureReview.md#nomenclature)

[Background](https://github.com/CoderSales/Quantitative-Research-Methods-Research-Project-version-1/blob/main/PreparationForSubmission/LiteratureReview.md#background)

[RShiny](https://github.com/CoderSales/Quantitative-Research-Methods-Research-Project-version-1/blob/main/PreparationForSubmission/LiteratureReview.md#rshiny)

[Progress (Continued)](https://github.com/CoderSales/Quantitative-Research-Methods-Research-Project-version-1/blob/main/PreparationForSubmission/LiteratureReview.md#progress-continued)

[Development of Ideas](https://github.com/CoderSales/Quantitative-Research-Methods-Research-Project-version-1/blob/main/PreparationForSubmission/LiteratureReview.md#development-of-ideas)

[Potential for Future Work](https://github.com/CoderSales/Quantitative-Research-Methods-Research-Project-version-1/blob/main/PreparationForSubmission/LiteratureReview.md#potential-for-future-work)

[Application](https://github.com/CoderSales/Quantitative-Research-Methods-Research-Project-version-1/blob/main/PreparationForSubmission/LiteratureReview.md#application)

[Frequency Processing Idea](https://github.com/CoderSales/Quantitative-Research-Methods-Research-Project-version-1/blob/main/PreparationForSubmission/LiteratureReview.md#frequency-processing-idea)

[A comparison of Video and Audio Processing Requirements](https://github.com/CoderSales/Quantitative-Research-Methods-Research-Project-version-1/blob/main/PreparationForSubmission/LiteratureReview.md#a-comparison-of-video-and-audio-processing-requirements)

[Google Chrome Extension](https://github.com/CoderSales/Quantitative-Research-Methods-Research-Project-version-1/blob/main/PreparationForSubmission/LiteratureReview.md#google-chrome-extension)

[Note on Running Extension if Hosting Locally](https://github.com/CoderSales/Quantitative-Research-Methods-Research-Project-version-1/blob/main/PreparationForSubmission/LiteratureReview.md#note-on-running-extension-if-hosting-locally)

[Note on Andrea Stocco Paper](https://github.com/CoderSales/Quantitative-Research-Methods-Research-Project-version-1/blob/main/PreparationForSubmission/LiteratureReview.md#note-on-andrea-stocco-paper)

[Notes on John Muschelli Literature](https://github.com/CoderSales/Quantitative-Research-Methods-Research-Project-version-1/blob/main/PreparationForSubmission/LiteratureReview.md#notes-on-john-muschelli-literature)

[Coursera](https://github.com/CoderSales/Quantitative-Research-Methods-Research-Project-version-1/blob/main/PreparationForSubmission/LiteratureReview.md#coursera)

[AWS](https://github.com/CoderSales/Quantitative-Research-Methods-Research-Project-version-1/blob/main/PreparationForSubmission/LiteratureReview.md#aws)

[AWS S3 Client Package](https://github.com/CoderSales/Quantitative-Research-Methods-Research-Project-version-1/blob/main/PreparationForSubmission/LiteratureReview.md#aws-s3-client-package)

[EC2](https://github.com/CoderSales/Quantitative-Research-Methods-Research-Project-version-1/blob/main/PreparationForSubmission/LiteratureReview.md#ec2)

[Note on Theory of Machine Learning](https://github.com/CoderSales/Quantitative-Research-Methods-Research-Project-version-1/blob/main/PreparationForSubmission/LiteratureReview.md#note-on-theory-of-machine-learning)

[Linking this Project to Machine Learning](https://github.com/CoderSales/Quantitative-Research-Methods-Research-Project-version-1/blob/main/PreparationForSubmission/LiteratureReview.md#linking-this-project-to-machine-learning)

[Machine Learning | Python | Scikit learn](https://github.com/CoderSales/Quantitative-Research-Methods-Research-Project-version-1/blob/main/PreparationForSubmission/LiteratureReview.md#machine-learning--python--scikit-learn)

[Random Forest Classifier](https://github.com/CoderSales/Quantitative-Research-Methods-Research-Project-version-1/blob/main/PreparationForSubmission/LiteratureReview.md#random-forest-classifier)

[Random Forest Classifier | R | origins | Breiman | Fortran](https://github.com/CoderSales/Quantitative-Research-Methods-Research-Project-version-1/blob/main/PreparationForSubmission/LiteratureReview.md#random-forest-classifier--r--origins--breiman--fortran)

[R / python Random Forest comparison | origins](https://github.com/CoderSales/Quantitative-Research-Methods-Research-Project-version-1/blob/main/PreparationForSubmission/LiteratureReview.md#r--python-random-forest-comparison--origins)

## Nomenclature

ERP = event-related brain potential

ERF = event-related magnetic field

ANOVA = Analysis of Variance

## Background

I began this Research Project by considering a few ideas.

One was to use the R Programming Language for some statistical computation.

Another was to try to combine R with another programming language.

The first idea here was to try to incorporate Java with R.

I started learning Java last semester and R this semester.

There is some documentation for combining Java and R.

However, after a recommendation by two different lecturers, one in Political Science and the other the Quantitative Research Methods Module Director Dr. James Sweeney, I decided to use RShiny.

The first step in the process was downloading and installing R.

The next step was to get RStudio running, from the Posit webpage, for which I was grateful to Dr. Sweeney for answering questions I had in this regard.

Then I got RShiny running.

### RShiny

#### Software Framework

RShiny is a frontend framework for presenting analysis done using R visually in a webpage.

## Progress (Continued)

For RShiny I completed at least 2 introductory tutorials.

The first allowed for a Web App to run from a single file.

The second allowed for two files to run the website, an app.r file and a server.r file.  This configuration is compatible with the client-server Web paradigm.

There was a step to use RServer, which I made some inroads into also.

____

### Development of Ideas

One idea for this project was to try to use some sort of frequency processing on EEG brain wave data.  On discussion Dr. Sweeney emphasised the importance of simplicity and clear focus with the project.  To that end it was important to use something that would be achievable in the timeframe.  Instead of trying to use EEG data, perhaps brain images may be easier to work with.  I noticed that one approach with handling images is to lower the resolution, in order to simplify the process of extracting meaning.  Another simplification proposed by Dr. Sweeney was to focus on edge detection for simpler shapes.  Noted issues for fMRI images were the complexity.  Dr. Sweeney pointed out that these are essentially numerous cross section images of the brain, and therefore, the processing needs can be challenging.   From this and consultation with literature, sources were found to deal with this.  Amazon Web Services allows processing using their servers, S3 buckets.  I accessed a public dataset to this end and set up an EC2 (Elastic Compute) instance.

I was able to run some analyses using AWS and the fmri R-Package.  Other related R packages were oro.nifti, and neruohcp. 

One related source was the Human Connectome Project (HCP).

From the Documentation folder in this GitHub repository [here](https://github.com/CoderSales/Quantitative-Research-Methods-Research-Project-version-1/blob/main/Documentation/09on20240516at1111hours/A04TryToApplyGraphingFromFmriPaperToHCP.md): the following:

____

One idea was to try to combine the following: 

- `fmri` paper: [Coordinate-Based Meta-Analysis of fMRI | Studies with R | by Andrea Stocco](https://journal.r-project.org/archive/2014/RJ-2014-020/RJ-2014-020.pdf), documented in this repository here: [A01ReviewPaper.md](/Documentation/05post20240510at1748hours/A01ReviewPaper.md), 

- HCP webpage: [Getting Data from the Human Connectome Project (HCP)](https://cran.r-project.org/web/packages/neurohcp/vignettes/hcp.html), 

    -    ( which refers to: [Public Connectome Data](https://db.humanconnectome.org/) )

    , and

- [AWS S3 Client Package](https://cran.r-project.org/web/packages/aws.s3/readme/README.html)

____


### Potential for Future Work

The next step may be to use the neuroconductor package.  I signed up for a Coursera course on this, however, this will not feature much in this project due to my timing for signup coming towards the end of the project.

### Application

From discussion with Dr Sweeney, there may be a subgroup of Statistics Researchers who do not use R but could benefit.  An Application of this Research could address this, potentially.  The RShiny Web-based Graphical User Interface could provide a positive user experience for those not currently using R, who are doing Quantitative Analysis.

I feel this is analogous to the argument made by [Breiman, L. (2001) Statistical Modeling: The Two Cultures, Statistical Science, 2001, Vol. 16, No. 3, 199–231, available: https://www-jstor-org.glucksman.idm.oclc.org/stable/2676681?sid=primo [accessed: 19-May-2024].](https://www-jstor-org.glucksman.idm.oclc.org/stable/2676681?sid=primo), that "there are two cultures in the use of statistical modeling to reach conclusions from data", in that, there are different schools of thought on how to approach research generally, and different fields have different strengths.

### Frequency Processing Idea

One of the difficulties inherent in dealing with sound and waves is the relatively high frequencies involved.

Also, it is often necessary to use Fast Fourier Transforms to convert time domain to frequency domain for processing including displaying the spectrum of frequences on an Equaliser, which must be calculated as sound is passed through the system.

#### A comparison of Video and Audio Processing Requirements

For comparison, 200 Hz is considered a very high refresh rate for a television, while, in sound 48 kHz is considered low to standard.

Therefore any compute done on audio has this complexity built in.

To that end, it has long been possible for consumers to use hardware and software capable of dealing with the rapid calculations involved in audio processing.

I wonder if some of the sound processing techniques from the music recording industry could be used somehow to find application in processing brain waves in EEG analysis.

____

### Google Chrome Extension

Another Project I worked on to support this one was a Google Extension to allow referencing in a way that would create a title with a link that could be pasted into a markdown file like this one and would automatically be formatted as a working link.  The Extension is based on one of the introductory tutorials on making Google Extensions for Google Chrome, called tab-manager.  During this Research Project I wrote (or at least modified) my first Google Chrome Extension.

Here is the repository: [javascript-chrome-extension-2](https://github.com/CoderSales/javascript-chrome-extension-2).

#### Note on Running Extension if Hosting Locally

I am hosting it locally using the "load unpacked" button on the [chrome://extensions](chrome://extensions) page in the Google Chrome Browser.  

The extension collects the web addresses of open pages (from a given Google Account, once the domain has been specified in the popup.js file), and assembles them in the Console.

The Console can be accessed by pinning the extension to the browser, clicking refresh from the [chrome://extensions](chrome://extensions) page,

clicking the (purple square) Extension in the top right of the Chrome Browser,

right clicking on the dropdown from the extension

Selecting Inspect

and then Clicking Console in the top of the Windows which opens,

and scrolling down to (on the right hand side of the page popup.js:82

copying all the formatted references 

and pasting into a markdown document.

These are the open tabs separated per window by horizontal rules.

____

### Note on Andrea Stocco Paper

I was able to run the code and reproduce the images from [Stocco, A. (2004) Coordinate-Based Meta-Analysis of fMRI
Studies with R, The R Journal Vol. 6/2, December 2014, available: https://journal.r-project.org/archive/2014/RJ-2014-020/RJ-2014-020.pdf.](https://journal.r-project.org/archive/2014/RJ-2014-020/RJ-2014-020.pdf) except for the last line on page 13, before the Summary whereby running the display legend command gave an error instead of the legend.

____

### Notes on John Muschelli Literature

I ran this basic installation and setup page for Getting Started with neurohcp: [Getting Data from the Human Connectome Project (HCP) | John Muschelli | 2020-10-14](https://cran.r-project.org/web/packages/neurohcp/vignettes/hcp.html).

- Note: This site features the neurohcp package and uses neuroconductor.org as the source domain.

#### Coursera

[Introduction to Neurohacking In R](https://www.coursera.org/learn/neurohacking)

- John Muschelli features on the Coursera course.

____

## AWS

### AWS S3 Client Package

[AWS S3 Client Package](https://cran.r-project.org/web/packages/aws.s3/readme/README.html)

From the above site: "aws.s3 is a simple client package for the Amazon Web Services (AWS) Simple Storage Service (S3) REST API."

### EC2

[Amazon EC2](https://aws.amazon.com/ec2/)

From the Amazon EC2 website: "Amazon Elastic Compute Cloud (Amazon EC2) offers the broadest and deepest compute platform".

Having access to large scale processing is one potential approach to address the issue of how to deal with the complexity of fmri images.

## Note on Theory of Machine Learning

### Linking this Project to Machine Learning

Although development herein was experimental, issues involved would include: machine learning for edge detection.

### Machine Learning | Python | Scikit learn

Scikit learn is a python based package for doing machine learning.  

#### Random Forest Classifier

Here is the documentation page for the Random Forest Classifier: [sklearn.ensemble.RandomForestClassifier](https://scikit-learn.org/stable/modules/generated/sklearn.ensemble.RandomForestClassifier.html).

Random Forest Classifiers are sets of Decision Trees, where Hyper parameter tuning is applied to do high level manipulation of the way the model makes decisions based on the many parameters in the dataset.

One issue here would be that :

#### Random Forest Classifier | R | origins | Breiman | Fortran

Although that is an example of a python package, an analogous R package would be:

[randomForest: Breiman and Cutler's Random Forests for Classification and Regression](https://cran.r-project.org/web/packages/randomForest/index.html) which is "based on Breiman (2001)".

##### R / python Random Forest comparison | origins

I feel the python version has nice documentation, in that it describes the model succinctly.

However, it is also interesting to see that the R Docummentation clearly identifies that Breiman was involved in origins of the idea, originally in Fortran, and makes reference to the site: [Random Forests | Leo Breiman and Adele Cutler](https://www.stat.berkeley.edu/~breiman/RandomForests/) which identifies that Random Forests are a trademark (TM) of Leo Breiman and Adele Cutler.

Here is the R Reference Manual for the Random Forest package [Package ‘randomForest’](https://cran.r-project.org/web/packages/randomForest/randomForest.pdf).

____

## Search

## Machine Learning fmri images

Google Scholar Search String: [Machine Learning fmri images](https://scholar.google.com/scholar?hl=en&as_sdt=0%2C5&q=Machine+Learning+fmri+images&btnG=)

Result: [Fan, Y., Shen, D., and Davatzikos, C. (2006) Detecting Cognitive States from fMRI Images by Machine Learning and Multivariate Classification, Conferences >2006 Conference on Computer V... available: https://ieeexplore.ieee.org/abstract/document/1640530?casa_token=Cjz0bJxV6CYAAAAA:NybNn_T-fvHKkzm2oI1330BQgT2FN9m28OIIK8QI4o1r1EZLtnqaHbN9OUPSvR6KLcIyGPVT [accessed: 20-05-2024].](https://ieeexplore.ieee.org/abstract/document/1640530?casa_token=Cjz0bJxV6CYAAAAA:NybNn_T-fvHKkzm2oI1330BQgT2FN9m28OIIK8QI4o1r1EZLtnqaHbN9OUPSvR6KLcIyGPVT)

The above paper talks about: "mass-univariate analysis techniques".

### mass-univariate analysis techniques

Google Search String: [mass-univariate analysis techniques](https://www.google.com/search?q=mass-univariate+analysis+techniques&sourceid=chrome&ie=UTF-8)

Result: [Groppe, D., M., Urbach, T., P. and Kutas, M. (2011) Mass univariate analysis of event-related brain potentials/fields I: A critical tutorial review, Psychophysiology. 2011 Dec; 48(12): pp. 1711–1725.(edited form), 2011 Sep 6. (online), avaialble: https://www.ncbi.nlm.nih.gov/pmc/articles/PMC4060794/ / doi: 10.1111/j.1469-8986.2011.01273.x [accessed 20-05-2024].](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC4060794/)

The above abstract mentions that: "Event-related potentials (ERPs) and magnetic fields (ERFs) are typically analyzed via ANOVAs on mean activity in a priori windows."  It mentions that: "Mass univariate analyses complement and, at times, obviate traditional analyses."  It reviews "this approach as applied to ERP/ERF data".

"In this article, we consider in depth one type of approach, *mass univariate analyses*", "in which a large number of univariate tests, e.g., t-tests, can be properly used to compare ERPs/ERFs at an exhaustive number of time points and scalp locations."

## References


### Conferences

[Fan, Y., Shen, D., and Davatzikos, C. (2006) Detecting Cognitive States from fMRI Images by Machine Learning and Multivariate Classification, Conferences >2006 Conference on Computer V... available: https://ieeexplore.ieee.org/abstract/document/1640530?casa_token=Cjz0bJxV6CYAAAAA:NybNn_T-fvHKkzm2oI1330BQgT2FN9m28OIIK8QI4o1r1EZLtnqaHbN9OUPSvR6KLcIyGPVT [accessed: 20-05-2024].](https://ieeexplore.ieee.org/abstract/document/1640530?casa_token=Cjz0bJxV6CYAAAAA:NybNn_T-fvHKkzm2oI1330BQgT2FN9m28OIIK8QI4o1r1EZLtnqaHbN9OUPSvR6KLcIyGPVT)

### Journals Articles / Papers

[Groppe, D., M., Urbach, T., P. and Kutas, M. (2011) Mass univariate analysis of event-related brain potentials/fields I: A critical tutorial review, Psychophysiology. 2011 Dec; 48(12): pp. 1711–1725.(edited form), 2011 Sep 6. (online), avaialble: https://www.ncbi.nlm.nih.gov/pmc/articles/PMC4060794/ / doi: 10.1111/j.1469-8986.2011.01273.x [accessed 20-05-2024].](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC4060794/)

#### cran.r-project | Papers

[Coordinate-Based Meta-Analysis of fMRI | Studies with R | by Andrea Stocco](https://journal.r-project.org/archive/2014/RJ-2014-020/RJ-2014-020.pdf)

### Webpages

[Random Forests | Leo Breiman and Adele Cutler](https://www.stat.berkeley.edu/~breiman/RandomForests/)

#### cran.r-project | Documentation

[randomForest: Breiman and Cutler's Random Forests for Classification and Regression](https://cran.r-project.org/web/packages/randomForest/index.html)

[Getting Data from the Human Connectome Project (HCP)](https://cran.r-project.org/web/packages/neurohcp/vignettes/hcp.html)

#### AWS

[AWS S3 Client Package](https://cran.r-project.org/web/packages/aws.s3/readme/README.html)

[Amazon EC2](https://aws.amazon.com/ec2/)

#### GitHub

##### This Project

[Literature Review](https://github.com/CoderSales/Quantitative-Research-Methods-Research-Project-version-1/edit/main/PreparationForSubmission/LiteratureReview.md)

[Quantitative Research Methods Research Project version 1](https://github.com/CoderSales/Quantitative-Research-Methods-Research-Project-version-1/)
