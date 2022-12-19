# Radial-TFs

Requirements: 
- narrowPeak bed files from nf-core ChIP-Seq Pipeline for transcription factors in myeloid and lymphoid cell lines
- GPSeq data for myeloid and/or lymphoid cells

Peaks can be analyzed in three ways: 
- all peaks: including any peak identified in any ChIP-Seq replicate for that TF
- intersect peaks: including peaks only identified in all reps of the experiment
- top interscept peaks: filtering for the top 500 peaks in each replicate, then intersecting them

To get intersect peaks: 

`bedtools intersect -a {REP_1_NAME}.narrowPeak -b {REP_2_NAME}.narrowPeak > total_intersect.bed`

To get top intersect peaks: 

`sort -t$'\t' -k5 -nr {REP_NAME}.narrowPeak | head -500 > {REP_NAME}_score_sorted_top.narrowPeak 

bedtools intersect -a {REP_1_NAME}_peaks_score_sorted_top.narrowPeak -b {REP_1_NAME}_peaks_score_sorted_top.narrowPeak > top_intersect_score.bed`


All these files should be organized into folders in the following way: 

`Lymphoid/TranscriptionFactor/CellType` or `Myeloid/TranscriptionFactor/CellType`

