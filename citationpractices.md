





# knitr citationpractices manuscript
 * author of this file: Heather Piwowar, <hpiwowar@gmail.com>
 * license: CC0
 * Acknowledgements: thanks to Yihui Xie for knitr and Carl Boettiger for his clear examples of this literate programming framework. 
 * Generated on <code class="knitr inline">Thu Jul 19 12:19:22 2012</code>

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












# Making data Count: tracking data citations through the scholarly literature and beyond

The References section is a fundamental part of any research paper.  When the references in a paper are indexed, the references contribute to the set of known relationships between scholarship.  Over the past 50 years, the resulting citation indices have become  backbones of scholarly reward and discovery systems.  We now rely on citation indices to such a large extent that if a scholarly contribution does not participate in the citation system it is a bystander to academic reward and discovery.

It is crucially important, therefore, that all scholarship of note participates fully in the citation system: a research object needs a well-defined citation representation, it needs to be cited in the references section when appropriate, citations to it need to be indexed, and finally the indexed data needs to be interpreted and used.

Research datasets did not historically participate in the citation system as independent objects: datasets were often attributed through proxy articles or or overlooked due to non-indexible attribution in the methods or acknowlegement sections.  There has been growing recognition that reserach data should be treated as a first-class research object.

For data citations to be useful, data must be citable, must be cited, and then must be indexed.

To date, conversations about data citation have largely ignored the step of indexing data citations.  In this report we focus on this tracking stage: what needs to happen to facilitate the indexing, interpretation, and use of citations to datasets. 


## 1. Why data citation tracking

Data attribution tracking has many uses, from the commonly touted goal of rewarding data collecting investigators to less-frequently highlighted infrastructure uses in discovery and filtering.  Below, we explore reasons to track citations to datasets themselves to motivate and inform infrastructure and metrics that will be needed.

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
 

(Piwowar _et. al._ 2011)

Documenting this value is often a condition of funding.

### Discover associated analyses, datasets, and researcher communities

Just as journals often citations of articles on their websites to provide context and discovery, data repositories may want to list reuses on the page that provides the data.  Indeed, ICPSR and ORNL DAAC do this now, based on time-consuming manual searches.

Data citations could also facilitate discovery of associated datasets through recommender systems (Michener _et. al._ 2011).  A paper that cites two datasets is a valuable clue that someone who is interested in the first dataset would also be interested in the second.

### Alert investigators of reanalyses

Without citation tracking it is difficult for investigators to receive notifications of reanalyses of a particular dataset.  This is important for  data collection investigators: the team that collected the data is often very interested to learn about and verify future analyses (Tenopir _et. al._ 2011) (Whitlock, 2011).

Alerts would also be useful to data using scientists: those considering or in the midst of a reanalysis may want to sign up for alerts to learn of what others are publishing.

Full-text search alerts are poor approximations for citation-based alerts.  Citation-based alerts forthe paper describing data collection are also a poor solution, since data reanalyses can get lost in the citation deluge received by very popular papers.

### Filter for frequently used -- or neglected! -- datasets 

Some datasets are used often whereas others are never used (Piwowar, 2012).  Scientists may want to filter datasets by the frequency of use.  Some scientists may be looking for dataset that has been used frequently: frequent reuse may serve as a quality indicator by signalling a strong reputation and believability (Wang & Strong, 1996) (Pradhan, 2005).

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

### Impact elsewhere in academic reserach

As scholarly discussion moves online and is captured by a wide variety of product types, evidence of impact may occur in a wide variety of fora, beyond the traditional scholarly literature.  For example, dataset metadata may cite other datasets.  Academics may bookmark datasets using general purposes bookmarking tools (i.e. delicious) or general-purpose reference managers (Mendeley and Zotero).  Datasets of interest may be the topic of blogs, tweets, and preprints.  The number of times a dataset has been viewed or downloaded is also interesting.

Downloads area already displayed in some data repositories (Dryad, FigShare).  ICPSR, in particular, reveals aggregated statistics about download uses at the dataset level, which can reveal, for example whether students find a particular dataset useful.

Several tools are beginning to reveal these statistics and  discussion of datasets in social media (altmetric.com, total-impact).Such measurements are often called alternative metrics, or altmetrics.

(Chavan & Ingwersen, 2009)

F1000R preprints

### Impact outside academic research

Reuse by students, journalists, policy makers, clinitians, startup companies, established industry leaders -- all of these uses are valuable and worth noting to fuel reward and discovery.

(Wallis _et. al._ 2006)

Tracking citations in research publications, however, fail to capture these impacts.  As diverse uses move online, and datasets begin to be identified witn unique identifiers, more and more uses can be tracked automatrically.  Evidence of impact will likely be found in syllabi, textbooks, statistical package READMEs, patent applications, data journalism news articles, blogs, and more.

### Context of reuses

Automated determination of citation function [Teufel2006] and its role in new ideas within the paper [teufel2000].

(Teufel _et. al._ 2006)
(Teufel & Moens, 2000)
(Shotton, 2010)


### Reuses of the reuses

Sometimes the best way to look at the value of something is to look at its second-order use:  Did the metaanalysis which included the datset cause a significant change in healthcare practice?  How impactful was the blog post *about* the dataset?

A limited version of this type of analysis is directly possible from a citation graph, the same way that PageRank or EigenFactor are based on linked networks.  These approaches ignore the issue of the role of the dataset in acheiving the second-order effect, so they must be used in concert with complementary information.  Nonetheless, this sort of information is key to understanding the true value of a resource. 


### Impact flavour

We want to do more than just measure numbers.  We want to assess *type*. (Priem _et. al._ 2012)

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

(Chavan & Ingwersen, 2009)
(Lozano _et. al._ 2012)
(Seglen, 1997)
(Todd & Ladle, 2008)


### Aggregation: project-level, grant-level, repository-level and beyond

Metrics have many audiences. 

For many fields and datatypes it seems appropriate to track data on the dataset or data package level.  "Dataset-level metrics" are analogous to "article-level metrics" now gaining ground for research papers.

(Neylon & Wu, 2009)

The specific level of granularity may differ for diferent fields and datatypes (data file, data package, data row).  If data citations are tracked at the level of granularity they are cited, higher-level analyses can aggregate them.

(Van de Sompel _et. al._ 2009)

A good rule of thumb might be to track data attribution at the highest level of abstraction with common methods of collection and contributing investigators and institutions.


## 3. How to get there

### Standardize

(Mooney & Newton, 2012)
(Mooney, 2011)
(Altman & King, 2007)
(Cook, 2008)
(Sieber & Trumbo, 1995)
(Cronin, 1995)


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

(Seeber, 2008)

### Fix problematic policies

* Limit on number of references

* Putting references in supplementary methods
[Citations in supplementary information are invisible]

* Only including peer-reviewed resources in references

* Not including data sharing paper as a citation.  This would be the most natural way to link a paper that describes data collection and dataset, yet none of Dryad's journals do it.  There is a concern this would be counted as citation grabbing.  Unfortunately, without it, we are left with trying to use metadata that is often incomplete to find these relationships.


data journalism


(Seeber, 2008)

Problems differentiating data sharing from data reuse

(N\'{e}v\'{e}ol _et. al._ 2011)

Linking database submissions to primary citations with PubMed Central: (Piwowar & Chapman, 2008)

Identifying data sharing in biomedical literature: (Piwowar & Chapman, 2008)


### Open, machine-readable reference lists

not nc

(Shotton, 2012)
(Shotton _et. al._ 2009)
https://researchremix.wordpress.com/2012/04/19/data-citation-text-mining/

### Build lots of tools

We are making promises to data creators about attribution and reward that we can’t keep.  ”Make your data citeable!” is the cry.  Ok.  So citeable is step one.  Cited is step two.  But for the citation to be useful, it has to be indexed so that citation metrics can be tracked and admired and used.  Who is indexing data citations right now?  As far as I can tell: absolutely no one.

(Bakkalbasi _et. al._ 2006)

Some tracking tools, like Google Scholar, have decided not to track datasets.

Others are are only willing to track peer-reviewed resources (http://f1000research.com/2012/07/09/we-are-almost-there/).

The two major bibliometric resources, Web of Science and Scopus, do not retain dois or urls in the references they collect.  As a result, dataset identifiers are lost and citations to data cannot be tracked.

<img src="http://dl.dropbox.com/u/5485507/datacitation/datacitationstudy/figure/ORNLDAACinPaper.png" height=200/>

<img src="http://dl.dropbox.com/u/5485507/datacitation/datacitationstudy/figure/ORNLDAACinScopus.png" height=200/>

Funding

(Larsen & Ins, 2010)
Tracking dataset citations using common citation tracking tools doesnât work (Piwowar, 2010)
Thomson Reuters announces subscription-based data citation tracking tool (Piwowar, 2012)

Tools to ping

(Pepler, 2008)


Tools that support data citation in manuscripts:

(character(0))


### Do the research





Correlations between metadata and reuse

### Invite (and act on!) evidence of impact






## 4. Conclusion

A future where data attribution counts.
A future about *what kind* of contribution a dataset makes, not just a number.
Emerging data citation best practices are not yet supported by existing attribution tracking tools.  Agreement on policy and technical infrastructure must go hand in hand in order for benefits of reuse to be realized.
Data is the lifeblood of science, let’s give it the respect it deserves.


<div class="chunk"><div class="rcode"><div class="source"><pre class="knitr">  <span class="functioncall">names</span><span class="keyword">(</span><span class="symbol">biblio</span><span class="keyword">)</span>
</pre></div><div class="output"><pre class="knitr">##  [1] "abbott:2010"                         
##  [2] "altman:2007"                         
##  [3] "anon:2007"                           
##  [4] "anon:2009"                           
##  [5] "anon:2010"                           
##  [6] "armbruster:2008"                     
##  [7] "bachrach:2004"                       
##  [8] "bakkalbasi:2006"                     
##  [9] "bornmann:2008"                       
## [10] "callaghan:2009"                      
## [11] "carlisle:2012"                       
## [12] "cech:2003"                           
## [13] "chavan:2009"                         
## [14] "cook:2008"                           
## [15] "costello:2009"                       
## [16] "cronin:1995"                         
## [17] "edmunds:2012"                        
## [18] "edwards:2011"                        
## [19] "feelders:2000"                       
## [20] "haustein:2011"                       
## [21] "hine:2006"                           
## [22] "howison:2011"                        
## [23] "lane:2010"                           
## [24] "larsen:2010"                         
## [25] "lawrence:2011"                       
## [26] "lozano:2012"                         
## [27] "michener:2011"                       
## [28] "miller:2011"                         
## [29] "mons:2011"                           
## [30] "mooney:2011"                         
## [31] "mooney:2012"                         
## [32] "nelson:2012"                         
## [33] "neveol:2011"                         
## [34] "neylon:2009"                         
## [35] "opportunities-for-data-exchange:2012"
## [36] "parsons:2010"                        
## [37] "pepler:2008"                         
## [38] "pienta:2010"                         
## [39] "piwowar:2012"                        
## [40] "piwowar:2012b"                       
## [41] "piwowar:2012a"                       
## [42] "piwowar:2010"                        
## [43] "piwowar:2008a"                       
## [44] "piwowar:2008"                        
## [45] "piwowar:2011a"                       
## [46] "piwowar:2011"                        
## [47] "pradhan:2005"                        
## [48] "prat:2008"                           
## [49] "priem:2012"                          
## [50] "rohlfing:2012"                       
## [51] "sayogo:2012"                         
## [52] "schofield:2009"                      
## [53] "seeber:2008"                         
## [54] "seglen:1997"                         
## [55] "shafer:2009"                         
## [56] "shotton:2012"                        
## [57] "shotton:2010"                        
## [58] "shotton:2009"                        
## [59] "sieber:1995"                         
## [60] "sinnott:2005"                        
## [61] "starr:2011"                          
## [62] "tenopir:2011"                        
## [63] "teufel:2000"                         
## [64] "teufel:2006"                         
## [65] "thorisson:2009"                      
## [66] "todd:2008"                           
## [67] "van-de-sompel:2009"                  
## [68] "vasseur:2003"                        
## [69] "wallis:2006"                         
## [70] "wang:1996"                           
## [71] "whitlock:2011"                       
## [72] "wouters:"                            
## [73] "wynholds:2012"                       
</pre></div><div class="source"><pre class="knitr">
<span class="comment">#citep(biblio[names(biblio)])</span>
</pre></div></div></div>


## References

<p>Altman M and King G (2007).
&ldquo;A proposed standard for the scholarly citation of quantitative data.&rdquo;
<EM>D-Lib Magazine</EM>, <B>13</B>(3/4).
<a href="http://gking.harvard.edu/files/abs/cite-abs.shtml">http://gking.harvard.edu/files/abs/cite-abs.shtml</a>.

<p>Anon (2007).
&ldquo;Compete, collaborate, compel.&rdquo;
<EM>Nat Genet</EM>, <B>39</B>(8).
<a href="http://dx.doi.org/10.1038/ng0807-931">http://dx.doi.org/10.1038/ng0807-931</a>.

<p>Anon (2009).
&ldquo;Data producers deserve citation credit.&rdquo;
<EM>Nature genetics</EM>, <B>41</B>(10), pp. 1045.
<a href="http://www.ncbi.nlm.nih.gov/pubmed/19786949">http://www.ncbi.nlm.nih.gov/pubmed/19786949</a>.

<p>Anon (2010).
&ldquo;Discussing standards.&rdquo;
<EM>Nature genetics</EM>, <B>42</B>(11), pp. 915.
ISSN 1546-1718, <a href="http://dx.doi.org/10.1038/ng1110-915">http://dx.doi.org/10.1038/ng1110-915</a>, <a href="http://www.ncbi.nlm.nih.gov/pubmed/20980979">http://www.ncbi.nlm.nih.gov/pubmed/20980979</a>.

<p>Bachrach CA and King RB (2004).
&ldquo;Data sharing and duplication: is there a problem?&rdquo;
<EM>Archives of pediatrics \&amp; adolescent medicine</EM>, <B>158</B>(9), pp. 931&ndash;2.
ISSN 1072-4710, <a href="http://archpedi.jamanetwork.com/article.aspx?articleid=485802">http://archpedi.jamanetwork.com/article.aspx?articleid=485802</a>.

<p>Bakkalbasi N, Bauer K, Glover J and Wang L (2006).
&ldquo;Three options for citation tracking: Google Scholar, Scopus and Web of Science.&rdquo;
<EM>Biomedical digital libraries</EM>, <B>3</B>, pp. 7.
ISSN 1742-5581, <a href="http://www.pubmedcentral.nih.gov/articlerender.fcgi?artid=1533854\&amp;tool=pmcentrez\&amp;rendertype=abstract">http://www.pubmedcentral.nih.gov/articlerender.fcgi?artid=1533854\&amp;tool=pmcentrez\&amp;rendertype=abstract</a>.

<p>Callaghan S, Hewer F, Pepler S and Hardaker P (2009).
&ldquo;Overlay journals and data publishing in the meteorological sciences.&rdquo;
<EM>Ariadne</EM>, pp. 1&ndash;8.
<a href="http://www.ariadne.ac.uk/issue60/callaghan-et-al/">http://www.ariadne.ac.uk/issue60/callaghan-et-al/</a>.

<p>Cech T, Eddy S, Eisenberg D, Hersey K, Holtzman S, Poste G, Raikhel N, Scheller R, Singer D and Waltham M (2003).
&ldquo;Sharing publication-related data and materials: responsibilities of authorship in the life sciences.&rdquo;
<EM>Plant physiology</EM>, <B>132</B>(1), pp. 19&ndash;24.
ISSN 0032-0889, <a href="http://dx.doi.org/10.1104/pp.900068">http://dx.doi.org/10.1104/pp.900068</a>.

<p>Chavan VS and Ingwersen P (2009).
&ldquo;Towards a data publishing framework for primary biodiversity data: challenges and potentials for the biodiversity informatics community.&rdquo;
<EM>BMC bioinformatics</EM>, <B>10 Suppl 1</B>, pp. S2.
ISSN 1471-2105, <a href="http://dx.doi.org/10.1186/1471-2105-10-S14-S2">http://dx.doi.org/10.1186/1471-2105-10-S14-S2</a>, <a href="http://www.pubmedcentral.nih.gov/articlerender.fcgi?artid=2775148\&amp;tool=pmcentrez\&amp;rendertype=abstract">http://www.pubmedcentral.nih.gov/articlerender.fcgi?artid=2775148\&amp;tool=pmcentrez\&amp;rendertype=abstract</a>.

<p>Cook R (2008).
&ldquo;Editorial: Citations to Published Data Sets.&rdquo;
<EM>FLUXNET newsletter</EM>, <B>4</B>, pp. 1&ndash;2.

<p>Cronin B (1995).
&ldquo;The Scholar's Courtesy: The Role of Acknowledgement in the Primary Communication Process.&rdquo;
<a href="http://onlinebooks.library.upenn.edu/webbin/book/lookupid?key=olbp40644">http://onlinebooks.library.upenn.edu/webbin/book/lookupid?key=olbp40644</a>.

<p>Edmunds SC, Pollard TJ, Hole B and Basford A (2012).
&ldquo;Adventures in data citation: sorghum genome data exemplifies the new gold standard.&rdquo;
<EM>BMC Research Notes</EM>, <B>5</B>(1), pp. 223.
ISSN 1756-0500, <a href="http://www.ncbi.nlm.nih.gov/pubmed/22571506">http://www.ncbi.nlm.nih.gov/pubmed/22571506</a>.

<p>Howison J (2011).
&ldquo;Scientific software production: incentives and collaboration.&rdquo;
<EM>Proceedings of the ACM 2011 conference on</EM>.
<a href="http://dl.acm.org/citation.cfm?id=1958904">http://dl.acm.org/citation.cfm?id=1958904</a>.

<p>Larsen PO and Ins Mv (2010).
&ldquo;The rate of growth in scientific publication and the decline in coverage provided by Science Citation Index.&rdquo;
<EM>Scientometrics</EM>, <B>84</B>(3), pp. 575&ndash;603.
ISSN 0138-9130, <a href="http://www.pubmedcentral.nih.gov/articlerender.fcgi?artid=2909426\&amp;tool=pmcentrez\&amp;rendertype=abstract">http://www.pubmedcentral.nih.gov/articlerender.fcgi?artid=2909426\&amp;tool=pmcentrez\&amp;rendertype=abstract</a>.

<p>Lozano GA, Lariviere V and Gingras Y (2012).
&ldquo;The weakening relationship between the Impact Factor and papers' citations in the digital age.&rdquo;
<EM>arXiv</EM>, pp. 14.
1205.4328, <a href="http://arxiv.org/abs/1205.4328">http://arxiv.org/abs/1205.4328</a>.

<p>Michener WK, Porter J, Servilla M and Vanderbilt K (2011).
&ldquo;Long term ecological research and information management.&rdquo;
<EM>Ecological Informatics</EM>, <B>6</B>(1), pp. 13&ndash;24.
ISSN 15749541, <a href="http://dx.doi.org/10.1016/j.ecoinf.2010.11.005">http://dx.doi.org/10.1016/j.ecoinf.2010.11.005</a>, <a href="http://linkinghub.elsevier.com/retrieve/pii/S1574954110001159">http://linkinghub.elsevier.com/retrieve/pii/S1574954110001159</a>.

<p>Miller DR (2011).
&ldquo;Publication fraud: implications to the individual and to the specialty.&rdquo;
<EM>Current opinion in anaesthesiology</EM>, <B>24</B>(2), pp. 154&ndash;9.
ISSN 1473-6500, <a href="http://dx.doi.org/10.1097/ACO.0b013e328344529d">http://dx.doi.org/10.1097/ACO.0b013e328344529d</a>, <a href="http://www.ncbi.nlm.nih.gov/pubmed/21252647">http://www.ncbi.nlm.nih.gov/pubmed/21252647</a>.

<p>Mons B, Haagen Hv, Chichester C, Hoen P', Dunnen JTd, Ommen Gv, Mulligen Ev, Singh B, Hooft R, Roos M, Hammond J, Kiesel B, Giardine B, Velterop J, Groth P and Schultes E (2011).
&ldquo;The value of data.&rdquo;
<EM>Nature genetics</EM>, <B>43</B>(4), pp. 281&ndash;3.
ISSN 1546-1718, <a href="http://www.ncbi.nlm.nih.gov/pubmed/21445068">http://www.ncbi.nlm.nih.gov/pubmed/21445068</a>.

<p>Mooney H (2011).
&ldquo;Citing data sources in the social sciences: do authors do it?&rdquo;
<EM>Learned Publishing</EM>, <B>24</B>(2), pp. 10.
<a href="http://www.ingentaconnect.com/content/alpsp/lp/2011/00000024/00000002/art00004;jsessionid=9kingso9bep58.alexandra">http://www.ingentaconnect.com/content/alpsp/lp/2011/00000024/00000002/art00004;jsessionid=9kingso9bep58.alexandra</a>.

<p>Mooney H and Newton M (2012).
&ldquo;The Anatomy of a Data Citation: Discovery, Reuse, and Credit.&rdquo;
<EM>Journal of Librarianship and Scholarly Communication</EM>, <B>1</B>(1).
ISSN 2162-3309, <a href="http://jlsc-pub.org/jlsc/vol1/iss1/6">http://jlsc-pub.org/jlsc/vol1/iss1/6</a>.

<p>Névéol A, Wilbur WJ and Lu Z (2011).
&ldquo;Extraction of data deposition statements from the literature: a method for automatically tracking research results.&rdquo;
<EM>Bioinformatics (Oxford, England)</EM>, <B>27</B>(23), pp. 3306&ndash;12.
ISSN 1367-4811, <a href="http://www.pubmedcentral.nih.gov/articlerender.fcgi?artid=3223368\&amp;tool=pmcentrez\&amp;rendertype=abstract">http://www.pubmedcentral.nih.gov/articlerender.fcgi?artid=3223368\&amp;tool=pmcentrez\&amp;rendertype=abstract</a>.

<p>Neylon C and Wu S (2009).
&ldquo;Article-level metrics and the evolution of scientific impact.&rdquo;
<EM>PLoS Biology</EM>, <B>7</B>(11), pp. e1000242.
<a href="http://dx.doi.org/10.1371/journal.pbio.1000242">http://dx.doi.org/10.1371/journal.pbio.1000242</a>.

<p>Opportunities for Data Exchange (2012).
&ldquo;REPORT ON BEST PRACTICES FOR CITABILITY OF DATA AND ON EVOLVING ROLES.&rdquo;

<p>Parsons Ma, Duerr R and Minster J (2010).
&ldquo;Data Citation and Peer Review.&rdquo;
<EM>Eos, Transactions American Geophysical Union</EM>, <B>91</B>(34), pp. 297.
ISSN 0096-3941, <a href="http://dx.doi.org/10.1029/2010EO340001">http://dx.doi.org/10.1029/2010EO340001</a>, <a href="http://www.agu.org/pubs/crossref/2010/2010EO340001.shtml">http://www.agu.org/pubs/crossref/2010/2010EO340001.shtml</a>.

<p>Pepler CS (2008).
&ldquo;JISC Final Report CITATION , LOCATION, And DEPOSITION IN DISCIPLINE \&amp; INSTITUTIONAL REPOSITORIES CLADDIER.&rdquo;

<p>Piwowar HA and Chapman WW (2008).
&ldquo;Linking database submissions to primary citations with PubMed Central.&rdquo;
In <EM>BioLINK Workshop at ISMB</EM>, pp. 4.

<p>Piwowar HA (2010).
&ldquo;Tracking dataset citations using common citation tracking tools doesn't work.&rdquo;
<a href="http://researchremix.wordpress.com/2010/11/09/tracking-dataset-citations-using-common-citation-tracking-tools-doesnt-work/">http://researchremix.wordpress.com/2010/11/09/tracking-dataset-citations-using-common-citation-tracking-tools-doesnt-work/</a>.

<p>Piwowar HA, Carlson JD and Vision TJ (2011).
&ldquo;Beginning to track 1000 datasets from public repositories into the published literature.&rdquo;
<EM>Proceedings of the American Society for Information Science and Technology</EM>, <B>48</B>(1), pp. 1&ndash;4.
ISSN 00447870, <a href="http://doi.wiley.com/10.1002/meet.2011.14504801337">http://doi.wiley.com/10.1002/meet.2011.14504801337</a>.

<p>Piwowar H (2012).
&ldquo;Thomson Reuters announces subscription-based data citation tracking tool.&rdquo;
<a href="http://researchremix.wordpress.com/2012/06/28/data-citation-index/">http://researchremix.wordpress.com/2012/06/28/data-citation-index/</a>.

<p>Piwowar H (2012).
&ldquo;Care about data citation? Then you care about text-mining access.&rdquo;
<a href="https://researchremix.wordpress.com/2012/04/19/data-citation-text-mining/">https://researchremix.wordpress.com/2012/04/19/data-citation-text-mining/</a>.

<p>Pradhan S (2005).
&ldquo;Believability as an information quality dimension.&rdquo;
<EM>Proceedings of the International Conference on Information Quality (IQ)</EM>.
<a href="http://mitiq.mit.edu/ICIQ/Documents/IQ Conference 2005/Papers/BelievabilityasanIQDimension.pdf">http://mitiq.mit.edu/ICIQ/Documents/IQ Conference 2005/Papers/BelievabilityasanIQDimension.pdf</a>.

<p>Priem J, Piwowar HA and Hemminger BM (2012).
&ldquo;Altmetrics in the wild: Using social media to explore scholarly impact.&rdquo;
<EM>arXiv12034745v1 csDL 20 Mar 2012</EM>, <B>1203.4745</B>, pp. 1&ndash;23.
1203.4745, <a href="http://arxiv.org/abs/1203.4745">http://arxiv.org/abs/1203.4745</a>.

<p>Sayogo DS and Pardo TA (2012).
&ldquo;Exploring the Motive for Data Publication in Open Data Initiative: Linking Intention to Action.&rdquo;
In <EM>2012 45th Hawaii International Conference on System Sciences</EM>, pp. 2623&ndash;2632.
<a href="http://dl.acm.org/citation.cfm?id=2116261.2116762">http://dl.acm.org/citation.cfm?id=2116261.2116762</a>.

<p>Schofield PN, Bubela T, Weaver T, Portilla L, Brown SD, Hancock JM, Einhorn D, Tocchini-Valentini G, Hrabe AM and Rosenthal N (2009).
&ldquo;Post-publication sharing of data and tools.&rdquo;
<EM>Nature</EM>, <B>461</B>(7261), pp. 171.

<p>Seeber F (2008).
&ldquo;Citations in supplementary information are invisible.&rdquo;
<EM>Nature</EM>, <B>451</B>(7181), pp. 887.
<a href="http://www.nature.com/nature/journal/v451/n7181/full/451887d.html">http://www.nature.com/nature/journal/v451/n7181/full/451887d.html</a>.

<p>Seglen P (1997).
&ldquo;Why the impact factor of journals should not be used for evaluating research.&rdquo;
<EM>BMJ</EM>, <B>314</B>(7079), pp. 498&ndash;502.
<a href="http://www.ncbi.nlm.nih.gov/entrez/query.fcgi?cmd=Retrieve\&amp;db=PubMed\&amp;dopt=Citation\&amp;list\_uids=9056804">http://www.ncbi.nlm.nih.gov/entrez/query.fcgi?cmd=Retrieve\&amp;db=PubMed\&amp;dopt=Citation\&amp;list\_uids=9056804</a>.

<p>Shafer SL (2009).
&ldquo;Tattered threads.&rdquo;
<EM>Anesthesia and analgesia</EM>, <B>108</B>(5), pp. 1361&ndash;3.
ISSN 1526-7598, <a href="http://dx.doi.org/10.1213/ane.0b013e3181a16846">http://dx.doi.org/10.1213/ane.0b013e3181a16846</a>, <a href="http://www.ncbi.nlm.nih.gov/pubmed/19372305">http://www.ncbi.nlm.nih.gov/pubmed/19372305</a>.

<p>Shotton D, Portwin K, Klyne G and Miles A (2009).
&ldquo;Adventures in semantic publishing: exemplar semantic enhancements of a research article.&rdquo;
<EM>PLoS computational biology</EM>, <B>5</B>(4), pp. e1000361.
ISSN 1553-7358, <a href="http://www.pubmedcentral.nih.gov/articlerender.fcgi?artid=2663789\&amp;tool=pmcentrez\&amp;rendertype=abstract">http://www.pubmedcentral.nih.gov/articlerender.fcgi?artid=2663789\&amp;tool=pmcentrez\&amp;rendertype=abstract</a>.

<p>Shotton D (2010).
&ldquo;CiTO, the Citation Typing Ontology.&rdquo;
<EM>Journal of biomedical semantics</EM>, <B>1 Suppl 1</B>, pp. S6.
ISSN 2041-1480, <a href="http://www.pubmedcentral.nih.gov/articlerender.fcgi?artid=2903725\&amp;tool=pmcentrez\&amp;rendertype=abstract">http://www.pubmedcentral.nih.gov/articlerender.fcgi?artid=2903725\&amp;tool=pmcentrez\&amp;rendertype=abstract</a>.

<p>Shotton D (2012).
&ldquo;Oxford University Press to support Open Citations.&rdquo;
<a href="http://opencitations.wordpress.com/2012/06/22/oxford-university-press-to-support-open-citations/">http://opencitations.wordpress.com/2012/06/22/oxford-university-press-to-support-open-citations/</a>.

<p>Sieber JE and Trumbo BE (1995).
&ldquo;(Not) giving credit where credit is due: Citation of data sets.&rdquo;
<EM>Science and Engineering Ethics</EM>, <B>1</B>(1), pp. 11&ndash;20.
ISSN 1353-3452, <a href="http://dx.doi.org/10.1007/BF02628694">http://dx.doi.org/10.1007/BF02628694</a>, <a href="http://www.springerlink.com/index/10.1007/BF02628694">http://www.springerlink.com/index/10.1007/BF02628694</a>.

<p>Sinnott R, Macdonald A, Lord P, Ecklund D and Jones A (2005).
&ldquo;Large-scale data sharing in the life sciences: Data standards, incentives, barriers and funding models (The Joint Data Standards Study).&rdquo;
<EM>The Biotechnology and Biological Sciences Research Council, The Department of Trade and Industry, The Joint Information Systems Committee for Support for Research, The Medical Research Council, The Natural Environment Research Council and The Wellcome Tru</EM>.
<a href="http://www.dcs.gla.ac.uk/publications/paperdetails.cfm?id=8109">http://www.dcs.gla.ac.uk/publications/paperdetails.cfm?id=8109</a>.

<p>Starr J and Gastl A (2011).
&ldquo;isCitedBy: A Metadata Scheme for DataCite.&rdquo;
<EM>D-Lib Magazine</EM>, <B>17</B>(1/2).
ISSN 1082-9873, <a href="http://www.dlib.org/dlib/january11/starr/01starr.html">http://www.dlib.org/dlib/january11/starr/01starr.html</a>.

<p>Tenopir C, Allard S, Douglass K, Aydinoglu AU, Wu L, Read E, Manoff M and Frame M (2011).
&ldquo;Data Sharing by Scientists: Practices and Perceptions.&rdquo;
<EM>PLoS ONE</EM>, <B>6</B>(6), pp. e21101.
ISSN 1932-6203, <a href="http://dx.doi.org/10.1371/journal.pone.0021101">http://dx.doi.org/10.1371/journal.pone.0021101</a>, <a href="http://dx.plos.org/10.1371/journal.pone.0021101">http://dx.plos.org/10.1371/journal.pone.0021101</a>.

<p>Teufel S and Moens M (2000).
&ldquo;What's yours and what's mine: Determining Intellectual Attribution in Scientific Text.&rdquo;
<EM>Proceedings of the 2000 Joint SIGDAT Conference on Empirical Methods in Natural Language Processing and Very Large Corpora</EM>.
<a href="http://www.cl.cam.ac.uk/~sht25/papers/emnlp00.pdf">http://www.cl.cam.ac.uk/~sht25/papers/emnlp00.pdf</a>.

<p>Teufel S, Siddharthan A and Tidhar D (2006).
&ldquo;Automatic classification of citation function.&rdquo;
In <EM>Proceedings of the 2006 Conference on Empirical Methods in Natural Language Processing</EM>, pp. 103&ndash;110.
<a href="http://www.cl.cam.ac.uk/~as372/sigdial-final.pdf">http://www.cl.cam.ac.uk/~as372/sigdial-final.pdf</a>.

<p>Thorisson GA (2009).
&ldquo;Accreditation and attribution in data sharing.&rdquo;
<EM>Nature biotechnology</EM>, <B>27</B>(11), pp. 984&ndash;5.
<a href="http://www.ncbi.nlm.nih.gov/pubmed/19898446">http://www.ncbi.nlm.nih.gov/pubmed/19898446</a>.

<p>Todd P and Ladle R (2008).
&ldquo;Hidden dangers of a citation culture.&rdquo;
<EM>ESEP.</EM>, <B>8</B>, pp. 13&ndash;16.
<a href="http://dx.doi.org/10.3354/esep00091">http://dx.doi.org/10.3354/esep00091</a>.

<p>Van de Sompel H, Lagoze C, Nelson ML, Warner S, Sanderson R and Johnston P (2009).
&ldquo;Adding eScience Assets to the Data Web.&rdquo;
<EM>Management</EM>, pp. 10.
0906.2135, <a href="http://arxiv.org/abs/0906.2135">http://arxiv.org/abs/0906.2135</a>.

<p>Wallis JC, Milojevic S, Borgman CL and Sandoval Wa (2006).
&ldquo;The Special Case of Scientific Data Sharing with Education.&rdquo;
<EM>Proceedings of the American Society for Information Science and Technology</EM>, <B>43</B>(1), pp. 1&ndash;13.
<a href="http://doi.wiley.com/10.1002/meet.14504301169">http://doi.wiley.com/10.1002/meet.14504301169</a>.

<p>Wang RY and Strong DM (1996).
&ldquo;Beyond accuracy: what data quality means to data consumers.&rdquo;
<EM>Journal of Management Information Systems</EM>, <B>12</B>(4), pp. 5.
<a href="http://w3.cyu.edu.tw/ccwei/PAPER/ERP/data quality(JMIS).pdf">http://w3.cyu.edu.tw/ccwei/PAPER/ERP/data quality(JMIS).pdf</a>.

<p>Whitlock MC (2011).
&ldquo;Data archiving in ecology and evolution: best practices.&rdquo;
<EM>Trends in ecology \&amp; evolution</EM>, <B>26</B>(2), pp. 61&ndash;5.
ISSN 0169-5347, <a href="http://dx.doi.org/10.1016/j.tree.2010.11.006">http://dx.doi.org/10.1016/j.tree.2010.11.006</a>, <a href="http://www.ncbi.nlm.nih.gov/pubmed/21159406">http://www.ncbi.nlm.nih.gov/pubmed/21159406</a>.





