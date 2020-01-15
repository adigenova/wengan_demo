# Wengan demo
This repository contains a test dataset and the instructions to test [Wengan](https://github.com/adigenova/wengan) (version 0.1).


## Download the Wengan code
This test use the precompiled binnaries of the wengan v0.1, the binaries can be donwloaded with the following command:

```
wget https://github.com/adigenova/wengan/releases/download/0.1/wengan-v0.1-bin-Linux.tar.gz
tar zxvf wengan-v0.1-bin-Linux.tar.gz
# set WG to 
export WG=$PWD/wengan-v0.1-bin-Linux/wengan.pl
```

## Runnig the E.coli demo


### Dataset
The E.coli test sequencing data was collected from public repositories.

### Hardware used
This test was run in a node of the cluster leftraru [(NLHPC Chile)](http://www.nlhpc.cl/en/). The node has the following hardware and software: 

1. CPUs : Intel(R) Xeon(R) Gold 6152 CPU @ 2.10GHz (44 threads).
2. RAM : 188 Gb RAM.
3. File System : Lustre (EXAScaler)
4. Operating system : Linux 3.10.0-862.14.4.el7.x86_64  


### Wengan commands 


#### Running WenganD

```
#WG should point to wengan.pl script (found in the root installation directory)
WG=$PATH_TO/wengan-v0.1-bin-Linux/wengan.pl
# Assembling Illumina + Nanopore reads
perl ${WG} -x ontraw -a D -s ecoli/reads/EC.50X.R1.fastq.gz,ecoli/reads/EC.50X.R2.fastq.gz -l ecoli/reads/EC.ONT.30X.fa.gz -p ec_Wd_or1 -t 10 -g 5
# Assembling Illumina + PacBio (CLR) reads
perl ${WG} -x pacraw -a D -s ecoli/reads/EC.50X.R1.fastq.gz,ecoli/reads/EC.50X.R2.fastq.gz -l ecoli/reads/EC.PAC.30X.fa.gz -p ec_Wd_pr1 -t 10 -g 5
```

##### Expected results 
The fasta file *.SPolished.asm.wengan.fasta ( ec\_Wd\_or1.SPolished.asm.wengan.fasta and  ec\_Wd\_pr1.SPolished.asm.wengan.fasta respectively) contains the final genome assembly reported by Wengan. Both hybrid datasets are assembled to a single contig sequence (Genome Size of ~4.6 Mb).

##### Computational resource
The expected runtime with a single core is about 10 minutes and with 10 cores about 2 Minutes. The maximum RAM usage is around ~9 Gb.
 
#### Running WenganA

```
#WG should points to wengan.pl script (found in root installation directory)
WG=$PATH_TO/wengan-v0.1-bin-Linux/wengan.pl
# Assembling Illumina + Nanopore reads
perl ${WG} -x ontraw -a A -s ecoli/reads/EC.50X.R1.fastq.gz,ecoli/reads/EC.50X.R2.fastq.gz -l ecoli/reads/EC.ONT.30X.fa.gz -p ec_Wa_or1 -t 10 -g 5
# Assembling Illumina + PacBio (CLR) reads
perl ${WG} -x pacraw -a A -s ecoli/reads/EC.50X.R1.fastq.gz,ecoli/reads/EC.50X.R2.fastq.gz -l ecoli/reads/EC.PAC.30X.fa.gz -p ec_Wa_pr1 -t 10 -g 5
```

##### Expected results 
The fasta file *.SPolished.asm.wengan.fasta ( ec\_Wa\_or1.SPolished.asm.wengan.fasta and  ec\_Wa\_pr1.SPolished.asm.wengan.fasta respectively) contains the final genome assembly reported by Wengan. Both hybrid datasets are assembled to a single contig sequence (Genome Size of ~4.6 Mb).

##### Computational resource
The expected runtime with a single core is about 10 minutes and with 10 cores about 2 Minutes. The maximum RAM usage is around ~4 Gb.

#### Running WenganM

```
#WG should points to wengan.pl script (found in root installation directory)
WG=$PATH_TO/wengan-v0.1-bin-Linux/wengan.pl
# Assembling Illumina + Nanopore reads
perl ${WG} -x ontraw -a M -s ecoli/reads/EC.50X.R1.fastq.gz,ecoli/reads/EC.50X.R2.fastq.gz -l ecoli/reads/EC.ONT.30X.fa.gz -p ec_Wm_or1 -t 10 -g 5
# Assembling Illumina + PacBio (CLR) reads
perl ${WG} -x pacraw -a M -s ecoli/reads/EC.50X.R1.fastq.gz,ecoli/reads/EC.50X.R2.fastq.gz -l ecoli/reads/EC.PAC.30X.fa.gz -p ec_Wm_pr1 -t 10 -g 5
```

##### Expected results 
The fasta file *.SPolished.asm.wengan.fasta ( ec\_Wm\_or1.SPolished.asm.wengan.fasta and  ec\_Wm\_pr1.SPolished.asm.wengan.fasta respectively) contains the final genome assembly reported by Wengan. Both hybrid datasets are assembled to a single contig sequence (Genome Size of ~4.6 Mb).

##### Computational resource
The expected runtime with a single core is about 10 minutes and with 10 cores about 2 Minutes. The maximum RAM usage is around ~3 Gb.


