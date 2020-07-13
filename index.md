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
<script src="https://cdnjs.cloudflare.com/ajax/libs/d3/3.5.17/d3.min.js"></script>

<script>
	
var treeData = [{
	"name": "machine learning",
	"url":"https://h3abionet.github.io/H3ABioNet-ML-glossary/intro_to_ml.html",
	"parent": "null",
	"children": [{
		"name": "Good data size",
		"parent": "machine learning",
		"children": [{
				"name": "Pre-processing",
				"url":"https://github.com/h3abionet/H3ABioNet-ML-glossary/preprocessing_intro.html",
				"parent": "Good data size",
				"children": [{
					"name": "Known outcomes",
					"parent": "Pre-processing",
					"children": [{
						"name": "Supervised Learning",
						"url":"https://h3abionet.github.io/H3ABioNet-ML-glossary/Supervised-Learning-1-0.html",
						"parent": "Known outcomes",
						"children": [{
								"name": "Predict a group (classification)",
								"parent": "Supervised Learning"
							},
							{
								"name": "Predict a continuous value (regression)",
								"parent": "Supervised Learning",
								"children": [{
									"name": "result validation",
									"parent": "Predict a continuous value (regression)",
									"parent": "Predict a group (classification)",
									"children": [{
										"name": "cross validation",
										"parent": "result validation"
									}]
								}]
							}
						]
					}]
				}, {
					"name": "Unknown outcomes",
					"parent": "Pre-processing",
					"children": [{
						"name": "Unsupervised Learning",
						"url":"https://h3abionet.github.io/H3ABioNet-ML-glossary/unsupervised_learning_intro.html",
						"parent": "Unknown outcomes",
						"children": [{
								"name": "Identify groups (clustering)",
								"parent": "Unsupervised Learning"
							},
							{
								"name": "reduce number of variables",
								"parent": "Unsupervised Learning",
								"children": [{
									"name": "PCA",
									"url":"https://h3abionet.github.io/H3ABioNet-ML-glossary/pca.html",
									"parent": "reduce number of variables"
								}]
							}
						]
					}]
				}]
			},
			{
				"name": "Inadequate data size",
				"parent": "machine learning",
				"children": [{
					"name": "Enrich set",
					"parent": "Inadequate data size"
				}]
			}
		]
	}]
}];

// ************** Generate the tree diagram	 *****************
var margin = {top: 20, right: 120, bottom: 20, left: 120},
	width = 960 - margin.right - margin.left,
	height = 500 - margin.top - margin.bottom;

var i = 0,
	duration = 750,
	root;

var tree = d3.layout.tree()
	.size([height, width]);

var diagonal = d3.svg.diagonal()
	.projection(function(d) { return [d.y, d.x]; });

var svg = d3.select("#graph").append("svg")
	.attr("width", width + margin.right + margin.left)
	.attr("height", height + margin.top + margin.bottom)
  .append("g")
	.attr("transform", "translate(" + margin.left + "," + margin.top + ")");

root = treeData[0];
root.x0 = height / 2;
root.y0 = 0;

update(root);

d3.select(self.frameElement).style("height", "500px");

function update(source) {

  // Compute the new tree layout.
	root = treeData[0]
	if (source.parent.name){
		root = source.parent;
	}

  var nodes = tree.nodes(root).reverse(),
	  links = tree.links(nodes);

  // Normalize for fixed-depth.
  nodes.forEach(function(d) { d.y = d.depth * 180; });

  // Update the nodes…
  var node = svg.selectAll("g.node")
	  .data(nodes, function(d) { return d.id || (d.id = ++i); });

  // Enter any new nodes at the parent's previous position.
  var nodeEnter = node.enter().append("g")
	  .attr("class", "node")
	  .attr("transform", function(d) { return "translate(" + source.y0 + "," + source.x0 + ")"; })
		<!-- .on("click", click) -->
	;

  nodeEnter.append("circle")
	  .attr("r", 1e-6)
	  .style("fill", function(d) { return d._children ? "lightsteelblue" : "#fff"; })
	  .on("click", click)
	;

	nodeEnter
			.append("a")
				 .attr("xlink:href", function (d) { return d.url; })
		.append("text")
	  .attr("x", function(d) { return d.children || d._children ? -13 : 13; })
	  .attr("dy", ".35em")
		.attr("text-anchor", function(d) { return d.children || d._children ? "end" : "start"; })
	  .text(function(d) { return d.name; })
		.style("fill-opacity", 1e-6);



  // Transition nodes to their new position.
  var nodeUpdate = node.transition()
	  .duration(duration)
	  .attr("transform", function(d) { return "translate(" + d.y + "," + d.x + ")"; });

  nodeUpdate.select("circle")
	  .attr("r", 10)
	  .style("fill", function(d) { return d._children ? "lightsteelblue" : "#fff"; });

  nodeUpdate.select("text")
	  .style("fill-opacity", 1);

  // Transition exiting nodes to the parent's new position.
  var nodeExit = node.exit().transition()
	  .duration(duration)
	  .attr("transform", function(d) { return "translate(" + source.y + "," + source.x + ")"; })
	  .remove();

  nodeExit.select("circle")
	  .attr("r", 1e-6);

  nodeExit.select("text")
	  .style("fill-opacity", 1e-6);

  // Update the links…
  var link = svg.selectAll("path.link")
	  .data(links, function(d) { return d.target.id; });

  // Enter any new links at the parent's previous position.
  link.enter().insert("path", "g")
	  .attr("class", "link")
	  .attr("d", function(d) {
		var o = {x: source.x0, y: source.y0};
		return diagonal({source: o, target: o});
	  });

  // Transition links to their new position.
  link.transition()
	  .duration(duration)
	  .attr("d", diagonal);

  // Transition exiting nodes to the parent's new position.
  link.exit().transition()
	  .duration(duration)
	  .attr("d", function(d) {
		var o = {x: source.x, y: source.y};
		return diagonal({source: o, target: o});
	  })
	  .remove();

  // Stash the old positions for transition.
  nodes.forEach(function(d) {
	d.x0 = d.x;
	d.y0 = d.y;
  });

	function nothing(d){}
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

</script>


* [Introduction to Machine Learning]({{ site.baseurl}}{% link pages/introduction_to_ml.md %})
* [Supervised Learning]({{ site.baseurl}}{% link pages/categories/supervised/supervised_intro.md %})
* [Unsupervised Learning]({{ site.baseurl}}{% link pages/categories/unsupervised/unsupervised_learning_intro.md %})
* [Semi-supervised Learning]({{ site.baseurl}}{% link pages/categories/semi-supervised/semi-supervised_intro.md %})
* [Assessing model performance]({{ site.baseurl}}{% link pages/categories/performance/performance_intro.md %})
* [Choosing the right estimator]({{ site.baseurl}}{% link pages/choosing_estimator/choosing_estimator.md %})


You can use the buttons at the top of the page to navigate through the Glossary different terms, or the side panel to access the subsections within each.

This ML glossary repo was [forked from this H3ABioNet-SOPs repo](https://github.com/h3abionet/H3ABionet-SOPs). Contributions are welcome! To do so, open an issue or a pull request. Additionally, check out our [contribution guide]({{ site.baseurl}}{% link pages/contributing/cont_tech-guide-1.md %}).

### Funding
The H3ABioNet Machine Learning Glossary was developped by the H3ABioNet Machine Learning and Big Data project members. The development of  is supported by the H3Africa program grant U24HG006941 from the National Human Genome Research Institute (NHGRI) of the National Institutes of Health (NIH) entitled “H3ABioNet: Informatics Solutions for H3Africa”. The content is solely the responsibility of the authors and does not necessarily represent the official views of the National Institutes of Health.

[//]: <> (These are common abbreviations in the page.)
*[ML]: Machine Learning
*[H3Africa]: Human Heredity and Health in Afrcia Consortium
*[H3ABioNet]: The Bioinformatics Network within the H3Africa Consortium
