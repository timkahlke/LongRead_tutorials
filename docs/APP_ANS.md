# Tutorial Answers

## Basecalling 

### Basecalling using Guppy

**1. What’s the name of the configuration file guppy needs to basecall the tutorial data?**

Show the list of all available configuration kits using

```
guppy_basecaller --print_workflows
```

<img src="figures/A1.png" height="300px">

As mentioned the tutorial data was created using a *FLO-MIN106* flowcell and a *SQK-LSK108* library kit. Scrolling though the list will identify the config file *dna_r9.4.1_450bps_hac* as the appropriate basecalling model for tis flowcell+library-kit combination.

<div style="background-color:#fcfce5;border-radius:5px;border-style:solid;border-color:gray;padding:5px">
  {% octicon info height:32 class:"right left" aria-label:hi %} 
  The <i>_hac</i> in the model means it is the <i>High Accuracy</i> model. Additionally, you will always have to add the file extension <i>cfg</i> when calling guppy.
</div>

----

### Quality Control using FastQC

**1. How many reads are in the sample?**

4725, as shown in the FastQC Window in the *Basic Statistics* tab.

<img src="figures/A2.png" height="200px">

**2. What is the mean quality?**

If you have a look at the *Per base sequence quality* tab the average q-score seems to be ~15, i.e., ~3% error probability, for most of the sequence parts.

<img src="figures/A3.png" height="200px">

**3. Overall, how good is your data?**

Overall, I'd consider the data ok from what I can see:
 * longest read ~100k (See Basic Statistics window) 
 * Average Q-score of 15 which is good
 
However, it would be good to also see a read length distribution and Qscore distribution before making that call.

**4. Are there areas that should be trimmed?**

The *Per base sequence content* tab shows uneven distributions of bases in the starts of all reads. If the nucleotides at the beginning were randomly distributed (As they should be) then the A and T line should be approximately identical to the G and C lines (as they are in the rest of the plots). Diversion from this can indicate increased error rates as well as adapter or primer sequences that have to be removed.

<img src="figures/A4.png" height="200px">

<div style="background-color:#fcfce5;border-radius:5px;border-style:solid;border-color:gray;padding:5px">
  {% octicon info height:32 class:"right left" aria-label:hi %} 
  The <i>Per base sequence content</i> assumes a relatively large number of reads to average over at each position. For low numbers of reads the distribution of AT and GC at each site will show a different pattern. For example, as indicated by the missing error bars in the last ~20,000 nucleotides only the longest read contributes to the plot which explains the less even sequence content lines.
</div>


**5. Are there any sequence parts that should be removed as part fo the Quality Control step?**

As indicated by the *Adapter Content* tab some/all of the reads still contain PCR primers and sequencing adapters. These have to be trimmed/clipped as part of the QC process using tools such as Trimmomatic or Cutadapt.

----

### Quality Control using PycoQC

**1. How many reads do you have in total?

~270k reads in total (see the *Basecall summary* of PucoQC's output page

<img src="figures/A5.png" height="200px">

**2. What are the median, minimum and maximum read lengths, what is the N50?**

The median read length as well as the N50 can be found for all as well as for all *passed* reads, i.e., reads that passed MinKNOWs quality settings, can be found in the basecall summary of PycoQC.

For the minimum and maximum read lengths hover look at the *Basecalled read lengths* plot. If you hover over the start and the end of the plotted length distribution you will see the length followed by the number of reads.
The minimum  read length for the passed reads is about 200bp, the maximum length ~130,000bp.

<img src="figures/A6.png" height="200px">

**3. What do the mean quality and the quality distribution of the run look like? Remember, Q10 = 10% error rate**

The majority of the reads has a Qscore of <10, i.e., an error rate of >10%. Given that the tutorial data was initially basecalled with Oxford Nanopore's old basecaller Albacore these results are normal. However, as seen in the previous tutorial, the average QScores of data basecalled with Guppy is usually much higher.

**4. 
