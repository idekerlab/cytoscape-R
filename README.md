# Sample cyREST workflows in R 

![](https://cytoscape.org/images/screenshots/structure-aware-layout.jpg)
Fig. 1: Yeast PPI visualized with Cytoscape (generated by _Workflow 1_).

by [Keiichiro Ono](http://keiono.github.io/)

## Introduction
This is a collection of R workflows to use Cytoscaep from R via [cyREST app](http://apps.cytoscape.org/apps/cyrest).

## Updates
* 6/15/2015 - First release


## System Requirments
### Supported platforms
* Mac OS X (tested on Yosemite)
* Windows (tested on Windows 8.1 64 bit)
* Linux (tested on Ubuntu 14.0.4)

### Reruired Software Packages
* [R](http://www.r-project.org/) (Tested on R version 3.2.0)
* Latest version of [Java 8](http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)
* [Cytoscape](http://www.cytoscape.org/) 3.2.1 or later
* [RStudio](http://www.rstudio.com/)
    * Some of the examples are written in [R Markdown format](http://rmarkdown.rstudio.com/).  RStudio is the best application to render and execute them.

#### R Packages
* [RJSON](http://cran.r-project.org/web/packages/rjson/index.html)
* [igraph](http://igraph.org/r/)
* [httr](http://cran.r-project.org/web/packages/httr/index.html)

## How to Use

### Quick Start Guide
In addition to main workflows, there are some small tutorials in ___rmarkdown___ directory.  I recommend to try them first.

* Install all required software
* Start Cytoscape
* Open web browser and visit [cyREST page in App Store](http://apps.cytoscape.org/apps/cyrest)
* Click ___Install___ button to directly install the App from this page
    * Note: __Do NOT install app from App menu.__ It installs older version of cyREST.  This is a known bug in Cytoscape.
* Clone this repository
* Open the directory with RStudio
* Run ```r_markdown/basic1.Rmd``` to start basic workflow

#### Basic Lesons

![](http://chianti.ucsd.edu/~kono/images/r_basic_2.png)

1. [Overview](https://github.com/idekerlab/cy-rest-R/blob/develop/r_markdown/basic1.Rmd)
1. [Working with igraph and Cytoscape](https://github.com/idekerlab/cy-rest-R/blob/develop/r_markdown/basic2.Rmd)
1. [More igraph and Visual Styles](https://github.com/idekerlab/cy-rest-R/blob/develop/r_markdown/basic3.Rmd)

## Workflows
There are some _workflow*_ R files in the top directory.  They are designed to star from an empty Cytoscape session. To run these scripts, simply start Cytoscape and run the R script from R console.  Make sure you installed all dependencies!

#### Workflow 1: Automatic layout and visualization based on network structure
This workflow is designed to demonstrate how the combination of Cytoscape and igraph makes your network visualization better than manual visuaization. It executes the following steps automatically:

1. Load SIF network file (yeast network)
1. Extract largest connected component (subgraph)
1. Remove duplicate edges
1. Calculate basic statistics including:
    * Betweenness
    * PageRank
    * Edge Betweenness
1. Find community structures using multiple algorithms
1. Convert it into Cytoscpae-conpatible JSON
1. Generate visual style using statistics and community structure calculated above
1. Send the data to Cytoscape
1. Run Kamada-Kawai layout algorithm using community structure
1. Visualize it

You can use your own network if you want.

##### How to run
* Start Cytoscape (w/ latest version of cyREST installed)
* Start RStudio
* Run ___workflow1_structure_based_visualization.R___

#### Workflow 2: Interactome visualization as a collection of subgraphs

![](http://chianti.ucsd.edu/~kono/images/humannet_session2.png)

This is a simple script to import [HumanNet](http://www.functionalnet.org/humannet/about.html) interactome data from their web site, and add some extra annotations using [Bioconductor]() packages.  It automatically generates subgraphs using chromosome name (1-22, X/Y, and mitocondrial DNA).

To run this workflow, you need to install some Bioconductor libraries first.

(TBD)

## How to Cite
(TBD)

## What's Next?
These examples are using low-level, raw cyREST API.  It provides full access to most of the data objects, but you need a lot of _boilerplate_ code to do simplu stuff.  To avoid this issue, RCytoscape group is working on next generation of RCytoscape using cyREST as its backend:

* [RCy3](https://github.com/tmuetze/Bioconductor_RCy3_the_new_RCytoscape)

Once this is ready, we'll add more examples using this Bioconductor package. 


## Questions?
Please contact me (kono at ucsd edu).

----
&copy; Keiichiro Ono (UC, San Diego Trey Ideker Lab)

Source code license: [MIT](http://opensource.org/licenses/MIT)

Texts and images are licensed under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/) 
