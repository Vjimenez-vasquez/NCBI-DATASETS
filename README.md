# NCBI-DATASETS
NCBI-DATASETS

```r
# 5.1: generar un archivo *.txt que contenga la lista de accesiones "genome" a descargar (ej. GCA_002811845.1), este será el input del programa a emplear

# 5.2: install NCBI-DATASETS

conda create -n ncbi_datasets
conda activate ncbi_datasets
conda install -c conda-forge ncbi-datasets-cli

# 5.3: run commands

#!/bin/bash

genome=$1
for file in $(cat $genome)
do 
datasets download genome accession ${file} --filename ${file}.zip ;
unzip ${file}.zip -d ${file}/ ;
rm ${file}.zip ;
cp ${file}/*/*/*/*.fna .
rm -r ${file}/ ;
done

for file in *.fna
do
mv "$file" "$(echo "$file" | sed -e 's/.1_.*/.1.fasta/g')"
mv "$file" "$(echo "$file" | sed -e 's/.2_.*/.2.fasta/g')"
mv "$file" "$(echo "$file" | sed -e 's/.3_.*/.3.fasta/g')"
done 
ls ;
```

# USAGE
```r
./command_ncbidatasets.sh genomes.txt
```

# OUTPUT
```r
genomas descargados en formato *.fasta
```
