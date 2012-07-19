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
    knit("citationpractices_knit_.md")

or, from the command line, to generate an html file:

    R -e "library(knitr); knit('citationpractices_knit_.md')"; pandoc --toc -r markdown -w html -H static/header.html citationpractices.md > citationpractices.html

The stats.html file can be viewed directly in a browser.
The images are stored in my Public Dropbox folder.

After pushing the .md files to GitHub, the citationpractices.md file can also be viewed at [https://github.com/hpiwowar/citation11k/blob/master/analysis/stats.md](https://github.com/hpiwowar/citation11k/blob/master/analysis/stats.md) .

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

<!--begin.rcode knitCitationsBibtexExperiment, echo=FALSE, results="asis", cache=FALSE
  # set up citations
biblio = read.bibtex("tracking.bib")
end.rcode-->


# Making data Count: tracking data citations through the scholarly literature and beyond

The References section is a fundamental part of any research paper.  When the references in a paper are indexed, the references contribute to the set of known relationships between scholarship.  Over the past 50 years, the resulting citation indices have become  backbones of scholarly reward and discovery systems.  We now rely on citation indices to such a large extent that if a scholarly contribution does not participate in the citation system it is a bystander to academic reward and discovery.

It is crucially important, therefore, that all scholarship of note participates fully in the citation system: a research object needs a well-defined citation representation, it needs to be cited in the references section when appropriate, citations to it need to be indexed, and finally the indexed data needs to be interpreted and used.

Research datasets did not historically participate in the citation system as independent objects: datasets were often attributed through proxy articles or or overlooked due to non-indexible attribution in the methods or acknowlegement sections.  There has been growing recognition that reserach data should be treated as a first-class research object.

For data citations to be useful, data must be citable, must be cited, and then must be indexed.

To date, conversations about data citation have largely ignored the step of indexing data citations.  In this report we focus on this tracking stage: what needs to happen to facilitate the indexing, interpretation, and use of citations to datasets. 


## 1. Why data citation tracking

Data attribution tracking has many uses, from the commonly touted goal of rewarding data collecting investigators to less-frequently highlighted infrastructure uses in discovery and filtering.  Below, we explore reasons to track citations to datasets themselves to motivate and inform infrastructure and metrics that will be needed.

### Encourage data archiving

Almost all investigators report that citation is important to them: it was the the most important condition for sharing data in the survey by <!--rinline citep(biblio["tenopir:2011"]) -->, mentioned by 92% of respondents.  Investigators who believe proper attribution is important have been found more likely to both intend to share data and to self-report actual data sharing in a structural model of motivation <!--rinline citep(biblio["sayogo:2012"]) -->.

Many editorials and white papers have called for data citations to reward data collecting investigators who make their data available for reuse. <!--rinline citep(biblio[c("cech:2003", "sinnott:2005", "anon:2007", "anon:2009", "thorisson:2009", "schofield:2009", "anon:2010", "edmunds:2012")]) -->

Journal editorials that introduce a new policies for data archiving often cite evidence that studies with publicly-available datasets receive more citations [see http://datadryad.org/jdap].


### Reward the most useful collection, curation, and dissemination of data

Evidence suggests that a wide base of datasets are reused <!--rinline citep(biblio["piwowar:2012a"]) -->, so many investigators who make their data available are likely to receive an increase in citations.

While many datasets are reused, not all datasets are reused the same number of times.  More research is needed to understand what correlates with reuse, but probably metadata and infrastructure play a role:  can a new investigator easily find a dataset, understand it, and integrate it into established systems?

Citation tracking will aligns incentives: it provides the most reward for the most useful data.  This is likely to encourage investigators and repositories to collect, curate, and disseminate data in ways that are most useful to future investigators.

Data citation also encourages early dissemination.  The earlier a data is published, the sooner it can begin attracting citations. <!--rinline citep(biblio["edmunds:2012"]) --> reports this incentive helped make early dissemination of a recent high-profile dataset attractive to its authors.

### Include all relevant contributors in reward structure

Citing and tracking datasets independently from research papers facilitate rewarding relevant contributors upon data use.  Investigators who contribute to data collection may be different than those who contribute to resulting publications.  For example, n some cases data curators or editors ought to be rewarded within a data citation.  Data repositories also deserve attribution.

Some of these roles may be included in the text of the reference itself <!--rinline citep(biblio["parsons:2010"]) -->.  Others are recorded in the metadata behind the unique identifier included in the reference <!--rinline citep(biblio["starr:2011"]) -->.  Resolving the identifier to its metadata allows linking in these significant relationships.

It is also very important to data archives to document the value they provide to their funders 
<!--rinline #citep(biblio["fry:2009"]) --> 

<!--rinline citep(biblio["piwowar:2011"]) -->

Documenting this value is often a condition of funding.

### Discover associated analyses, datasets, and researcher communities

Just as journals often citations of articles on their websites to provide context and discovery, data repositories may want to list reuses on the page that provides the data.  Indeed, ICPSR and ORNL DAAC do this now, based on time-consuming manual searches.

Data citations could also facilitate discovery of associated datasets through recommender systems <!--rinline citep(biblio["michener:2011"]) -->.  A paper that cites two datasets is a valuable clue that someone who is interested in the first dataset would also be interested in the second.

### Alert investigators of reanalyses

Without citation tracking it is difficult for investigators to receive notifications of reanalyses of a particular dataset.  This is important for  data collection investigators: the team that collected the data is often very interested to learn about and verify future analyses <!--rinline citep(biblio["tenopir:2011"]) --> <!--rinline citep(biblio["whitlock:2011"]) -->.

Alerts would also be useful to data using scientists: those considering or in the midst of a reanalysis may want to sign up for alerts to learn of what others are publishing.

Full-text search alerts are poor approximations for citation-based alerts.  Citation-based alerts forthe paper describing data collection are also a poor solution, since data reanalyses can get lost in the citation deluge received by very popular papers.

### Filter for frequently used -- or neglected! -- datasets 

Some datasets are used often whereas others are never used <!--rinline citep(biblio["piwowar:2012a"]) -->.  Scientists may want to filter datasets by the frequency of use.  Some scientists may be looking for dataset that has been used frequently: frequent reuse may serve as a quality indicator by signalling a strong reputation and believability <!--rinline citep(biblio["wang:1996"]) --> <!--rinline citep(biblio["pradhan:2005"]) -->.

Meanwhile, a different set of researchers may want to search for datasets that have been used infrequently, as they look for those with untapped research potential.

### Identify analyses based on problematic datasets

Sometimes it turns out that a dataset has quality problems.  Whether data is intentionally faked [Carlisle], an innocent mistake, or even just considered misleading due to constantly improving quality standards, the result is the same: analyses built on data sometimes need reconsidered and the literature corrected <!--rinline citep(biblio["miller:2011"]) --> <!--rinline citep(biblio["shafer:2009"]) -->.  Citation tracking is needed so that analyses based on a given dataset be found.

### Avoid harmful shoehorning

In an attempt to piggyback on the infrastructure and reward system for publishign research articles, several new and existing publishers have been lanching "data journals."  Some data overlay journals add value to an archived dataset, by providing more thorough metadata than would otherwise be available, or formal peer-review <!--rinline citep(biblio["callaghan:2009"]) -->.  In other instances they merely serve as a proxy citation to a dataset.  Relying on a system that shoehorns data into the existing journal system to facilitate formal attribution is a reasonable stop-gap measure, but not the best long term solution.  

Supporting direct citation to archived datasets avoids compromise solutions that cost time and money.  Instead, data citations should be ready to evolve as scientific publication moves toward  nanopublications <!--rinline citep(biblio["mons:2011"]) -->.

### Trail-blaze for recognition of other research types

Citation of research data is much further along than citation to other types of non-traditional scholarly products, such as software <!--rinline citep(biblio["howison:2011"]) -->.  Tracking data citations will blaze the trail for  recognition of other research types. 

### Drive policy, funding, and tool requirements based on evidence

Finally, tracking data reuse allows policy makers, funders, and tool builders to know what has facilited reuse and what hasn't.  Real evidence is needed to inform decision about what kind of standards facilitate reuse, how much data curation is necessary, whether embargoes strike an appropriate balance, and whether tool features are being used.  For example, some policy makers were concerned that data availability would lead to duplicated analyses; evidence based on tracking down data reuses suggests this is not the case <!--rinline citep(biblio["bachrach:2004"]) -->.

Without evidence we are running blind, and surely wasting money, time, and opportunities.



## 2. What to Count

### Dataset impact in the academic literature

The most clear expectation for tracking data citations is to count the number of times that dataset unique identifiers occur in formal reference lists in the published literature.  This is analigous to counting citations to research papers.

### Impact elsewhere in academic reserach

As scholarly discussion moves online and is captured by a wide variety of product types, evidence of impact may occur in a wide variety of fora, beyond the traditional scholarly literature.  For example, dataset metadata may cite other datasets.  Academics may bookmark datasets using general purposes bookmarking tools (i.e. delicious) or general-purpose reference managers (Mendeley and Zotero).  Datasets of interest may be the topic of blogs, tweets, and preprints.  The number of times a dataset has been viewed or downloaded is also interesting.

Downloads area already displayed in some data repositories (Dryad, FigShare).  ICPSR, in particular, reveals aggregated statistics about download uses at the dataset level, which can reveal, for example whether students find a particular dataset useful.

Several tools are beginning to reveal these statistics and  discussion of datasets in social media (altmetric.com, total-impact).Such measurements are often called alternative metrics, or altmetrics.

<!--rinline citep(biblio["chavan:2009"]) -->

F1000R preprints

### Impact outside academic research

Reuse by students, journalists, policy makers, clinitians, startup companies, established industry leaders -- all of these uses are valuable and worth noting to fuel reward and discovery.

<!--rinline citep(biblio["wallis:2006"]) -->

Tracking citations in research publications, however, fail to capture these impacts.  As diverse uses move online, and datasets begin to be identified witn unique identifiers, more and more uses can be tracked automatrically.  Evidence of impact will likely be found in syllabi, textbooks, statistical package READMEs, patent applications, data journalism news articles, blogs, and more.

### Context of reuses

Automated determination of citation function [Teufel2006] and its role in new ideas within the paper [teufel2000].

<!--rinline citep(biblio["teufel:2006"]) -->
<!--rinline citep(biblio["teufel:2000"]) -->
<!--rinline citep(biblio["shotton:2010"]) -->


### Reuses of the reuses

Sometimes the best way to look at the value of something is to look at its second-order use:  Did the metaanalysis which included the datset cause a significant change in healthcare practice?  How impactful was the blog post *about* the dataset?

A limited version of this type of analysis is directly possible from a citation graph, the same way that PageRank or EigenFactor are based on linked networks.  These approaches ignore the issue of the role of the dataset in acheiving the second-order effect, so they must be used in concert with complementary information.  Nonetheless, this sort of information is key to understanding the true value of a resource. 


### Impact flavour

We want to do more than just measure numbers.  We want to assess *type*. <!--rinline citep(biblio["priem:2012"]) -->

### Impact Story rather than Impact Factor

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

<!--rinline citep(biblio["chavan:2009"]) -->
<!--rinline citep(biblio["lozano:2012"]) -->
<!--rinline citep(biblio["seglen:1997"]) -->
<!--rinline citep(biblio["todd:2008"]) -->


### Aggregation: project-level, grant-level, repository-level and beyond

Metrics have many audiences. 

For many fields and datatypes it seems appropriate to track data on the dataset or data package level.  "Dataset-level metrics" are analogous to "article-level metrics" now gaining ground for research papers.

<!--rinline citep(biblio["neylon:2009"]) -->

The specific level of granularity may differ for diferent fields and datatypes (data file, data package, data row).  If data citations are tracked at the level of granularity they are cited, higher-level analyses can aggregate them.

<!--rinline citep(biblio["van-de-sompel:2009"]) -->

A good rule of thumb might be to track data attribution at the highest level of abstraction with common methods of collection and contributing investigators and institutions.


## 3. How to get there

### Standardize

<!--rinline citep(biblio["mooney:2012"]) -->
<!--rinline citep(biblio["mooney:2011"]) -->
<!--rinline citep(biblio["altman:2007"]) -->
<!--rinline citep(biblio["cook:2008"]) -->
<!--rinline citep(biblio["sieber:1995"]) -->
<!--rinline citep(biblio["cronin:1995"]) -->


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

<!--rinline citep(biblio["seeber:2008"]) -->

### Fix problematic policies

* Limit on number of references

* Putting references in supplementary methods
[Citations in supplementary information are invisible]

* Only including peer-reviewed resources in references

* Not including data sharing paper as a citation.  This would be the most natural way to link a paper that describes data collection and dataset, yet none of Dryad's journals do it.  There is a concern this would be counted as citation grabbing.  Unfortunately, without it, we are left with trying to use metadata that is often incomplete to find these relationships.


data journalism


<!--rinline citep(biblio["seeber:2008"]) -->

Problems differentiating data sharing from data reuse

<!--rinline citep(biblio["neveol:2011"]) -->

Linking database submissions to primary citations with PubMed Central: <!--rinline citep(biblio["piwowar:2008"]) -->

Identifying data sharing in biomedical literature: <!--rinline citep(biblio["piwowar:2008"]) -->


### Open, machine-readable reference lists

not nc

<!--rinline citep(biblio["shotton:2012"]) -->
<!--rinline citep(biblio["shotton:2009"]) -->
https://researchremix.wordpress.com/2012/04/19/data-citation-text-mining/

### Build lots of tools

We are making promises to data creators about attribution and reward that we can’t keep.  ”Make your data citeable!” is the cry.  Ok.  So citeable is step one.  Cited is step two.  But for the citation to be useful, it has to be indexed so that citation metrics can be tracked and admired and used.  Who is indexing data citations right now?  As far as I can tell: absolutely no one.

<!--rinline citep(biblio["bakkalbasi:2006"]) -->

Some tracking tools, like Google Scholar, have decided not to track datasets.

Others are are only willing to track peer-reviewed resources (http://f1000research.com/2012/07/09/we-are-almost-there/).

The two major bibliometric resources, Web of Science and Scopus, do not retain dois or urls in the references they collect.  As a result, dataset identifiers are lost and citations to data cannot be tracked.

<img src="http://dl.dropbox.com/u/5485507/datacitation/datacitationstudy/figure/ORNLDAACinPaper.png" height=200/>

<img src="http://dl.dropbox.com/u/5485507/datacitation/datacitationstudy/figure/ORNLDAACinScopus.png" height=200/>

Funding

<!--rinline citep(biblio["larsen:2010"]) -->
Tracking dataset citations using common citation tracking tools doesnât work <!--rinline citep(biblio["piwowar:2010"]) -->
Thomson Reuters announces subscription-based data citation tracking tool <!--rinline citep(biblio["piwowar:2012"]) -->

Tools to ping

<!--rinline citep(biblio["pepler:2008"]) -->


Tools that support data citation in manuscripts:

<!--rinline citep(biblio["opportunities-for-data-exchange:2012"]) -->


### Do the research





Correlations between metadata and reuse

### Invite (and act on!) evidence of impact






## 4. Conclusion

A future where data attribution counts.
A future about *what kind* of contribution a dataset makes, not just a number.
Emerging data citation best practices are not yet supported by existing attribution tracking tools.  Agreement on policy and technical infrastructure must go hand in hand in order for benefits of reuse to be realized.
Data is the lifeblood of science, let’s give it the respect it deserves.


<!--begin.rcode citeEveryone, echo=TRUE, eval=TRUE
  names(biblio)

#citep(biblio[names(biblio)])
end.rcode-->

## References

<!--begin.rcode bib, results='asis', echo=FALSE, cache=FALSE, eval=TRUE
bibliography(sort=TRUE)
end.rcode-->



