# Error correction <img src="figures/LR.png" height="40px">

[{% octicon arrow-left height:32 class:"right left" vertical-align:middle aria-label:hi %}](ASS_S.md) [{% octicon home height:32 class:"right left" aria-label:hi %}](index.md) [{% octicon arrow-right height:32 class:"right left" aria-label:hi %}](ECR_R.md)

----
 * [Consensus sequence using Racon](EC_R.md)
 * [Consensus sequence using minipolish](EC_MI.md)
 * [Consensus sequence using Medaka](EC_ME.md)
 * [Error correction using Pilon](EC_P.md)
 
 ----
 
Despite recent advances one of the main problems with Long-Read technologies is the increased error rate, especially in Oxford Nanopore data. One way to address this is the building of a *consensus sequence*. To build a consensus sequence all reads are aligned to the assembly and for each position in the assembly the nucleotide with the highest number of reads supporting it is chosen as the *consensus* nucleotide. 

Additionally, some tools try to further improve the consensus sequence, e.g., through resolution of insertion-deletion errors (INDELS) or by taking into account the raw signal instead of just the basecalled reads.

Often higher accuracy can be achieved by repeating the consensus-building several times and/or combining several consensus and error correction tools.

<div style="background-color:#fcfce5;border-radius:5px;border-style:solid;border-color:gray;padding:5px">
  {% octicon info height:32 class:"right left" aria-label:hi %} 
  Although the error rate of Long-Read sequences can be reduced significantly (<1%) using error correction tools they can also introduce new errors by removing real variants, e.g. low frequency alleles in communities or haploid genomes.
</div>




