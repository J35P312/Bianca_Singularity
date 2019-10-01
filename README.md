# Bianca_Singularity
Singularity container for running basic Bioinformatic analysis on the Bianca cluster.

The environent contains 

	Abyss

	bedtools
	
	BESST

	BCFtools

	biobambam

	bwa
	
	CD-hit

	Cite-seq-count
	
	cyvcf2
	
	Fermi2

	GATK 4

	IchorCNA

	Lumpy

	minimap2

	mummer

	picard tools
	
	pysam
	
	pytabix

	samtools
	
	Star

	Tabix

	VT

	WisecondorX

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
