# Practice 3 : Using the && separator

* On the console, type the 2 following linux commands to get data necessary for the next :

```bash
# get the file on the web and decompress the gzip file 
wget http://itrop.ird.fr/LINUX-TP/LINUX4JEDI-TP.tar.gz && tar -xzvf LINUX4JEDI-TP.tar.gz
```

* Check the content of your home directory on the server now 
* Delete the file `LINUX4JEDI.tar.gz` on the server - `rm`
* Execute the `tree` command 

??? example "details"
    ```bash
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
    ```
 

![](img/arbo.png){: style="height:100px;width:1200px"; align=left}  

