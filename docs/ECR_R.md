# Error Correction using Racon <img src="figures/LR.png" height="40px">

[{% octicon arrow-left height:32 class:"right left" vertical-align:middle aria-label:hi %}](ECR.md) [{% octicon home height:32 class:"right left" aria-label:hi %}](index.md) [{% octicon arrow-right height:32 class:"right left" aria-label:hi %}](ECR_MI.md)

The software package Racon was developed to complement the minimap2/miniasm pipeline but can be used for any long-read assembly. It provides a fasta consensus algorithm that uses either 2nd generation short reads or raw noisy long-reads to correct draft assemblies.

Change into the miniasm directory in *practicals/error_correction_practical/racon*. For convenience the trimmed nanofilt reads as well as the miniasm assembly were copied into this directory. Use minimap2 to map the trimmed nanofilt reads back to the miniasm assembly and then use the filtered reads and the mapping to build the consensus assembly.

```
minimap2 ./miniasm_unitigs.fasta nanofilt_result.fastq \
 > minimap.racon.paf

racon nanofilt_result.fastq \
minimap.racon.paf miniasm_unitigs.fasta \ 
> ./miniasm.racon.consensus.fasta
```

Analyse the assembly quality by comparing the consensus assembly to the published sequence using *dnadiff* and *Assemblytics* (for details see the [Assembly using minimap/miniasm](ASS_M.md) tutorial).

```
dnadiff ~/course_data/precompiled/chr17.fasta -p racon_first \
miniasm.racon.consensus.fasta
```

<div style="background-color:#cfedfe;border-radius:5px;border-style:solid;border-color:gray;padding:5px">
  {% octicon question height:32 class:"right left" aria-label:hi %} 
  <ol>
    <li>Did Racon improve the assembly, if so, how?</li>
  </ol>
</div>
[Answer](APP_ANS.md#1-did-racon-improve-the-assembly-if-so-how)

Create a directory *round_2* in the *racon/miniasm* directory and change into it. Now repeat the process but this time use the consensus assembly you just created with racon.

```
mkdir round_2

cd round_2

minimap2 ../miniasm.racon.consensus.fasta \
../nanofilt_result.fastq > round2.paf

racon ../nanofilt_result.fastq round2.paf \
../miniasm.racon.consensus.fasta \
> miniasm.racon.consensus.round2.fasta 
```

Analyse the second consensus assembly as before.


<div style="background-color:#cfedfe;border-radius:5px;border-style:solid;border-color:gray;padding:5px">
  {% octicon question height:32 class:"right left" aria-label:hi %} 
  <ol start="2">
    <li>What changed / got better / got worse?</li>
  </ol>
</div>
[Answers](APP_ANS.md#2-what-changed-got-better--got-worse)

<br>

<div style="background-color:#fcfce5;border-radius:5px;border-style:solid;border-color:gray;padding:5px">
  {% octicon info height:32 class:"right left" aria-label:hi %} 
  Although multiple rounds of racon can increase the quality of an assembly there are indications that it also fragments the assembly and may decrease quality by removing structural variants and SNPs. Published assembly workflows differ in the number of rounds but rarely apply more than 4 rounds of racon.
</div>



