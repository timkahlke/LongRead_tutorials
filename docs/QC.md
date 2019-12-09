[{% octicon arrow-left height:32 class:"right left" vertical-align:middle aria-label:hi %}](BS_G.md) [{% octicon home height:32 class:"right left" aria-label:hi %}](index.md) [{% octicon arrow-right height:32 class:"right left" aria-label:hi %}](QC_F.md)

# Quality Control of Raw Reads

----

 * [Quality Control using FastQC](QC_F.md) <img src="figures/SL.png" height="30px">
 * [Quality Control using PycoQC](QC_P.md) <img src="figures/ONT.png" height="30px">
 * [Quality Control using MinION_QC](QC_M.md) <img src="figures/ONT.png" height="30px">

----

The initial every sequencing project is the quality control step to assess the quality of your data. This will give you some stats of your sequencing data, such as length and quality score distributions, as well as highlight potential problems with your input DNA/RNA, the sequencing run or the data itself.

An increasing number of tools is available for sequence data QC, with different strength and applicaton cases. In this tutorial we will introduce 3 different tools: [FastqQC](https://www.bioinformatics.babraham.ac.uk/projects/fastqc/), [PycoQC](https://github.com/a-slide/pycoQC) and [MinIONQC](https://github.com/roblanf/minion_qc).

**Data directory:** *~/course_data/practicals/qc_practical*

