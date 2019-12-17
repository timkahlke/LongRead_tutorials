# Genome assembly using Shasta <img src="figures/LR.png" height="40px">

[{% octicon arrow-left height:32 class:"right left" vertical-align:middle aria-label:hi %}](ASS_F.md) [{% octicon home height:32 class:"right left" aria-label:hi %}](index.md) [{% octicon arrow-right height:32 class:"right left" aria-label:hi %}](EC.md)

The third assembler we introduce is Shasta, a long-read assembler with very fast run-time that also produces contigs (in contrast to miniasms unitigs).

Change into directory *assembler_practical/shasta*. In contrast to the other assemblers Shasta expects fasta files as input, not fastq. Thus, before you can run Shasta you will have to convert the guppy fastq to a fasta file using the Shasta command FastqToFastq.py and then run shasta on the output fasta file.

```
FastqToFasta.py \
~/course_data/practicals/basecalling_practical/all_guppy.fastq \
all_guppy.fasta

shasta --input all_guppy.fasta
```

This will create a directory *ShastaRun* as output containing, among others, the assembly in fasta format (Assembly.fasta). 

As before, assess the assembly using assembly-stats, dnadiff and Assemblytics.

<div style="background-color:#cfedfe;border-radius:5px;border-style:solid;border-color:gray;padding:5px">
  {% octicon question height:32 class:"right left" aria-label:hi %} 
  <ol>
    <li>Which of the assemblies/assemblers would you use for your project?</li>
    <li>What are the strengths/weaknesses of the different assemblers?</li>
  </ol>
</div>
[Answers](APP_ANS.md#genome-assembly-using-shasta)


