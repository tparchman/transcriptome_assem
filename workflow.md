# Transcriptome assembly workflow
Jakoby Palma, Fall 2024

## Accessing remote servers
    $ ssh jpalma@ponderosa.biology.unr.edu
    
password: G00gle_it (temporary; those are zeros not ones.)
   
 change during first login using:
 
    $ passwd 

Make sure you work in the "working" directory

    $ cd working/jpalma

## Loading modules on Ponderosa

    $ module avail
Shows what tools are available within that directory

    $ module load sratoolkit/2.9.0 
Activates the specified tool, in this case it activates sratoolkit

## Accessing and downloading data from NCBI using `sratoolkit`

I am collecting raw RNAseq data from *Pinus*

```sh
sratools fastqdump SSR102398547238940   

```

Below I am downloading RNAseq data for *Pinus occidentalis*

```sh
sratools fastqdump SSR102398547238940   

```


## Using `trinity` to assemble tne RNAseq data for each species