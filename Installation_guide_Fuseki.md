# Apache Jena Fuseki Installation Guide

This guide outlines the steps required to install and configure Apache Jena Fuseki for managing RDF datasets.

## Prerequisites

- Ensure that Java is installed on your system. You can verify the installation by running:

  ```bash
  java -version
  ```
  
## Dowload apache fuseki 

From https://jena.apache.org/download/index.cgi :
- Choose apache-jena-fuseki-5.3.0.tar.gz (or the zip file)
- Navigate to the directory where you want to install Fuseki (e.g., /usr/local) and extract the archive:
```bash
tar xvfz apache-jena-fuseki-5.3.0.tar.gz
rm apache-jena-fuseki-5.3.0.tar.gz
```
- (Optional) Create a symbolic link to make future upgrades easier: 
```bash
ln -s apache-jena-fuseki-5.3.0 fuseki
```
## Configuration
Increase JVM Heap Size

For large datasets, increasing the Java heap size is recommended:
- Navigate to the Fuseki directory:
```bash
cd fuseki
```
- Edit the fuseki-server script : 
Locate the following line: `JVM_ARGS=${JVM_ARGS:--Xmx4G}`
Replace it with: `JVM_ARGS=${JVM_ARGS:--Xmx16G}`
This will allocate up to 16 GB of memory to the Java Virtual Machine.

## Set the FUSEKI_HOME Environment Variable

To simplify command-line usage, it is helpful to define the FUSEKI_HOME environment variable:

- Open your .bashrc file for editing:
```bash
nano ~/.bashrc
```
- Add the following line, modify the path for that points to wherever you installed fuseki :
```bash
 export FUSEKI_HOME=/usr/local/fuseki
 ```
- Apply the changes to your current session:
```bash
source ~/.bashrc
```

## Check Fuseki server installation 

- Check environment variable is correctly set and working : 
```bash
echo $FUSEKI_HOME
```
- Check version of fuseki server : 
```bash
$FUSEKI_HOME/fuseki-server -version
```

## Load the bio-tools RDF file and the EDAM ontology:
```bash
${FUSEKI_HOME}/fuseki-server --file=../edam_biotools/bioschemas-dump_05_01_2025.ttl --file=../edam_biotools/EDAM_1.25.owl  /biotoolsEdam
```
Loading might take a while. When you see something like :  
`14:15:51 INFO  Server          :: Started 2025/04/08 14:15:51 CEST on port 3030`  your server is ready.

Do NOT close the terminal, if want to kiil server CTRL+C
