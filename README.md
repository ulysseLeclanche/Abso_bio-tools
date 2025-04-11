# Assessing bioinformatics software annotations: bio.tools case-study 

The article [Assessing bioinformatics software annotations: bio.tools case-study](JOBIM2025_submission_219.pdf) has been submitted to jobim 2025. 

This github repository contains the code used in the article to extract metadata from the bio.tools RDF schema, create article figures and calculate tool annotation statistics. 

## Using fuseki

To load the turtle file and make SPARQL queries on it, a fuseki server is required. If necessary, follow the [Apache Jena Fuseki installation guide](Installation_guide_Fuseki). 

The command for loading the bio-tools RDF file and the EDAM ontology with the Fuseki server is as follows: 
```bash
${FUSEKI_HOME}/fuseki-server --file=../edam_biotools/bioschemas-dump_05_01_2025.ttl --file=../edam_biotools/EDAM_1.25.owl  /biotoolsEdam
```
Loading might take a while. When you see something like :  
`14:15:51 INFO  Server          :: Started 2025/04/08 14:15:51 CEST on port 3030`  your server is ready.
Do NOT close the terminal, if want to kiil server CTRL+C

## Creating a conda environment

All the python packages needed to run the notebooks are described in the `environment.yml` file. This file allows you to directly create a conda environment to run the notebooks: 
```bash
conda env create --file environment.yml
```

## Github repository organization

- The `Dataframes`  folder contains all the data tables in tsv format used to create the figures. 

- The `edam_biotools`  folder contents the metadata file from the bio.tools RDF schema and the version of the edam ontology used. 

- The `Figures` Figures folder have the python notebooks for reproducing each figure in the article. 

- The `Tool_annotations_metrics`  folder includes a notebook for reproducing figure dataframes and calculating information on redundancy or deprecated classes in the edam ontology. 
