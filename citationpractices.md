





# knitr citationpractices manuscript
 * author of this file: Heather Piwowar, <hpiwowar@gmail.com>
 * license: CC0
 * Acknowledgements: thanks to Yihui Xie for knitr and Carl Boettiger for his clear examples of this literate programming framework. 
 * Generated on <code class="knitr inline">Mon Jul  9 16:35:34 2012</code>

<!---

To execute the R code in this file and embed the results in the text, I start R, set the working directory, then run the following:

    library(knitr)  
    knit("stats_knit_.md")

or, from the command line, to generate an html file:

    R -e "library(knitr); knit('citationpractices_knit_.md')"; pandoc --toc -r markdown -w html -H static/header.html citationpractices.md > citationpractices.html

The stats.html file can be viewed directly in a browser.
The images are stored in my Public Dropbox folder.

After pushing the .md files to GitHub, the stats.md file can also be viewed at [https://github.com/hpiwowar/citation11k/blob/master/analysis/stats.md](https://github.com/hpiwowar/citation11k/blob/master/analysis/stats.md) .

To extract the R code in a separate .R file called stats_knit_.R, run knit with tangle set to TRUE:

    R -e "library(knitr); knit('citationpractices_knit_.md', tangle=T)"
"""
-->









# Making data citation Count

We have a citation graph for papers.
Why do we need a citation graph for data? What would we do with it?

Cite as first class objects, track those citations.

## 1. What can data citation tracking do for us

Data citation tracking is needed to build a research infrastructure that:


### Encourages data archiving

Recognizing data as first-class trackable research objects will encourage researchers to make more datasets available.

Many calls for this:
- Nature biotech 27, 579 2009
- the one that cited plos one?
- Nature 361 168 2009

Authors claim that citation is important to them [Tenopir] and indeed evidence of a citation boost has been cited in many policies as motivation [cite citations?].  [also evo study?]

### Rewards collection, curation, and dissemination of useful data

Furthermore, if usage of datasets is tracked it give investigators incentive to maximize uses.  This will enourage naturally encourage best standards, metadata, documentation.  Aligns incentives.

### Includes all relevant contributors in reward structure

Data often has different investigator contributors than authors (would be interesting to look at in Dryad dataset).  In addition, also has different value-add contributors: data repository for example.  In some cases journal has contributed, in other cases hasn't.

Some data archives have attempted to determine value themselves, to make case to their funders.  Unforunately, as we discuss below, very time consuming and resource intensive!  For example, ORNL DAAC....

### Discovers associated datasets and researcher communities

Reward is only one readon to track data citations.  Other reasons is that it facilitates discovery of associated datasets.  A paper that cites two datasets is a valuable clue that perhaps someone who encounters the first dataset would also be interested in the second.  

"if you liked that dataset, you'll like this dataset" 

[is anyone doing this yet?]

### Filters for frequently used -- or neglected! -- datasets 

Scientists may want to filter datasets by the frequency of use.  Some scientists may be looking for dataset that are tried and true: those used often.  Others may be looking for overlooked datasets, those that haven't been used much with perhaps a great deal of unrealized value.

### Identifies analyses based on problematic datasets

Sometimes it turns out that a dataset has quality problems.  Whether intentionally faked data, an innocent mistake, or even just constantly improving quality standards, the result is the same: analyses built on data sometimes need reconsidered.  How can analyses based on a given dataset be found? 

http://onlinelibrary.wiley.com/doi/10.1111/j.1365-2044.2012.07128.x/abstract
http://arstechnica.com/science/2012/07/new-record-for-faking-data-set-by-japanese-researcher/


### Avoids harmful shoehorning

In an attempt to piggyback on the infrastructure and reward system for publishign rearch articles, several new and existing publishers have been lanching "data journals."  These typically expect a short description of a dataset and serve as a proxy citation to the dataset.

Relying on a system that shoehorns data into the existing journal system is a reasonable stop-gap measure, but not the best long term solution.  For example, a journal typically includes peer review, whereas most datasets are not peer reviewed before publication.  Journals have not excelled at structured metadata or APIs.  

Supporting data citations of datasets directly avoids moving datasets toward system that is likely not the best fit.

### Drives policy, funding, and tool requirements based on evidence

Finally, tracking data reuse allows policy makers, funders, and tool builders to know what has facilited reuse and what hasn't.  Real evidence is needed to inform decision about what kind of standards facilitate reuse, how much dat curation is necessary, whether embargoes strike an appropriate balance, and whether tool features are being used.  

Without this data we are running blind, and surely wasting money and time.

## 2. Current state and obstacles to improvement

### Awareness

### Encouragement and expectation

The primary focus in most fields is data that supports the findings in peer-reviewed journal publications.  We investigated a wide variety of sources for data citation policies that authors must comply with, from funders, repositories, and journals.  We found limited and variable guidance.  

Table:  regression information for which journals are most likely to have policies.  If we look into these further, we can see that journals with highest impact factors are most likely to have policies.  
Graph:  boxplot of journal impact factors, for “no policy, requests, requires” ?
Paragraph of results like in Nic’s ASIS&T poster abstract:  

Best practices are also in the self-interest of the journal..... to the extent that best practices lead to reuse and attribution and citations, everyone wins.

Table:  Data citation policies of Funders, Journal, Repositories.  Subdivide with line in between funders, journals, and repositories.  Columns:

* No policy for data citation (lists all funders with no policy, in alphabetical order)
* Mentions data citation (lists all funders that mention data citation, with exerpt in parantheses)
http://precedings.nature.com/documents/5452/version/1

We examined actual attribution practice by researchers.  Researchers are clearly mixing and matching different expectations in a very context sensitive manner.

### Agreement on best practices
granularity
versioning
table that shows the different combinations of how data is cited

consistency within Genbank conventions vs chaos elsewhere
some try to give attibuion by including author name, as an example

Discussion of data citation styles: Altman, King (2007); Lawrence et al. (2008); Green (2010); Starr and Gastl (2011)

### Existing problematic policies

journal citation restrictions


### Tracking tools

### Access to the literature to build tracking tools


## 3. What we want to Count

### Dataset-level metrics

### Project-level metrics 

### Repository impact story rather than Repository impact factor

### Reuses from outside the literature

### Reuses from outside academia

### Reuses of the reuses

### Impact flavour

## 4. Conclusion

A future where data attribution counts.
A future about *what kind* of contribution a dataset makes, not just a number.
Emerging data citation best practices are not yet supported by existing attribution tracking tools.  Agreement on policy and technical infrastructure must go hand in hand in order for benefits of reuse to be realized.
Data is the lifeblood of science, let’s give it the respect it deserves





