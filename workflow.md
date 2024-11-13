# Transcriptome assembly workflow
Jakoby Palma, Fall 2024

## Accessing remote servers
    $ ssh jpalma@ponderosa.biology.unr.edu
    
password: G00gle_it (temporary; those are zeros not O's.)
   
 change during first login using:
 
    $ passwd 

Make sure you work in the "working" directory

    $ cd working/jpalma

## Transfering data to remote servers

```Sh
$ rsync -av eriogonum_RNAseq jpalma@ponderosa.biology.unr.edu:/working/jpalma/


```

## Loading modules on Ponderosa

    $ module avail
Shows what tools are available within that directory

    $ module load sratoolkit/2.9.0 
Activates the specified tool, in this case it activates sratoolkit

## Accessing and downloading data from NCBI using `sratoolkit`

I am collecting raw RNAseq data from *Eriogonum*, using transriptome data from Walker et al. 2018 Am J Bot.

### For E. rotundiflorum
    $ fastq-dump --defline-seq '@$sn[_$rn]/$ri' --split-files SRR6435329

### For E. callistum
    $ fastq-dump --defline-seq '@$sn[_$rn]/$ri' --split-files SRR6435325

### For E. inflatum
    $ fastq-dump --defline-seq '@$sn[_$rn]/$ri' --split-files SRR6435283

### For E. arcuatum
    $ fastq-dump --defline-seq '@$sn[_$rn]/$ri' --split-files SRR6435289

## Tools for assessing raw fastq files

```Sh
grep '^@' SRR6435283_1.fastq -c
```
Finds all ID lines and counts the number of RNA fragments.

## Using `trinity` to assemble tne RNAseq data for each species
    $ module load Trinity/2.4.0
    $ module load bowtie2/2.2.5
    $ Trinity --seqType fq --max_memory 100G --left SRR6435329_1.fastq  --right SRR6435329_2.fastq --CPU > run.log 2>&1 &
This would use `trinity` to assemble the E. rotundiflorum data that was previously pulled.

## De novo assembly of E. callistum from SRA using `trinity`
    $ module load Trinity/2.4.0
    $ module load bowtie2/2.2.5
    $ Trinity --seqType fq --max_memory 100G --left SRR6435325_1.fastq  --right SRR6435325_2.fastq --CPU 6 > run.log 2>&1 & 