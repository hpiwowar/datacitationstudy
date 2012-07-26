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


# Making data Count: tracking data impact through the scholarly literature and beyond

Citation tracking is a key component of our scholarly infrastructure.  When a research object is used, referenced, and indexed, it forms a navigable and countable link between the citing article and the cited object.  Over the past 50 years, the resulting indices have become backbones of scholarly reward and discovery systems.

It is crucially important, therefore, that all noteworthy scholarship participates fully in the citation system.  The first step is that all research objects must be citeable.  Then, when appropriate, research objects must be attributed in the References section of a paper, the reference must be indexed, and finally the citation index needs to be interpreted and used.

Research datasets have not historically participated in the citation system as independent objects: datasets have been attributed by proxy through article that describe data collection, or informally in acknowledgment sections.  In recent years there has been growing recognition that research data should be treated as a first-class research objects.  Much attention has been paid to defining standard data citation formats and education.

To date, however, there has been little conversation and even less progress on ensuring that data citations, once referenced, are indexed.  We focus on this tracking stage: what is needed to facilitate the indexing, interpretation, and use of impact metrics for datasets. 


## 1. Why data impact tracking?

### Encourage data archiving

Many editorials and white papers have called for data citations to reward data collecting investigators who make their data available for reuse <!--rinline citep(biblio[c("cech:2003", "sinnott:2005", "anon:2007", "anon:2009", "thorisson:2009", "schofield:2009", "anon:2010", "edmunds:2012")]) -->.

Evidence suggests policy suggestions are on track: most researchers state that citation is an important incentive for making their data available: anticipating citations was the most important condition for sharing data in a recent study <!--rinline citep(biblio["tenopir:2011"]) -->, mentioned by 92% of respondents.  Within a structural model of motivation, investigators who valued proper attribution were found more likely to share data than those who didn't <!--rinline citep(biblio["sayogo:2012"]) -->.

Indeed, when journals announce stronger policies for data archiving, they often make the case in part by highlighting evidence of increased citation rate [see http://datadryad.org/jdap].


### Reward the most useful collection, curation, and dissemination of data

A large proportion of investigators who make their data available will receive a citation boost, given that a substantial portion of available datasets are reused <!--rinline citep(biblio["piwowar:2012b"]) -->.

That said, the largest citation boost will probably correlate with datasets that are reused most often.  More research is needed to understand what factors correlate with high levels of reuse, but metadata and infrastructure likely play a role: can a new investigator easily find a dataset, understand it, and integrate it into established systems?

Another way to increase the citation boost by a certain date is to make it available earlier.  A recent article reports that this incentive made early dissemination of a recent high-profile dataset more attractive to its authors <!--rinline citep(biblio["edmunds:2012"]) -->.

Reward that correlates with successful data reuse will aligning incentives for data creators, curators, and reusers, encouraging the most useful collection, curation, and dissemination.

### Include all relevant contributors in reward structure

Tracking attribution to datasets as standalone research objects provides a specific path of reward for those who contributed to the dataset.  The existence of this path eliminates several problems with reliance on attribution through a research article byline.

First, it provides a path to reward to all of those who contributed to the data product, including those who are normally overlooked: techs, data curators, data editors, and data repositories.  Individuals and entities can be included in either the data reference itself <!--rinline citep(biblio["parsons:2010"]) --> or through linked metadata <!--rinline citep(biblio["starr:2011"]) -->, assuming these links are maintained in the index.  Tracked contributions are notably important for data archives, because they often need to provide regular evidence of their value to funders 
<!--rinline citep(biblio["fry:2009"]) --> <!--rinline citep(biblio["piwowar:2011a"]) -->.

Second, attribution to datasets allows the byline of a research article to be restricted to those who have made an intellectual contribution to the article and given their final approval over the manuscript <!--rinline citep(biblio["rohlfing:2012"]) -->, because  alternate paths exist to attribute other contributions.

Third, attribution to datasets appropriately provides double-attribution for those who do double work: investigators who contribute to both a reusable dataset product and an intellectual analysis paper are rewarded for both <!--rinline citep(biblio["whitlock:2011"]) -->.

### Discover associated analyses, datasets, and researcher communities

Just as journals often provide links to articles that cite their articles, for context and discovery, data repositories may wish to provide links to known reuses of datasets.  Indeed, ICPSR and ORNL DAAC do this now, based on data collected through time-consuming manual searches.  Automatically indexed data citations make it much simpler to include these links.

Data citation links could also be used to recommend datasets  <!--rinline citep(biblio["michener:2011"]) -->.  If two datasets are often cited together, it is likely that a website visitor exploring the first dataset may also be interested in the second.

### Alert investigators of reanalyses

Citation tracking makes it possible for investigators to receive notifications of reanalyses of a particular dataset.  The team that collected the data is often very interested to learn about and verify future analyses <!--rinline citep(biblio["tenopir:2011"]) --> <!--rinline citep(biblio["whitlock:2011"]) -->.  Alerts would also be useful to scientists who reuse data: those considering or in the midst of a reanalysis may want to sign up for alerts to learn what others are publishing.

Substitutes for alerts based on citations to datasets are problematic.  Alerts based on full-text searches are inaccurate and have poor recall.  Alerts based instead on the paper describing data collection are also a poor solution, since data reanalyses can get lost in the citation deluge received by very popular papers.

### Filter for frequently used -- or neglected! -- datasets 

Some scientists may want to filter datasets by the frequency of use.  One scientists may be particularly interested in data that has been used frequently: frequent reuse may serve as a quality indicator of reputation and believability <!--rinline citep(biblio["wang:1996"]) --> <!--rinline citep(biblio["pradhan:2005"]) -->.  Another researcher may be interested in data that has been used infrequently, to find a datasets rich with untapped research potential.

### Identify analyses based on problematic datasets

Occasionally a dataset is found to have quality problems.  Whether data is intentionally faked [Carlisle], found to have errors due to an innocent mistake, or even just considered misleading due to constantly improving quality standards, the result is the same: analyses built on data sometimes sometimes need to be reconsidered.  Citation indexing allows the literature build on these results to be identified and reinterpreted <!--rinline citep(biblio["miller:2011"]) --> <!--rinline citep(biblio["shafer:2009"]) -->.

### Avoid harmful shoehorning

Several publishers have launched "data journals", piggybacking on the existing article infrastructure and reward system.  Some data overlay journals add value to an archived dataset by providing additional metadata or formal peer-review <!--rinline citep(biblio["callaghan:2009"]) -->.  In other instances, data journals simply serve as a proxy citation to a dataset.

Shoehorning data into the existing journal system to facilitate formal attribution is a reasonable stop-gap measure, but not the best long term solution.  Supporting direct citation to archived datasets avoids compromise solutions that cost time and money.

### Trail-blaze for recognition of other research types

Progress toward citation of research data is much further along than citation to other types of non-traditional scholarly products, such as research software <!--rinline citep(biblio["howison:2011"]) -->.  Tracking data citations will blaze the trail for recognition of other types of research objects. 

### Drive policy, funding, and tool requirements based on evidence

Finally, tracking data allows policy makers, funders, and tool builders to know what has facilitated data reuse and what hasn't.  Real evidence is needed to inform decision about what kind of standards facilitate reuse, how much data curation is necessary, whether embargoes strike an appropriate balance, and whether tool features are being used.

For example,  policy makers concerned that data availability would lead to duplicated analyses have since received evidence this is not the case <!--rinline citep(biblio["bachrach:2004"]) -->.

Making decisions without evidence surely leads to wasted money, time, and opportunities.


## 2. What to Count

### Dataset citations in the academic literature

The most obvious  metric for tracking data citations is to count the number of times that dataset unique identifiers occur in formal reference lists in the published literature.  This is analogous to counting citations to research papers.

"Dataset-level metrics" are analogous to "article-level metrics" now gaining ground for research papers.  <!--rinline citep(biblio["neylon:2009"]) -->.  Project-level aggregation and grant-level aggregation may also be useful for investigators summarizing their impact to their insitution or funder.

### Impact beyond citations

Citations often take years to accrue; citations based on data reuse may take even longer than citations that pay attribution to an idea.  An early indicator of citation count may be found in download statistics.  Several data repositories already display download counts (Dryad, FigShare).  ICPSR, takes this one step further, displaying aggregated breakdown statistics about what sort of authenticated users have downloaded the datasets.  As discussed in <!--rinline citep(biblio["chavan:2009"]) -->, many associated metrics can also be displayed, including number of unique visits and number of loyal visits.

Other indications of dataset impact can be found online.  For example, datasets may cite other datasets in their metadata.  Academics may bookmark datasets using general purposes bookmarking tools (i.e. delicious) or general-purpose reference managers (Mendeley and Zotero).  Datasets may be the topic of preprints, blogs, and tweets.

Several tools are beginning to reveal these statistics and  discussion of datasets in social media (altmetric.com, total-impact).Such measurements are often called alternative metrics, or altmetrics.

### Impact beyond academic research

Much data reuse may go on outside academia, reuse by journalists, policy makers, clinicians, industry, and students <!--rinline citep(biblio["wallis:2006"]) -->.

Tracking citations in research publications, however, fail to capture these impacts.  Evidence of impact will likely be found in syllabi, textbooks, statistical package READMEs, patent applications, data journalism news articles, blogs, and more. 


### Reuses of the reuses

Another valuable metric is second-order use:  how impactful is the research which uses the dataset?  A citation-based version of second-order impact can be derived from the full citation graph.

### Context

Reference links offer much richer data than mere counts.  The reference link is made in a context that can be used to weight or characterize the relationship.  CiTO -- the Citation Typing Ontology -- defines relationships between citing and cited document, including "confirms", "extends", "updates", "corrects", and "refutes". <!--rinline citep(biblio["shotton:2010"]) -->.  These relationships usually implicit in the full text of an article.  Widespread use of citation typing will either require large-scale manual annotation or automated classification of citation function <!--rinline citep(biblio["teufel:2006"]) -->.

There are other aspects of reference context that may also be interesting.  Understanding the relative importance of a dataset to a paper may be proportional to the number of citation mentions it includes.  The section of the reference may also be instructive.

### Impact flavour

Datasets likely make different types of impact.  Some may be great for calibration, others for training, others to test new methods.  A few datasets may be particularly useful for exploring new hypotheses.

This "impact flavour" won't be clear from citation counts alone, but it can likely be derived from a combination of impact indicators and context <!--rinline citep(biblio["priem:2012"]) -->.  Understanding the impact flavour of a dataset allows different datasets to be appreciated and discovered based on their strengths.

### Impact Story rather than Impact Factor

It is possible to imagine using these metrics to calculate a  Repository Impact Factor.  While it is important for repositories to measure the value they provide, optimizing for a high average impact would likely to lead to decisions that are not ideal for efficient or effective research.  For example, maintaining a high average citation count would discourage preserving datasets from small niche domains and untested research fronts. 

Thanks to a wide array of metrics and context, a repository's impact story can instead be told as a more complex story that highlights the types of reuse it has facilitated.  This story could be told qualitatively, through visible success stories that might be discovered through tracking data reuse.  Subtle impact patterns can also be captured and described quantitatively.


## 3. How to get there

### Standardize

The first task, and the one that has received most attention thus far, is to make data citable.  This involves hosting the data in a permanent location, giving it a unique identifier, deciding on a level of granularity and version for citation, and defining other metadata that may accompany it.

Citeable data is not enough unless there are standard ways to cite the data.  This has two components: citations that are meaningful to humans, and those that can be parsed by machines.

Discussion of data citation styles: Altman, King (2007); Lawrence et al. (2008); Green (2010); Starr and Gastl (2011)


Standard data citation formats for humans

The citation fields need to be included in the 

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



consistency within Genbank conventions vs chaos elsewhere
some try to give attribution by including author name, as an example


<!--rinline citep(biblio["seeber:2008"]) -->

### Fix problematic journal policies

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

Identifying data sharing in biomedical literature: <!--rinline citep(biblio["piwowar:2008a"]) -->


### Open up machine-readable reference lists

not nc

<!--rinline citep(biblio["shotton:2012"]) -->
<!--rinline citep(biblio["shotton:2009"]) -->
https://researchremix.wordpress.com/2012/04/19/data-citation-text-mining/

### Build tools

We are making promises to data creators about attribution and reward that we can’t keep.  ”Make your data citeable!” is the cry.  Ok.  So citeable is step one.  Cited is step two.  But for the citation to be useful, it has to be indexed so that citation metrics can be tracked and admired and used.  Who is indexing data citations right now?  As far as I can tell: absolutely no one.

<!--rinline citep(biblio["bakkalbasi:2006"]) -->

Some tracking tools, like Google Scholar, have decided not to track datasets.

Others are are only willing to track peer-reviewed resources (http://f1000research.com/2012/07/09/we-are-almost-there/).

The two major bibliometric resources, Web of Science and Scopus, do not retain dois or urls in the references they collect.  As a result, dataset identifiers are lost and citations to data cannot be tracked.

<img src="http://dl.dropbox.com/u/5485507/datacitation/datacitationstudy/figure/ORNLDAACinPaper.png" height=200/>

<img src="http://dl.dropbox.com/u/5485507/datacitation/datacitationstudy/figure/ORNLDAACinScopus.png" height=200/>

Funding

<!--rinline citep(biblio["larsen:2010"]) -->
Tracking dataset citations using common citation tracking tools doesn't work <!--rinline citep(biblio["piwowar:2010"]) -->
Thomson Reuters announces subscription-based data citation tracking tool <!--rinline citep(biblio["piwowar:2012"]) -->

Tools to ping

<!--rinline citep(biblio["pepler:2008"]) -->


Tools that support data citation in manuscripts:

<!--rinline citep(biblio["opportunities-for-data-exchange:2012"]) -->


### Do research

Much research is needed.


How should citation data contribute to metrics for research evaluation?  Metrics need to be more reliable, more transparent, and more flexible metrics of scientific performance.  As Julia Lane discusses <!--rinline citep(biblio["lane:2010"]) -->, we need to focus on what the data mean and how they can best be interpreted, as well as more basic research into how measurement can change behaviour, and how changes to incentives alter the way research is performed.  She suggests this will require participation from computer scientists, natural scientists, social scientists, economists, and funders.

What can 

How best to fund this?

https://twitter.com/rdmpage/status/225337983690211330


1. Research on whether these policies are effective.  data archiving etc
2. on how to fund, run these programs
3. 


### Invite (and act on!) evidence of impact

Finally, evidence of impact

NIH RFI
NSF biosketch
tenure committees

science of science policy


## 4. Conclusion

A future where data attribution counts.
A future about *what kind* of contribution a dataset makes, not just a number.
Emerging data citation best practices are not yet supported by existing attribution tracking tools.  Agreement on policy and technical infrastructure must go hand in hand in order for benefits of reuse to be realized.
Data is the lifeblood of science, let’s give it the respect it deserves.

## 5. References

<!--begin.rcode bib, results='asis', echo=FALSE, cache=FALSE, eval=TRUE
bibliography(sort=TRUE)
end.rcode-->

## X. misc notes

All the biblio keys, cited and not:
<!--begin.rcode citeEveryone, echo=TRUE, eval=TRUE
  names(biblio)
  #citep(biblio[names(biblio)])
end.rcode-->



