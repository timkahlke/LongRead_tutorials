# Error Correction using Medaka <img src="figures/LR.png" height="40px">

[{% octicon arrow-left height:32 class:"right left" vertical-align:middle aria-label:hi %}](ECR_MI.md) [{% octicon home height:32 class:"right left" aria-label:hi %}](index.md) [{% octicon arrow-right height:32 class:"right left" aria-label:hi %}](ECR_P.md)

In addition to graph-based methods such as racon several tools use neural networks for error correction. The first polishing tool to use neural networks, [Nanopolish](https://github.com/jts/nanopolish), used the raw signal in the fast5 files of aligned reads to drastically reduce errors in the consensus sequences. Although still considered the best assembly polishing tool recent tests, such as [Ryan Wick's Racon comparison](https://github.com/rrwick/August-2019-consensus-accuracy-update#racon) show that the consensus tool Medaka can achieve comparable results despite only working with mapped fastq reads. Given the significantly shorter run-times of Medaka we will not introduce nanopolish in this practical. **However, I recommend running Nanopolish for real assemblies and compare the outcome to other error correction tools**.

Change into directory *~/course_data/practicals/error_correction_practical/medaka*. You will find two folders in there: flye as well as miniasm. These contain the nanofilt reads as well as the flye assembly and the miniasm consensus sequence produced with 2 rounds of racon (feel free to check why I didn’t provide the flye consensus sequence, i.e., what the effect of racon on this particular flye assembly is).

First change into the miniasm directory and run medaka on the consensus assembly:

```
medaka_consensus –d miniasm.racon_consensus.fasta \
-i filtered.fastq -o medaka_output –m r941_min_high_g303
```

The above command runs medaka on the miniasm-racon consensus using the filtered reads. The –m model specifies the basecalling model used by guppy to produce the reads.
Medaka will write its results to the folder *medaka_output*. Use dnadiff to compare the *consensus.fasta* in the directory with the reference chr_17.fasta in the *precompiled* folder. 

<div style="background-color:#cfedfe;border-radius:5px;border-style:solid;border-color:gray;padding:5px">
  {% octicon question height:32 class:"right left" aria-label:hi %} 
  <ol>
    <li>What did medaka change, what got better or worse?</li>
    <li>How does the Medaka compare to the Minipolish?</li>
  </ol>
</div>
[Answers](APP_ANS.md#1-what-did-medaka-change-what-got-better-or-worse)

Now change into the medaka/flye  directory and polish the flye assembly with medaka:

```
medaka_consensus –d flye_assembly.fasta -i filtered.fastq \
-o medaka_output –m R941_min_high_g303 –b 50
```

<div style="background-color:#fcfce5;border-radius:5px;border-style:solid;border-color:gray;padding:5px">
  {% octicon info height:32 class:"right left" aria-label:hi %} 
  The medaka call for the flye assembly has an additional option: -b 50. This reduces the batchsize and is needed if there is not enough memory. Otherwise you might get an OOM error. If so, set the number even lower than 50.
</div>

As before, compare the medaka result in file *medaka_output/consensus.fasta* with the reference. 

<div style="background-color:#cfedfe;border-radius:5px;border-style:solid;border-color:gray;padding:5px">
  {% octicon question height:32 class:"right left" aria-label:hi %} 
  <ol start="3">
    <li>How did the assembly change?</li>
  </ol>
</div>




