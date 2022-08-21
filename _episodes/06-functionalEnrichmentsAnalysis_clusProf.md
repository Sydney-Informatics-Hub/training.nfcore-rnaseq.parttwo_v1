---
title: "Functional enrichment analysis"
teaching: 10
exercises: 10
questions:
- "What is functional enrichment analysis?"
- "What is over-represntation analysis?" 
- "What are Gene Ontologies?"


objectives:
- "Understand enrichment analysis."
- "Introduction to Gene ontology (GO)"

keypoints:
- XXX
---

#### Functional enrichment analysis

- The output of RNA-seq differential expression analysis is a list of significant differentially expressed genes (DEGs). 
- There are various types of analyses that can be done to gain greater biological insight on the DEGs.
   - Determine whether there is enrichment of known biological functions, interactions, or pathways
   - Identify genes’ involvement in novel pathways or networks by grouping genes together based on similar trends.
   - Use global changes in gene expression by visualizing all genes being significantly up- or down-regulated in the context of external interaction data.


#### Over-representation analysis

- There are a range of functional enrichment tools that perform some type of “over-representation” analysis by querying databases containing information about gene function and interactions.
- These databases typically categorize genes into groups based on shared function, or involvement in a pathway, or presence in a specific cellular location, or other categorizations, e.g. functional pathways, etc.
- Essentially, known genes are binned into categories that have been consistently named (controlled vocabulary) based on how the gene has been annotated functionally. These categories are independent of any organism, however each organism has distinct categorizations available.

<p align="center">
  <img src="{{ page.root }}/fig/overrepresentation_analysis.png" style="margin:10px;height:350px"/>
  </p>

To determine whether any of the categories are over-represented, we need to 
- Calculate how many of the DE genes overlap with genes associated with specific functional categories (e.g. pathway/gene ontology etc)
- Identify the statistically significant categories using the proportion of genes associated with a specific category in the DE gene list to number of genes associated with the same category in the background set.

#### How can over-representation analysis help?
- We can go from a list of changing genes to a list of affected biologial processes.  This can give us a better underatandign of the functional differences between the conditions under study.
- We also reduce the dataset from a large number DE genes to a smaller number of functions/processes. 
- Up/Down regulated genes to Up/Down regulated processes between two conditions.

#### Gene Ontology project
- One of the most widely-used categorizations is the Gene Ontology (GO) established by the [Gene Ontology project](http://geneontology.org/page/go-consortium-contributors-list).
- Tools that investigate enrichment of biological functions or interactions often use the Gene Ontology (GO) categorizations, i.e. the GO terms to determine whether any have significantly modified representation in a given list of genes.

#### GO Ontologies
- GO terms provide a standardized vocabulary to describe genes and gene products from different species. GO terms allow us to assign functionality to genes and gene products.
- GO terms are organized into three independent controlled vocabularies (ontologies) in a species-independent manner:
- **Biological process**: refers to the biological role involving the gene or gene product, and could include “transcription”, “signal transduction”, and “apoptosis”.
- **Molecular function**: represents a function carried out by the gene; such activities could include “ligand”, “GTPase”, and “transporter”.
- **Cellular component**: refers to the location in the cell of the gene product. Cellular components could include “nucleus”, “lysosome”, and “plasma membrane”.




