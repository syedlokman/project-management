---
template: blog-post
title: BED Tools II
slug: bed_2
date: 2023-12-24 05:19
description: BED Tools II
---
"In this section we will illustrate
some of the other functionality that is implemented in the BEDtools package. So we're going to be looking first at
how we can perform some basic five format conversion and the very useful ones to convert from
bamtobed format and the other way around. So just like we've done before,
let's see bedtools. Let's just try them too. Bed. [SOUND]
Okay. And we can read the usage,
we can read information about the command line options and the basic usage,
bedtools bamtobed, that's the name of the sub command and number of
options and then the input bam file. And a few interesting and informative, and very useful command line options
that I've found, are here. Split. So split or spliced ban alignments
are reported as separate ban entries. They are split at the NCR operations which
correspond to influence in then Is priced alignments. And there's also this cigar option which
will add the cigar stream to the bed entry as the seventh column. So let's give it a try and we'll try this
with our alignment file in A1 to A1-4. So first bamtobed. Let's type the input in 814.bam,
and let's modulate this. So, as command line parameters,
let's use cigar. And we're not going to use the option
[INAUDIBLE], let's see what we obtain. So as you can tell, there's one line for
every alignment in the ban file, chromosome and it's bed format,
chromosome start and end position. Then we have the identifier, ID photo
read, plus strain, not sure what this is. And then we have the cigar. And for the purposes of illustrating
how the split reads are being manipulated here,
I like to pick one of these. Let's find one that's
fairly easy to remember. Let's mark down this alignment here. 3, 7, 0, 4, 0, 0, aqnd this large alignment. And you might notice
the span of the alignment, the alignment spans somewhere
around 170,000 bases. So that's a very long tool interval. I'm going to copy this And we'll remember that it starts at
chromosome one, position 14,806 and so on. So, that is running bedtools, BAM to BED. And specifying the cigar and to convert
from a BAM format to a BED format. Now let's use the option of split. Okay? And you might not be able to see here. So the cigar option is not valid here. It's not effective but
I'm going to do a grip on err188, and I think I actually have that, yes. And let's see what we get. So you might remember that there were two. Okay, this probably now that
those all chromosome one. It has multiple locations on the genome. So, as you can tell here it
is split in the number, so this was the first alignment,
the short one and then the long alignment is
actually shown as two blocks here. A block is 24 bases long, actually 23, and another block is about
170 thousand bases away. So it corresponds to the two pieces on the two X zones,
separated by the interrupt. So ban to bed with the split
option will split the alignments, spliced alignments, into a number of
blocks that correspond to the number of X zones that are contained in that
aren't covered by that align. And it's probably the more
correct way to look at it. Now we can also perform
the operation in reverse. So we can start with a bed file and
convert it into a bend file. So let's see the format bedtools, the command line usage for bed to bam. And the usage is fairly simple bedtools,
bed to bam. A number of options dash
I the input of which can be in any of the three
formats specified here. Bed GFF and VCF, and then a genome. Now the genome file has
a very specific format, it's not really a genome
file it's a header file. And I'm going to
demonstrate by showing you basically it contains the identifier for
the chromosome. Followed by the length of the chromosome
and that's all that it needs. So now let's illustrate by
transform by converting from one of those three formats and
location formats. Lets write the input first,
fc.gtf, let's say. Genome ht38c, okay. And notice that one of
them options here is that. The bed12. The BAM CIGAR string
will reflect the block. So it's related to the split option that we saw in the previous subcommand. So now let's run bedtools bedtobam
without using the bed 12. Let's see what we get. Okay, and indeed we should have
saved that into refseq.bam. And now we can use samtools view
to look at the refseq.bam and you can see it here, Chromosomes,
start position, and so on. As you can see the output
contains one line for every exon, represented on the line. We're going to repeat this operation. Now with the RefSeq.bed, b, e, d. We're going to save that as,
again, over sim refseq.bam. And would send towards you, we can now view
the contents of these five. Okay, and what you will notice here,
for instance, right from the very first line is that there is one line now,
one alignment, for each gene. But notice the length. The cigar string corresponding
to the first alignment, 59,129. This is because it contains the inference. So it is shown as an alignment
that starts at the beginning of the gene and
ending at this very last nucleotide. But containing all the intervening
inferring positions. So if we want to show
a more realistic picture of the alignment that shows
introns that separate exons, then we need to specify That we want,
that the input. Is embed 12. So now let's look at
that particular output. Santours view refsig.bam [NOISE] Okay. And now you can see that
the cigar string truly represents the axon internal structure of the gene,
62. The first axon in this gene will have
62 bases, followed by an interval of 12,698 bases, followed by
an external plane 54, and so on. So careful about the use of
this split modulator in this particular types of operations. We can use these conversions in order
to go from a BAM format to a BED formatted file and
therefore use it in overlap or intersect type of operations
using vectors intersect. So this is what we could do,
for instance with the alignment card NA12814.map,
however, we won't illustrate it here. There is one exercise that
you can take from home. The last operation, the one that can
perform with bed tools would be. I will be able to illustrate. So, given a set of intervals
represented into a format such as GPS. So seven genome allocations. The comments sacrament
get facade announce one to retreat the facade sequences
corresponding to those annotations. You might find these useful
in the number of operations. For instance, if you want to calculate for
sequence operations of gene operations such as determining
the longest open reading frame. Or for instance to create an index for
trans subatomic analysis. Which is what we're going to
be covering in lecture four. So let's get started. Just like before, we'll look at
the command line then options bedtools, getfasta, and then help. So the format is bedtools
getfasta a number of options, inputfasta file,
which corresponds to the genome so that's a genome file, then a bid five,
that corresponds to the annotations. Then finally the output fast data file. There there a couple of. There are a few options here. So input split again, so in the case where we have bad records that contain blocks,
for instance axons within a G. So let's give this a try,
bedtools getfasta, we keep the options, -fi, and this is going to be the genome, 2, 2, 3. Hg38c.fa -bed, and let's start with RefSeq.gtf. And the output can be refsic.gtf.foxstate. Genomes, that's a typo so
we'll correct that. Lets verify that it's there. Oh yes. Hg38, sorry about that. And now lets look at
the file ref c.jpf.fast Okay. And then there's going to be one line for
every exon, or for every feature in the jpf file. So it's more useful, in fact,
to use RefSeq as a bed file. So let's see what we obtained
without the additional modulators. So we'll store the output. Input file genome file. We have a bed file, RefSeq.bed,
the output is RefSeq.bed.fasta. So now let's look at RefSeq.bed.fasta. And now you see that we have very,
very long lines. And why is that? Because we used a BED formatted file,
which contained one line for every gene. And given that we did not
specify that they are blocks. That each line consists of block. Exonic blocks interspersed by introns,
then the full interval from the beginning to end of the genes was considered
as the span of the gene. So this corresponds to the genomic
sequence containing introns and exons and introns at that particular genes block. So we can change that. Let's look at these. And we can use split to indicate that our bed file contains multiple blocks for entry. And now If we view the file, we're going to recognize that each gene
has its appropriate, its correct length. So the exonic blocks, the fasta sequence
is called corresponding to exonic blocks, were extracted and then they were together
to form the entire sequence of the gene. So we have just illustrated how to use,
overall we have just illustrated how to use bedtools in order to
perform genome arithmetic and other manipulations of sequences and
genomic features. And with this our second lecture, on
Sequences in Genomic Features is complete. See you next time."
