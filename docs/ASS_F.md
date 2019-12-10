# Genome assembly using Flye <img src="figures/LR.png" height="40px">

[{% octicon arrow-left height:32 class:"right left" vertical-align:middle aria-label:hi %}](ASS_M.md) [{% octicon home height:32 class:"right left" aria-label:hi %}](index.md) [{% octicon arrow-right height:32 class:"right left" aria-label:hi %}](ASS_S.md)

Another assembler that can be used for long-reads such as PacBio and Oxford Nanopore is Flye. In contrast to the minimap and miniasm pipeline Flye also produces a polished consensus sequence for the assembly which significantly reduces the error rate (more about consensus sequences and polishing in the next practicals).

Change into the *Flye*  directory in the *assembler_practical* folder and run flye on the raw basecalled reads

```
flye --nano-raw \
~/course_data/precompiled/all_guppy.fastq \
--genome-size 1m --out-dir ./flye_output
```
As you can see, flye requires the input reads (--nano-raw) as well as an output directory and the (expected) size of the final assembly which, in this case is set to 1 megabase (1,000,000 bases). The output of flye are several files including the assembly in fasta format.

<div style="background-color:#fcfce5;border-radius:5px;border-style:solid;border-color:gray;padding:5px">
  {% octicon info height:32 class:"right left" aria-label:hi %} 
  Flye takes significantly more time and resources to run. On an average laptop this assembly will take approximately 10 minutes. If you don’t want to wait just stop flye (Ctrl-c) and copy the precompiled result files from directory <i>~/course_data/precompiled/flye_output</i>  into this directory.
</div>

When Flye is finished use *assembly-stats*  to get a first overview over the finished assembly.

<div style="background-color:#cfedfe;border-radius:5px;border-style:solid;border-color:gray;padding:5px">
  {% octicon question height:32 class:"right left" aria-label:hi %} 
  <ol>
    <li>Does the assembly differ from the miniasm assembly, e.g., wrt total length, number of contigs and length of the contigs?</li>
  </ol>
 </div>
 
Now align the flye assembly to the reference chromosome using dnadiff

```
dnadiff –p flye_dnadiff ~/course_data/precompiled/chr17.fasta \
flye_output/assembly.fasta
```

Open the flye_dnadiff.report file (e.g. double-click on the file). 

<div style="background-color:#cfedfe;border-radius:5px;border-style:solid;border-color:gray;padding:5px">
  {% octicon question height:32 class:"right left" aria-label:hi %} 
  <ol start="2">
    <li>How many contigs aligned with the reference? What is the error rate?</li>
  </ol>
</div>

Now upload the flye_ddnadiff.delta to Assemblytics and inspect the dot plots.

<div style="background-color:#cfedfe;border-radius:5px;border-style:solid;border-color:gray;padding:5px">
  {% octicon question height:32 class:"right left" aria-label:hi %} 
  <ol start="3">
    <li>How many contigs align well with the reference?</li>
    <li>Does the alignment differ from the reference, e.g., does the Flye assembly extend the start or stop of the reference? Are there inversions? </li>
  </ol>
</div>
<br>

<div style="background-color:#fcfce5;border-radius:5px;border-style:solid;border-color:gray;padding:5px">
  {% octicon info height:32 class:"right left" aria-label:hi %} 
You can zoom in on parts of the dot plot by 
<ul>
  <li>clicking the name of a contig: this will only show the dot plot for this contig with the reference</li>
  <li>double-clicking on a specific region in the dot plot To zoom out simply  right-click (click with 2 fingers on a touch pad)</li>
  </ul>
</div>

