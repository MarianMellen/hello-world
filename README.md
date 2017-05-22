# oxBS-Seq processing
This is a collection of commands that I use to process oxBS-Seq fastq

#Link to my working folder

ln -s /path/to/fastq.gz

#cat deeper sequenced fastq
cat fastq1.gz fastq2.gz fastq3.gz > allfiles-cat.gz

#Trimming and fastqc
trim_galore --stringency 3 --fastqc --paired R1.fastq R2.fastq

#BISMARK alignment
$ bismark --bowtie2 -R 1 -p 4 --multicore 4 --non_directional path/to/bismark10/ -1 R1.fq -2 R2.fq &
 
#scale up multicore for faster alignment not p!
 
$ deduplicate_bismark -p --bam inputfile.bam
 
 
#multiple options for this one if needed
$ bismark_methylation_extractor --paired-end --no_overlap --comprehensive --merge_non_CpG --report --bedGraph --counts --multicore 10 --cytosine_report --genome_folder bismark10/ input.deduplicated.bam
