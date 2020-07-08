# Requirement Analysis

##  Functional Requirement

### Expectation:

1. Put checkpoints at each step to let the users make sure every step is correct.
2. Separate Network Construction Step from Preprocess Steps so as to allow the users to preprocess the data themselves;
3. Provide a function for the preprocess steps of TCGA & GTEx respecctively.

### User Input and Output

####  1. Prepare Data
- gene expression 
- genotype data 
- annotation (separate for gene and snp)

### 2. Prepare Setting File

- one file is enough
	- preprocess gene
	- genotype
	- netowork
	
.yml

```par
filepath: ./
genotypename: example.geno
snpname: example.snp
indivname: example.ind
evecoutname: example.pca.evec
evaloutname: example.eval
altnormstyle: NO
numoutevec: 2
numoutlieriter: 5
numoutlierevec: 2
outliersigmathresh: 6.0
qtmode: 0
```
provide default file

#### change settings
```bash
programm -change_settings --parameter value
```
#### lookup settings
```bash
programm -show_settings  --parameter
```

### 3 or 5.  Match genotype and geneexp ?
? not sure before or after
user provide sample ids ?
```bash
tnet geno_geneexp_match 
```

### 4.  Preprocess Genotype Data

```bash
tnet -preprocess_genotype --setting1 v1 --setting2
```

### 5. Preprocess Gene Data

```bash
tnet -preprocess_gene_exp --setting1 v1 --setting2
```
### 6. Control Covariates & Population Structure

```bash
tnet control_cov
```

### 7. Cis-eQTL

```bash
tnet cis-eQTL
- range
- type
- number of cpu
- parallel?
```
estimate wall time

### 8. Network

```
tnet network_analysis
- number of gene
- number of bootstraps 
```

 ```
 tnet summary
```


### Summary

This project aims to streamline the process of constructing gene regulatory networks using RNA-Seq.

Main steps are as following:

- Preprocess
	- Preprocessing Genotype Data
	- Preprocessing Gene Expression Data
	- Matching Gene Expression Data with Genotype Data
	- Preprocess Genotype Data (Con't)
	- Separating SNPs based on MAF
- Cis-eQTL Analysis
	- Common e-QTL analysis
	- Low-Frequency Cis-eQTL Analysis
	- Rare Cis-eQTL Analysis 
	-  Combined Common, Low-Frequency, and Rare eQTL Results
- Network Analysis
	- Network Analysis
	- Bootstrap Analysis
	- Network Visualization

### Basic Input & Output Diagram
Input & output  process can be summarized as following:
#### Preprocess
```mermaid
graph LR;
Genotype/jpt.ped--> PreprecessingGenotypeData -->B
```

### Function 1

#### Input 
- format:
- example
	```r
		### 
		### 
		```
	
#### Process

Breif introduction to the algorithm

#### Output
- format:
- example
	```r
		### 
		### 
		```

### Function 2

## Environment Requirement

### Development Environment
 - development language: R/shell
 - development platform: 
 - collaboration: github
 - Test:

# Architecture Design

## Basic Idea

Three layers of 

```mermaid
sequenceDiagram
User Interface ->> User Interface: check paramter or settings 
User Interface ->> File Management: check input file valid or not
File Management -->> User Interface: return file status
User Interface ->> Execute Function: input paramter
File Management -->> User Interface: return file status 

```

## Structure Design

### File structure
- directory 1
	- directory 2
	- 
### Class & Function Structure


## Workflow Design



```mermaid
sequenceDiagram
User Interface ->> Bob: Hello Bob, how are you?
Bob-->>John: How about you John?
Bob--x Alice: I am good thanks!
Bob-x John: I am good thanks!
Note right of John: Bob thinks a long<br/>long time, so long<br/>that the text does<br/>not fit on a row.

```

## Style & Convention

### R programming  convention

Google's R style Guide:
[http://web.stanford.edu/class/cs109l/unrestricted/resources/google-style.html](http://web.stanford.edu/class/cs109l/unrestricted/resources/google-style.html)
<!--stackedit_data:
eyJoaXN0b3J5IjpbODYwOTI1OTgxLC0xMDE0MDc2OTE3LDE3Nj
U0NTMxNTMsLTEzMDc1NTMxNjksLTYwMTI5NTA4NywxNDkxNTA0
NTI2LC02Mjc4NDQ0NDEsMzE2NzgyNTk1LC0xNzMyNjYwNDg3LD
E2NDYwMjA0NiwyNjYyNTI3OCwzNDc0MjMzNjcsMTMzMTQxODQ4
MSwtMTMzOTA3MjU4MSwtMTY3MDQyNzM1MV19
-->