# Read trimming and filtering using NanoFilt <img src="figures/ONT.png" height="40px">

[{% octicon arrow-left height:32 class:"right left" vertical-align:middle aria-label:hi %}](FTR_P.md) [{% octicon home height:32 class:"right left" aria-label:hi %}](index.md) [{% octicon arrow-right height:32 class:"right left" aria-label:hi %}](ASS.md)

Trimming parts of a sequence can improve your data. Additionally, it can be beneficial to remove short read especially for whole genome sequencing projects. As usual there are many different tools to approach read trimming/fitlering. As mentioned, a common tool for  Illumina data is Trimmomatic. In this tutorial we will use the open-source tool NanoFilt to further trim and filter our MinION reads.

Create directory for your NanoFilt output called *nanofilt* in the *trimming_practical* folder, change into it and
 * remove all sequences shorter than 500 nucleotides (option -l)
 * trim the first 10 nucleotides off all reads (option --headcrop)

```
mkdir ~/course_data/practicals/trimming_practical/nanofilt

cd ~/course_data/practicals/trimming_practical/nanofilt

NanoFilt –l 500 --headcrop 10 < ../porechop/porechopped.fastq \
 > ./nanofilt_trimmed.fastq
```
<br>
<div style="background-color:#fcfce5;border-radius:5px;border-style:solid;border-color:gray;padding:5px">
  {% octicon info height:32 class:"right left" aria-label:hi %} 
  The “\” at the end of each line is only for convenience to write a long command into several lines. It tells the command-line that all lines still belong together although the are separated by “enter” keys. However, if you type all of the command, i.e., paths etc, in one line don’t’ use the backslash at the end of the lines.
</div>

NanoFilt does not provide options for input or output files. Therefore we will use the two redirect operators “>” and “<“ to 
 * redirect the file porechopped.fastq into NanoFilt (operator <) 
 * then redirect the output of NanoFilt into the file nanofilt_trimmed.fastq (>).

<div style="background-color:#cfedfe;border-radius:5px;border-style:solid;border-color:gray;padding:5px">
  {% octicon question height:32 class:"right left" aria-label:hi %} 
  Use FastQC to check the result file and compare it to the porechopped file and the original guppy fastq. Did NanoFIlt improve the data?
</div>

<br>
<div style="background-color:#fcfce5;border-radius:5px;border-style:solid;border-color:gray;padding:5px">
  {% octicon info height:32 class:"right left" aria-label:hi %} 
  Options heacrop and –l are just a few of the possible filter options of NanoFilt. It also provides options for filtering based on quality scores or maximum read length. For a complete list of all options type NanoFilt -h
</div>


