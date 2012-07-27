

<div class="chunk"><div class="rcode"><div class="error"><pre class="knitr R">## Error: 'prefix' is missing
</pre></div></div></div>



# knitr citationpractices manuscript
 * author of this file: Heather Piwowar, <hpiwowar@gmail.com>
 * license: CC0
 * Acknowledgements: thanks to Yihui Xie for knitr and Carl Boettiger for his clear examples of this literate programming framework. 
 * Generated on <code class="knitr inline">Fri Jul 27 14:34:32 2012</code>

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












# Making data Count: tracking data impact through the scholarly literature and beyond

Citation tracking is a key component of our scholarly infrastructure.  When a research object is used, referenced, and indexed, it forms a navigable and countable link between the citing article and the cited object.  Over the past 50 years, the resulting indices have become backbones of scholarly reward and discovery systems.

It is crucially important, therefore, that all noteworthy scholarship participates fully in the citation system.  The first step is that all research objects must be citeable.  Then, when appropriate, research objects must be attributed in the References section of a paper, the reference must be indexed, and finally the citation index needs to be interpreted and used.

Research datasets have not historically participated in the citation system as independent objects: datasets have been attributed by proxy through article that describe data collection, or informally in acknowledgment sections.  In recent years there has been growing recognition that research data should be treated as a first-class research objects.  Much attention has been paid to defining standard data citation formats and education.

To date, however, there has been little conversation and even less progress on ensuring that data citations, once referenced, are indexed.  We focus on this tracking stage: what is needed to facilitate the indexing, interpretation, and use of impact metrics for datasets. 


## 1. Why data impact tracking?

### Encourage data archiving

Many editorials and white papers have called for data citations to reward data collecting investigators who make their data available for reuse (Cech _et. al._ 2003; Sinnott _et. al._ 2005; Anon, 2007; Anon, 2009; Thorisson, 2009; Schofield _et. al._ 2009; Anon, 2010; Edmunds _et. al._ 2012).

Evidence suggests policy suggestions are on track: most researchers state that citation is an important incentive for making their data available: anticipating citations was the most important condition for sharing data in a recent study (Tenopir _et. al._ 2011), mentioned by 92% of respondents.  Within a structural model of motivation, investigators who valued proper attribution were found more likely to share data than those who didn't (Sayogo & Pardo, 2012).

Indeed, when journals announce stronger policies for data archiving, they often make the case in part by highlighting evidence of increased citation rate [see http://datadryad.org/jdap].


### Reward the most useful collection, curation, and dissemination of data

A large proportion of investigators who make their data available will receive a citation boost, given that a substantial portion of available datasets are reused (Piwowar, 2012).

That said, the largest citation boost will probably correlate with datasets that are reused most often.  More research is needed to understand what factors correlate with high levels of reuse, but metadata and infrastructure likely play a role: can a new investigator easily find a dataset, understand it, and integrate it into established systems?

Another way to increase the citation boost by a certain date is to make it available earlier.  A recent article reports that this incentive made early dissemination of a recent high-profile dataset more attractive to its authors (Edmunds _et. al._ 2012).

Reward that correlates with successful data reuse will aligning incentives for data creators, curators, and reusers, encouraging the most useful collection, curation, and dissemination.

### Include all relevant contributors in reward structure

Tracking attribution to datasets as standalone research objects provides a specific path of reward for those who contributed to the dataset.  The existence of this path eliminates several problems with reliance on attribution through a research article byline.

First, it provides a path to reward to all of those who contributed to the data product, including those who are normally overlooked: techs, data curators, data editors, and data repositories.  Individuals and entities can be included in either the data reference itself (Parsons _et. al._ 2010) or through linked metadata (Starr & Gastl, 2011), assuming these links are maintained in the index.  Tracked contributions are notably important for data archives, because they often need to provide regular evidence of their value to funders 
(Fry _et. al._ 2009) (Piwowar _et. al._ 2011).

Second, attribution to datasets allows the byline of a research article to be restricted to those who have made an intellectual contribution to the article and given their final approval over the manuscript (Rohlfing & Poline, 2012), because  alternate paths exist to attribute other contributions.

Third, attribution to datasets appropriately provides double-attribution for those who do double work: investigators who contribute to both a reusable dataset product and an intellectual analysis paper are rewarded for both (Whitlock, 2011).

### Discover associated analyses, datasets, and researcher communities

Just as journals often provide links to articles that cite their articles, for context and discovery, data repositories may wish to provide links to known reuses of datasets.  Indeed, ICPSR and ORNL DAAC do this now, based on data collected through time-consuming manual searches.  Automatically indexed data citations make it much simpler to include these links.

Data citation links could also be used to recommend datasets  (Michener _et. al._ 2011).  If two datasets are often cited together, it is likely that a website visitor exploring the first dataset may also be interested in the second.

### Alert investigators of reanalyses

Citation tracking makes it possible for investigators to receive notifications of reanalyses of a particular dataset.  The team that collected the data is often very interested to learn about and verify future analyses (Tenopir _et. al._ 2011) (Whitlock, 2011).  Alerts would also be useful to scientists who reuse data: those considering or in the midst of a reanalysis may want to sign up for alerts to learn what others are publishing.

Substitutes for alerts based on citations to datasets are problematic.  Alerts based on full-text searches are inaccurate and have poor recall.  Alerts based instead on the paper describing data collection are also a poor solution, since data reanalyses can get lost in the citation deluge received by very popular papers.

### Filter for frequently used -- or neglected! -- datasets 

Some scientists may want to filter datasets by the frequency of use.  One scientists may be particularly interested in data that has been used frequently: frequent reuse may serve as a quality indicator of reputation and believability (Wang & Strong, 1996) (Pradhan, 2005).  Another researcher may be interested in data that has been used infrequently, to find a datasets rich with untapped research potential.

### Identify analyses based on problematic datasets

Occasionally a dataset is found to have quality problems.  Whether data is intentionally faked [Carlisle], found to have errors due to an innocent mistake, or even just considered misleading due to constantly improving quality standards, the result is the same: analyses built on data sometimes sometimes need to be reconsidered.  Citation indexing allows the literature build on these results to be identified and reinterpreted (Miller, 2011) (Shafer, 2009).

### Avoid harmful shoehorning

Several publishers have launched "data journals", piggybacking on the existing article infrastructure and reward system.  Some data overlay journals add value to an archived dataset by providing additional metadata or formal peer-review (Callaghan _et. al._ 2009).  In other instances, data journals simply serve as a proxy citation to a dataset.

Shoehorning data into the existing journal system to facilitate formal attribution is a reasonable stop-gap measure, but not the best long term solution.  Supporting direct citation to archived datasets avoids compromise solutions that cost time and money.

### Trail-blaze for recognition of other research types

Progress toward citation of research data is much further along than citation to other types of non-traditional scholarly products, such as research software (Howison, 2011).  Tracking data citations will blaze the trail for recognition of other types of research objects. 

### Drive policy, funding, and tool requirements based on evidence

Finally, tracking data allows policy makers, funders, and tool builders to know what has facilitated data reuse and what hasn't.  Real evidence is needed to inform decision about what kind of standards facilitate reuse, how much data curation is necessary, whether embargoes strike an appropriate balance, and whether tool features are being used.

For example,  policy makers concerned that data availability would lead to duplicated analyses have since received evidence this is not the case (Bachrach & King, 2004).

Making decisions without evidence surely leads to wasted money, time, and opportunities.


## 2. What to Count

### Dataset citations in the academic literature

The most obvious  metric for tracking data citations is to count the number of times that dataset unique identifiers occur in formal reference lists in the published literature.  This is analogous to counting citations to research papers.

"Dataset-level metrics" are analogous to "article-level metrics" now gaining ground for research papers.  (Neylon & Wu, 2009).  Project-level aggregation and grant-level aggregation may also be useful for investigators summarizing their impact to their insitution or funder.

### Impact beyond citations

Citations often take years to accrue; citations based on data reuse may take even longer than citations that pay attribution to an idea.  An early indicator of citation count may be found in download statistics.  Several data repositories already display download counts (Dryad, FigShare).  ICPSR, takes this one step further, displaying aggregated breakdown statistics about what sort of authenticated users have downloaded the datasets.  As discussed in (Chavan & Ingwersen, 2009), many associated metrics can also be displayed, including number of unique visits and number of loyal visits.

Other indications of dataset impact can be found online.  For example, datasets may cite other datasets in their metadata.  Academics may bookmark datasets using general purposes bookmarking tools (i.e. delicious) or general-purpose reference managers (Mendeley and Zotero).  Datasets may be the topic of preprints, blogs, and tweets.

Several tools are beginning to reveal these statistics and  discussion of datasets in social media (altmetric.com, total-impact).Such measurements are often called alternative metrics, or altmetrics.

### Impact beyond academic research

Much data reuse may go on outside academia, reuse by journalists, policy makers, clinicians, industry, and students (Wallis _et. al._ 2006).

Tracking citations in research publications, however, fail to capture these impacts.  Evidence of impact will likely be found in syllabi, textbooks, statistical package READMEs, patent applications, data journalism news articles, blogs, and more. 


### Reuses of the reuses

Another valuable metric is second-order use:  how impactful is the research which uses the dataset?  A citation-based version of second-order impact can be derived from the full citation graph.

### Context

Reference links offer much richer data than mere counts.  The reference link is made in a context that can be used to weight or characterize the relationship.  CiTO -- the Citation Typing Ontology -- defines relationships between citing and cited document, including "confirms", "extends", "updates", "corrects", and "refutes". (Shotton, 2010).  These relationships usually implicit in the full text of an article.  Widespread use of citation typing will either require large-scale manual annotation or automated classification of citation function (Teufel _et. al._ 2006).

There are other aspects of reference context that may also be interesting.  Understanding the relative importance of a dataset to a paper may be proportional to the number of citation mentions it includes.  The section of the reference may also be instructive.

### Impact flavour

Datasets likely make different types of impact.  Some may be great for calibration, others for training, others to test new methods.  A few datasets may be particularly useful for exploring new hypotheses.

This "impact flavour" won't be clear from citation counts alone, but it can likely be derived from a combination of impact indicators and context (Priem _et. al._ 2012).  Understanding the impact flavour of a dataset allows different datasets to be appreciated and discovered based on their strengths.

### Impact Story rather than Impact Factor

It is possible to imagine using these metrics to calculate a  Repository Impact Factor.  While it is important for repositories to measure the value they provide, optimizing for a high average impact would likely to lead to decisions that are not ideal for efficient or effective research.  For example, maintaining a high average citation count would discourage preserving datasets from small niche domains and untested research fronts. 

Thanks to a wide array of metrics and context, a repository's impact story can instead be told as a more complex story that highlights the types of reuse it has facilitated.  This story could be told qualitatively, through visible success stories that might be discovered through tracking data reuse.  Subtle impact patterns can also be captured and described quantitatively.


## 3. How to get there

### Standardize

The first task in standars for data citation tracking, and the one that has received most attention thus far, is to make data citable.  This primarily involves hosting the data in a permanent location, deciding how to handle granularity and versions, assigning one or more unique identifiers, and revealing related metadata like title and author names.  Several data archives have led the way in making their data citeable, including DataVerse (Altman & King, 2007), Pagaea, ICPSR, ORNL DAAC (Cook, 2008), International Polar Year, Dryad, and FigShare.  WebCite is a complementary solution for data on websites.

DataCite has led the way to a standard set of minimum metadata for a citeable dataset, and a standard represetnation.  DataCite also provides a citation metadata repository so that metadata can be retrieved from a citation identifier alone.  As CrossRef has shown, keepign metadata in structured format is very useful.

Once data is citeable, ideally standards would emerge for how to cite it.  A citation standard has several components:

- which data elements are included in a citation reference
- the citation formatting of the data elements
- the location of the reference

Which data elements are included in a citation and how those elements are formatted has traditionally been the domain of journals that publish a paper with a references list.  Journals usually choose one of many established style guides, sometimes with custom modificatons.

The location of a citation list has also been specified by journal style guildelines.  It is common to include them in a "Referendes" section, but in some domains some formal or informal citation also occur in footnotes, acknowledgement sections, supplementary material, or in-text hyperlinks.

As we discuss in the next section, several style guides have begun to include specifications for datasets, and a few journals include related information in their instruction to author guidelines.

It is worth noting that, despite many calls and several competing standards (http://www.iso.org/iso/catalogue_detail.htm?csnumber=43320, http://dublincore.org/groups/citation/citstds.html, http://www.ncbi.nlm.nih.gov/pmc/pmcdoc/tagging-guidelines/citations/v3/toc.html, http://www.niso.org/publications/rp/RP-2005-03.pdf), scholarly publishing has not adopted a common format for citation of traditional reserach objects.  Although it would be helpful for indexing, it is unlikely that a single unified standard will emerge for how or where to cite a dataset.

### Educate, encourage, expect, and enforce data citation

As our existing infrastructure demonstrates, citation indexing is possible even without adhering to a single standard.  Although standards are unlikely, many stakeholders can help educate, encourage, expect, and enforce citation best practices that permit indexing.

The primary focus in most fields is data that supports the findings in peer-reviewed journal publications.  We investigated a wide variety of sources for data citation policies that authors must comply with, from funders, repositories, and journals.  We found limited and variable guidance.

Table:  regression information for which journals are most likely to have policies.  If we look into these further, we can see that journals with highest impact factors are most likely to have policies.
Graph:  boxplot of journal impact factors, for “no policy, requests, requires” ?
Paragraph of results like in Nic’s ASIS&T poster abstract:

Table:  Data citation policies of Funders, Journal, Repositories.  Subdivide with line in between funders, journals, and repositories.  Columns:

* No policy for data citation (lists all funders with no policy, in alphabetical order)
* Mentions data citation (lists all funders that mention data citation, with exerpt in parantheses)
http://precedings.nature.com/documents/5452/version/1

<img src="http://dl.dropbox.com/u/5485507/datacitation/datacitationstudy/figure/CitationPatterns.png" height=150/>
*Figure 1: Citation patterns*

(We examined actual attribution practice by researchers.  Researchers are clearly mixing and matching different expectations in a  context sensitive manner, consistency within Genbank conventions vs chaos elsewhere, some try to give attribution by including author name, as an example

Discussion of data citation styles: Altman, King (2007); Lawrence et al. (2008); Green (2010); Starr and Gastl (2011)

(Seeber, 2008)
(Mooney & Newton, 2012)
(Mooney, 2011)
(Sieber & Trumbo, 1995)
(Cronin, 1995)


### Fix problematic citation policies

Several journal policies need to be modified to fully support data citation tracking.

Some journals impose limits on number of references that can be cited.  For example, Nature allows a maximum of XXX references for Letters.  This becomes a problem when we ask authors to cite all datasets.  For example, XXX % of reanalyses of GEO data use XXX or more datasets.  How can these be included?

Some journals and standards permit (or even encourage) putting references in supplementary methods (http://www.niso.org/apps/group_public/download.php/7964/RP-15-201x%20Suppl_BWG_draft_for_comments.pdf).  Unfortunately, citations in supplmenetary methods sections are invisible (Seeber, 2008).  Exceptions exist: citations in Extended Method sections of Nature articles are indexed by Web of Science.  Unless journals have this set up, they should ensure all references are where they will be indexed.

A few journals discourage the use of non-peer-reviewed resources may in the references (https://www.ipcc-wg1.unibe.ch/guidancepaper/AR5GuidanceNotes_Literature.pdf).  Guideances need to be clear that datasets should be cited: if they are used, they should be cited.

Many journals discourage citing a dataset within the paper that describes the collection of the dataset, suggesting instead that the identifier is simply mentioned in the full text.  This practice fails to take advantage of the citation linking and tracking systems.  Admittedly it can be difficult to distinguish primary and secondary reuse when both use the same attribution mechansims (N\'{e}v\'{e}ol _et. al._ 2011; Piwowar & Chapman, 2008; Piwowar & Chapman, 2008), but it is possible.

Finally, editorials and news articles within journals need to link to articles and data directly (newspaper articles do also, and press releases).  This will become increasingly important as data journalism becomes more common.


### Open up machine-readable reference lists

Reference lists need to be open.  They are naturally open for libre OA articles, some barrier-based publishers are also making them open (Shotton, 2012).  Avoiding restrictions like Non-Commercial terms will be important to facilitate maximum reuse.

Ideally the reference lists would be machine readable.  Semantic markup would help to put into context (Shotton, 2010), though will be tricky to get authors to do the markup.

### Share more data

Journals and repositories could make usage and clickstream data available, based on standards for data reporting (http://www.jisc.ac.uk/publications/reports/2009/pirusfinalreport.aspx, http://www.cranfieldlibrary.cranfield.ac.uk/pirus2/tiki-index.php).

Exposing this information via an api is probably the best idea, but other mechansisms have been explored in the past and may have a role in the future (ie trackbacks (Pepler, 2008)).

### Build tools

The two major bibliometric resources, Web of Science and Scopus, do not retain dois or urls in the references they collect (Piwowar, 2010).  As a result, dataset identifiers are lost and citations to data cannot be tracked.  This is illustrated in Figures 2 and 3.

<img src="http://dl.dropbox.com/u/5485507/datacitation/datacitationstudy/figure/ORNLDAACinPaper.png" height=150/>
*Figure 2: citation of a dataset in a reference list*

<img src="http://dl.dropbox.com/u/5485507/datacitation/datacitationstudy/figure/ORNLDAACinScopus.png" height=100/>
*Figure 3: unique identifiers are not include in the Scopus record for this reference entry*

The third major citation tracking tool, Google Scholar, has explicitly decided not to track datasets.

Others are are only willing to track peer-reviewed resources (http://f1000research.com/2012/07/09/we-are-almost-there/).

New tools are coming out that track data citations.  The most high-profile is the Data Citation Index by Thomson Reuters.  Also of note, tracking citations and also other metrics of impact, are emergent tools altmetric.com and total-impact.

Tools for other parts of the data citation lifecycle are also important, including tools to visualize data citations and those to support data citation in manuscripts
(character(0)).

### Do agile research with decision makers

More research is needed into how data citations should be implemented, supported, and used.

How should citation data contribute to metrics for research evaluation?  As Julia Lane discusses (Lane, 2010), we need to learn what metrics of scientific performance mean and how they can best be interpreted.  We need more basic research into how measurement can change behaviour, and how changes to incentives alter the way research is performed.

As discussed in the sections above, data impact metrics have many applictions for discovery just waiting to be explored.

This call for more research, however, comes with a caveat.  It can be tempting to research metrics for metric's sakes.  Partnerships between stakeholders with problems that need bibliometrics solutions and cutting-edge bibliomatricians would perhaps focus bibliometrics research on priority problems and help decision-makers buy-in to the solutions.

### Ask for (and act on!) evidence of data impact

Finally, we have to ask for evidence of the impact of data.  Proactively expanding all requests for impact to include non-traditional products like data and software will remind investigators to include them, signal their value, and inspire tools to support collecting the evidence.

Natural times for this are in grant-submission biosketches, annual grant review forms, institutional annual and tenure reviews, and job application forms.

The responsibility for this progression rests with all of us, not just funders and department chairs.  Speaking out in the context of Request for Informations is a clear path, but proactively writing to committees to will help raise awareness of this issue.


## 4. Conclusion

A future where data attribution counts.
A future about *what kind* of contribution a dataset makes, not just a number.
Emerging data citation best practices are not yet supported by existing attribution tracking tools.  Agreement on policy and technical infrastructure must go hand in hand in order for benefits of reuse to be realized.
In the interest of all stakeholders. To the extent that best practices lead to reuse and attribution and citations, everyone wins.
Data is the lifeblood of science, let’s give it the respect it deserves.

(Do I want to make an image, like this but with a different emphasis? http://www.ands.org.au/guides/data_citation_poster.pdf)

## 5. References

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

<p>Fry J, Lockyer S, Oppenheim C, Houghton J and Rasmussen B (2009).
&ldquo;Identifying benefits arising from the curation and open sharing of research data produced by UK Higher Education and research institutes.&rdquo;
<EM>Report</EM>, pp. 1&ndash;89.

<p>Howison J (2011).
&ldquo;Scientific software production: incentives and collaboration.&rdquo;
<EM>Proceedings of the ACM 2011 conference on</EM>.
<a href="http://dl.acm.org/citation.cfm?id=1958904">http://dl.acm.org/citation.cfm?id=1958904</a>.

<p>Lane J (2010).
&ldquo;Let's make science metrics more scientific.&rdquo;
<EM>Nature</EM>.
<a href="http://www.nature.com/nature/journal/v464/n7288/abs/464488a.html">http://www.nature.com/nature/journal/v464/n7288/abs/464488a.html</a>.

<p>Michener WK, Porter J, Servilla M and Vanderbilt K (2011).
&ldquo;Long term ecological research and information management.&rdquo;
<EM>Ecological Informatics</EM>, <B>6</B>(1), pp. 13&ndash;24.
ISSN 15749541, <a href="http://dx.doi.org/10.1016/j.ecoinf.2010.11.005">http://dx.doi.org/10.1016/j.ecoinf.2010.11.005</a>, <a href="http://linkinghub.elsevier.com/retrieve/pii/S1574954110001159">http://linkinghub.elsevier.com/retrieve/pii/S1574954110001159</a>.

<p>Miller DR (2011).
&ldquo;Publication fraud: implications to the individual and to the specialty.&rdquo;
<EM>Current opinion in anaesthesiology</EM>, <B>24</B>(2), pp. 154&ndash;9.
ISSN 1473-6500, <a href="http://dx.doi.org/10.1097/ACO.0b013e328344529d">http://dx.doi.org/10.1097/ACO.0b013e328344529d</a>, <a href="http://www.ncbi.nlm.nih.gov/pubmed/21252647">http://www.ncbi.nlm.nih.gov/pubmed/21252647</a>.

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

<p>Piwowar HA and Chapman WW (2008).
&ldquo;Identifying data sharing in biomedical literature.&rdquo;
In <EM>AMIA Symposium</EM>, pp. 596&ndash;600.
<a href="http://www.ncbi.nlm.nih.gov/sites/entrez?Db=pubmed\&amp;Cmd=Retrieve\&amp;list\_uids=18998887\&amp;dopt=abstractplus">http://www.ncbi.nlm.nih.gov/sites/entrez?Db=pubmed\&amp;Cmd=Retrieve\&amp;list\_uids=18998887\&amp;dopt=abstractplus</a>.

<p>Piwowar HA (2010).
&ldquo;Tracking dataset citations using common citation tracking tools doesn't work.&rdquo;
<a href="http://researchremix.wordpress.com/2010/11/09/tracking-dataset-citations-using-common-citation-tracking-tools-doesnt-work/">http://researchremix.wordpress.com/2010/11/09/tracking-dataset-citations-using-common-citation-tracking-tools-doesnt-work/</a>.

<p>Piwowar HA, Vision TJ and Whitlock MC (2011).
&ldquo;Data archiving is a good investment.&rdquo;
<EM>Nature</EM>, <B>473</B>(7347), pp. 285.
ISSN 1476-4687, <a href="http://dx.doi.org/10.1038/473285a">http://dx.doi.org/10.1038/473285a</a>, <a href="http://dx.doi.org/10.1038/473285a">http://dx.doi.org/10.1038/473285a</a>.

<p>Piwowar H (2012).
&ldquo;Probability of observed third-party data reuse.&rdquo;
<EM>FigShare</EM>.
<a href="http://dx.doi.org/10.6084/m9.figshare.92959">http://dx.doi.org/10.6084/m9.figshare.92959</a>, <a href="http://figshare.com/articles/Probability\_of\_observed\_third-party\_data\_reuse/92959">http://figshare.com/articles/Probability\_of\_observed\_third-party\_data\_reuse/92959</a>.

<p>Pradhan S (2005).
&ldquo;Believability as an information quality dimension.&rdquo;
<EM>Proceedings of the International Conference on Information Quality (IQ)</EM>.
<a href="http://mitiq.mit.edu/ICIQ/Documents/IQ Conference 2005/Papers/BelievabilityasanIQDimension.pdf">http://mitiq.mit.edu/ICIQ/Documents/IQ Conference 2005/Papers/BelievabilityasanIQDimension.pdf</a>.

<p>Priem J, Piwowar HA and Hemminger BM (2012).
&ldquo;Altmetrics in the wild: Using social media to explore scholarly impact.&rdquo;
<EM>arXiv12034745v1 csDL 20 Mar 2012</EM>, <B>1203.4745</B>, pp. 1&ndash;23.
1203.4745, <a href="http://arxiv.org/abs/1203.4745">http://arxiv.org/abs/1203.4745</a>.

<p>Rohlfing T and Poline J (2012).
&ldquo;Why shared data should not be acknowledged on the author byline.&rdquo;
<EM>NeuroImage</EM>, <B>59</B>(4), pp. 4189&ndash;95.
ISSN 1095-9572, <a href="http://dx.doi.org/10.1016/j.neuroimage.2011.09.080">http://dx.doi.org/10.1016/j.neuroimage.2011.09.080</a>, <a href="http://www.ncbi.nlm.nih.gov/pubmed/22008368">http://www.ncbi.nlm.nih.gov/pubmed/22008368</a>.

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

<p>Shafer SL (2009).
&ldquo;Tattered threads.&rdquo;
<EM>Anesthesia and analgesia</EM>, <B>108</B>(5), pp. 1361&ndash;3.
ISSN 1526-7598, <a href="http://dx.doi.org/10.1213/ane.0b013e3181a16846">http://dx.doi.org/10.1213/ane.0b013e3181a16846</a>, <a href="http://www.ncbi.nlm.nih.gov/pubmed/19372305">http://www.ncbi.nlm.nih.gov/pubmed/19372305</a>.

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

<p>Teufel S, Siddharthan A and Tidhar D (2006).
&ldquo;Automatic classification of citation function.&rdquo;
In <EM>Proceedings of the 2006 Conference on Empirical Methods in Natural Language Processing</EM>, pp. 103&ndash;110.
<a href="http://www.cl.cam.ac.uk/~as372/sigdial-final.pdf">http://www.cl.cam.ac.uk/~as372/sigdial-final.pdf</a>.

<p>Thorisson GA (2009).
&ldquo;Accreditation and attribution in data sharing.&rdquo;
<EM>Nature biotechnology</EM>, <B>27</B>(11), pp. 984&ndash;5.
<a href="http://www.ncbi.nlm.nih.gov/pubmed/19898446">http://www.ncbi.nlm.nih.gov/pubmed/19898446</a>.

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



## X. misc notes

All the biblio keys, cited and not:
<div class="chunk"><div class="rcode"><div class="source"><pre class="knitr R">  <span class="functioncall">names</span>(biblio)
</pre></div><div class="output"><pre class="knitr R">##  [1] "abbott:2010"                         
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
## [20] "fry:2009"                            
## [21] "haustein:2011"                       
## [22] "hine:2006"                           
## [23] "howison:2011"                        
## [24] "lane:2010"                           
## [25] "larsen:2010"                         
## [26] "lawrence:2011"                       
## [27] "lozano:2012"                         
## [28] "michener:2011"                       
## [29] "miller:2011"                         
## [30] "mons:2011"                           
## [31] "mooney:2011"                         
## [32] "mooney:2012"                         
## [33] "nelson:2012"                         
## [34] "neveol:2011"                         
## [35] "neylon:2009"                         
## [36] "opportunities-for-data-exchange:2012"
## [37] "parsons:2010"                        
## [38] "pepler:2008"                         
## [39] "pienta:2010"                         
## [40] "piwowar:2012"                        
## [41] "piwowar:2012b"                       
## [42] "piwowar:2012a"                       
## [43] "piwowar:2010"                        
## [44] "piwowar:2008a"                       
## [45] "piwowar:2008"                        
## [46] "piwowar:2011a"                       
## [47] "piwowar:2011"                        
## [48] "pradhan:2005"                        
## [49] "prat:2008"                           
## [50] "priem:2012"                          
## [51] "rohlfing:2012"                       
## [52] "sayogo:2012"                         
## [53] "schofield:2009"                      
## [54] "seeber:2008"                         
## [55] "seglen:1997"                         
## [56] "shafer:2009"                         
## [57] "shotton:2012"                        
## [58] "shotton:2010"                        
## [59] "shotton:2009"                        
## [60] "sieber:1995"                         
## [61] "sinnott:2005"                        
## [62] "starr:2011"                          
## [63] "tenopir:2011"                        
## [64] "teufel:2000"                         
## [65] "teufel:2006"                         
## [66] "thorisson:2009"                      
## [67] "todd:2008"                           
## [68] "van-de-sompel:2009"                  
## [69] "vasseur:2003"                        
## [70] "wallis:2006"                         
## [71] "wang:1996"                           
## [72] "whitlock:2011"                       
## [73] "wouters:"                            
## [74] "wynholds:2012"                       
</pre></div><div class="source"><pre class="knitr R">  #<span class="functioncall">citep</span>(biblio[<span class="functioncall">names</span>(biblio)])
</pre></div></div></div>




