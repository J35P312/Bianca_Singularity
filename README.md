# Bianca_Singularity
A template config for creating singularity environments for the Bianca cluster. This config is based on the
truatpasteurdotfr/singularity-docker-anaconda environment.

The environent contains anaconda, mummer, picard tools, nextflow , bwa and samtools.

# Create the environment

	The singularity environment is built using the following command

		sudo singularity Bianca.simg Bianca_standard_env.conf


# Use the environment

	Create a sbatch script, instead of loading modules, you run the  following:

		singularity shell Bianca.simg

	now you have access to the conda packages within the Bianca.simg environment.
	
	you may leave  the environemnt by typing exit.


# Edit the  environment

Add more packages by editing Bianca_standard_env.conf. open the file using any text editor, and add your conda commands
after line 26. you may need to create multiple conda environments within the singularity environment.
