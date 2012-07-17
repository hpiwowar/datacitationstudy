<!--roptions dev='png', fig.width=7, fig.height=7, tidy=FALSE, cache=FALSE, echo=TRUE, message=FALSE, warning=FALSE, autodep=TRUE, cache.path='/tmp/knitr-cache/' -->

<!--begin.rcode setup, echo=FALSE, cache=FALSE

# use imgur for hosting figures
# go to static/my_imgur_api_key.txt and add your own api key

upload_images = TRUE

if (upload_images) {
   #opts_knit$set(upload.fun = imgur_upload)
   opts_knit$set(upload.fun = function (file){
      sprintf("http://dl.dropbox.com/u/5485507/datacitation/datacitationstudy/%s", file)    
    })
} else {
    opts_chunk$set(fig.path='figure/')
}

# use html style links to plots, rather than markdown style         
knit_hooks$set(plot = hook_plot_html)
build_dep()

require(knitcitations)
cleanbib()
# to get knitcitations:
#library(devtools)
#install_github("knitcitations", "cboettig")
 
end.rcode-->


# knitr citationpractices manuscript
 * author of this file: Heather Piwowar, <hpiwowar@gmail.com>
 * license: CC0
 * Acknowledgements: thanks to Yihui Xie for knitr and Carl Boettiger for his clear examples of this literate programming framework. 
 * Generated on <!--rinline date() -->

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


<!--begin.rcode workspace, messages=FALSE, echo=FALSE
# Clear the workspace and load package dependencies: 
rm(list=ls())   
require(ggplot2, quietly=T)
require(gplots, quietly=T)
require(reshape2, quietly=T)
require(plyr, quietly=T)
require(rms, quietly=T)
require(polycor, quietly=T)
require(ascii, quietly=T)
require(knitcitations)
# to get knitcitations:
#library(devtools)

options(scipen=8)

end.rcode-->

<!--begin.rcode gfmtable, echo=FALSE, cache=FALSE
# From https://gist.github.com/2050761
gfm_table <- function(x, ...){
  y <- capture.output(print(ascii(x, ...), type = 'org'))
  # substitute + with | for table markup
  # TODO: modify regex so that only + signs in markup, like -+- are substituted
  y <- gsub('[+]', '|', y)
  return(writeLines(y))
} 
#gfm_table(anova(fit))
end.rcode-->


# Making data Count: tracking data citations through the scholarly literature and beyond

The References section is a fundamental part of any research paper.  When the references in a paper are indexed, the references contribute to the set of known relationships between scholarship.  Over the past 50 years, the resulting citation indices have become  backbones of scholarly reward and discovery systems.  We now rely on citation indices to such a large extent that if a scholarly contribution does not participate in the citation system it is a bystander to academic reward and discovery.

It is crucially important, therefore, that all scholarship of note participates fully in the citation system: a research object needs a well-defined citation representation, it needs to be cited in the references section when appropriate, citations to it need to be indexed, and finally the indexed data needs to be interpreted and used.

Research datasets did not historically participate in the citation system as independent objects: datasets were often attributed through proxy articles or or overlooked due to non-indexible attribution in the methods or acknowlegement sections.  There has been growing recognition that reserach data should be treated as a first-class research object.  As a result, worldwide initiatives have recently developed initial standards for citation representations for data.  Many datasets now do have recommended citation formats.  In this report we look at what comes next: what needs to happen to facilitate the indexing, interpretation, and use of citations to datasets. 


(Why do we need a citation graph for data? What would we do with it?  How do we get there?)


## 1. What can data citation tracking do for us

Many editorials and white papers have called for 

Data attribution tracking has many uses, from the commonly touted goal of "rewarding data collecting investigators" to less-frequently highlighted infrastructure uses in discovery and filtering.  Below, we explore reasons to track citations to datasets themselves to motivate and inform infrastructure and metrics that will be needed.

### Encourage data archiving


Almost all investigators report that citation is important to them: it was the the most important condition for sharing data in the survey by [Tenopir], mentioned by 92% of respondents.  Investigators who believe proper attribution is important have been found more likely to both intend to share data and to self-report actual data sharing in a structural model of motivation [Sayogo]. 

1. Tenopir C, Allard S, Douglass K, et al. Data Sharing by Scientists: Practices and Perceptions Neylon C, ed. PLoS ONE. 2011;6(6):e21101. Available at: http://dx.plos.org/10.1371/journal.pone.0021101 [Accessed June 30, 2011].
1. Sayogo DS, Pardo TA. Exploring the Motive for Data Publication in Open Data Initiative: Linking Intention to Action. In: 2012 45th Hawaii International Conference on System Sciences. IEEE; 2012:2623-2632. Available at: http://dl.acm.org/citation.cfm?id=2116261.2116762 [Accessed July 16, 2012].

Many editorials and white papers have called for data citations to reward data collecting investigators who make their data available for reuse.

1. Cech T, Eddy S, Eisenberg D, et al. Sharing publication-related data and materials: responsibilities of authorship in the life sciences. Plant physiology. 2003;132(1):19-24.
2. Sinnott R, Macdonald A, Lord P, Ecklund D, Jones A. Large-scale data sharing in the life sciences: Data standards, incentives, barriers and funding models (The Joint Data Standards StudyÂ). The Biotechnology and Biological Sciences Research Council, The Department of Trade and Industry, The Joint Information Systems Committee for Support for Research, The Medical Research Council, The Natural Environment Research Council and The Wellcome Tru. 2005. Available at: http://www.dcs.gla.ac.uk/publications/paperdetails.cfm?id=8109.
3. Anon. Compete, collaborate, compel. Nat Genet. 2007;39(8). Available at: http://dx.doi.org/10.1038/ng0807-931.
4. Anon. Data producers deserve citation credit. Nature genetics. 2009;41(10):1045. Available at: http://www.ncbi.nlm.nih.gov/pubmed/19786949.
5. Thorisson GA. Accreditation and attribution in data sharing. Nature biotechnology. 2009;27(11):984-5. Available at: http://www.ncbi.nlm.nih.gov/pubmed/19898446.
6. Schofield PN, Bubela T, Weaver T, et al. Post-publication sharing of data and tools. Nature. 2009;461(7261):171.
7. Anon. Discussing standards. Nature genetics. 2010;42(11):915. Available at: http://www.ncbi.nlm.nih.gov/pubmed/20980979 [Accessed July 14, 2012].
8. Edmunds SC, Pollard TJ, Hole B, Basford A. Adventures in data citation: sorghum genome data exemplifies the new gold standard. BMC Research Notes. 2012;5(1):223. Available at: http://www.ncbi.nlm.nih.gov/pubmed/22571506 [Accessed May 10, 2012].

Evidence that studies with publicly-available datasets receive more citations has been cited by many editorials within several editorials when journals introduce a new policies for data archiving [see http://datadryad.org/jdap].


### Reward the most useful collection, curation, and dissemination of data

Evidence suggests that a wide base of datasets are reused, suggesting that many investigators who make their data available will receive an increase in citations.

1. Piwowar H. Probability of observed third-party data reuse. FigShare. 2012. Available at: http://figshare.com/articles/Probability_of_observed_third-party_data_reuse/92959 [Accessed July 16, 2012].

While many datasets are reused, not all datasets are reused the same number of times.  More research is needed to understand what correlates with reuse, but probably metadata and infrastructure play a role:  can a new investigator easily find a dataset, understand it, and integrate it into established systems?

Citation tracking will aligns incentives: it provides the most reward for the most useful data.  This is likely to encourage investigators and repositories to collect, curate, and disseminate data in ways that are most useful to future investigators.

Data citation also encourages early dissemination.  The earlier a data is published, the sooner it can begin attracting citations.  [Edmunds] reports this incentive helped make early dissemination of a recent high-profile dataset attractive to its authors.

1. Edmunds SC, Pollard TJ, Hole B, Basford A. Adventures in data citation: sorghum genome data exemplifies the new gold standard. BMC Research Notes. 2012;5(1):223. Available at: http://www.ncbi.nlm.nih.gov/pubmed/22571506 [Accessed May 10, 2012].

### Include all relevant contributors in reward structure

Citing and tracking datasets independently from research papers facilitate rewarding relevant contributors upon data use.  Investigators who contribute to data collection may be different than those who contribute to resulting publications.  In some cases data curators ought to be rewarded within a data citation.  Data repositories also deserve attribution.

Some of these roles may be included in the text of the reference itself.  Others are recorded in the metadata behind the unique identifier included in the reference.  Resolving the identifier to its metadata allows linking in these significant relationships.

1. Starr J, Gastl A. isCitedBy: A Metadata Scheme for DataCite. D-Lib Magazine. 2011;17(1/2). Available at: http://www.dlib.org/dlib/january11/starr/01starr.html [Accessed February 27, 2012].


[move this down??? Some data archives have attempted to determine value themselves, to make case to their funders.  Unforunately, as we discuss below, very time consuming and resource intensive!  For example, ORNL DAAC....
In an attempt to make their case to funders they currently spend many hours a year manually collecting indication of th ...]

### Alert investigators of reanalyses

Without citation tracking it is difficult for investigators to receive notifications of reanalyses of a particular dataset.  This is important for  data collection investigators: the team that collected the data is often very interested to learn about and verify future analyses [Tenopir, Whitlock 2011].

1. Whitlock MC. Data archiving in ecology and evolution: best practices. Trends in ecology & evolution. 2011;26(2):61-5. Available at: http://www.ncbi.nlm.nih.gov/pubmed/21159406 

Investigators considering or in the midst of a reanalysis may want to sign up for alerts of what others are publishing.

Full-text search alerts are poor approximations for citation-based alerts.  Citation-based alerts forthe paper describing data collection are also a poor solution, since data reanalyses can get lost in the citation deluge received by very popular papers.

### Discover associated datasets and researcher communities

Reward is only one readon to track data citations.  Other reasons is that it can facilitate discovery of associated datasets through recommender systems [Michener].  A paper that cites two datasets is a valuable clue that someone who is interested in the first dataset would also be interested in the second.

1. Michener WK, Porter J, Servilla M, Vanderbilt K. Long term ecological research and information management. Ecological Informatics. 2011;6(1):13-24. Available at: http://linkinghub.elsevier.com/retrieve/pii/S1574954110001159 [Accessed July 17, 2012].

### Filter for frequently used -- or neglected! -- datasets 

Some datasets are used often and others are never used [Piwowar, Vision 2012].  Scientists may want to filter datasets by the frequency of use .  Some scientists may be looking for dataset that are tried and true: those used often.  Others may be looking for overlooked datasets, those that haven't been used much with perhaps a great deal of unrealized value.

1. Piwowar H. Probability of observed third-party data reuse. FigShare. 2012. Available at: http://figshare.com/articles/Probability_of_observed_third-party_data_reuse/92959 [Accessed July 16, 2012].


### Identify analyses based on problematic datasets

Sometimes it turns out that a dataset has quality problems.  Whether data is intentionally faked [Carlisle], an innocent mistake, or even just considered misleading due to constantly improving quality standards, the result is the same: analyses built on data sometimes need reconsidered and the literature corrected [Shafer; Miller].  Citation tracking is needed so that analyses based on a given dataset be found.

1. Shafer SL. Tattered threads. Anesthesia and analgesia. 2009;108(5):1361-3. Available at: http://www.ncbi.nlm.nih.gov/pubmed/19372305 [Accessed July 17, 2012].
1. Miller DR. Publication fraud: implications to the individual and to the specialty. Current opinion in anaesthesiology. 2011;24(2):154-9. Available at: http://www.ncbi.nlm.nih.gov/pubmed/21252647 [Accessed July 17, 2012].


### Avoid harmful shoehorning

In an attempt to piggyback on the infrastructure and reward system for publishign research articles, several new and existing publishers have been lanching "data journals."  Some data overlay journals add value to an archived dataset, by providing more thorough metadata than would otherwise be available, or formal peer-review [Callaghan].  In other instances they merely serve as a proxy citation to a dataset.  Relying on a system that shoehorns data into the existing journal system to facilitate formal attribution is a reasonable stop-gap measure, but not the best long term solution.  Supporting direct citation to archived datasets avoids compromise solutions that cost time and money.

1. Callaghan S, Hewer F, Pepler S, Hardaker P. Overlay journals and data publishing in the meteorological sciences. Ariadne. 2009;(July):1-8. Available at: http://www.ariadne.ac.uk/issue60/callaghan-et-al/ [Accessed July 17, 2012].

### Trail-blaze for recognition of other research types

Citation of research data is much further along than citation to other types of non-traditional scholarly products, such as software [Howison].  Tracking data citations will blaze the trail for  recognition of other research types. 

1. Howison J. Scientific software production: incentives and collaboration. Proceedings of the ACM 2011 conference on. 2011. Available at: http://dl.acm.org/citation.cfm?id=1958904 [Accessed July 17, 2012].

### Drive policy, funding, and tool requirements based on evidence

Finally, tracking data reuse allows policy makers, funders, and tool builders to know what has facilited reuse and what hasn't.  Real evidence is needed to inform decision about what kind of standards facilitate reuse, how much data curation is necessary, whether embargoes strike an appropriate balance, and whether tool features are being used.

Without this evidence we are running blind, and surely wasting money, time, and opportunities.



## 2. What we want to Count

### Dataset-level metrics

For many fields and datatypes it seems appropriate to track data on the dataset or data package level.  "Dataset-level metrics" are analigous to "article-level metrics" now gaining ground for research papers.

The specific level of granularity may differ for diferent fields and datatypes (data file, data package, data row).  A good rule of thumb might be to track data attribution at the highest level of abstraction with common methods of collection and contributing investigators and institutions.

### Project-level and grant-level metrics 

Some journals may fear that a move to attribute data reuse directly with the dataset will reduce attribution to original research articles.  Not unless warrented: in cases where data reuse investigators use data description and metadata from the research article associated with a dataset, they ought to be encouraged to also cite the article (see Dryad's data citation policy).

Some scholars have been worried this will be viewed as gratuitous citation collection.  This would only be true if the citations were naively added together and compared to citation rates without independent data and articles.  Instead, let's build a model that appropriately represents the impact of a whole project: project-level metrics, based on all of its component item-level impact metrics.

Related to project-level metrics is the idea of grant-level metrics.

### Repository impact story rather than Repository impact factor

Several calls have been made for a "repository impact factor".  While it is important for repositories to measure the value they provide, trying to optimise for a high "impact factor" calculated the same way as the journal impact factor is likely to lead to decisions that are not optimised for efficient or effective research.  For example, it would encourage repositories to exclude datasets from niche areas or untested research fronts, in case these datsets drag down its citation impact average. 

A repository's impact story should instead be told as a more complex story of the types of reuse it has faciliated, as described below.  This can be done qualitatively, through visible success stories.  With thoughtful impact tracking, subtle impact patterns can also be captured and described quantitatively.

Chevan has called for a "Data Usage Index"

* Visits
* Description
* Unique Visits Loyal Visits
* Download Events
* Download Frequency 
* Download Volume 
* Download Impact
* Avg. Download Freq. 
* Usage Ratio

1. Chavan VS, Ingwersen P. Towards a data publishing framework for primary biodiversity data: challenges and potentials for the biodiversity informatics community. 2009:1-11.


### Impact from outside the literature

Discussion heretofore has focused on data citations in the published scholarly literature.  As scholarly discussion moves online and is captured by a wide variety of product types, evidence of impact may occur in a wide variety of fora.  For example, dataset metadata may cite other datasets.  Academics may bookmark datasets using general purposes bookmarking tools (i.e. delicious) or general-purpose reference managers (Mendeley and Zotero).  Datasets of interest may be the topic of blogs, tweets, and preprints.  The number of times a dataset has been viewed or downloaded is also interesting.

These measurements are often called alternative metrics, or altmetrics. 


### Impact from outside academia

Datasets may also be used outside of university researchers.  Reuse by students, journalists, policy makers, clinitians, startup companies, established industry leaders -- all of these uses are valuable and worth noting, particularly when the original data collection was collected with public money.  It is difficult to track these types of uses online, but unique identifiers and open resources begin to make it possible.


icpsr downloads

### Reuses of the reuses

Sometimes the best way to look at the value of something is to look at its second-order use:  Did  the metaanalysis which included the datset cause a significant change in healthcare practice?  How impactful was the blog post *about* the dataset?

A limited version of this type of analysis is directly possible from a citation graph, the same way that PageRank or EigenFactor are based on linked networks.  These approaches ignore the issue of the role of the dataset in acheiving the second-order effect, so they must be used in concert with complementary information.  Nonetheless, this sort of information is key to understanding the true value of a resource. 



### Context of reuses

Automated determination of citation function [Teufel2006] and its role in new ideas within the paper [Siddharthan2007].

1. Teufel S, Siddharthan A, Tidhar D. Automatic classification of citation function. In: Proceedings of the 2006 Conference on Empirical Methods in Natural Language Processing.; 2006:103-110. Available at: http://www.cl.cam.ac.uk/~as372/sigdial-final.pdf.
1. Siddharthan A, Teufel S. Whose idea was this, and why does it matter? Attributing scientific work to citations. In: Proceedings of NAACL/HLT-07.; 2007. Available at: http://citeseerx.ist.psu.edu/viewdoc/summary?doi=10.1.1.62.3178.



### Impact flavour

Finally, we want to do more than just measure numbers.  We want to assess *type*. [Priem]

## 3. How to get there

### Standardize


### Educate, encourage, expect, and enforce

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

<img src="http://dl.dropbox.com/u/5485507/datacitation/datacitationstudy/figure/CitationPatterns.png" height=200/>


granularity
versioning
table that shows the different combinations of how data is cited

consistency within Genbank conventions vs chaos elsewhere
some try to give attibuion by including author name, as an example

Discussion of data citation styles: Altman, King (2007); Lawrence et al. (2008); Green (2010); Starr and Gastl (2011)



### Fix problematic policies

* Limit on number of references

* Putting references in supplementary methods
[Citations in supplementary information are invisible]

* Only including peer-reviewed resources in references

* Not including data sharing paper as a citation.  This would be the most natural way to link a paper that describes data collection and dataset, yet none of Dryad's journals do it.  There is a concern this would be counted as citation grabbing.  Unfortunately, without it, we are left with trying to use metadata that is often incomplete to find these relationships.

1. Piwowar HA, Chapman WW. Linking database submissions to primary citations with PubMed Central. In: BioLINK Workshop at ISMB.; 2008:4.

data journalism


### Open the reference lists

1. Shotton D. Oxford University Press to support Open Citations. Open Citations and Semantic Publishing blog. 2012. Available at: http://opencitations.wordpress.com/2012/06/22/oxford-university-press-to-support-open-citations/ [Accessed July 16, 2012].

not nc


### Build lots of tools

We are making promises to data creators about attribution and reward that we can’t keep.  ”Make your data citeable!” is the cry.  Ok.  So citeable is step one.  Cited is step two.  But for the citation to be useful, it has to be indexed so that citation metrics can be tracked and admired and used.  Who is indexing data citations right now?  As far as I can tell: absolutely no one.

Some tracking tools, like Google Scholar, have decided not to track datasets.

Others are are only willing to track peer-reviewed resources (http://f1000research.com/2012/07/09/we-are-almost-there/).

The two major bibliometric resources, Web of Science and Scopus, do not retain dois or urls in the references they collect.  As a result, dataset identifiers are lost and citations to data cannot be tracked.

<img src="http://dl.dropbox.com/u/5485507/datacitation/datacitationstudy/figure/ORNLDAACinPaper.png" height=200/>

<img src="http://dl.dropbox.com/u/5485507/datacitation/datacitationstudy/figure/ORNLDAACinScopus.png" height=200/>

Funding

### Do the research




### Invite (and act on!) evidence of impact






## 4. Conclusion

A future where data attribution counts.
A future about *what kind* of contribution a dataset makes, not just a number.
Emerging data citation best practices are not yet supported by existing attribution tracking tools.  Agreement on policy and technical infrastructure must go hand in hand in order for benefits of reuse to be realized.
Data is the lifeblood of science, let’s give it the respect it deserves.




