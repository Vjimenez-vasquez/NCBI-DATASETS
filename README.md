# NCBI-DATASETS
NCBI-DATASETS

```r
# 5.1: install NCBI-DATASETS

conda create -n ncbi_datasets
conda activate ncbi_datasets
conda install -c conda-forge ncbi-datasets-cli

# 5.2: run commands

#!usr/bin

for file in $(cat genomes.txt)
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
