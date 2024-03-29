# Welcome to Microbiome@UP Data Analysis Page

## About
This page will help you analyse data by following a few simple steps (using the provided scripts of course)
If there is anything you feel needs to get revised or clarified please send it through the [issues tab](https://github.com/SAmicrobiomes/Wrangler/issues)

### Metagenomic data preprocessing 

## 1 - FastQC

Before we get started, make sure you read up on what a fastq file is, and how different it is from a fasta. While at it check this [page as well](https://support.illumina.com/help/BaseSpace_OLH_009008/Content/Source/Informatics/BS/QualityScoreEncoding_swBS.htm). The previous quality score encoding page should checked in concert with [this one here](https://en.wikipedia.org/wiki/Phred_quality_score).
      
### 2 - Assembly

### 3 - Binning
#### 3.1 Read mapping
```
for items in *fasta; do bwa index $items; done
```

```
for f in $(ls *paired.fastq.gz | sed -e 's/_R1_001_paired.fastq.gz//' -e 's/_R2_001_paired.fastq.gz//' | sort -u)
do
/apps/bwa-0.7.17/bin/bwa mem -t 24 $f\_megahit_output.fasta  $f\_R1_001_paired.fastq.gz $f\_R2_001_paired.fastq.gz | /apps/samtools-1.10/bin/samtools sort -@24 -o $f\.bwa.bam -
done
```





