Genome Modeling System Enhancement
==================================

This project is the enhancement of The Genome Modeling System (GMS) for supporting more model types.  
Please check more detailed in <a href="https://github.com/genome/gms">Genome Modeling System</a>

<img src="https://github.com/HealthHackAu2016/gms/blob/ubuntu-12.04/assets/dna-1280.jpg"></img>


# Problem Description
GMS is being widely used for years in many cases of genetics. Research can run integrated tools and manage generated results within command line environment.
But development has been slowing down and stopped in 2015. GMS gradually couldn't support state of the art technologies since then. To solve this situation, this project needs more contributors to continue development.
On this stage, we'd like to add more model types for current version of GMS which includes:

 - Bwa mem
 - Bwa aln
 - Somatic-variation upgrade
 - Clin-seq upgrade
 - etc

<img src="https://github.com/HealthHackAu2016/gms/blob/ubuntu-12.04/assets/gms_commandtree.png"></img>

# Challenge
GMS is well-documented for users. But unfortunately they don't provide corresponding documents in repository to let developers understand software structure and data flow. 
To some degree, developers can only understand codes from users' manual and wiki. So we started **REVERSE ENGINEERING**.

# Strategy


# How To Use
## Installation
### Installation on Ubuntu
Be sure to log out and back in after install. You will need the system to recognize that you are in the "genome" group.
For a standard, standalone, configuration on Ubuntu 12.04 run:


    // install git ssh make if you don't have
    sudo apt-get install git ssh make
    
    // clone from repo
    git clone https://github.com/genome/gms.git
    
    // change to gms folder
    cd gms
    
    // run makefile
    make
    
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

# License

**MIT License**

Copyright (c) 2016 GeneGenie

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.

# Quick navigation:



