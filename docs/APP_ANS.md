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


[test](#quality-control-using-fastqc)

The *Per base sequence content* tab shows uneven distributions of bases in the starts of all reads. If the nucleotides at the beginning were randomly distributed (As they should be) then the A and T line should be approximately identical to the G and C lines (as they are in the rest of the plots). Diversion from this can indicate increased error rates as well as adapter or primer sequences that have to be removed.

<img src="figures/A4.png" height="200px">

<div style="background-color:#fcfce5;border-radius:5px;border-style:solid;border-color:gray;padding:5px">
  {% octicon info height:32 class:"right left" aria-label:hi %} 
  The <i>Per base sequence content</i> assumes a relatively large number of reads to average over at each position. For low numbers of reads the distribution of AT and GC at each site will show a different pattern. For example, as indicated by the missing error bars in the last ~20,000 nucleotides only the longest read contributes to the plot which explains the less even sequence content lines.
</div>

[bla](quality-control-using-fastqc)

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

**4. Have a look at the “Basecalled Reads PHRED Quality” and “Read length vs PHRED quality plots”. Is there a link between read length and PHRED score?**

In general, there is no link between read length and read quality. However, in runs with a lot of short reads these the horter reads are sometimes of lower quality than the rest.

**5. Have a look at the “Read Length over Experiment time” plot. Did the read length change over time? What could the reason be?

In the current example the read length increases over the time of the sequencing run. This is especially true for libraries that show a wide spread in the length distirbution of the molecules. One explanation is that the adapter density is higher for lots of short fragments and therefore the chance of a shorter fragment to attach to a pore is higher. Also, shorter molecules may move faster over the chip. Over time, however, the shorter fragments are becoming rarer and thus more long fragments attach to pores and are sequenced.

<img src="figures/A9.png" height="200px">

<div style="background-color:#fcfce5;border-radius:5px;border-style:solid;border-color:gray;padding:5px">
  {% octicon info height:32 class:"right left" aria-label:hi %} 
  This effect will be minimised or removed if a flow cell is re-primed/re-loaded with more library, of course, as it will reload short fragments. Additionally, fragmented and size-selected libraries will not show the same effect as they have a narrow molecule-length distribution.
</div>

**6. Given the number of active pores, yield over time, and channel activity over time, do you think this was a successful sequencing run? Why/why not?**

A look at the *Channel activity over Time* plot already gives a good indication of the run quality: it's crap! The vast majority of channels/pores are in-active (white) throughout the sequncing run. You would hope for a plot that is dark on the X-axis and with higher Y-values (increasing time) doesn't get too light/white. Depending if you chose "Reads" or "Bases" on the left the colour indicates either number fo bases or reads per time interval

<img src="figures/A10.png" height="200px">

Additionally, the "Cummulative" plot area (light blue) in the *Output over experiment time* indicates that 50% of all reads and almost 50% of all bases were produced in the first 5h of the 25h experiment. Although it is normal that yield decreases over time a decrease like this is not a good sign.

<img src="figures/A11.png" height="200px">

**7. Inspect the “output over experiment time” graph. Can you explain the shown curve-pattern? Would you have stopped the run earlier? Think about how the MinION works, especially with regards to adjustment of the applied currents.**

As you might know (or should?) Nanopore sequencing works as follows:
 * a membrane separates two chambers (above and below the membrane) with different electronic potential.
 * when sequencing charged particles flow from the upper chamber through the pores into the lower chamber
 * over time the flow of particles from the upper to the lower part of the membrane equalises the charge on both sides, hence over time a higher current has to be applied to "suck" the charged particles from one side of the membrane to the other
 * Additionally, over the course of a sequencing run the membrane pores may "die" and become inactive.
 
That means that the MinKNOW software does two things:
 1. Increase the negative voltage applied to the flowcell in 5mV steps every 2 hours (starting from -180mV)
 2. Switching to a new group of pores for sequencing every 8h (this depends on software version and demuxing settings)
 
Both events can increase the yield drastically (especially for sub-optimal libraries) although a change of the mux-group or *re-muxing* will have the bigger effect.

<img src="figures/A12.png" height="200px">

Additionally, this flow cell included 3 different runs on different days with 

As already mentioned in the question before the stats show that this library was not great. Options would have been
 1. Immediately stop the run, wash the flowcell and re-do DNA extraction to not waste your flow cell (Best solution)
 2. Re-mux the pores every 2 hours to increase yield and stop as soon as most pores are gone (waste of flow cell but at least increases yield as much as possible)
 3. Stop after 5h or at latest 10h when >70% of the data are produced. Running the flow cell another 10h without producing much data was definitely a waste of flow cell
 
 **8. If you want to you can generate the PycoQC plots for run_3/sequencing_summary.txt and compare it to run_1. What are the differences?**
 
 One of the main differences is that run_3 includes reads from not just one but 18 runs (see RunIDs in the summary table) and the cummulative sequencing time is >60h.
 
 <img src="figures/A13.png" height="200px">
 
 Additionally, this flow cell included 3 different libraries run on different days and for each library the run was stopped and re-started several times to force a re-mux of the pores. The *Read length over experiment time* clearly shows the start of each new library
 
 <img src="figures/A14.png" height="200px">
 
 Additionally, the yield over time plots shows several peaks in the first 10h of sequencing whenever the run was re-started.
 
 <img src="figures/A15.png" height="200px">
 
 which was also correlated with a better pore activity
 
 <img src="figures/A16.png" height="200px">

However, despite increased yield and pore activity in run_3 it is still far from being a nice run!



 
 
