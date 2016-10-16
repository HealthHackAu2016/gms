Genome Modeling System Enhancement
==================================

This project is for enhancement of The Genome Modeling System (GMS)
Check more detailed in <a href="https://github.com/genome/gms">Genome Modeling System</a>

# Problem Description
    


<img src="https://raw.githubusercontent.com/wiki/genome/gms/Images/gms_commandtreev2.png"></img>

# Strategy

# Progress


# How To Use
## Installation
### Installation on Ubuntu 12.04
Be sure to log out and back in after install. You will need the system to recognize that you are in the "genome" group.
For a standard, standalone, configuration on Ubuntu 12.04 run:


    $   sudo apt-get install git ssh make
    $   git clone https://github.com/genome/gms.git
    $   cd gms
    $   make
    
Once the installation completes make sure to log out and log in again to ensure your user permissions are set properly.

## Run
    
    // Step 1: Create Processing file
    genome processing-profile create reference-alignment --name='{name}' --read-aligner-name='bwa' --read-aligner-version='0.7.12' --read-aligner-params='mem -t 16 ::' --sequencing-platform='solexa' --dna-type='genomic dna' --transcript-variant-annotator-version='2' --transcript-variant-annotator-filter='top' --snv-detection-strategy='samtools r963 [-A -B] filtered by snp-filter v1' --indel-detection-strategy='samtools r963 [-A -B] filtered by indel-filter v1' --picard-version='1.46' --samtools-version='r963' --merger-name='picard' --merger-version='1.46' --duplication-handler-name='picard' --duplication-handler-version='1.46' --coverage-stats-params='1,5,10,15,20,30,40:0,500'
    
    // Step 2: Check Processing file
    genome processing-profile list reference-alignment

    // Step 3: Define Model
    genome model define reference-alignment  --reference-sequence-build='GRCh37-lite-build37'  --annotation-reference-build='124434505'  --subject='H_NJ-HCC1395-HCC1395_BL'  --processing-profile='{processing-profile-id}'  --dbsnp-build='127786607'  --model-name='{name}'

    // Step 4: Assign Data to Model
    genome model instrument-data assign by-expression --model='{model-name}'

    //Step 5: Build Model
    genome model build start "name='{model-name}'"

# Dependency









# Quick navigation:



