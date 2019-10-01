Bootstrap: docker
From: ubuntu:16.04

%environment
SHELL=/bin/bash
PATH=/opt/anaconda/bin:${PATH}
LC_ALL=C.UTF-8

%runscript
    echo "This is what happens when you run the container..."
    export PATH=/opt/anaconda/bin:${PATH}    

%post
    echo "Hello from inside the container"
    apt-get update
    apt-get -y install wget git bzip2 build-essential gcc zlib1g-dev language-pack-en-base apt-transport-https make cmake unzip python3
    update-locale LC_ALL=en_US.UTF-8 LANG=en_US.UTF-8

    cd /root/ && wget https://repo.continuum.io/miniconda/Miniconda2-latest-Linux-x86_64.sh
    cd /root/ && chmod 700 ./Miniconda2-latest-Linux-x86_64.sh
    cd /root/ && bash ./Miniconda2-latest-Linux-x86_64.sh -b -p /opt/anaconda/

    export PATH=/opt/anaconda/bin:${PATH}

    conda config --add channels defaults
    conda config --add channels conda-forge
    conda config --add channels bioconda

    conda install -f -c conda-forge -c bioconda wisecondorx
    pip install -U git+https://github.com/CenterForMedicalGeneticsGhent/WisecondorX
    conda install r-ichorcna
    conda install -c bioconda samtools sambamba minimap2 biobambam bedtools cd-hit fermi2 star pysam pytabix freebayes
    conda install -c bioconda lumpy-sv mummer4 bwa picard abyss gatk4 vt bcftools tabix salmon blast cyvcf2 star-fusion
    pip install BESST
    pip install svdb
    pip install CITE-seq-Count
    
    cd /

    mkdir reference
    cd reference
    wget ftp://ftp.ebi.ac.uk/pub/databases/gencode/Gencode_human/release_32/gencode.v32.annotation.gtf.gz
    wget ftp://ftp.ebi.ac.uk/pub/databases/gencode/Gencode_human/release_32/GRCh38.primary_assembly.genome.fa.gz
    wget ftp://ftp.ebi.ac.uk/pub/databases/gencode/Gencode_human/release_32/gencode.v32.transcripts.fa.gz

    wget ftp://ftp.ebi.ac.uk/pub/databases/gencode/Gencode_human/release_32/GRCh37_mapping/gencode.v32lift37.annotation.gtf.gz
    wget ftp://ftp.ebi.ac.uk/pub/databases/gencode/Gencode_human/release_32/GRCh37_mapping/gencode.v32lift37.transcripts.fa.gz
    wget ftp://ftp.ebi.ac.uk/pub/databases/gencode/Gencode_human/release_32/GRCh37_mapping/GRCh37.primary_assembly.genome.fa.gz

    wget ftp://ftp.ebi.ac.uk/pub/databases/gencode/Gencode_human/release_32/GRCh37_mapping/gencode.v32lift37.metadata.HGNC.gz
    wget ftp://ftp.ebi.ac.uk/pub/databases/gencode/Gencode_human/release_32/gencode.v32.metadata.HGNC.gz

    wget https://hgdownload.cse.ucsc.edu/goldenPath/panPan2/bigZips/panPan2.fa.gz
    wget https://hgdownload.cse.ucsc.edu/goldenPath/panTro5/bigZips/panTro5.fa.gz

    samtools faidx GRCh38.primary_assembly.genome.fa.gz
    samtools faidx GRCh37.primary_assembly.genome.fa.gz
    samtools faidx panPan2.fa.gz
    samtools faidx panTro5.fa.gz
    
