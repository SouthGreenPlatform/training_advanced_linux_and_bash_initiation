
# Practice 1 : Get Connecting on a linux server by `ssh`

In mobaXterm:
1. Click the session button, then click SSH.
  * In the remote host text box, type: HOSTNAME (see table below)
  * Check the specify username box and enter your user name
2. In the console, enter the password when prompted.
Once you are successfully logged in, you will use this console for the rest of the lecture.

| Cluster HPC | hostname| 
| :------------- | :------------- | 
| IRD HPC |  bioinfo-inter.ird.fr | 

* Connect on the HPC

-----------------------

# Practice 2 : Preparing working environnement 

* Move into the directory /scratch2
* Create a working directory such as Formation-X (X corresponds to your login id/number) 
* Move into this directory just created and check the current/working directory just by looking the prompt
 
-----------------------

<a name="practice-3"></a>
### Practice 3 : Using the && separator

* On the console, type the 2 following linux commands to get data necessary for the next :

{% highlight bash %}
# get the file on the web and decompress the gzip file 
wget http://itrop.ird.fr/LINUX-TP/LINUX4JEDI-TP.tar.gz && tar -xzvf LINUX4JEDI-TP.tar.gz
{% endhighlight %}

* Check the content of your home directory on the server now 
* Delete the file LINUX4JEDI.tar.gz on the server - `rm`
* Execute the `tree` command 

<details>
{% highlight bash %}
bash-4.2# tree -L 2  
.
|-- 1-fastq
|   |-- SRR8517015_1.10000.fastq
|   |-- SRR8517015_2.10000.fastq
|   |-- SRX5320622_1.10000.fastq
|   |-- SRX5320622_2.10000.fastq
|   |-- SRX5320631_1.10000.fastq
|   `-- SRX5320631_2.10000.fastq
|-- 2-bam
|   |-- B1.starMSU7.chr1.sorted.bam
|   |-- B1.starMSU7.chr1.sorted.bam.bai
|   |-- B2.starMSU7.chr1.sorted.bam
|   |-- B2.starMSU7.chr1.sorted.bam.bai
|   |-- G1.starMSU7.chr1.sorted.bam
|   |-- G1.starMSU7.chr1.sorted.bam.bai
|   |-- G2.starMSU7.chr1.sorted.bam
|   `-- G2.starMSU7.chr1.sorted.bam.bai
|-- 3-RNAseqCount
|   |-- erz340_suppl_supplementary_table_s5.csv
|   `-- erz340_suppl_supplementary_table_s5_new.csv
|-- 4-vcf
|   `-- OgOb-all-MSU7-CHR6.GATKVARIANTFILTRATION.shuf.100000.vcf.gz
|-- 9-denovoAssembly
|   |-- DAOSW_abyss-contigs.fa -> Ob/DAOSW_abyss-contigs.fa
|   |-- Ob
|   |-- Og
|   `-- TOG5681_abyss-contigs.fa -> Og/TOG5681_abyss-contigs.fa
|-- Bank
|   |-- all.con
|   `-- all.seq
|-- Other
|   |-- abcd.txt
|   |-- contact.txt
|   |-- example.txt
|   `-- test.list
|-- Script
|   |-- helloworld-var.sh
|   |-- helloworld.sh
|   |-- q
|   |-- script.sh
|   `-- testNum.sh
|-- erz340.pdf
`-- erz340_suppl_supplementary_table_s1.csv
{% endhighlight %}

 </details>
 
<img width="80%" class="img-responsive" src="{{ site.url }}/images/tpLinux/arbo3.png"/>


 
-----------------------
<a name="practice-4"></a>
### Practice 4 :  Monitoring processes

#### Displaying the list of processes
* Type the command `w` through 2 consoles : one connected on bioinfo-master, the other connected on one node
* Type (on the node) the command `ps` without option, then with the option `u`, `ua`,  `uax`
* Type the command `top` on the node 
* Then use the "option" c to display the complete process
* Then use the "option" u to display only your processes

#### Kill a process - downloading files from SRA through two ways

* Go into the directory `LINUX4JEDI-TP/1-fastq` 
* Display the size of all fastq files - `ls -lh, du -h`

We want to download one fastq file from NCBI SRA (available here https://www.ncbi.nlm.nih.gov/sra?linkname=bioproject_sra_all&from_uid=518559) using SRAtoolkit as below :

{% highlight bash %}
module load bioinfo/sratoolkit/2.9.2 
fastq-dump --gzip --split-files SRXXXX
{% endhighlight %}

This will download the SRA file (in sra format) and then convert them to fastq.gz file . More details on https://isugenomics.github.io/bioinformatics-workbook/dataAcquisition/fileTransfer/sra.html

* Download the fastq file in the directory `LINUX4JEDI-TP/1-fastq` `fastq-dump, &`
* Check that 2 fastq files are downloading `ls -lhrt, watch -n 5 -d`
* Display the list of processes `ps -ux, jobs`
* kill your process "fastq-dump" directly from bioinfo-master `kill -9`

-----------------------



<a name="practice-5"></a>
### Practice 5 : Searching for text using `https://regex101.com/`

* Go to the web site https://regex101.com/
* Copy the following accession gene names and paste it in the field `test string`
{% highlight bash %}
xkn59438
yhdck2
eihd39d9
chdsye847
hedle3455
xjhd53e
45da
de37dp
{% endhighlight %}

* print only the accession names that satisfy the following criteria – treat each criterion separately
> * contain the number 5
> * contain the letter d or e
> * contain the letters d and e in that order
> * contain the letters d and e in that order with a single letter between them
> * contain both the letters d and e in any order
> * start with x or y
> * start with x or y and end with e
> * contain three or more digits in a row
> * end with d followed by either a, r or p

------------------------

<a name="practice-6"></a>
### Practice 6 : Searching for text using `grep`

* List the content of the directory `LINUX4JEDI-TP/Bank` 
* Display the first 10 lines of all the files that are the `Bank` directory - `head`
* Display the last 20 lines of all the files  - `tail`
* Count the sequences number in the two files that are the `Bank` directory - `grep`
* Print the line that contains the gene name `DEFL` - `grep regexp`, all.seq
* Print the line that contains the gene name `DEFL` following just by one digit - `grep regexp`, all.seq

Infos:  The file all.con contains the sequence of the asian rice genome (fasta format) and all. pep contains the sequence of all the genes annotated on the rice genome (fasta format).


#### from a gff file

We have the genome reference (all.con, fasta file) and we want to download the annotation of our genome reference (gff format).
* Go on the following page : http://rice.uga.edu/pub/data/Eukaryotic_Projects/o_sativa/annotation_dbs/pseudomolecules/version_7.0/all.dir
* Copy the url of the rice genome annotation file that we will use to download the file directly on the server (all.gff3)
* Go to the `bank` directory and type the following command :

{% highlight bash %}
wget PUT_GFF_URL
{% endhighlight %}

* Count the number of genes annotated in the genome reference (lines with the word `gene` in the gff file) - `grep`
* Search for the nbs-lrr genes - `grep`
* Count the number of gene `DEFL` following just by one digit - `grep regexp`
* Count the number of gene `DEFL` following by one or two digit ranging from 1 to 50 - `grep regexp`
* Counts the number of mRNA in the chromosome 1 - `grep -c regexp`
* Counts the number of mRNA in the first five chromosomes - `grep -c regexp`
* count the number of gene by chromosome - `grep, cut, sort, uniq` 

-----------------------

<a name="practice-7"></a>
### Practice 7 :  Displaying lines with `sed`
For this exercise, you will work on the fastq file LINUX4JEDI-TP/1-fastq/SRR8517015_1.10000.fastq

* Print the 8 first lines
* Print the lines 5 to 12
* Print only the sequences ids
* Print only the sequences ids and nucleotides sequences

-----------------------

<a name="practice-8"></a>
### Practice 8 : Deleting lines with `sed`
For this exercise, you will work on the fastq file LINUX4JEDI-TP/1-fastq/SRR8517015_1.10000.fastq

* Delete the end of the file from the line 9
* Delete the lines containing only a `+`
* Delete the lines containing only a `+` and the quality sequences

-----------------------

<a name="practice-9"></a>
### Practice 9 : File parsing with `sed` using regexp (regular expression)

#### Fastq file
For this exercise, you will work on the fastq file `LINUX4JEDI-TP/1-fastq/SRR8517015_1.10000.fastq`
* Print only read sequences using a regular expression (print only lines with the letters ATCG)

#### vcf file
For this exercise, you will work with the vcf file `LINUX4JEDI-TP/4-vcf/OgOb-all-MSU7-CHR6.GATKVARIANTFILTRATION.shuf.100000.vcf.gz`
* Print only the line corresponding to the header (line starting by #) or polymorphisms passing all filters (line with tag `PASS`)

-----------------------

<a name="practice-10"></a>
### Practice 10 : File modification with `sed`

#### From fasta files in `LINUX-TP/Fasta`
* In the `LINUX4JEDI-TP/9-denovoAssembly` directory, there are two files : `DAOSW_abyss-contigs.fa`and `TOG5681_abyss-contigs.fa`. Before to generate a unique file with all 2 libraries, we would like to tag each sequence per its origin. In each file, add the respective tag DAOSW_ / TOG5681_ just before the identifier.

{% highlight bash %}
# File DAOSW_abyss-contigs.fa initially
>0 71 531
CTTTTTGAACTTTTTCATTCCGGTCAAAAAAATATCGCACCCGTGGGGGCTCAATATATGCCAATATTGGC
>2 217 449


# File DAOSW_abyss-contigs.rename.fasta
>DAOSW_0 71 531
CTTTTTGAACTTTTTCATTCCGGTCAAAAAAATATCGCACCCGTGGGGGCTCAATATATGCCAATATTGGC
>DAOSW_2 217 449

{% endhighlight %}

Rq : First test the sed command on one file, then store the results in new files named DAOSW_abyss-contigs.renamed.fasta and TOG5681_abyss-contigs.renamed.fasta

> BONUS : try to modify each line starting with > such as :  `>0 71 531` to `>DAOSW_0`

#### vcf file `LINUX4JEDI-TP/4-vcf/OgOb-all-MSU7-CHR6.GATKVARIANTFILTRATION.shuf.100000.vcf.gz`
* Now, in the VCF file, we would like to replace the genotypes by allelic dose. This means that we should replace the whole field by `0` when the genotype is `0/0`, by `1` when the genotype is `0/1` and `2` when the genotype is `1/1`

#### With fastq files in LINUX4JEDI-TP/1-fastq/
* Transform the file SRR8517015_1.10000.fastq into a fasta format
* In one command line, transform all fastq files of the directory in fasta (save the files before) - `sed -i`

-----------------------

<a name="practice-11"></a>
### Practice 11 : Manipulating files with `awk`

### From a fasta file

#### seqtk
Seqtk (https://github.com/lh3/seqtk) is a fast and lightweight tool for processing sequences in the FASTA or FASTQ format. It seamlessly parses both FASTA and FASTQ files which can also be optionally compressed by gzip.

We are going to use seqtk comp to get statistics  get the nucleotide composition of FASTA/Qprint the size of the genome 

* Run seqtk comp on the file `Bank/all.con - `seqtk comp all.con`  
* Using awk, first print the whole line of the output generated by seqtk, then print only the columns 1 and 2 - `| awk `
* Print the column 1 and 2 only for chr1 to chr12
* Calculate the genome size in pb

#### From the gff file precedently downloaded
* Extract the coordinate from the gff file
* Calculate the mean of the gene length
* Calculate the mean of the gene length for the chromosome 1
* Count the number of genes above 2000bp length
* Bonus: calculate the mean of gene length for each chromosome in one command line


-----------------------

<a name="practice-12"></a>
### Practice 12 : For loop with bash

* Go into the directory `LINUX4JEDI-TP/1-fastq/`
* List the directory content
* Run fastq-stats program ( [more](http://manpages.ubuntu.com/manpages/xenial/man1/fastq-stats.1.html) to get stats about the fastq file `SRR8517015_1.10000.fastq`
* 
{% highlight bash %}
fastq-stats -D SRR8517015_1.10000.fastq
{% endhighlight %}

* Use a `for` loop to run fastq-stats with each fastq file in the directory
* 
{% highlight bash %}
for file in *fastq; do 
  fastq-stats -D $file > $file.fastq-stats ; 
done;
{% endhighlight %}

-----------------------
<a name="practice-13"></a>
### Practice 13 : The last but not the least practice

#### A bash script to download fastq files from a file that contains a list of accessions

Write a bash script that :
* takes as argument a file that contains a list of accessions (/scratch/accession.list)
* reads this file and downloads fastq files (reverse and forward) for each accession - fastq-dump

{% highlight bash %}
# Use the following code to read the file (variable $filename) line by line
while read line;
do
echo $line;
done < $filename
{% endhighlight %}

-----------------------
#### A bash script to get basic statistics on each fastq file (in the directory 1-fastq) using fastq-stats

##### Before writing the script, we will test the fastq-stats command on a bash terminal

* Run fastq-stats on a fastq file
* Run fastq-stats on a fastq file and get the column 2 of the output of the command 
* Run fastq-stats on a fastq file, get the column 2 of the output of the command and turn the column into a single row - `linux command: paste -s`
* Save the output of the command in the file 
 
{% highlight bash %}
# fastq-dump output
reads	10000
len	125
len mean	125.0000
len stdev	0.0000
len min	125
phred	33
window-size	10000
cycle-max	35
qual min	2
qual max	38
qual mean	36.1021
qual stdev	4.2358
%A	25.5594
%C	24.3560
%G	26.1111
%T	23.8691
%N	0.1043
total bases	1250000

# We want this format
10000	125	125.0000	0.0000	125	33	10000	35	2	38	36.1021	4.2358	25.5594	24.3560	26.111123.8691	0.1043	1250000
{% endhighlight %}


##### Write a bash script 

Write a bash script that :
* takes as argument a directory (absolute path) that contains fastq files 
* executes the command fastq-stats as seen just before , the output is saved into a file

##### Bonus

On a terminal, use awk to parse all files created by the previous bash script and to generate the following output:

{% highlight bash %}
SRR8517015_1.10000.fastq.stats          10000        125        125.0000        0.0000        125        33        10000        35        2        38        36.1021        4.2358        25.5594        24.3560        26.1111        23.8691        0.1043        1250000
SRR8517015_2.10000.fastq.stats          10000        125        125.0000        0.0000        125        33        10000        35        2        38        34.4527        7.0727        23.5631        25.5657        25.6063        25.2649        0.0000        1250000
SRX5320622_1.10000.fastq.stats          10000        125        125.0000        0.0000        125        33        10000        35        2        38        36.4891        3.6410        26.3371        24.0457        24.8703        24.6883        0.0586        1250000
{% endhighlight %}

----------------------- 
#### Analysis of the read count file `3-RNAseqCount/erz340_suppl_supplementary_table_s5.csv`

Goal : Get the chromosome and its positions (start-stop) for some genes differentially expressed using the read count file and the gff file downladed

##### Get the first ten rows with the lowest p-value 
* display the first lines of this file
* substitute the ";" by the "\t"
* As the file is already sorted, extract the first ten lines and save the result in a new file called `my_10_genes.tab`

<details>
{% highlight bash %}
[tranchant@node6 3-RNAseqCount]$ head erz340_suppl_supplementary_table_s5.csv 
gene_id;log2FoldChange;lfcSE;pvalue;padj;symbols;MsuAnnotation
LOC_Os06g06750;4,02391987172844;0,291852309336462;4,76E-32;1,20E-27;MADS5;OsMADS5 - MADS-box family gene with MIKCc type-box, expressed
LOC_Os03g11614;6,14058803847572;0,534044090654195;2,40E-25;3,03E-21;LHS1;OsMADS1 - MADS-box family gene with MIKCc type-box, expressed
LOC_Os04g43580;-2,32647724746766;0,178467573376802;1,70E-22;1,43E-18;G1L4;DUF640 domain containing protein, putative, expressed
LOC_Os02g45770;4,57158531291166;0,416805180501083;1,13E-21;7,08E-18;MFO1;OsMADS6 - MADS-box family gene with MIKCc type-box, expressed
LOC_Os03g14140;5,01958570820803;0,502245405032766;1,05E-18;5,29E-15;;POEI16 - Pollen Ole e I allergen and extensin family protein precursor, expressed
{% endhighlight %}
</details>

* sort the file on the locus name and save the result into a new file `my_10_genes.sorted.tab`

##### Get the columns chr, start, stot, info from the gff file

* print the columns chr, start, stot, info of the gff file
* print the columns chr, start, stot, info of the gff file but only for lines with the word `gene` in the gff file
* print only the locus identifier of each line of the gff file (eg : ID=LOC_Os01g01010)
* print only the locus identifier of each line of the gff file (eg : LOC_Os01g01010)
* generate the following file : 

{% highlight bash %}
[tranchant@node6 3-RNAseqCount]$ head all.gene.loc.csv 
Chr1 gene 2903 10817 LOC_Os01g01010
Chr1 gene 11218 12435 LOC_Os01g01019
Chr1 gene 12648 15915 LOC_Os01g01030
Chr1 gene 16292 20323 LOC_Os01g01040
{% endhighlight %}

* sort the file all.gene.loc.csv on the locus name and save the output in a new file

* Join the lines of the two files previously created on the common field (locus identifier) - linux command join


                  
 