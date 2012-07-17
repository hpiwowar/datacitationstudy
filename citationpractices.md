





# knitr citationpractices manuscript
 * author of this file: Heather Piwowar, <hpiwowar@gmail.com>
 * license: CC0
 * Acknowledgements: thanks to Yihui Xie for knitr and Carl Boettiger for his clear examples of this literate programming framework. 
 * Generated on <code class="knitr inline">Tue Jul 17 15:49:57 2012</code>

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












# Making data Count: tracking data citations through the scholarly literature and beyond

The References section is a fundamental part of any research paper.  When the references in a paper are indexed, the references contribute to the set of known relationships between scholarship.  Over the past 50 years, the resulting citation indices have become  backbones of scholarly reward and discovery systems.  We now rely on citation indices to such a large extent that if a scholarly contribution does not participate in the citation system it is a bystander to academic reward and discovery.

It is crucially important, therefore, that all scholarship of note participates fully in the citation system: a research object needs a well-defined citation representation, it needs to be cited in the references section when appropriate, citations to it need to be indexed, and finally the indexed data needs to be interpreted and used.

Research datasets did not historically participate in the citation system as independent objects: datasets were often attributed through proxy articles or or overlooked due to non-indexible attribution in the methods or acknowlegement sections.  There has been growing recognition that reserach data should be treated as a first-class research object.  As a result, worldwide initiatives have recently developed initial standards for citation representations for data.  Many datasets now do have recommended citation formats.  In this report we look at what comes next: what needs to happen to facilitate the indexing, interpretation, and use of citations to datasets. 


(Why do we need a citation graph for data? What would we do with it?  How do we get there?)


## 1. Why data citation tracking

Many editorials and white papers have called for 

Data attribution tracking has many uses, from the commonly touted goal of "rewarding data collecting investigators" to less-frequently highlighted infrastructure uses in discovery and filtering.  Below, we explore reasons to track citations to datasets themselves to motivate and inform infrastructure and metrics that will be needed.

### Encourage data archiving

Almost all investigators report that citation is important to them: it was the the most important condition for sharing data in the survey by (Tenopir _et. al._ 2011), mentioned by 92% of respondents.  Investigators who believe proper attribution is important have been found more likely to both intend to share data and to self-report actual data sharing in a structural model of motivation (Sayogo & Pardo, 2012).

Many editorials and white papers have called for data citations to reward data collecting investigators who make their data available for reuse. (Cech _et. al._ 2003; Sinnott _et. al._ 2005; Anon, 2007; Anon, 2009; Thorisson, 2009; Schofield _et. al._ 2009; Anon, 2010; Edmunds _et. al._ 2012)

Journal editorials that introduce a new policies for data archiving often cite evidence that studies with publicly-available datasets receive more citations [see http://datadryad.org/jdap].


### Reward the most useful collection, curation, and dissemination of data

Evidence suggests that a wide base of datasets are reused (Piwowar, 2012), so many investigators who make their data available are likely to receive an increase in citations.

While many datasets are reused, not all datasets are reused the same number of times.  More research is needed to understand what correlates with reuse, but probably metadata and infrastructure play a role:  can a new investigator easily find a dataset, understand it, and integrate it into established systems?

Citation tracking will aligns incentives: it provides the most reward for the most useful data.  This is likely to encourage investigators and repositories to collect, curate, and disseminate data in ways that are most useful to future investigators.

Data citation also encourages early dissemination.  The earlier a data is published, the sooner it can begin attracting citations. (Edmunds _et. al._ 2012) reports this incentive helped make early dissemination of a recent high-profile dataset attractive to its authors.

### Include all relevant contributors in reward structure

Citing and tracking datasets independently from research papers facilitate rewarding relevant contributors upon data use.  Investigators who contribute to data collection may be different than those who contribute to resulting publications.  For example, n some cases data curators or editors ought to be rewarded within a data citation.  Data repositories also deserve attribution.

Some of these roles may be included in the text of the reference itself (Parsons _et. al._ 2010).  Others are recorded in the metadata behind the unique identifier included in the reference (Starr & Gastl, 2011).  Resolving the identifier to its metadata allows linking in these significant relationships.

It is also very important to data archives to document the value they provide to their funders 
 

(Piwowar _et. al._ 2011); documenting this value is often a condition of funding.

### Discover associated analyses, datasets, and researcher communities

Just as journals often citations of articles on their websites to provide context and discovery, data repositories may want to list reuses on the page that provides the data.  Indeed, ICPSR and ORNL DAAC do this now, based on time-consuming manual searches.

Data citations could also facilitate discovery of associated datasets through recommender systems (Michener _et. al._ 2011).  A paper that cites two datasets is a valuable clue that someone who is interested in the first dataset would also be interested in the second.

### Alert investigators of reanalyses

Without citation tracking it is difficult for investigators to receive notifications of reanalyses of a particular dataset.  This is important for  data collection investigators: the team that collected the data is often very interested to learn about and verify future analyses (Tenopir _et. al._ 2011) (Whitlock, 2011).

Alerts would also be useful to data using scientists: those considering or in the midst of a reanalysis may want to sign up for alerts to learn of what others are publishing.

Full-text search alerts are poor approximations for citation-based alerts.  Citation-based alerts forthe paper describing data collection are also a poor solution, since data reanalyses can get lost in the citation deluge received by very popular papers.

### Filter for frequently used -- or neglected! -- datasets 

Some datasets are used often whereas others are never used (Piwowar, 2012).  Scientists may want to filter datasets by the frequency of use.  Some scientists may be looking for dataset that has been used frequently: frequent reuse may serve as a quality indicator by signalling a strong reputation and believability (Wang & Strong, 1996) (NULL).

Meanwhile, a different set of researchers may want to search for datasets that have been used infrequently, as they look for those with untapped research potential.

### Identify analyses based on problematic datasets

Sometimes it turns out that a dataset has quality problems.  Whether data is intentionally faked [Carlisle], an innocent mistake, or even just considered misleading due to constantly improving quality standards, the result is the same: analyses built on data sometimes need reconsidered and the literature corrected (Miller, 2011) (Shafer, 2009).  Citation tracking is needed so that analyses based on a given dataset be found.

### Avoid harmful shoehorning

In an attempt to piggyback on the infrastructure and reward system for publishign research articles, several new and existing publishers have been lanching "data journals."  Some data overlay journals add value to an archived dataset, by providing more thorough metadata than would otherwise be available, or formal peer-review (Callaghan _et. al._ 2009).  In other instances they merely serve as a proxy citation to a dataset.  Relying on a system that shoehorns data into the existing journal system to facilitate formal attribution is a reasonable stop-gap measure, but not the best long term solution.  

Supporting direct citation to archived datasets avoids compromise solutions that cost time and money.  Instead, data citations should be ready to evolve as scientific publication moves toward  nanopublications (Mons _et. al._ 2011).

### Trail-blaze for recognition of other research types

Citation of research data is much further along than citation to other types of non-traditional scholarly products, such as software (Howison, 2011).  Tracking data citations will blaze the trail for  recognition of other research types. 

### Drive policy, funding, and tool requirements based on evidence

Finally, tracking data reuse allows policy makers, funders, and tool builders to know what has facilited reuse and what hasn't.  Real evidence is needed to inform decision about what kind of standards facilitate reuse, how much data curation is necessary, whether embargoes strike an appropriate balance, and whether tool features are being used.  For example, some policy makers were concerned that data availability would lead to duplicated analyses; evidence based on tracking down data reuses suggests this is not the case (Bachrach & King, 2004).

Without evidence we are running blind, and surely wasting money, time, and opportunities.



## 2. What to Count

### Dataset impact in the academic literature

The most clear expectation for tracking data citations is to count the number of times that dataset unique identifiers occur in formal reference lists in the published literature.  This is analigous to counting citations to research papers.

### Impact in other academic realms

As scholarly discussion moves online and is captured by a wide variety of product types, evidence of impact may occur in a wide variety of fora, beyond the traditional scholarly literature.  For example, dataset metadata may cite other datasets.  Academics may bookmark datasets using general purposes bookmarking tools (i.e. delicious) or general-purpose reference managers (Mendeley and Zotero).  Datasets of interest may be the topic of blogs, tweets, and preprints.  The number of times a dataset has been viewed or downloaded is also interesting.

Downloads area already displayed in some data repositories (Dryad, FigShare).  ICPSR, in particular, reveals aggregated statistics about download uses at the dataset level, which can reveal, for example whether students find a particular dataset useful.

Several tools are beginning to reveal these statistics and  discussion of datasets in social media (altmetric.com, total-impact).Such measurements are often called alternative metrics, or altmetrics.

1. Chavan VS, Ingwersen P. Towards a data publishing framework for primary biodiversity data: challenges and potentials for the biodiversity informatics community. 2009:1-11.

F1000R preprints

### Impact outside academic research

Reuse by students, journalists, policy makers, clinitians, startup companies, established industry leaders -- all of these uses are valuable and worth noting to fuel reward and discovery.

1. Wallis JC, Milojevic S, Borgman CL, Sandoval W a. The Special Case of Scientific Data Sharing with Education. Proceedings of the American Society for Information Science and Technology. 2006;43(1):1-13. Available at: http://doi.wiley.com/10.1002/meet.14504301169.

Tracking citations in research publications, however, fail to capture these impacts.  As diverse uses move online, and datasets begin to be identified witn unique identifiers, more and more uses can be tracked automatrically.  Evidence of impact will likely be found in syllabi, textbooks, statistical package READMEs, patent applications, data journalism news articles, blogs, and more.

### Context of reuses

Automated determination of citation function [Teufel2006] and its role in new ideas within the paper [Siddharthan2007].

1. Teufel S, Siddharthan A, Tidhar D. Automatic classification of citation function. In: Proceedings of the 2006 Conference on Empirical Methods in Natural Language Processing.; 2006:103-110. Available at: http://www.cl.cam.ac.uk/~as372/sigdial-final.pdf.
1. Siddharthan A, Teufel S. Whose idea was this, and why does it matter? Attributing scientific work to citations. In: Proceedings of NAACL/HLT-07.; 2007. Available at: http://citeseerx.ist.psu.edu/viewdoc/summary?doi=10.1.1.62.3178.


1. Shotton D. CiTO, the Citation Typing Ontology. Journal of biomedical semantics. 2010;1 Suppl 1:S6. Available at: http://www.pubmedcentral.nih.gov/articlerender.fcgi?artid=2903725&tool=pmcentrez&rendertype=abstract [Accessed March 29, 2012].

### Reuses of the reuses

Sometimes the best way to look at the value of something is to look at its second-order use:  Did the metaanalysis which included the datset cause a significant change in healthcare practice?  How impactful was the blog post *about* the dataset?

A limited version of this type of analysis is directly possible from a citation graph, the same way that PageRank or EigenFactor are based on linked networks.  These approaches ignore the issue of the role of the dataset in acheiving the second-order effect, so they must be used in concert with complementary information.  Nonetheless, this sort of information is key to understanding the true value of a resource. 


### Impact flavour

We want to do more than just measure numbers.  We want to assess *type*. [Priem]

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

1. Chavan VS, Ingwersen P. Towards a data publishing framework for primary biodiversity data: challenges and potentials for the biodiversity informatics community. 2009:1-11.

1. Lozano GA, Lariviere V, Gingras Y. The weakening relationship between the Impact Factor and papersâ citations in the digital age. 2012:14. Available at: http://arxiv.org/abs/1205.4328 [Accessed July 11, 2012].

1. Seglen P. Why the impact factor of journals should not be used for evaluating research. BMJ. 1997;314(7079):498-502. Available at: http://www.ncbi.nlm.nih.gov/entrez/query.fcgi?cmd=Retrieve&db=PubMed&dopt=Citation&list_uids=9056804 .


Add citation to problem with the impact factor


Citations have problems and don't tell the whole story

1. Todd P, Ladle R. Hidden dangers of a Âcitation cultureÂ. ESEP. 2008;8:13-16.

### Aggregation: project-level, grant-level, repository-level and beyond

Metrics have many audiences. 

For many fields and datatypes it seems appropriate to track data on the dataset or data package level.  "Dataset-level metrics" are analogous to "article-level metrics" now gaining ground for research papers.

1. Neylon C, Wu S. Article-level metrics and the evolution of scientific impact. PLoS Biology. 2009;7(11):e1000242.

The specific level of granularity may differ for diferent fields and datatypes (data file, data package, data row).  If data citations are tracked at the level of granularity they are cited, higher-level analyses can aggregate them.

1. Sompel HVD, Lagoze C, Nelson ML, et al. Adding eScience Assets to the Data Web Aggregations in Scholarly Communication. Management.

A good rule of thumb might be to track data attribution at the highest level of abstraction with common methods of collection and contributing investigators and institutions.


## 3. How to get there

### Standardize

1. Mooney H, Newton M. The Anatomy of a Data Citation: Discovery, Reuse, and Credit. Journal of Librarianship and Scholarly Communication. 2012;1(1). Available at: http://jlsc-pub.org/jlsc/vol1/iss1/6 [Accessed May 16, 2012].
1. Mooney H. Citing data sources in the social sciences: do authors do it? Learned Publishing. 2011;24(2):10. Available at: http://www.ingentaconnect.com/content/alpsp/lp/2011/00000024/00000002/art00004;jsessionid=9kingso9bep58.alexandra [Accessed October 31, 2011].

1. Altman M, King G. A proposed standard for the scholarly citation of quantitative data. D-Lib Magazine. 2007;13(3/4). Available at: http://gking.harvard.edu/files/abs/cite-abs.shtml.
1. Cook R. Editorial: Citations to Published Data Sets. FLUXNET newsletter. 2008;4:1-2.

1. Sieber JE, Trumbo BE. (Not) giving credit where credit is due: Citation of data sets. Science and Engineering Ethics. 1995;1(1):11-20. Available at: http://www.springerlink.com/index/10.1007/BF02628694.

1. Cronin B. The Scholarâs Courtesy: The Role of Acknowledgement in the Primary Communication Process. 1995. Available at: http://onlinebooks.library.upenn.edu/webbin/book/lookupid?key=olbp40644 [Accessed January 9, 2012].

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

1. Seeber F. Citations in supplementary information are invisible. Nature. 2008;451(7181):887. Available at: http://www.nature.com/nature/journal/v451/n7181/full/451887d.html [Accessed August 12, 2010].

### Fix problematic policies

* Limit on number of references

* Putting references in supplementary methods
[Citations in supplementary information are invisible]

* Only including peer-reviewed resources in references

* Not including data sharing paper as a citation.  This would be the most natural way to link a paper that describes data collection and dataset, yet none of Dryad's journals do it.  There is a concern this would be counted as citation grabbing.  Unfortunately, without it, we are left with trying to use metadata that is often incomplete to find these relationships.

1. Piwowar HA, Chapman WW. Linking database submissions to primary citations with PubMed Central. In: BioLINK Workshop at ISMB.; 2008:4.

data journalism



1.  Seeber F. Citations in supplementary information are invisible. Nature. 2008;451(7181):887. Available at: http://www.nature.com/nature/journal/v451/n7181/full/451887d.html [Accessed August 12, 2010].

Problems differentiating data sharing from data reuse

1. NNNN A, Wilbur WJ, Lu Z. Extraction of data deposition statements from the literature: a method for automatically tracking research results. Bioinformatics (Oxford, England). 2011;27(23):3306-12. Available at: http://www.pubmedcentral.nih.gov/articlerender.fcgi?artid=3223368&tool=pmcentrez&rendertype=abstract [Accessed March 21, 2012].
1. Piwowar HA, Chapman WW. Linking database submissions to primary citations with PubMed Central. In: BioLINK Workshop at ISMB.; 2008:4.
2. Piwowar HA, Chapman WW. Identifying data sharing in biomedical literature. In: AMIA Symposium.; 2008:596-600. Available at: http://www.ncbi.nlm.nih.gov/sites/entrez?Db=pubmed&Cmd=Retrieve&list_uids=18998887&dopt=abstractplus.

### Open, machine-readable reference lists

1. Shotton D. Oxford University Press to support Open Citations. Open Citations and Semantic Publishing blog. 2012. Available at: http://opencitations.wordpress.com/2012/06/22/oxford-university-press-to-support-open-citations/ [Accessed July 16, 2012].
1. Piwowar H. Care about data citation? Then you care about text-mining access. Research Remix blog. 2012. Available at: https://researchremix.wordpress.com/2012/04/19/data-citation-text-mining/ [Accessed July 15, 2012].

not nc


1. Shotton D. Oxford University Press to support Open Citations. Open Citations and Semantic Publishing blog. 2012. Available at: http://opencitations.wordpress.com/2012/06/22/oxford-university-press-to-support-open-citations/ [Accessed July 16, 2012].

1. Shotton D, Portwin K, Klyne G, Miles A. Adventures in semantic publishing: exemplar semantic enhancements of a research article. PLoS computational biology. 2009;5(4):e1000361. Available at: http://www.pubmedcentral.nih.gov/articlerender.fcgi?artid=2663789&tool=pmcentrez&rendertype=abstract [Accessed March 11, 2012].

### Build lots of tools

We are making promises to data creators about attribution and reward that we can’t keep.  ”Make your data citeable!” is the cry.  Ok.  So citeable is step one.  Cited is step two.  But for the citation to be useful, it has to be indexed so that citation metrics can be tracked and admired and used.  Who is indexing data citations right now?  As far as I can tell: absolutely no one.

1. Bakkalbasi N, Bauer K, Glover J, Wang L. Three options for citation tracking: Google Scholar, Scopus and Web of Science. Biomedical digital libraries. 2006;3:7. Available at: http://www.pubmedcentral.nih.gov/articlerender.fcgi?artid=1533854&tool=pmcentrez&rendertype=abstract [Accessed March 6, 2012].

Some tracking tools, like Google Scholar, have decided not to track datasets.

Others are are only willing to track peer-reviewed resources (http://f1000research.com/2012/07/09/we-are-almost-there/).

The two major bibliometric resources, Web of Science and Scopus, do not retain dois or urls in the references they collect.  As a result, dataset identifiers are lost and citations to data cannot be tracked.

<img src="http://dl.dropbox.com/u/5485507/datacitation/datacitationstudy/figure/ORNLDAACinPaper.png" height=200/>

<img src="http://dl.dropbox.com/u/5485507/datacitation/datacitationstudy/figure/ORNLDAACinScopus.png" height=200/>

Funding

1. Larsen PO, Ins M von. The rate of growth in scientific publication and the decline in coverage provided by Science Citation Index. Scientometrics. 2010;84(3):575-603. Available at: http://www.pubmedcentral.nih.gov/articlerender.fcgi?artid=2909426&tool=pmcentrez&rendertype=abstract [Accessed March 13, 2012].

1. Piwowar HA. Tracking dataset citations using common citation tracking tools doesnât work. Research Remix blog. 2010. Available at: http://researchremix.wordpress.com/2010/11/09/tracking-dataset-citations-using-common-citation-tracking-tools-doesnt-work/ [Accessed July 15, 2012].
1. Piwowar H. Thomson Reuters announces subscription-based data citation tracking tool. Research Remix blog. 2012. Available at: http://researchremix.wordpress.com/2012/06/28/data-citation-index/ [Accessed July 15, 2012].

Tools to ping

1. Pepler CS. JISC Final Report CITATION , LOCATION, And DEPOSITION IN DISCIPLINE & INSTITUTIONAL REPOSITORIES CLADDIER. 2008;(April 2007).


### Do the research





Correlations between metadata and reuse

### Invite (and act on!) evidence of impact






## 4. Conclusion

A future where data attribution counts.
A future about *what kind* of contribution a dataset makes, not just a number.
Emerging data citation best practices are not yet supported by existing attribution tracking tools.  Agreement on policy and technical infrastructure must go hand in hand in order for benefits of reuse to be realized.
Data is the lifeblood of science, let’s give it the respect it deserves.


<div class="chunk"><div class="rcode"><div class="source"><pre class="knitr">  <span class="functioncall">names</span><span class="keyword">(</span><span class="symbol">biblio</span><span class="keyword">)</span>
</pre></div><div class="output"><pre class="knitr">##  [1] "hine:2006"       "pienta:2010"     "altman:2007"    
##  [4] "bachrach:2004"   "bakkalbasi:2006" "cook:2008"      
##  [7] "costello:2009"   "edmunds:2012"    "haustein:2011"  
## [10] "priem:2012"      "mons:2011"       "mooney:2011"    
## [13] "mooney:2012"     "neveol:2011"     "parsons:2010"   
## [16] "piwowar:2008a"   "piwowar:2008"    "prat:2008"      
## [19] "schofield:2009"  "seeber:2008"     "seglen:1997"    
## [22] "shotton:2010"    "shotton:2009"    "sieber:1995"    
## [25] "sinnott:2005"    "starr:2011"      "tenopir:2011"   
## [28] "teufel:2000"     "teufel:2006"     "thorisson:2009" 
## [31] "todd:2008"       "wang:1996"       "feelders:2000"  
## [34] "vasseur:2003"    "anon:2007"       "anon:2009"      
## [37] "anon:2010"       "larsen:2010"     "wynholds:2012"  
## [40] "piwowar:2011"    "piwowar:2010"    "piwowar:2012b"  
## [43] "piwowar:2012"    "piwowar:2011a"   "cech:2003"      
## [46] "shotton:2012"    "sayogo:2012"     "bornmann:2008"  
## [49] "wouters:1900"    "piwowar:2012a"   "whitlock:2011"  
## [52] "michener:2011"   "howison:2011"    "carlisle:2012"  
## [55] "miller:2011"     "shafer:2009"     "callaghan:2009" 
## [58] "wallis:2006"     "edwards:2011"    "neylon:2009"    
</pre></div><div class="source"><pre class="knitr">
<span class="comment">#citep(biblio[names(biblio)])</span>
</pre></div></div></div>


## References

<div class="error"><pre class="knitr">## Error: EXPR must be a length 1 vector
</pre></div>


1. Armbruster C. Access, Usage and Citation Metrics: What Function for Digital Libraries and Repositories in Research Evaluation?
2. Fry J, Lockyer S, Oppenheim C, Houghton J, Rasmussen B. Identifying benefits arising from the curation and open sharing of research data produced by UK Higher Education and research institutes. 2009:1-89.
3. Hine C. Databases as Scientific Instruments and Their Role in the Ordering of Scientific Work. Social Studies of Science. 2006;36(2):269-298. Available at: http://sss.sagepub.com/cgi/doi/10.1177/0306312706054047 [Accessed March 6, 2012].
4. Pienta A, Alter G. The enduring value of social science research: The use and reuse of primary research data. Russell The Journal Of The Bertrand Russell Archives. 2010. Available at: http://141.213.232.243/handle/2027.42/78307 [Accessed July 14, 2012].
5. Altman M, King G. A proposed standard for the scholarly citation of quantitative data. D-Lib Magazine. 2007;13(3/4). Available at: http://gking.harvard.edu/files/abs/cite-abs.shtml.
6. Bachrach CA, King RB. Data sharing and duplication: is there a problem? Archives of pediatrics & adolescent medicine. 2004;158(9):931-2. Available at: http://archpedi.jamanetwork.com/article.aspx?articleid=485802 [Accessed July 11, 2012].
7. Bakkalbasi N, Bauer K, Glover J, Wang L. Three options for citation tracking: Google Scholar, Scopus and Web of Science. Biomedical digital libraries. 2006;3:7. Available at: http://www.pubmedcentral.nih.gov/articlerender.fcgi?artid=1533854&tool=pmcentrez&rendertype=abstract [Accessed March 6, 2012].
8. Chavan VS, Ingwersen P. Towards a data publishing framework for primary biodiversity data: challenges and potentials for the biodiversity informatics community. 2009:1-11.
9. Cook R. Editorial: Citations to Published Data Sets. FLUXNET newsletter. 2008;4:1-2.
10. Costello MJ. Motivating Online Publication of Data. BioScience. 2009;59(5):418-427.
11. Cronin B. The Scholarâs Courtesy: The Role of Acknowledgement in the Primary Communication Process. 1995. Available at: http://onlinebooks.library.upenn.edu/webbin/book/lookupid?key=olbp40644 [Accessed January 9, 2012].
12. Edmunds SC, Pollard TJ, Hole B, Basford A. Adventures in data citation: sorghum genome data exemplifies the new gold standard. BMC Research Notes. 2012;5(1):223. Available at: http://www.ncbi.nlm.nih.gov/pubmed/22571506 [Accessed May 10, 2012].
13. Haustein S, Siebenlist T. Applying social bookmarking data to evaluate journal usage. Journal of Informetrics. 2011;In Press. Available at: http://www.sciencedirect.com/science/article/B83WV-52S72KS-1/2/a1b5622db7d1b63e2a1078669e0b9960.
14. Priem J, Piwowar HA, Hemminger BM. Altmetrics in the wild: Using social media to explore scholarly impact. arXiv12034745v1 csDL 20 Mar 2012. 2012;1203.4745:1-23. Available at: http://arxiv.org/abs/1203.4745.
15. Lozano GA, Lariviere V, Gingras Y. The weakening relationship between the Impact Factor and papersâ citations in the digital age. 2012:14. Available at: http://arxiv.org/abs/1205.4328 [Accessed July 11, 2012].
16. Mons B, Haagen H van, Chichester C, et al. The value of data. Nature genetics. 2011;43(4):281-3. Available at: http://www.ncbi.nlm.nih.gov/pubmed/21445068 [Accessed March 21, 2012].
17. Mooney H. Citing data sources in the social sciences: do authors do it? Learned Publishing. 2011;24(2):10. Available at: http://www.ingentaconnect.com/content/alpsp/lp/2011/00000024/00000002/art00004;jsessionid=9kingso9bep58.alexandra [Accessed October 31, 2011].
18. Mooney H, Newton M. The Anatomy of a Data Citation: Discovery, Reuse, and Credit. Journal of Librarianship and Scholarly Communication. 2012;1(1). Available at: http://jlsc-pub.org/jlsc/vol1/iss1/6 [Accessed May 16, 2012].
19. NÃ©vÃ©ol A, Wilbur WJ, Lu Z. Extraction of data deposition statements from the literature: a method for automatically tracking research results. Bioinformatics (Oxford, England). 2011;27(23):3306-12. Available at: http://www.pubmedcentral.nih.gov/articlerender.fcgi?artid=3223368&tool=pmcentrez&rendertype=abstract [Accessed March 21, 2012].
20. Parsons M a., Duerr R, Minster J-B. Data Citation and Peer Review. Eos, Transactions American Geophysical Union. 2010;91(34):297. Available at: http://www.agu.org/pubs/crossref/2010/2010EO340001.shtml.
21. Pepler CS. JISC Final Report CITATION , LOCATION, And DEPOSITION IN DISCIPLINE & INSTITUTIONAL REPOSITORIES CLADDIER. 2008;(April 2007).
22. Piwowar HA, Chapman WW. Linking database submissions to primary citations with PubMed Central. In: BioLINK Workshop at ISMB.; 2008:4.
23. Piwowar HA, Chapman WW. Identifying data sharing in biomedical literature. In: AMIA Symposium.; 2008:596-600. Available at: http://www.ncbi.nlm.nih.gov/sites/entrez?Db=pubmed&Cmd=Retrieve&list_uids=18998887&dopt=abstractplus.
24. Pradhan S. BELIEVABILITY AS AN INFORMATION QUALITY DIMENSION. Available at: http://mitiq.mit.edu/ICIQ/Documents/IQ Conference 2005/Papers/BelievabilityasanIQDimension.pdf [Accessed July 11, 2012].
25. Prat N, Madnick S. Measuring Data Believability: A Provenance Approach. In: Proceedings of the 41st Annual Hawaii International Conference on System Sciences (HICSS 2008). IEEE; 2008:393-393. Available at: http://ieeexplore.ieee.org/xpl/articleDetails.jsp?arnumber=4439098 [Accessed July 11, 2012].
26. Schofield PN, Bubela T, Weaver T, et al. Post-publication sharing of data and tools. Nature. 2009;461(7261):171.
27. Seeber F. Citations in supplementary information are invisible. Nature. 2008;451(7181):887. Available at: http://www.nature.com/nature/journal/v451/n7181/full/451887d.html [Accessed August 12, 2010].
28. Seglen P. Why the impact factor of journals should not be used for evaluating research. BMJ. 1997;314(7079):498-502. Available at: http://www.ncbi.nlm.nih.gov/entrez/query.fcgi?cmd=Retrieve&db=PubMed&dopt=Citation&list_uids=9056804 .
29. Shotton D. CiTO, the Citation Typing Ontology. Journal of biomedical semantics. 2010;1 Suppl 1:S6. Available at: http://www.pubmedcentral.nih.gov/articlerender.fcgi?artid=2903725&tool=pmcentrez&rendertype=abstract [Accessed March 29, 2012].
30. Shotton D, Portwin K, Klyne G, Miles A. Adventures in semantic publishing: exemplar semantic enhancements of a research article. PLoS computational biology. 2009;5(4):e1000361. Available at: http://www.pubmedcentral.nih.gov/articlerender.fcgi?artid=2663789&tool=pmcentrez&rendertype=abstract [Accessed March 11, 2012].
31. Sieber JE, Trumbo BE. (Not) giving credit where credit is due: Citation of data sets. Science and Engineering Ethics. 1995;1(1):11-20. Available at: http://www.springerlink.com/index/10.1007/BF02628694.
32. Sinnott R, Macdonald A, Lord P, Ecklund D, Jones A. Large-scale data sharing in the life sciences: Data standards, incentives, barriers and funding models (The Joint Data Standards StudyÂ). The Biotechnology and Biological Sciences Research Council, The Department of Trade and Industry, The Joint Information Systems Committee for Support for Research, The Medical Research Council, The Natural Environment Research Council and The Wellcome Tru. 2005. Available at: http://www.dcs.gla.ac.uk/publications/paperdetails.cfm?id=8109.
33. Starr J, Gastl A. isCitedBy: A Metadata Scheme for DataCite. D-Lib Magazine. 2011;17(1/2). Available at: http://www.dlib.org/dlib/january11/starr/01starr.html [Accessed February 27, 2012].
34. Tenopir C, Allard S, Douglass K, et al. Data Sharing by Scientists: Practices and Perceptions Neylon C, ed. PLoS ONE. 2011;6(6):e21101. Available at: http://dx.plos.org/10.1371/journal.pone.0021101 [Accessed June 30, 2011].
35. Teufel S, Moens M. Whatâs yours and what's mine: Determining Intellectual Attribution in Scientific Text. Proceedings of the 2000 Joint SIGDAT Conference on Empirical Methods in Natural Language Processing and Very Large Corpora. 2000. Available at: http://www.cl.cam.ac.uk/~sht25/papers/emnlp00.pdf.
36. Teufel S, Siddharthan A, Tidhar D. Automatic classification of citation function. In: Proceedings of the 2006 Conference on Empirical Methods in Natural Language Processing.; 2006:103-110. Available at: http://www.cl.cam.ac.uk/~as372/sigdial-final.pdf.
37. Thorisson GA. Accreditation and attribution in data sharing. Nature biotechnology. 2009;27(11):984-5. Available at: http://www.ncbi.nlm.nih.gov/pubmed/19898446.
38. Todd P, Ladle R. Hidden dangers of a Âcitation cultureÂ. ESEP. 2008;8:13-16.
39. Wang RY, Strong DM. Beyond accuracy: what data quality means to data consumers. Journal of Management Information Systems. 1996;12(4):5. Available at: http://w3.cyu.edu.tw/ccwei/PAPER/ERP/data quality(JMIS).pdf [Accessed July 11, 2012].
40. Feelders a, Daniels H, Holsheimer M. Methodological and practical aspects of data mining. Information & Management. 2000;37(5):271-281. Available at: http://linkinghub.elsevier.com/retrieve/pii/S0378720699000518.
41. Vasseur B, Devillers R. Ontologital Approach of the Fitness of Use of Geospatial Datasets. Proceedings of the 6th AGILE. 2003. Available at: http://dataquality.free.fr/sample/articles/AGILE03-BVetAL.PDF [Accessed July 15, 2012].
42. anon. Compete, collaborate, compel. Nat Genet. 2007;39(8). Available at: http://dx.doi.org/10.1038/ng0807-931.
43. anon. Data producers deserve citation credit. Nature genetics. 2009;41(10):1045. Available at: http://www.ncbi.nlm.nih.gov/pubmed/19786949.
44. anon. Discussing standards. Nature genetics. 2010;42(11):915. Available at: http://www.ncbi.nlm.nih.gov/pubmed/20980979 [Accessed July 14, 2012].
45. Larsen PO, Ins M von. The rate of growth in scientific publication and the decline in coverage provided by Science Citation Index. Scientometrics. 2010;84(3):575-603. Available at: http://www.pubmedcentral.nih.gov/articlerender.fcgi?artid=2909426&tool=pmcentrez&rendertype=abstract [Accessed March 13, 2012].
46. Wynholds LA, Wallis JC, Borgman CL, Sands A, Traweek S. Data, data use, and scientific inquiry. In: Proceedings of the 12th ACM/IEEE-CS joint conference on Digital Libraries - JCDL  â12. New York, New York, USA: ACM Press; 2012:19. Available at: http://dl.acm.org/citation.cfm?id=2232817.2232822 [Accessed July 13, 2012].
47. Piwowar HA, Carlson JD, Vision TJ. Beginning to track 1000 datasets from public repositories into the published literature. Proceedings of the American Society for Information Science and Technology. 2011;48(1):1-4. Available at: http://doi.wiley.com/10.1002/meet.2011.14504801337 [Accessed May 19, 2012].
48. Piwowar HA. Tracking dataset citations using common citation tracking tools doesnât work. Research Remix blog. 2010. Available at: http://researchremix.wordpress.com/2010/11/09/tracking-dataset-citations-using-common-citation-tracking-tools-doesnt-work/ [Accessed July 15, 2012].
49. Piwowar H. Thomson Reuters announces subscription-based data citation tracking tool. Research Remix blog. 2012. Available at: http://researchremix.wordpress.com/2012/06/28/data-citation-index/ [Accessed July 15, 2012].
50. Piwowar H. Care about data citation? Then you care about text-mining access. Research Remix blog. 2012. Available at: https://researchremix.wordpress.com/2012/04/19/data-citation-text-mining/ [Accessed July 15, 2012].
51. Piwowar HA, Vision TJ, Whitlock MC. Data archiving is a good investment. Nature. 2011;473(7347):285. Available at: http://dx.doi.org/10.1038/473285a [Accessed August 8, 2011].
52. Cech T, Eddy S, Eisenberg D, et al. Sharing publication-related data and materials: responsibilities of authorship in the life sciences. Plant physiology. 2003;132(1):19-24.
53. Shotton D. Oxford University Press to support Open Citations. Open Citations and Semantic Publishing blog. 2012. Available at: http://opencitations.wordpress.com/2012/06/22/oxford-university-press-to-support-open-citations/ [Accessed July 16, 2012].
54. Sayogo DS, Pardo TA. Exploring the Motive for Data Publication in Open Data Initiative: Linking Intention to Action. In: 2012 45th Hawaii International Conference on System Sciences. IEEE; 2012:2623-2632. Available at: http://dl.acm.org/citation.cfm?id=2116261.2116762 [Accessed July 16, 2012].
55. Bornmann L, Daniel H-D. What do citation counts measure? A review of studies on citing behavior. Journal of Documentation. 2008;64(1):45-80. Available at: /journals.htm?issn=0022-0418&volume=64&issue=1&articleid=1657903&show=html [Accessed July 16, 2012].
56. Wouters P. A Citation Culture. Available at: http://garfield.library.upenn.edu/wouters/wouters.pdf [Accessed July 16, 2012].
57. Piwowar H. Probability of observed third-party data reuse. FigShare. 2012. Available at: http://figshare.com/articles/Probability_of_observed_third-party_data_reuse/92959 [Accessed July 16, 2012].
58. Zimmerman AS. Data Sharing and Secondary Use of Scientific Data: Experiences of Ecologists. Available at: http://deepblue.lib.umich.edu/handle/2027.42/39373.
59. Whitlock MC. Data archiving in ecology and evolution: best practices. Trends in ecology & evolution. 2011;26(2):61-5. Available at: http://www.ncbi.nlm.nih.gov/pubmed/21159406 [Accessed July 15, 2012].
60. Michener WK, Porter J, Servilla M, Vanderbilt K. Long term ecological research and information management. Ecological Informatics. 2011;6(1):13-24. Available at: http://linkinghub.elsevier.com/retrieve/pii/S1574954110001159 [Accessed July 17, 2012].
61. Howison J. Scientific software production: incentives and collaboration. Proceedings of the ACM 2011 conference on. 2011. Available at: http://dl.acm.org/citation.cfm?id=1958904 [Accessed July 17, 2012].
62. Carlisle JB. The analysis of 168 randomised controlled trials to test data integrity. Anaesthesia. 2012;67(5):521-37. Available at: http://www.ncbi.nlm.nih.gov/pubmed/22404311 [Accessed July 17, 2012].
63. Miller DR. Publication fraud: implications to the individual and to the specialty. Current opinion in anaesthesiology. 2011;24(2):154-9. Available at: http://www.ncbi.nlm.nih.gov/pubmed/21252647 [Accessed July 17, 2012].
64. Shafer SL. Tattered threads. Anesthesia and analgesia. 2009;108(5):1361-3. Available at: http://www.ncbi.nlm.nih.gov/pubmed/19372305 [Accessed July 17, 2012].
65. Callaghan S, Hewer F, Pepler S, Hardaker P. Overlay journals and data publishing in the meteorological sciences. Ariadne. 2009;(July):1-8. Available at: http://www.ariadne.ac.uk/issue60/callaghan-et-al/ [Accessed July 17, 2012].
66. Wallis JC, Milojevic S, Borgman CL, Sandoval W a. The Special Case of Scientific Data Sharing with Education. Proceedings of the American Society for Information Science and Technology. 2006;43(1):1-13. Available at: http://doi.wiley.com/10.1002/meet.14504301169.
67. Edwards PN, Mayernik MS, Batcheller a. L, Bowker GC, Borgman CL. Science friction: Data, metadata, and collaboration. Social Studies of Science. 2011;41(5):667-690. Available at: http://sss.sagepub.com/cgi/doi/10.1177/0306312711413314 [Accessed July 17, 2012].
68. Sompel HVD, Lagoze C, Nelson ML, et al. Adding eScience Assets to the Data Web Aggregations in Scholarly Communication. Management.
69. Neylon C, Wu S. Article-level metrics and the evolution of scientific impact. PLoS Biology. 2009;7(11):e1000242.


