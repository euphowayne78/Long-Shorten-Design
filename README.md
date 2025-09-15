# Long-Shorten-Design

The following block takes in DNA/RNA sequence in fasta format. Multiple sequences input are allowed.  
  
**Used case**  
1) Ensure that you are in the work directory.  
2) Edit parameters/filenames to readin and output.  
3) You can define your own prefix (left adapter sequence) and suffix (left adapter sequence), otherwise, the defaults will be used.   

**Format of input fasta file**<br>    
\>Name_of_input_sequence [5' UTR length, ORF length, 3'UTR length]  
Input_Sequence

**Functionality**  
1) Design sensor sequences originating from all possible CCA sites in input mRNA except for sites with insufficient flanks (76 nt on either side), which are excluded.  
2) Left and right adapter sequences can be omitted or replaced by alternative sequences with the constrains that the final design sequence should maintain its translation reading frame.   
3) The design sequence will contain a total of 4 MS2 loops, each with a different sequence that are regularly spaced creating 5 aneealing sites.  
4) Final design follows the following sequence structure: 21 nt AS1--MS2 Loop 1--21 nt AS2--MS2 Loop 2--24 nt AS3--TAG--24 nt AS3--MS2 Loop 3--21 nt AS4--MS2 Loop 4--21 nt AS5. Total length = 219 bp; 279 bp with adapters.    
5) Output CSV and fasta file. CSV file contains label, full_seq, aa_seq and region_class.   
6) Design sequences with BspQI/SapI sites are excluded.   
7) Region class is defined as either 5U, 5U-ORF, ORF, ORF-3U or 3U based on where the design sequence span along the input mRNA.
8) Label: f"{rna_name}_{idx}", where idx refer to position of CCA site along input mRNA.  