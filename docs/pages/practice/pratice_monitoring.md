## Practice

### Displaying the list of processes

* Type the command `w` through 2 consoles : one connected on bioinfo-master, the other connected on one node
* Type (on the node) the command `ps` without option, then with the option `u`, `ua`,  `uax`
* Type the command `top` on the node 
* Then use the "option" c to display the complete process
* Then use the "option" u to display only your processes

### Kill a process - downloading files from SRA through two ways

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



