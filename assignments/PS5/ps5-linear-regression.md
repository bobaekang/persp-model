Problem set \#5: linear regression
================
MACS 30100 - Perspectives on Computational Modeling
**Due Monday February 13th at 11:30am**

-   [Describe the data (1 point)](#describe-the-data-1-point)
-   [Simple linear regression (2 points)](#simple-linear-regression-2-points)
-   [Multiple linear regression (2 points)](#multiple-linear-regression-2-points)
-   [Multiple linear regression model (with even more variables!) (3 points)](#multiple-linear-regression-model-with-even-more-variables-3-points)
-   [Interactive linear regression model (2 points)](#interactive-linear-regression-model-2-points)
-   [Submission instructions](#submission-instructions)
    -   [If you use R](#if-you-use-r)
    -   [If you use Python](#if-you-use-python)

![](https://s3.amazonaws.com/media.thecrimson.com/photos/2014/10/02/103651_1299339.jpg)

[Joe Biden](https://en.wikipedia.org/wiki/Joe_Biden) was the 47th Vice President of the United States. He was the subject of [many memes](http://distractify.com/trending/2016/11/16/best-of-joe-and-obama-memes), [attracted the attention of Leslie Knope](https://www.youtube.com/watch?v=NvbMB_GGR6s), and [experienced a brief surge in attention due to photos from his youth](http://www.huffingtonpost.com/entry/joe-young-hot_us_58262f53e4b0c4b63b0c9e11).

`biden.csv` contains a selection of variables from the [2008 American National Election Studies survey](http://www.electionstudies.org/) that allow you to test competing factors that may influence attitudes towards Joe Biden. The variables are coded as follows:

-   `biden` - feeling thermometer ranging from 0-100[1]
-   `female` - 1 if respondent is female, 0 if respondent is male
-   `age` - age of respondent in years
-   `dem` - 1 if respondent is a Democrat, 0 otherwise
-   `rep` - 1 if respondent is a Republican, 0 otherwise
-   `educ` - number of years of formal education completed by respondent
    -   `17` - 17+ years (aka first year of graduate school and up)

Describe the data (1 point)
===========================

Plot a histogram of `biden` with a binwidth of `1`. Make sure to give the graph a title and proper *x* and *y*-axis labels. In a few sentences, describe any interesting features of the graph.

Simple linear regression (2 points)
===================================

Estimate the following linear regression:

*Y* = *β*<sub>0</sub> + *β*<sub>1</sub>*X*<sub>1</sub>

where *Y* is the Joe Biden feeling thermometer and *X*<sub>1</sub> is age. Report the parameters and standard errors.

1.  Is there a relationship between the predictor and the response?
2.  How strong is the relationship between the predictor and the response?
3.  Is the relationship between the predictor and the response positive or negative?
4.  Report the *R*<sup>2</sup> of the model. What percentage of the variation in `biden` does `age` alone explain? Is this a good or bad model?
5.  What is the predicted `biden` associated with an `age` of 45? What are the associated 95% confidence intervals?
6.  Plot the response and predictor. Draw the least squares regression line.

Multiple linear regression (2 points)
=====================================

It is unlikely `age` alone shapes attitudes towards Joe Biden. Estimate the following linear regression:

*Y* = *β*<sub>0</sub> + *β*<sub>1</sub>*X*<sub>1</sub> + *β*<sub>2</sub>*X*<sub>2</sub> + *β*<sub>3</sub>*X*<sub>3</sub>

where *Y* is the Joe Biden feeling thermometer, *X*<sub>1</sub> is age, *X*<sub>2</sub> is gender, and *X*<sub>3</sub> is education. Report the parameters and standard errors.

1.  Is there a statistically significant relationship between the predictors and response?
2.  What does the parameter for `female` suggest?
3.  Report the *R*<sup>2</sup> of the model. What percentage of the variation in `biden` does age, gender, and education explain? Is this a better or worse model than the age-only model?
4.  Generate a plot comparing the predicted values and residuals, drawing separate smooth fit lines for each party ID type. Is there a problem with this model? If so, what?

Multiple linear regression model (with even more variables!) (3 points)
=======================================================================

Estimate the following linear regression:

*Y* = *β*<sub>0</sub> + *β*<sub>1</sub>*X*<sub>1</sub> + *β*<sub>2</sub>*X*<sub>2</sub> + *β*<sub>3</sub>*X*<sub>3</sub> + *β*<sub>4</sub>*X*<sub>4</sub> + *β*<sub>5</sub>*X*<sub>5</sub>

where *Y* is the Joe Biden feeling thermometer, *X*<sub>1</sub> is age, *X*<sub>2</sub> is gender, *X*<sub>3</sub> is education, *X*<sub>4</sub> is Democrat, and *X*<sub>5</sub> is Republican.[2] Report the parameters and standard errors.

1.  Did the relationship between gender and Biden warmth change?
2.  Report the *R*<sup>2</sup> of the model. What percentage of the variation in `biden` does age, gender, education, and party identification explain? Is this a better or worse model than the age + gender + education model?
3.  Generate a plot comparing the predicted values and residuals, drawing separate smooth fit lines for each party ID type. By adding variables for party ID to the regression model, did we fix the previous problem?

Interactive linear regression model (2 points)
==============================================

Let's explore this relationship between gender and Biden warmth more closely. Perhaps the effect of gender on Biden warmth differs between partisan affiliation. That is, not only do we need to account for the effect of party ID in our linear regression model, but that gender has a different effect for Democrats and Republicans. Democrats are already predisposed to favor Joe Biden and have warm thoughts about him, whereas Republicans are predisposed to dislike him. But because Biden is so charming, he can woo female Republicans better than male Republicans. This suggests an **interactive** relationship between gender and party ID.

Filter your dataset to remove any independent respondents (keeping only those who identify as Democrats or Republicans), and estimate the following linear regression:

*Y* = *β*<sub>0</sub> + *β*<sub>1</sub>*X*<sub>1</sub> + *β*<sub>2</sub>*X*<sub>2</sub> + *β*<sub>3</sub>*X*<sub>1</sub>*X*<sub>2</sub>

where *Y* is the Joe Biden feeling thermometer, *X*<sub>1</sub> is gender, and *X*<sub>2</sub> is Democrat. Report the parameters and standard errors.

1.  Estimate predicted Biden warmth feeling thermometer ratings and 95% confidence intervals for female Democrats, female Republicans, male Democrats, and male Republicans. Does the relationship between party ID and Biden warmth differ for males/females? Does the relationship between gender and Biden warmth differ for Democrats/Republicans?

Submission instructions
=======================

Assignment submission will work the same as earlier assignments. Submit your work as a pull request before the start of class on Monday. Store it in the same locations as you've been using. However the format of your submission should follow the procedures outlined below.

If you use R
------------

Submit your assignment as a single [R Markdown document](http://rmarkdown.rstudio.com/). R Markdown is similar to Juptyer Notebooks and compiles all your code, output, and written analysis in a single reproducible file.

If you use Python
-----------------

Either:

1.  Submit your assignment following the same procedures as required by Dr. Evans. Submit a Python script containing all your code, plus a $\\LaTeX$ generated PDF document with your results and substantive analysis.
2.  Submit your assignment as a single Jupyter Notebook with your code, output, and written analysis compiled there.

[1] Feeling thermometers are a common metric in survey research used to gauge attitudes or feelings of warmth towards individuals and institutions. They range from 0-100, with 0 indicating extreme coldness and 100 indicating extreme warmth.

[2] Independents must be left out to serve as the baseline category, otherwise we would encounter perfect multicollinearity.
