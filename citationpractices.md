





# knitr citationpractices manuscript
 * author of this file: Heather Piwowar, <hpiwowar@gmail.com>
 * license: CC0
 * Acknowledgements: thanks to Yihui Xie for knitr and Carl Boettiger for his clear examples of this literate programming framework. 
 * Generated on <code class="knitr inline">Tue Jul 10 13:55:56 2012</code>

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

Also encourages early dissemination.  The earlier the data is published, the sooner it can begin attracting citations.

### Includes all relevant contributors in reward structure

Data often has different investigator contributors than authors (would be interesting to look at in Dryad dataset).  In addition, also has different value-add contributors: data repository for example.  In some cases journal has contributed, in other cases hasn't.

Some data archives have attempted to determine value themselves, to make case to their funders.  Unforunately, as we discuss below, very time consuming and resource intensive!  For example, ORNL DAAC....

### Alerts investigators of reanalyses

Without citation tracking it is difficult for investigators to receive notifications of reanalyses of a particular dataset.  This is important for  data collection investigators: the team that collected the data is often very interested to learn about and verify future analyses.  It is also important to investigators who may be in the midst of using a dataset in their own research: what are others doing with it?

Full-text search alerts are poor approximations for citation-based alerts.  Citation-based alerts based on citations of a paper describing data collection are also a poor solution, since reanalyses can get lost in the citation deluge received by very popular papers.  

### Discovers associated datasets and researcher communities

Reward is only one readon to track data citations.  Other reasons is that it facilitates discovery of associated datasets.  A paper that cites two datasets is a valuable clue that perhaps someone who encounters the first dataset would also be interested in the second.  

"if you liked that dataset, you'll like this dataset" 

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

Because the recommendations to cite datasets are relatively recent, most researchers were not trained or mentored in these practices.

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

For many fields and datatypes it seems appropriate to track data on the dataset or data package level.  "Dataset-level metrics" are analigous to "article-level metrics" now gaining ground for research papers.  

The specific level of granularity may differ for diferent fields and datatypes (data file, data package, data row).  A good rule of thumb might be to track data attribution at the highest level of abstraction with common methods of collection and contributing investigators and institutions.

### Project-level and grant-level metrics 

Some journals may fear that a move to attribute data reuse directly with the dataset will reduce attribution to original research articles.  Not unless warrented: in cases where data reuse investigators use data description and metadata from the research article associated with a dataset, they ought to be encouraged to also cite the article (see Dryad's data citation policy).

Some scholars have been worried this will be viewed as gratuitous citation collection.  This would only be true if the citations were naively added together and compared to citation rates without independent data and articles.  Instead, let's build a model that appropriately represents the impact of a whole project: project-level metrics, based on all of its component item-level impact metrics.

### Repository impact story rather than Repository impact factor

Several calls have been made for a "repository impact factor".  While it is important for repositories to measure the value they provide, trying to optimise for a high "impact factor" calculated the same way as the journal impact factor is likely to lead to decisions that are not optimised for efficient or effective research.  For example, it would encourage repositories to exclude datasets from niche areas or untested research fronts, in case these datsets drag down its citation impact average. 

A repository's impact story should instead be told as a more complex story of the types of reuse it has faciliated, as described below.  This can be done qualitatively, through visible success stories.  With thoughtful impact tracking, subtle impact patterns can also be captured and described quantitatively.

### Reuses from outside the literature

Discussion heretofore has focused on data citations in the published scholarly literature.  As scholarly discussion moves online and is captured by a wide variety of product types, evidence of impact may occur in a wide variety of fora.  For example, dataset metadata may cite other datasets.  Academics may bookmark datasets using general purposes bookmarking tools (i.e. delicious) or general-purpose reference managers (Mendeley and Zotero).  Datasets of interest may be the topic of blogs, tweets, and preprints.  The number of times a dataset has been viewed or downloaded is also interesting.  

These measurements are often called alternative metrics, or altmetrics.  

### Reuses from outside academia

Datasets may also be used outside of university researchers.  Reuse by students, journalists, policy makers, clinitians, startup companies, established industry leaders -- all of these uses are valuable and worth noting, particularly when the original data collection was collected with public money.  It is difficult to track these types of uses online, but unique identifiers and open resources begin to make it possible.

### Reuses of the reuses

Sometimes the best way to look at the value of something is to look at its second-order use:  Did  the metaanalysis which included the datset cause a significant change in healthcare practice?  How impactful was the blog post *about* the dataset?  

A limited version of this type of analysis is directly possible from a citation graph, the same way that PageRank or EigenFactor are based on linked networks.  These approaches ignore the issue of the role of the dataset in acheiving the second-order effect, so they must be used in concert with complementary information.  Nonetheless, this sort of information is key to understanding the true value of a resource. 

### Impact flavour

Finally, we want to do more than just measure numbers.  We want to assess *type*.

## 4. Conclusion

A future where data attribution counts.
A future about *what kind* of contribution a dataset makes, not just a number.
Emerging data citation best practices are not yet supported by existing attribution tracking tools.  Agreement on policy and technical infrastructure must go hand in hand in order for benefits of reuse to be realized.
Data is the lifeblood of science, let’s give it the respect it deserves.






