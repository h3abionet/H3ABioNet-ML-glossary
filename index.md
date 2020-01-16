---
title: ""
keywords: H3ABioNet, Machine Learning, Supervised Learning, Unsupervised Learning, Classification, Regression, Clustering, Dimensionality Reduction
tags: [formating]
last_updated: July 29, 2019
author_profile: true
authors: Amel, Anmol & Shakun
hide_sidebar: true
toc: false
permalink: index.html
---

[![H3ABioNet logo](assets/images/LOGO-HEADER.jpg "H3ABioNet logo")](https://h3abionet.org)

This website aims to provide information about machine learning terms glossary within the [H3ABioNet](https://h3abionet.org/) consortium, by introducing the ML jargon and explaining it using very simple terms and including examples from the biomedical research field. We believe this Glossary will help folks from non computing background get familiar with ML terms and methods in order to enhance the use of ML to answer biological questions.

Biologists no longer rely on traditional laboratories to discover novel biomarkers for a given disease, but make use of the continuously growing genomic datasets that are publicly available to determine the biomarkers. Technologies for capturing data in biology are becoming cheaper and more effective, and this has given rise to a new era of big data in bioinformatics. These large biological datasets can be effectively analysed using machine learning aproaches.

<style>

.node circle {
  fill: #fff;
  stroke: steelblue;
  stroke-width: 3px;
}

.node text {
  font: 12px sans-serif;
}

.link {
  fill: none;
  stroke: #ccc;
  stroke-width: 2px;
}

</style>

<div id="graph"></div>

<!-- load the d3.js library -->	
<script src="https://d3js.org/d3.v4.min.js"></script>
<script>

var treeData =
  {
    "name": "machine learning",
    "children": [
      { 
        "name": "Supervised Learning",
        "children": [
          { "name": "Classification" },
          { "name": "Regression" }
        ]
      },
      { 
        "name": "Unsupervised Learning",
        "children": [
          { "name": "Clustering" },
          { "name": "Dimensionality Reduction" }
        ]
      }
    ]
  };

// Set the dimensions and margins of the diagram
var margin = {top: 20, right: 20, bottom: 100, left: 190},
    width = 1160 - margin.left - margin.right,
    height = 600 - margin.top - margin.bottom;

// append the svg object to the body of the page
// appends a 'group' element to 'svg'
// moves the 'group' element to the top left margin
var svg = d3.select("#graph").append("svg")
    .attr("width", width + margin.left + margin.right)
    .attr("height", height + margin.top + margin.bottom)
  .append("g")
    .attr("transform", "translate("
          + margin.left + "," + margin.top + ")");
 
var i = 0,
    duration = 750,
    root;

// declares a tree layout and assigns the size
var treemap = d3.tree().size([height, width]);

// Assigns parent, children, height, depth
root = d3.hierarchy(treeData, function(d) { return d.children; });
root.x0 = height / 2;
root.y0 = 0;

// Collapse after the second level
root.children.forEach(collapse);

update(root);

// Collapse the node and all it's children
function collapse(d) {
  if(d.children) {
    d._children = d.children
    d._children.forEach(collapse)
    d.children = null
  }
}

function update(source) {

  // Assigns the x and y position for the nodes
  var treeData = treemap(root);

  // Compute the new tree layout.
  var nodes = treeData.descendants(),
      links = treeData.descendants().slice(1);

  // Normalize for fixed-depth.
  nodes.forEach(function(d){ d.y = d.depth * 180});

  // ****************** Nodes section ***************************

  // Update the nodes...
  var node = svg.selectAll('g.node')
      .data(nodes, function(d) {return d.id || (d.id = ++i); });

  // Enter any new modes at the parent's previous position.
  var nodeEnter = node.enter().append('g')
      .attr('class', 'node')
      .attr("transform", function(d) {
        return "translate(" + source.y0 + "," + source.x0 + ")";
    })
    .on('click', click);

  // Add Circle for the nodes
  nodeEnter.append('circle')
      .attr('class', 'node')
      .attr('r', 1e-6)
      .style("fill", function(d) {
          return d._children ? "lightsteelblue" : "#fff";
      });

  // Add labels for the nodes
  nodeEnter.append('text')
      .attr("dy", ".35em")
      .attr("x", function(d) {
          return d.children || d._children ? -13 : 13;
      })
      .attr("text-anchor", function(d) {
          return d.children || d._children ? "end" : "start";
      })
      .text(function(d) { return d.data.name; });

  // UPDATE
  var nodeUpdate = nodeEnter.merge(node);

  // Transition to the proper position for the node
  nodeUpdate.transition()
    .duration(duration)
    .attr("transform", function(d) { 
        return "translate(" + d.y + "," + d.x + ")";
     });

  // Update the node attributes and style
  nodeUpdate.select('circle.node')
    .attr('r', 10)
    .style("fill", function(d) {
        return d._children ? "lightsteelblue" : "#fff";
    })
    .attr('cursor', 'pointer');


  // Remove any exiting nodes
  var nodeExit = node.exit().transition()
      .duration(duration)
      .attr("transform", function(d) {
          return "translate(" + source.y + "," + source.x + ")";
      })
      .remove();

  // On exit reduce the node circles size to 0
  nodeExit.select('circle')
    .attr('r', 1e-6);

  // On exit reduce the opacity of text labels
  nodeExit.select('text')
    .style('fill-opacity', 1e-6);

  // ****************** links section ***************************

  // Update the links...
  var link = svg.selectAll('path.link')
      .data(links, function(d) { return d.id; });

  // Enter any new links at the parent's previous position.
  var linkEnter = link.enter().insert('path', "g")
      .attr("class", "link")
      .attr('d', function(d){
        var o = {x: source.x0, y: source.y0}
        return diagonal(o, o)
      });

  // UPDATE
  var linkUpdate = linkEnter.merge(link);

  // Transition back to the parent element position
  linkUpdate.transition()
      .duration(duration)
      .attr('d', function(d){ return diagonal(d, d.parent) });

  // Remove any exiting links
  var linkExit = link.exit().transition()
      .duration(duration)
      .attr('d', function(d) {
        var o = {x: source.x, y: source.y}
        return diagonal(o, o)
      })
      .remove();

  // Store the old positions for transition.
  nodes.forEach(function(d){
    d.x0 = d.x;
    d.y0 = d.y;
  });

  // Creates a curved (diagonal) path from parent to the child nodes
  function diagonal(s, d) {

    path = `M ${s.y} ${s.x}
            C ${(s.y + d.y) / 2} ${s.x},
              ${(s.y + d.y) / 2} ${d.x},
              ${d.y} ${d.x}`

    return path
  }

  // Toggle children on click.
  function click(d) {
    if (d.children) {
        d._children = d.children;
        d.children = null;
      } else {
        d.children = d._children;
        d._children = null;
      }
    update(d);
  }
}

</script>


* [Introduction to Machine Learning]({{ site.baseurl}}{% link pages/introduction_to_ml.md %})
* [Supervised Learning]({{ site.baseurl}}{% link pages/categories/supervised/supervised_learning.md %})
* [Unsupervised Learning]({{ site.baseurl}}{% link pages/categories/unsupervised/unsupervised_learning.md %})
* [Data preprocessing]({{ site.baseurl}}{% link pages/genomics_analysis/RNA-Seq/RNA-Seq-1-0.md %})
* [Choosing the right estimator]({{ site.baseurl}}{% link pages/choosing_estimator/choosing_estimator.md %})


You can use the buttons at the top of the page to navigate through the Glossary different terms, or the side panel to access the subsections within each.

This ML glossary repo was [forked from this H3ABioNet-SOPs repo](https://github.com/h3abionet/H3ABionet-SOPs). Contributions are welcome! To do so, open an issue or a pull request. Additionally, check out our [contribution guide]({{ site.baseurl}}{% link pages/contributing/cont_tech-guide-1.md %}).

-------------------
# Types of Machine Learning Algorithms:
There are several main types of machine learning algorithms in common use: supervised, unsupervised, semi-supervised, reinforcement learning and statistical methods:

## i) Supervised learning approaches
These approaches use a training dataset where the outcome is known, and the relationship between a set of predictors (independent variables, risk factors) and the outcome can be modelled, and then tested on a test set as well as used to predict the outcome where it is not known.

| field1 | field2 |
|---|---|

## ii) Unsupervised learning algorithms.
These algorithms are used where there is no target or outcome variable to predict, and the primary aim is to identify clusters of items in a dataset according to specific features or characteristics. The computer learns to identify patterns in the data without human guidance about how the different clusters should be determined. 

| field1 | field2 |
|---|---|

## iii) Semi-supervised learning algorithms 
These fall between supervised and unsupervised ML algorithms, where only a subset of the data are labelled – so that where data are unlabelled, their features may still contribute understanding about the group parameters. 

| field1 | field2 |
|---|---|

## iv) Reinforcement learning algorithms
These are used to train a machine to make specific decisions and then continually improve this process through trial-and-error – learning from past experience and capturing knowledge to improve decision-making. The reinforcement learning algorithm (or agent) learns iteratively from experience, with feedback that acts as the reinforcement signal to modify the algorithm’s behaviour.

| field1 | field2 |
|---|---|

## v) Statistical methods. 

| field1 | field2 |
|---|---|

%figure (upload Fig 1b and 2)

## Summary of some applications of ML in Bioinformatics

| Type of ML | Algorithm name | Bioinformatics application [refs] |
|---|---|---|
|Supervised|Linear regression|Correlating the codon usage pattern with the protein regulation level using linear regression models [Bioinformatics study of the relationship between protein regulation and sequence properties](https://doi.org/10.1016/j.ygeno.2012.07.003)|
||Logistic Regression|Logistic regression for disease classification using microarray data: model selection in a large p and small n case [article](https://doi.org/10.1093/bioinformatics/btm287)|
||Decision Tree|Classification between disease group and non-disease group as well as to distinguish among different disease sub-types, using features generated from protein sequence and structure data [article](https://www.ncbi.nlm.nih.gov/pubmed/20139917)|
||Support Vector Machines (SVM)|Can also be used to classify between disease group and non-disease group like a Decision Tree. Other applications of SVM are: (1) prediction of membrane protein types in whole sequences. (2) prediction of translation initiation sites in biological sub-sequences [article](https://doi.org/10.1093/bib/5.4.328)|
||Naïve Bayes|Rapid Assignment of rRNA Sequences into the New Bacterial Taxonomy [article](http://aem.asm.org/content/73/16/5261.full.pdf)|
||K-Nearest Neighbour|Gene function prediction from heterogeneous data [article](https://doi.org/10.1186/1471-2105-7-S1-S11)|
||Random Forest|Used in pathway analysis and genetics association and epistasis detection [article](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC3387489/)|
||Dimensionality Reduction Algorithms|E.g. PCA.  See Statistical; can be used for the visualization of microarray gene expression data [article](https://doi.org/10.1186/1471-2105-11-567).
Can also  be for biomarker discovery from high-throughput biological data [article](https://doi.org/10.1093/bib/bbn005)|
||Gradient Boosting algorithms|Predicting protein solvent accessibility which is a pivotal intermediate step towards modeling protein tertiary structures directly from one-dimensional sequences  [article](https://doi.org/10.1186/s12859-015-0851-2 )|
||Neural networks|Can be used for promoter recognition [article](https://www.ncbi.nlm.nih.gov/pubmed/2818859). Drug resistance prediction in HIV [article](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC5558779/) |
||Association rules|Used to identify promising secondary phenotype candidates. Predictions rely on a large gene–phenotype annotation set that is used to find occurrence patterns of phenotypes.  [article](https://www.ncbi.nlm.nih.gov/pubmed/24932005 )|
|Unsupervised|K-means clustering|Used in gene expression studies to identify the functions of previously unstudied genes  - to reduce the data set [article](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC3180043/)|
|Statistical|Principal Component Analysis|Used in studies to explain variation of gene expressions [article](https://www.ncbi.nlm.nih.gov/pubmed/21242203)|
||Independent Component Analysis||

## Glossary
|Term|Explanation|
|---|---|
|Big Data|Big data refers to large and complex datasets characterized by: (1) Volume: defines the huge amount of data that is produced. The data is so large and complex that it can no longer be saved or analyzed using conventional data processing methods. (2) Variety refers to the diversity of data types and data sources. (3) Velocity refers to the speed with which the data is generated, analyzed and reprocessed. (4) Veracity: uncertainty of data|
---------------------

### Funding
The H3ABioNet Machine Learning Glossary was developped by the H3ABioNet Machine Learning and Big Data project members. The development of  is supported by the H3Africa program grant U24HG006941 from the National Human Genome Research Institute (NHGRI) of the National Institutes of Health (NIH) entitled “H3ABioNet: Informatics Solutions for H3Africa”. The content is solely the responsibility of the authors and does not necessarily represent the official views of the National Institutes of Health.

### References


[//]: <> (These are common abbreviations in the page.)
*[ML]: Machine Learning
*[H3Africa]: Human Heredity and Health in Afrcia Consortium
*[H3ABioNet]: The Bioinformatics Network within the H3Africa Consortium
