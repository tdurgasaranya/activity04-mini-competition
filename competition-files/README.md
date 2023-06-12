Linear Regression Mini-competition
================

In this repository/directory you should see the following items:

- `README.md` - this document.
- `mini-competition.Rmd` - an empty RMarkdown file for you to keep track
  of your explorations/work and provide detailed notes.

## The “rules”

You and your team have been “hired” by GVSU’s [K-12
Connect](https://www.gvsu.edu/k12connect/) to assess factors that might
contribute to students’ academic success. Your primary goal is to
analyze data from the [Parent and Family Involvement
(PFI)](https://www.census.gov/programs-surveys/nhes.html) in Education
Surveys to provide insights on factors impacting K-12 education. More
specifically, you need to determine the “best” linear regression model
to provide recommendations to GVSU’s K-12 Connect on the impacts of
school choice and family engagement in school activities and homework.
This is a more broad research topic - keep in mind that you are fitting
linear regression models.

By **6:00 pm on Monday, June 19** you need to create a Google slide deck
that only contains a title slide (with only your team member’s names and
presentation title) and up to five additional slides. At least one
member from each team will provide a 5-minute maximum presentation of
these slides. Your slides should minimally include:

1.  A reflection of the process your team took to explore and decide on
    your final model (go beyond stating the steps you took - explain
    why), and
2.  Your final model and a description of how “good” it fits the data
    (you will need to explain how you determined “good-ness”).

Instead of asking questions after each presentation, we will hopefully
have time at the end to have a closing conversation. Also, to help
create slides quickly (so you can focus on the modeling task), we will
use Google Slides instead of creating [slides in
RMarkdown](https://rmarkdown.rstudio.com/lesson-11.html).

Upload your slides to this Google folder by the deadline:
<https://drive.google.com/drive/folders/1kgG_XZd0v8jB2vQueaAwKlt3Ns47HCeI?usp=sharing>

Presentation order will be randomly determined around 4:31 pm and edits
to your slides will not be allowed.

While this is a friendly competition, the main purpose is to share your
ideas/process and learn from your peers and their ideas/process. I
(Bradford) will determine the “best” group based *only* on your
presentation by assessing each of the following categories on a
“missing/attempted/sufficient”-scale (or 0/0.5/1 point-scale; I will be
very [stingy](https://www.merriam-webster.com/dictionary/stingy) with
awarding “1”s except for the last category):

- Clarity of your presentation,
- Soundness of your approach,
- Aesthetically pleasing presentation, and
- Maximum of 5-minutes and five slides + title (only 0 or 1 possible).

The best group based on these categories will receive a prize/gift.

### Data

GVSU’s K-12 Connect obtained data from the Parent and Family Involvement
(PFI) in Education dataset that is collected by the US Census Bureau for
the Department of Education. You are provided with two years worth of
data: 2016 and 2019. Note that each year is a separate tab in the data
file.

You can view, download, or upload using
[`{googlesheets4}`](https://googlesheets4.tidyverse.org/) from this url:

<https://docs.google.com/spreadsheets/d/1FbcKFJ6K0f5qAUOm5PGKxsR1f0Vw0CcG/edit#gid=1836780098>

This is a relatively large data file and I encourage you to use the
[Parent and Family Involvement
(PFI)](https://www.census.gov/programs-surveys/nhes.html) resource page
to answer questions about variables. You will likely need to do some
digging.

As this might be your first experience using academic data, here are
some examples. Note that the following is copied from This is
Statistic’s Fall Data Challenge announcement page. I am not providing
you a direct link because students’ presentations are included and I do
not want you to feel tempted to simply copy these. Also, their research
task is slightly different than yours - you must use a specific
statistical method while they did not need to. Happy to provide you with
a direct link after the competition.

### In the News

Today’s students will lead the future, so it’s no wonder the question of
how to advance their success is a popular topic in media coverage. With
the recent years of remote and hybrid learning, and many returning to
in-person classrooms, interest in the topic has surged.

Here are some recent headlines that highlight the status of familial
involvement in their children’s K-12 education:

K-12 Dive: [Parents encouraged to talk to schools about students’ math
progress](https://www.k12dive.com/news/parents-encouraged-to-talk-to-schools-about-students-math-progress/629353/)

The NWEA research organization found that student achievement in
mathematics for the 2021-2022 school year has significantly declined
since the pandemic. While schools explore different learning recovery
opportunities to boost academic achievement in K-12 students, one
campaign recommends the involvement of parents and guardians to help
practice their math skills with their children. This article explores
how parents can aid the improvement of their children’s student success.

Public School Review: [Parental Involvement is Key to Student
Success](https://www.publicschoolreview.com/blog/parental-involvement-is-key-to-student-success)

Research has shown that reading at home can improve children’s reading
skills. This article shares how parental and guardian involvement in
their children’s K-12 education could have a positive impact on a
child’s academic performance and boost the morale of their teachers.

The 74: [The Biggest Blind Spot in Education: Parents’ Role in Their
Children’s
Learning](https://www.the74million.org/article/the-biggest-blind-spot-in-education-parents-role-in-their-childrens-learning/)

Family members can have a larger impact on a student’s public school
academic performance than teachers, according to this analysis. The 2020
national test results revealed the pandemic had a significant effect on
student education, leading to an overall decline in test scores in the
past decade. This article explores a connection to family involvement
for student performance.

### Tools & Research

For the 2022 Fall Data Challenge, students will apply their statistical
skills to analyze real-world K-12 educational experience data and
provide recommendations and insights supported by their analysis.

In addition to the provided PFI dataset, students have the option to
utilize additional datasets on the topic to inform their analysis. Here
are some examples of tools and resources that explore the topic from
different perspectives.

[NAEP Data Explorers](https://www.nationsreportcard.gov/ndecore/landing)

This dataset tool from the National Assessment of Educational Progress
(NAEP) and the National Center for Education Statistics provides results
and factors related to student education from The Nation’s Report Card
assessments throughout the years.

[The Urban Institute Data
Catalog](https://datacatalog.urban.org/search/type/dataset)

This collection of open data contributed by researchers and data
scientists of the Urban Institute allows individuals access to public
datasets that explore various societal issues.

## Suggestions to get started

- Make appropriate exploratory graphs and numerical summary tables for
  each variable and pairs of variables. Note that there are some
  qualitative variables in the dataset. Also, do you need to consider
  any potential interaction terms or polynomial terms?
- Explore if you need to do anything to ensure the reference groups
  listed in the variable description table.
- What methods have we explored to assess a model’s “good-ness”? As a
  group, come up with this list and what each tells us. In [Additional
  Methods](#additional-methods) below, I provide some further
  descriptive (i.e., not statistical inference focused) methods to check
  for “good-ness”.
- Fit your candidate models.
- Assess which of your candidates is “best”.

## Additional methods

The *ISL* text discusses some methods for checking a model’s “good-ness”
or adjusting for issues when checking the conditions for linear
regression models (i.e., Section 3.3.3). I briefly provide how to
implement or check for these *Potential Problems* (in order as presented
in the text), but remember that the text provides more detail with how
to interpret or know if these adjustments are necessary. Throughout this
section, I provide additional resources that I find useful.

You might have heard of the adjusted $R^2$, *Akaike information
criterion* (AIC), *Bayesian information criterion*, and *Mallow’s* $C_p$
model metrics before. We will explore these in more detail in Chapter 6
(Week 12).

### 1. Non-linearity of the data

If the *errors* display a pattern where linearity might be a concern,
you can transform variables to see if these “fix” this issue. Some
online documents that provide good overviews of transformations are:

- [Transformations: an
  introduction](http://fmwww.bc.edu/repec/bocode/t/transint.html) by
  Nicholas J. Cox, Durham University
- [A guide to Data
  Transformation](https://medium.com/analytics-vidhya/a-guide-to-data-transformation-9e5fa9ae1ca3)
  by Tim M. Schendzielorz
- [Lesson 9: Data
  Transformations](https://online.stat.psu.edu/stat501/lesson/9) by Penn
  State’s Department of Statistics

These would all be done in a data `mutate`-tion step (e.g., using your
`{dplyr}` skills). For example,

``` r
# add natural log transformation to existing dataset
data <- data %>%
  mutate(log_variable =  log(variable))
```

You would then use this transformed variable in your linear regression
model instead of the un-transformed variable.

### 2. Correlation of error terms

This should be an issue for these data and time-series is not an
expected topic for this course. However, for your project you might want
to extend your learning by performing a time-series analysis.

### 3. Non-constant variance of error terms

Transforming a variable (see above) could be one way to address this
issue. A more advanced method would be weighted least squares, but not
necessary for this model - another potential extending your learning
that is covered in Chapter 7.

### 4. Outliers

The `broom::augment` function contains a lot of additional metrics
related to assessing outliers. For example, the text mentions
*studentized residuals* which is the `.std.resid` column in the
resulting tibble from using this function.

You can also visually identify and highlight outliers (e.g.,
[`gghighlight::gghighlight`](https://yutannihilation.github.io/gghighlight/articles/gghighlight.html#gghighlight)
which combines a filtering flavor to point out specific values).

### 5. High leverage points

Again, the `broom::augment` function contains a lot of additional
metrics. The text mentions *leverage statistics* $h_i$ which is the
`.hat` column in the resulting tibble from using this function. You can
then use your `{dplyr}` skills to help you identify any extreme values
(e.g., see the text for how to calculate the suggested cutoff value).

This online document discusses outliers and high leverage points:

- [Lesson 9.1: Distinction Between Outliers and High Leverage
  Observations](https://online.stat.psu.edu/stat462/node/170/) by Drs
  Iain Pardoe, Laura Simon, and Derek Young of Penn State.

### 6. Collinearity

In addition to inspecting a correlation/scatterplot matrix (e.g.,
`GGally::ggpairs`), you can also compute the *variance inflation factor*
(VIF) for each predictor. To compute these values, explore
[`car::vif`](https://cran.r-project.org/web/packages/car/car.pdf#vif)
from Dr. John Fox (*emeritus*, McMaster University) *et al*.
