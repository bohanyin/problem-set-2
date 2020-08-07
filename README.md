# Fit a regression model predicting feelings toward Biden, and then implement a couple validation techniques to evaluate the original findings using the simple holdout approach and the bootstrap

## Joe Biden and Validation

[Joe Biden](https://en.wikipedia.org/wiki/Joe_Biden) was the 47th Vice President of the United States. He was the subject of [many memes](http://distractify.com/trending/2016/11/16/best-of-joe-and-obama-memes), [attracted the attention of Leslie Knope](https://www.youtube.com/watch?v=NvbMB_GGR6s), and [experienced a brief surge in attention due to photos from his youth](http://www.huffingtonpost.com/entry/joe-young-hot_us_58262f53e4b0c4b63b0c9e11).

The goal here is to fit a regression model predicting feelings toward Biden, and then implement a couple validation techniques to evaluate the original findings. The validation techniques include the simple holdout approach and the bootstrap.

#### The 2008 NES Data

The `nes2008.csv` data contains a paired down selection of features from the full [2008 American National Election Studies survey](http://www.electionstudies.org/). These data will allow you to test competing factors that may influence attitudes towards Joe Biden. The variables are coded as follows:

* `biden` - feeling thermometer ranging from 0-100. Feeling thermometers are a common metric in survey research used to gauge attitudes or feelings of "warmth" towards individuals and institutions. They range from 0-100, with 0 indicating extreme "coldness" and 100 indicating extreme "warmth."
* `female` - 1 if respondent is female, 0 if respondent is male
* `age` - age of respondent in years
* `educ` - number of years of formal education completed by respondent
* `dem` - 1 if respondent is a Democrat, 0 otherwise
* `rep` - 1 if respondent is a Republican, 0 otherwise

For this exercise we consider the following functional form,

$$Y = \beta_0 + \beta_{1}X_1 + \beta_{2}X_2 + \dots + \beta_{p}X_p  + \epsilon,$$

where $Y$ is the Joe Biden feeling thermometer, and $[X_1 \dots X_p]$ are the predictive features, including age, gender, education, Democrat, and Republican. The reason for including both `dem` and `rep` party affiliation features is to allow for capturing the preferences of Independents, which must be left out to serve as the baseline category, otherwise we would encounter perfect multicollinearity.
