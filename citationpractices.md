




# knitr citationpractices manuscript
 * author of this file: Heather Piwowar, <hpiwowar@gmail.com>
 * license: CC0
 * Acknowledgements: thanks to Yihui Xie for knitr and Carl Boettiger for his clear examples of this literate programming framework. 
 * Generated on <code class="knitr inline">Sat Jul  7 21:24:51 2012</code>

To execute the R code in this file and embed the results in the text, I start R, set the working directory, then run the following:

    library(knitr)  
    knit("stats_knit_.md")

or, from the command line, to generate an html file:

    R -e "library(knitr); knit('stats_knit_.md')"; pandoc --toc -r markdown -w html -H static/header.html stats.md > stats.html

The stats.html file can be viewed directly in a browser.
The images are stored in my Public Dropbox folder.

After pushing the .md files to GitHub, the stats.md file can also be viewed at [https://github.com/hpiwowar/citation11k/blob/master/analysis/stats.md](https://github.com/hpiwowar/citation11k/blob/master/analysis/stats.md) .

To extract the R code in a separate .R file called stats_knit_.R, run knit with tangle set to TRUE:

    R -e "library(knitr); knit('citationpractices_knit_.md', tangle=T)"

<div class="chunk"><div class="rcode"><div class="error"><pre class="knitr">## Error: cannot open the connection
</pre></div><div class="error"><pre class="knitr">## Error: cannot open the connection
</pre></div></div></div>





# Data Citation in the Wild*

##Abstract

The NSF data management mandate has brought issues of data management to the fore.  There is particular interest in the availability of data for reuse by other investigators and citation of reused data to recognize investigators who produce valuable data products.

New policies for data citation are being proposed and adopted.  Are data citation policies needed?  What policies are currently in place?  What is current practice?  Are there tools avaiable to discover and disseminate data citation links? What are the implications of this, in terms of reusability of data and incentives for data producing investigators?

The primary focus in most fields is data that supports the findings in peer-reviewed journal publications.  We investigated a wide variety of sources for data citation policies that authors must comply with, from funders, repositories, and journals.  We found limited and variable guidance.  

Many new policies are coming online - how to inform them? We examined actual attribution practice by researchers.  Researchers are clearly mixing and matching different expectations in a very context sensitive manner.  Emerging data citation best practices are not yet supported by existing attribution tracking tools.  Attributions are difficult to track.

Agreement on policy and technical infrastructure must go hand in hand in order for benefits of reuse to be realized.

## Methods

##Results



### Data attribution policy
Table:  Data reuse policies of Funders, Journal, Repositories.  Subdivide with line in between funders, journals, and repositories.  Columns:

* No policy for data citation (lists all funders with no policy, in alphabetical order)
* Mentions data citation (lists all funders that mention data citation, with exerpt in parantheses)

### Data attribution practice

Table:  heterogeneity of data citation policies (as in poster?) http://precedings.nature.com/documents/5452/version/1/files/npre20105452-1.pdf

### Data attribution tracking tools

<img src="http://researchremix.files.wordpress.com/2010/11/tracking_reuse_flowchart_20101123.pdf" class="plot" width=600/>

### Implications for incentives

Evidence that reuse is difficult to track:  Paragraph of results detailing manpower effort for DAAC to find reuses.

documentation of how difficult it is to retrieve the data
70-80 hours in discusson

Can be visualized like this
Include flowchart?
http://researchremix.wordpress.com/2010/11/08/flowchart-how-to-identify-dataset-reuse-in-the-published-literature/

Pull in things from the poster:
http://precedings.nature.com/documents/5452/version/1

Other stuff from Nic’s poster graphic?  



## Discussion

privilege of articles over data
do we know how to cite it
where to archive it
how to discover it
how to track it
who create it?
how can we use it?
how do you peer review it?

data all up in the air

fact that funders and institutions don’t have
the fact that journals don’t matters
the fact that repositories often don’t is really surpising

table that shows the different combinations of how data is cited

consistency within Genbank conventions vs chaos elsewhere
some try to give attibuion by including author name, as an example

Best practices are also in the self-interest of the journal..... to the extent that best practices lead to reuse and attribution and citations, everyone wins.

A future where data attribution counts.
A future about *what kind* of contribution a dataset makes, not just a number.

Data is the lifeblood of science, let’s give it the respect it deserves


<hr/>
<hr/>
<hr/>

### Extra notes, currently considered out of scope

Data archiving
Table:  Data archiving policies of Funders, Journal, Repositories.  Subdivide with line in between funders, journals, and repositories.  Columns:
No policy for data archiving (lists all with no policy, in alphabetical order)
Requests data archiving (lists all that mention data citation without requiring it, with exerpt in parantheses)
Requires data archiving, in some instances  (lists all that mention data citation without requiring it, with exerpt in parantheses)

Table:  regression information for which journals are most likely to have policies.  If we look into these further, we can see that journals with highest impact factors are most likely to have policies.  
Graph:  boxplot of journal impact factors, for “no policy, requests, requires” ?
Paragraph of results like in Nic’s ASIS&T poster abstract:  

Table:  Data archiving practice.  A row for each journal.  Columns
 number of papers that generated DNA sequence data, % that archived
 number of papers that generated treebase data, % that archived
 number of papers that generated other data, % that archived
Graph:  Data archiving practice over time.  A row for each journal we have over time, showing % deposit, with confidence intervals.
years

Could include data from:
long ago survey (as introductory motivation, along with explanation of landscape of existing data archives -- and gaps )
Nic’s policy inventory of repositories, funders, journals
Sarah’s article inventory on data sharing, data reuse, data citation practices (also highlight data production numbers?)
Valerie’s DAAC data reuse tracking experiences (manpower, inventory of data citation practices)
data reuse tracking flowchart 
experience tracking dois?  Though this is light on stats
