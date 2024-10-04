# Transcriptome assembly workflow
Jakoby Palma, Fall 2024


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