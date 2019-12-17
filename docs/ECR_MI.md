# Error Correction using Minipolish <img src="figures/LR.png" height="40px">

[{% octicon arrow-left height:32 class:"right left" vertical-align:middle aria-label:hi %}](ECR_R.md) [{% octicon home height:32 class:"right left" aria-label:hi %}](index.md) [{% octicon arrow-right height:32 class:"right left" aria-label:hi %}](ECR_ME.md)

Similarly to Racon the tool [Minipolish](https://github.com/rrwick/Minipolish/blob/master/README.md) is written specifically to improve minimap2/miniasm assemblies. In fact, minipolish uses Racon to polish miniasm assemblies but in contrast to Racon it produces output files in miniasm's *GFA* format instead of in fasta. Additonally, Minipolish was written with a focus on cirular replicons, e.g., bacterial genomes, plasmids and plastids, which it tries to cleanly corcularize, if possible.

Additionaly features/advantages:

 * It includes read overage in the output
 * rotates circular contigs/unitigs
 * Reduces/avoids introduction of gaps into the assembly 
 
 Change into the directory *minipolish* in directory *practicals/error_corection_practicals*. Use the provided nanofilt trimmed reads and the miniasm assembly to run minipolish
 
 ```
 minipolish -t 2 nanofilt_result.fastq miniasm.gfa > minipolished_assembly.gfa
 ```
 
The above command will run minipolish with 2 CPUs (-t 2) and re-direct (>) the output into the file *minipolished_assembly.gfa*.
 
<div style="background-color:#fcfce5;border-radius:5px;border-style:solid;border-color:gray;padding:5px">
  {% octicon info height:32 class:"right left" aria-label:hi %} 
  For cases where you don't already have a miniasm assembly Minipolish also provides a script that combines the commands for minimap2, miniasm and minipolish. For more details see the Minipolish home page.
</div>

As mentioned, one of the features of minipolish is that it writes the result into a *GFA* files which can be visualised with tools such as [Bandage](https://rrwick.github.io/Bandage/). However, for the moment we will "undo" this advantage and convert the GFA to fasta to compare Minipolish's performans to that of a pure Racon run.

Use *awk* to convert the GFA to fasta

```
awk ’/^S/{print “>”$2”\n”$3}’ miniasm.gfa > miniasm.fasta
```

Use dnadiff and potentially Assemblytics to compare the minipolish results to the raw assembly and Racon results.

<div style="background-color:#cfedfe;border-radius:5px;border-style:solid;border-color:gray;padding:5px">
  {% octicon question height:32 class:"right left" aria-label:hi %} 
  <ol>
    <li>What changed in the minipolish assembly, what got better, what worse?</li>
  </ol>
</div>
[Answer]()
 




