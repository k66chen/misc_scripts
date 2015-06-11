# ICGC data fetching scripts #

A set of scripts to parse and create ICGC data. Downloading files from the repository has been depreciated, so the scripts generally use the root folder containing all the projects as input now.

# Quick rundown of what each file does #

### allprojects.txt ###

A simple list of all project codes as of release 18. This used to be for generateall.sh, which runs the determineEmbargo on each product. Since this method has been depreciated, this file is not useful at the moment.

### clinicalTableFix.py ###

Reads the logfiles generated by findClinical and creates a "better" table. The reason this script exists is because sometimes we need to get a subset of projects or fields clinical data. The big table created from findClinical will always consider all projects and all fields.

### determineEmbargo.py ###

Script used to determine the embargo status of a site based on which release it originally debut and the number of whole genomes it has at certain periods of time. The full logic is found inside the script. This is the only script that uses the metadata from the repository, so it is slow since it needs to download everything.

### findAnalysisType.py ### 

Attempts to replicate the "Donor Analysis Type" numbers, working with raw data. Base script is findTotalDonors.

### findClinical.py ###

Finds clinical % metrics for projects. Uses some functions in parseForWGS.

### findDatatypes.py ###

Attempts to replicate the "Available Data Types" numbers, working with raw data. Base script is findTotalDonors.

### findTotalDonors.py ###

Finds the total number of donors as seen on the data portal. The primary goal of this script is to find orhpan donors and ignore them.

### generateall.sh ###

A quick bash script that calls determineEmbargo on a number of projects.

### make\_heat.r ###

Rscript that makes a heatmap off of a tab delimited file. Right now it is optimized for clinical data.

### parseForWGS.py ###

A badly named file, while originally finding whole genome counts for projects, now contains a number of functions that work with the ICGC projects.

### signedofflist.txt ###

Fairly useless, needed to have this on cluster.
