# Adapter Removal using PoreChop <img src="figures/ONT.png" height="40px">

[{% octicon arrow-left height:32 class:"right left" vertical-align:middle aria-label:hi %}](FTR.md) [{% octicon home height:32 class:"right left" aria-label:hi %}](index.md) [{% octicon arrow-right height:32 class:"right left" aria-label:hi %}](FTR_Q.md)

Similar to 2nd generation sequencing platforms data from most 3rd generation sequencing platforms contain linker, barcode or adapter sequences at the read beginning or end. Additionally, some sometimes artificial sequences are also included in the middle, e.g., for 2D library preparations of Oxford Nanopore sequencers. 

Although ONT's new basecaller *Guppy* can trim adapters (if told to) it might be a good idea to check and remove additional/overlooked adapters. Multiple tools exist for adapter trimming and filtering for 2nd generation Illumina reads, e.g. [Trimmomatic](http://www.usadellab.org/cms/?page=trimmomatic). In contrast, currently only one tools exists for trimming of Oxford Nanopore adapters: Porechop. <u>Unfortunately, the development of porechop is discontinued and it might not work for new library preparation kits</u>. However, for completeness I still include it in this practical as it may be useful for the older “standard” library preparation kits. Let’s hope that the developer (Ryan Wick) will find someone to continue the development.

Create a directory *porechop* in the directory *~/course_data/practicals/trimming_practical* and use porechop to remove adapters from the (pre-compiled) guppy reads we used in the basecalling tutorial.

```
mkdir ~/course_data/practicals/trimming_practical/porechop

porechop –i ~/course_data/precompiled/guppy_output/all_guppy.fastq \
-o trimming_practical/porechop/porechopped.fastq \--discard_middle
```

The above command will use the default values of porechop to search for adapters in all fastq files of the input directory, trim the reads and write them to file porechopped.fastq in the created porechop directory.  The “--discard_middle” option will remove reads with internal adapters (needed for 2D libraries and downstream us of  nanopolish).

<div style="background-color:#cfedfe;border-radius:5px;border-style:solid;border-color:gray;padding:5px">
  {% octicon question height:32 class:"right left" aria-label:hi %} 
  1. How many adapters did porechop remove?<br><br>
  2. Did it discard any reads? Why not?
</div>

## QC after trimming

Use the tool FastQC to look at your data and compare it to the un-chopped data (see the QC_practical for an introduction to FastQC). 

 1. Open FastQC by typing fastqc on the command line
 2. Use the File->Open menu in FastQC to first open the raw (concatenated) guppy fastq file
 3. When FastQC is done with the first file open the chopped fastq file

<div style="background-color:#cfedfe;border-radius:5px;border-style:solid;border-color:gray;padding:5px">
  {% octicon question height:32 class:"right left" aria-label:hi %} 
  3. Inspect the different graphs. Did the porechop step improve the data? If so, which parts were improved?
<br><br>
  4. Are there still areas of the sequences that you’d like to improve?

</div>

