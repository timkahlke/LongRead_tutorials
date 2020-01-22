# Sequence File Formats

[{% octicon arrow-left height:32 class:"right left" vertical-align:middle aria-label:hi %}](APP_DATA.md) [{% octicon home height:32 class:"right left" aria-label:hi %}](index.md) [{% octicon arrow-right height:32 class:"right left" aria-label:hi %}](APP_MET.md)

----

## Fast5

The FAST5 format is the standard sequencing output for Oxford Nanopore sequencers such as the MinION. It is based on the *hierarchical data format* [HDF5](https://en.wikipedia.org/wiki/Hierarchical_Data_Format) format which enables storage of large and comples data. In contrast to fasta and fastq files a FAST5 file is binary and can not be opened with a normal text editor. 

Data stored in nanopore FAST5 files can contain the sequence of a read in fastq format (after basecalling), the raw signal of the pore as well as several log files and other information.

----

## FastA

The fasta format is one of the simplest and most common file formats to store sequence data. A fasta file can contain one or many nucleotide or amino acid sequences.
The first line of a sequence in a fasta file starts with a “>” followed by a a series of sequence identifiers or attributes. Subsequent lines contain the nucleotide or amino acid sequence.

<div style="background-color:#fcfce5;border-radius:5px;border-style:solid;border-color:gray;padding:5px">
  {% octicon info height:32 class:"right left" aria-label:hi %} 
  Some fastA files contain the sequence in one long line. Other files only show 60 or 80 nucleotides per line and thus safe the sequence in multiple lines.
</div>

```
>NC_012064.1 Thalassiosira pseudonana CCMP1335 
TCCAAGAGTCGAAgtagtttcttcttcttatctctTTCAATCAAATAGTGATCTTGGTATGCCAGAAGTTGTGGTTTGTT
TCGTTTATACTCCACAAAACGTCTGTCTAGCTGTGTCATTTCTGATGCAAGAAGGAAGCTATCTGGGCCATGAAGAATTG
TGTTTCGCATCTTCCATTGTCCTTCAAAAATTTTCCATGTTTCCCCGATTAGCACCGTGGAGAGTTCGAAGGGgtctctt
ttcttctccattgtaccatcatcatatcgTCTGGGTGGTATCCACGTAGATTGTAGTGTTTATGCCCATTCCACATGATG
GAATCCCCGGAGAAGTGCATCACTACCGAGAGACTCTTGTCGCTCGATTGCTCGCAACGTATGTGAGCAGTGTAAAGCAT
ATGGATTCCGAGGGAGATGAACAAGTTTGCAAATCGCGTCA
```

Typical file extensions for fastA files are
 * .fnt 
 * .fna (nucleotide)  
 * .faa (amino acid)
 * .fasta 
 * .fa 
 * .fas
 
----

## FastQ

The fastq format is the de-facto standard of 2nd generation sequencing technology such as Illumina sequencers. It is similar to the fasta format but in addition to the sequence itself a fastq file also stores quality scores of the sequence. A fastq file stores every sequence in exactly 4 lines:
 1. The name/ID line starting with “@” followed by a sequence identifier
 2. The sequence itself
 3. A line starting with “+” (optionally followed by additional information, e.g., the read names again) which is an artifact that can be ignored nowadays
 4. The quality line with one character per sequence residue encoding the probability of a possible sequencing error ([Phred score](https://github.com/timkahlke/LongRead_tutorials/blob/master/docs/APP_MET.md#phred-score))
 
```
@4e131bcf-f814-485a-b02f-3d133030b06e 
TTGTTATGCCGCTTCGTTCAGTTACGTATTGCTCGACGGTTCCACTTTGAACGTTTGCGTTCAAATACTATAACTAGTTTTGCTCTCGTTTTAATCTTCCCCGTCTCTCCCAAA
+
??????+(+*(%%#()&.67:58D8.10;01.4.8.)(*'(.-,2,?<79C97:?2()((,%()**())'&&IIICCCIIII**(%%#()&.67:58D8.10;01.4.8II?%?
```

----



