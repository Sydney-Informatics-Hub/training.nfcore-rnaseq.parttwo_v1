---
title: "Setup RStudio on Nimbus VM"
teaching: 10
exercises: 0
questions:
- "How to get the full gene count-matrix for downstream analysis?"
- "How to open RStudio on the Pawsey training VM?"
- "How to use count matrix to identify differentially expressed genes?"



objectives:
- "Introduction to RStudio"
- "How to open RStudio on the Pawsey training VM?"

keypoints:
-

---

### R and RStudio
- R is a programming language for statistical computing and graphics.
- RStudio is an integrated development environment which can be used to write and excecute R-code.


#### Using R/RStudio IDE for DE analysis
- The gene-count matrix which was generated using the nefcore-rnaseq pipline can be used to perform statistical analyses and determine differentially expressed (DE) genes and pathways.
- Multiple independant packages/libraries have been developed in [R-programming](https://www.r-project.org/), which can be used for performing various kinds of 'omics' analysis. 
- R packages such as [DeSeq2](https://bioconductor.org/packages/release/bioc/html/DESeq2.html), [EdgeR](https://bioconductor.org/packages/release/bioc/html/edgeR.html) etc are used for identification of differencially expressed (DE) genes. We will be using DeSeq2 for our analysis.


### Run RStudio on the Nimbus trainee VM
This is a two step process

#### Step1: Run the rserver command (On the Nimbus VM)
```
# First, create a temporary rstudio-server  folder on your instance:
mkdir -p /tmp/rstudio-server
PASSWORD='abc' singularity exec -B /tmp/rstudio-server:/var/lib/rstudio-server -B /tmp/rstudio-server:/var/run/rstudio-server -B /data:/home rstudio_4.1.0.sif rserver --auth-none=0 --auth-pam-helper-path=pam-helper --server-user ubuntu
```
You should not see any output at this point, except a "running" command, i.e. the port is forwarded and running.

#### Step2: Open RStudio from a browser (On your local machine)
```
- Open up a browser window (IMPORTANT: Firefox does not work. Use Chrome or Safari.)
- Go to 146.118.XX.XX:8787
- Enter the username, which is your image operating system, e.g. ubuntu.
- Enter the password, which in this example is abc.
- Run your R commands as you normally would. All output is saved to the directory you have chosen to bind-mount in the RStudio server command.
- To end the session, simply exit from the browser. To also end the session on your Nimbus instance, run the following: lsof -ti:8787 | xargs kill -9
```

