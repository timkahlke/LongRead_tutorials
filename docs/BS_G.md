[{% octicon arrow-left height:32 class:"right left" vertical-align:middle aria-label:hi %}](SU_D.md) [{% octicon home height:32 class:"right left" aria-label:hi %}](index.md) [{% octicon arrow-right height:32 class:"right left" aria-label:hi %}](QC.md)

# Basecalling using Guppy <img src="figures/ONT.png" height="40px">

Base calling is the process of translating the electronic raw signal of the sequencer into bases, i.e., ATCG. As for most bioinformatic tasks there are many different tools to solve this problem. Here, we will only focus on the current state-of-the-art basecaller Guppy, which is the current “official” ONT basecaller. Although basecalling can be performed “live”, i.e., in real time while sequencing, it is often useful to separate the sequencing from basecalling. One advantage of “offline” basecalling is that the basecaller can use significant amounts of compute and read/write resources which may slow the sequencing process and, in rare cases, even lead to loss of sequencing data. 

Guppy is a neural network based basecaller that in additoin to basecalling also performs filtering of low quality reads, clipping of Oxford Nanopore adapters and estimation of methylation probabilities per base. 

<div style="background-color:#fcfce5;border-radius:5px;border-style:solid;border-color:gray;padding:5px">
  {% octicon info height:32 class:"right left" aria-label:hi %} 
Guppy uses significant amounts of compute resources/time, especially if run on a processor (CPU). Thus, basecalling especially for larger datasets often requires compute clusters (as provided by the NCI) or specific workstation computers. ONT also released a Guppy version that utilises graphics card chips (GPUs) instead of the “usual” computer processor (CPUs). The GPU version of guppy is significantly faster than the CPU version. However, the installation is restricted to specific computers/graphics cards and can unfortunately not be virtualised, e.g. with VirtualBox. 
</div>

As input, Guppy, as well as the now deprecated Albacore and all other basecallers, use files in *fast5* format as input.

First, change into the directory */course_data/practicals/basecalling_practical*. It contains a sub-directory called fast5 with fast5 files of a recent MinION run.  

Apart from the input fast5 files guppy requires a configuration file that sets the basecalling parameters depending on which flowcell and library preparation kit was used to produce the data. To list all supported flowcell and library kits type

```
guppy_basecaller --print_workflows
```

The provided data was prepared using the SQK-LSK108 library preparation kit that was sequenced on a MIN106 flowcell. 

<div style="background-color:#cfedfe;border-radius:5px;border-style:solid;border-color:gray;padding:5px">
  {% octicon question height:32 class:"right left" aria-label:hi %} 
What’s the name of the configuration file guppy needs to basecall the data?
</div>

To start the basecalling you can either specify the flowcell and the library kit using the parameters *-f FLO-MIN106* and *-k SQK-LSK108* or use option *–c* and the name of the configuration file. For convenience we’ll use the option -c. 

```
guppy_basecaller –i ./fast5 –s ./guppy_out –c dna_r9.4.1_450bps_hac.cfg --num_callers 2 --cpu_threads_per_caller 1
```

The command above will call guppy on the input fast5 directory option (-i) and write the output to the directory given with option -s. 

**The above command will run for several hours!** …. therefore please stop Guppy now by pressing Ctrl-c (hold the control key and then press ‘c’) and copy the folder  *guppy_output* from directory *course_data/precompiled* into the folder *basecalling_practical*.

<div style="background-color:#fcfce5;border-radius:5px;border-style:solid;border-color:gray;padding:5px">
  {% octicon info height:32 class:"right left" aria-label:hi %} 
Note One of the most common problems/mistakes when copying and moving files arise from incorrect paths. Keep in mind
 * what directory you are in (can check with command pwd)
 * where the directory is that you want to copy
 * what the correct path for the destination is
</div>

To copy a directory use the following command

```
cp –R SOURCE_TO_COPY DESTINATION
```

where
 * SOURCE_TO_COPY = the directory you want to copy
 * DESTINATION = the folder/directory you want to copy it to

Change into the directory *guppy_output* and have a look what is in there. As you can see there are several *.fastq* files with the basecalled reads, one or more *.log* files that contains log messages from guppy as well as a *sequencing_summary.txt* file.

It is often useful to concatenate all the different fastq files into one big file for downstream analyses. From within the *guppy_output* directory use the cat command to do this:


```
cat *.fastq > all_guppy.fastq
```

This will create one fastq file called *all_guppy.fastq* with all your basecalled reads in it.

