# Error Correction using Pilon <img src="figures/LR.png" height="40px">

[{% octicon arrow-left height:32 class:"right left" vertical-align:middle aria-label:hi %}](ECR_ME.md) [{% octicon home height:32 class:"right left" aria-label:hi %}](index.md) [{% octicon arrow-right height:32 class:"right left" aria-label:hi %}](VC.md)

Another popular error correction tool is Pilon. As medaka, Pilon can be run after Racon to further improve assembly quality by correcting Insertion/Deletion (Indel) errors as well as Single Nucleotide Polymorphisms (SNPs). 

To correct errors Pilon uses two common bioinformatic packages/tools:
 * BWA (short for Burrows-Wheeler Aligner) for read mapping
 * Samtools, for mapping file convertion and sorting


The Pilon workflow consists of 4 steps
 1. Map your reads (PacBio or Oxford Nanopore) back to your (consensus) assembly using BWA. This will create a mapping file in SAM format
 2. Convert your SAM file to the binary BAM format using samtools
 3. Sort and index the BAM file for faster access using samtools
 4. Run Pilon using the genome assembly and the sorted and indexed bam file

First, change into the pilon directory in your error_correction_practical folder. For convenience the miniasm assembly as well as the guppy-basecalled reads are already in that directory.

To map your reads to the assembly using BWA you will first have to index the assembly file (for faster access for BWA) and then run bwa mem for read mapping

```
# index the genome
Bwa index miniasm.racon_consensus.fasta

# map reads
bwa mem –t 2 miniasm.racon_consensus.fasta –x ont2d \
all_guppy.fastq > bwa_mapping.sam
```

The above statement will run bwa-mem with 2 processors (-t 2) using oxford nanopore reads (-x ont2d) and redirect the output into the output file bwa_mapping.sam

<div style="background-color:#fcfce5;border-radius:5px;border-style:solid;border-color:gray;padding:5px">
  {% octicon info height:32 class:"right left" aria-label:hi %} 
  Don’t pay attention to the “ont2D”. Although we specific 2D reads as input bwa-mem also runs on 1D reads. For PacBio reads use the –x pacbio option
</div>

After mapping the reads we have to do some true bioinformatics: file conversion!
First, convert the sam file to bam using “samtools view” (-bS means the input is sam and output is bam), then sort it with “samtools sort” and finally index the bam file using “samtools index”

```
samtools view -Sb bwa_mapping.sam > bwa_mapping.bam
samtools sort –o bwa_mapping.sorted.bam bwa_mapping.bam
samtools index bwa_mapping.sorted.bam
```

Now run Pilon using the assembly and sorted bam file

```
pilon --genome miniasm.consensus_sequence.fasta \
--bam bwa_mapping.sorted.bam --threads 2
```

The above command will run pilon with 2 threads and use the mapped read information for polishing of the miniasm assembly.

<div style="background-color:#fcfce5;border-radius:5px;border-style:solid;border-color:gray;padding:5px">
  {% octicon info height:32 class:"right left" aria-label:hi %} 
  Unfortunately, Pilon requires more compute resources than the provided VM offers and it will therefore die with an error mentioning “Java Heap Space”. The precompiled pilon results can be found in <i>~/course/data_precompiled/pilon_output</i>. Simply copy that directory into the <i>error_correction_practical/pilon</i> folder using “cp –R”.
</div>

In the pilon directory you will find the corrected assembly in file pilon.fasta. As before, use dnadiff and check the assembly report. 

<div style="background-color:#cfedfe;border-radius:5px;border-style:solid;border-color:gray;padding:5px">
  {% octicon question height:32 class:"right left" aria-label:hi %} 
  <ol>
    <il>How did the assembly change? Are there other improvements than purely sequence identity?</il>
    <il>What pipeline(s) would you try first for your own project?</il>
  </ol>
 </div>


