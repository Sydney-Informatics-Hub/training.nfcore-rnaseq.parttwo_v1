---
title: "DE genes to functional enrichment in R"
teaching: 10
exercises: 10
questions:
- "How to perform enrichment analysis in R (RStudio)?"
- "How to visualise functionally enriched Gene ontologies (GO) / pathways as networks?"

objectives:
- "Perform Functional enrichment analysis of the DE genes in 'R'"

keypoints:
- XXX
---

### ClusterProfiler for Gene Ontology (GO) over-representation analysis 
- We will be using the R-package clusterProfiler to perform over-representation analysis on GO terms. 
- The tool takes as input a list of significant genes (DEGs in this case) and a background gene list to perform statistical enrichment analysis using hypergeometric testing.
- The basic arguments allow the user to select the appropriate organism and GO ontology (BP, CC, MF) to test.

- Prepare input. 
- Filter for significant up and down regulated genes by P adjust and log fold change. 

```
# P adj < 0.05 
sig <- res_tidy.DE[res_tidy.DE$p.adjusted < 0.05, ]

# Upregulated: LFC > 1, remove NAs
sig.up <- sig[sig$estimate > 1, ]
sig.up <- na.omit(sig.up)
sig.up.LFC <- sig.up$estimate
names(sig.up.LFC) <- sig.up$gene
# Sort by LFC, decreasing
sig.up.LFC <- sort(sig.up.LFC, decreasing = TRUE)

# Downregulated: LFC < 1, remove NAs
sig.dn <- sig[sig$estimate < 1, ]
sig.dn <- na.omit(sig.dn)
sig.dn.LFC <- sig.dn$estimate
names(sig.dn.LFC) <- sig.dn$gene
# Sort by LFC, decreasing
sig.dn.LFC <- sort(sig.dn.LFC, decreasing = TRUE)
```


### Genes Down-regulated in WT


### GO over-representation analysis
- The clusterProfiler package implements enrichGO() for gene ontology over-representation test.
- Explanation 
- Observation 1
- Observation 2
```{r}
ego.up <- enrichGO(gene = names(sig.up.LFC),
                      OrgDb = org.Mm.eg.db, 
                      keyType = 'SYMBOL',
                      readable = FALSE,
                      ont = "ALL",
                      pAdjustMethod = "BH",
                      pvalueCutoff = 0.05, 
                      qvalueCutoff = 0.2)
```

