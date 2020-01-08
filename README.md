# Bianca_Singularity
Singularity container for running basic Bioinformatic analysis on the Bianca cluster.

The environment contains 

	Abyss

	bedtools
	
	BESST

	BCFtools

	biobambam

	bwa

	Canvas
	
	CD-hit

	Cite-seq-count
	
	ClustalO
	
	cyvcf2

	Delly

	ExpansionHunter
	
	Fermi2
	
	Freebayes

	GATK 4

	IchorCNA

	Lumpy

	Manta

	minimap2

	mummer

	picard tools
	
	pysam
	
	pytabix

	sambamba

	samtools
	
	Star
	
	Star-fusion
	
	SVDB

	Tabix

	TIDDIT

	VT

	WisecondorX

References are found in the /reference folder These references include:

    Gencode GRCh38    : GRCh38.primary_assembly.genome.fa.gz
    Gencode GRCh37    : GRCh37.primary_assembly.genome.fa.gz
    ENSMBL Bonobo 1.1 : Pan_paniscus.panpan1.1.dna.toplevel.fa.gz
    ENSMBL Pantro3    : Pan_troglodytes.Pan_tro_3.0.dna.toplevel.fa.gz
    ENSMBL Gorilla4   : Gorilla_gorilla.gorGor4.dna.toplevel.fa.gz

reference fai and dict are available for all these references; transcript fasta and gene annotation gtf are available for the human reference genomes (Gencode).
ENSMBL gtf files are available in the /reference/ENSMBL

# Create the environment

	The singularity environment is built using the following command

		sudo singularity build Bianca.simg Singularity

	Or downloaded through the following command:

		singularity pull --name Bianca.simg shub://J35P312/Bianca_Singularity


# Use the environment

	In an interactive session, instead of loading modules, you run the  following:

		singularity shell Bianca.simg

	now you have access to the conda packages within the Bianca.simg environment.
	
	you may leave  the environemnt by typing exit.

    in an sbatch script you may do the following:

        singularity exec Bianca.simg <command>

    for instance, you may run nucmer using the following command:
        singularity exec Bianca.simg nucmer ref.fa contigs.fa


# Edit the  environment

Add more packages by editing Bianca_standard_env.conf. open the file using any text editor, and add your conda commands
after line 26. you may need to create multiple conda environments within the singularity environment.
