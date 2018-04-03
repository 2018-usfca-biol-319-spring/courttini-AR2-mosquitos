# Analysis Report 2 on NEON mosquito dataset for BIOL 319
## Due as a pull request on Monday, April 16, 2017 before 11:59 pm

The **goals of this assignment** are twofold: 

1. to improve your skills in developing focused, testable ecological hypotheses that you can address using large datasets, and 
2. to have you continue to synthesize the data analysis techniques you have learned so far. 

To do so, you will conduct an analysis that is more complex, this time focusing on the population and community dynamics that you can address with a NEON mosquito dataset. You will continue to practice using R and RStudio to analyze and visualize ecological data, doing so in the context of a version-controlled workflow, and submitting your work as a Pull Request on GitHub.

**General overview:** Just like in previous assignments, you will do all your work for this assignment in the provided `Analysis.Rmd` file. It should use the existing code to read in and merge the two datasets, then use `dplyr` functions as needed to select subsets of that data, and then plot those data using the `ggplot` framework. Finally, you will need to describe the context for the results and interpret your findings in the context of background you read about each of the NEON regions and sites, which is [available here](http://www.neonscience.org/field-sites/field-sites-map/list). For example, [here's a description](http://www.neonscience.org/field-sites/field-sites-map/BART) of the Bartlett Experimental Forest (short ID: BART).

Please follow the instructions carefully and read them all before getting started.

This second analysis report assignment will be worth 50 points. Your report should end up being between 2000 and 3000 words long. To give you a sense for how long this is, think roughly 5-7 pages of text, single-spaced. You should feel free to reuse code and writing from your past assignments if they will help you support your argument. This analysis report should be largely a new report, however, since it is based on a new dataset. The grading breakdown will be as follows:

* 25 points - Completes all required steps, is well-written, sets up the approporiate context for your specific hypotheses, describes the methods you use in appropriate detail, uses visualization and statistics to test your hypotheses, and interprets the findings in the context of other relevent research.
* 5 points - R code chunks are appropriately commented, properly labeled, and well organized.
* 5 points - Appropriate use of git to version control the steps, including adding and committing the appropriate files at the specific steps below, and writing informative and appropriately formatted commit messages and an informative and appropriate pull request description.
* 5 points - Includes at least 10 citations for relevent peer-reviewed journal articles related to your hypotheses. By adding the citations to the `bibliography.bib` file, and then citing them in-text, when you knit the Rmd file an appropriate list of Sources Cited will be generated for you and added to the end of the rendered document. We have gone over how this works in class.
* 10 points - The final commit before the deadline passes Travis-CI checks (successful knitting and proper code style, details at the bottom of this README). Since Travis will only run on your code once you open a pull request (PR), feel free to open your PR well before the deadline to test it out.

You must submit your work as a Pull Request to the class organization ('2018-usfca-biol-319-spring') on GitHub by 11:59 pm on Monday, April 16 for full credit. Late assignments will not be accepted, since we will be peer reviewing each other's code after it is submitted.

Steps:

1. Fork this repository to your own GitHub account.
1. On your laptop, in RStudio, select File > New Project...
1. Choose 'Version Control', then 'git', then paste the URL from your fork and hit tab
1. This will autofill the project name, you can choose where this repository folder will be on your laptop
1. Select 'Open in New Session', then 'Create Project'
1. This should download the repository from GitHub and set up a new project for you in RStudio
1. Just like in the most recent previous assignments, we'll be working in the `Analysis.Rmd` file instead of an R script. So, just open the existing file (look for it in the file browser tab in the lower right-hand corner of RStudio). In this script, in addition to filling out each of the sections (Introduction, Methods, Results, Discussion), you will need to create a least 5 figures/tables. These will be different for each student, since you are all now working to create your own hypotheses. Don't present the same data in a figure and a table, just choose which of the two is more appropriate in order to make your argument. You can (and absolutely should!) reuse any code and text from previous assignments to complete this report. You can just copy and paste out of the files from past weeks or from class as needed. However, remember that it is critical that your report is driven by a focused set of hypotheses, and these should be creative and tied to the information available in the dataset. Don't just ask the same thing you did last time.
    * In your Rmd, you will need to incorporate the appropriate (labelled!) R code chunks to:
      * Use dplyr and ggplot functions to subset, visualize, and analyze the dataset.
      * Add R code chunks as necessary to apply appropriate statistical tests as necessary. You should report the type of test you used, the p-value it returned, and interpretation of what this p-value means about the data you plotted. We talked about how to do t-tests, ANOVAs, and regressions in class.
1. In the Introduction and Methods sections, you should include some background on the NEON project in general, the sites overall, and some additional information on the specific site or sites you are working with. The goal is to give a reader a sense of the diversity of ecosystem types that are represented and where they are located. In the methods, you should very briefly summarize how the data were collected (detailed info is available in the pdf files in the `data/documentation` folder). 
1. In the discussion section, the goal is for you to apply ecological thinking to explain the results of your hypothesis tests. As you interpret the results, think not only about the mosquitos that are present, but also about type of mammals found at each site, the vegetation that grows at each site, its climate, seasonal patterns, etc. Remember that in ecology, everything is connected!
1. Add and commit your Rmd file frequently as you work. Be sure to write [meaningful commit messages](https://chris.beams.io/posts/git-commit/) and a descriptive Pull Request title and description.
1. Knit your Rmd file to a github markdown document using the 'knit' button in RStudio and add/commit this md file and any generated figure files as well.
1. Push your commits back to your repository on GitHub. 
1. Open a pull request back to the class repository to submit your assignment. Make sure the Pull Request (PR) has a useful description of the changes you made. 20% of your points for this assignment will be based on your code passing the automated checks on Travis-CI. This will check for two things: that your Rmd file can be successfully knitted, and that your code follow proper style guidelines. If you want to check for any style errors while you are working on the code, you can install the 'lintr' package by typing the following at the console:

```r
install.packages("devtools")
devtools::install_github("jimhester/lintr")
```

and then whenever you want to check your code you can run at the R console (the command prompt) in RStudio:

```r
lintr::lint(filename = "Analysis.Rmd")
```

Don't hesistate to ask questions on Piazza as you work!

**NOTE:** There are some files in this repository that are used for automating testing.

##### Infrastructure for Automated Software Testing

- `.travis.yml`: a configuration file for automatically running [continuous integration](https://travis-ci.com) checks when you submit your pull request, to verify reproducibility of all `.Rmd` notebooks in the repo.  If all `.Rmd` notebooks can render successfully and pass linting (or code style and syntax checks), then the "Build Status" badge above will be green (`build success`), otherwise it will be red (`build failure`).  
- `.Rbuildignore`: a configuration file telling the build script which files to ignore.
- `DESCRIPTION`: a metadata file for the repository, based on the R package standard. Its main purpose here is as a place to list any additional R packages/libraries needed for any of the `.Rmd` files to run.
- `tests/render_rmds.R`: an R script that is run to execute the above described tests, rendering and linting all `.Rmd` notebooks.  
