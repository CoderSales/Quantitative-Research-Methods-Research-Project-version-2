# Deployed Web App

[demo Web App](https://codersales.shinyapps.io/demo/)

[Generated from](https://shiny.posit.co/r/articles/share/shinyapps/?_gl=1*1yfxfd8*_ga*NTg0NjIzNjkwLjE3MTMxODE3ODA.*_ga_HXP006LBGY*MTcxMzE4MTc3OS4xLjEuMTcxMzE4Mjk4OC4wLjAuMA..)

![Deployed Image](/src/images/Screenshot-2024-04-15-140618-DeployedImage.png)

____

to change instance type (amount of memory that the deployed app takes) use :

```r
rsconnect::configureApp("APPNAME", size="small")
```
