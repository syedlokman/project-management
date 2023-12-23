---
title: BED Tools I
slug: bed_1
date: 2023-12-24 05:20
description: BED Tools I
---
"In this section,
we are going to be looking at BEDtools, which comprising a suite of tools of
performing genome arithmetic, and more generally, looking at how we can
manipulate intervals and genomic features represent these intervals, or
groups of intervals along the genome. BEDtools is a versatile suite
which contains tools for not only general arithmetic, but
also for converting from one format to another, and also for
sequence manipulation such as extracting sequences within
a certain range or interval. So, we're going to get started. First, we're going to look
at BEDtools intersect, which allows us to determine overlaps
between sets of gene annotations. And then we're going to
look at some of the other types of operations that it allows. We illustrate that going back, with a
suite of examples, and with two questions. So, let's look at them,
let's look at the data files, you may recall that earlier in
the session, we downloaded a number of annotations from various
edit post stories. For instance we downloaded
the set of Alus annotation in the Alus.bed file listed here. Those are [INAUDIBLE]. We also downloaded
the RefSeg gene annotations, and we extracted those in both bed and
gtf format. So, let me show you a little bit just
the header of each of these files. Let's use head to show the top
ten lines of the Alus file. So, we have them representing
every location on the genome. Chromosomes start, end, the name, a numerical value, and
then plus or minus trend. Then for the RefSeq file, for
the gtf file, head RefSeq.gtf. So the gtf format, you can see it here, there's one line
corresponding to every exon as a feature. And then exon lines
are grouped by the gene. So, for instance,
the top three lines correspond to the gene non-coding gene
NR_110761 in the RefSeq database. We have the nine columns just to
remind you, chromosome, the source and then the type of feature exon or
start_codon CDS sometimes is transferred. Start and end coordinates of
the feature along the genome. Then a numerical value that represents
a score, used for visualization, but not used here. The information about the reading
frame in this coding sequence. And then the ninth column contains some
general information about the gene identifier, transcript identifier,
sometimes expression and other types of connotations. So this a gtf format, you also have
the same information but in bed format. Where now, we have one line
corresponding to every gene. Each gene is shown with its
corresponding exons as block, separated by commas here
in the last few columns. Same information,
just a more compacted presentation. These are the two types of
genomic features that we have. We also have a set of
alignments NA12814.ban in which we align RefSeq alignments, a subset of alignments from a sample. Let's take a look at what this looks like. Samtools view. Okay. Seventy five and so on. And they were both read one and
in read two. As you might recall,
the we determined that. Now using this set of operations, we might ask when to ask, let's say
the formal interbiological questions. The first one might be,
give me all the exons or all the genes, or all the transcripts that contain Alus or
in other words it overlap Alus. And the other one might be
give me all the alignments or expressed RNA segments that overlap Alus. So give me the expressed Alus
as represented in this sample. And we're going to try to answer
both of them, the first one. Now at the second one after we
are looking at the numbers segment. So for this purpose lets start by
looking at backtools common and see what are the particular operations. So backtools, if I just type backtools
you will see that I get a very long. A very long listing of all the command
line options that one can use and of the sub commands that one can use. So in order to better view these and
to be able to take my time analyzing them, I'm going to just redirect
the standard output, the standard error to a file
lets call bedtools.log. Now I can simply open it and
I can look at what is the functionality. You can see that BEDtools number is
a very versatile suite of tools and performs a number of different
types of operations. Perhaps the most important and the most
popular are the genome arithmetic. First of all, intersection, finding
overlapping intervals in various ways. But also identifying the closest and
potentially non overlapping interval, or clustering intervals,
subtracting intervals, and so on. But it's only one fo the types of
operations if you're going and scrolling down. Another one that I will be demonstrating,
and check our use for, is to perform format conversion,
particularly to transform bamtobed format. Conversely, go from bedtobam. Then there are also some subcommands for
sequence manipulation. For instance, getfasta to extract
the fast a sequences for given at least an intervals, so gene annotations
represent as a gtf or bed file. So with this in mind, it's the intersect
supplement is the one that we want. And let's do a singular operation here. So we're going to see what are the options
for the command line intersect. And that should have back doors. And the basic command line
is bedtools intersect, a list of options which we can read below. And then the two files
containing intervals, or annotations that need to be intersected. Introduce with -a and -b. So let's look at the options. First so the input can be the type
of input if it can be a bam file, and then the output, whether we want
the output to be bed file in that case. But a more important list is the type
of output, so the option wa for instance, we'll import your genome entry
in A every time there is an overlap. For every feature that contains
an overlap featuring the first file. Conversely, the option -wb will write the
original entry in B in the second file for every overlap for the feature in A. There's also an option, wo, that's more informative in the sense
that it will write for every overlap. It will write the original A and B entries
that overlap, concatenated along one line. And at the end of that line, it will list
the number of bases that form the overlap. And then there's a parallel option to
that, wao, that will again write the A and B entries concatenated and
the number of base overlaps but instead of reporting only the features
that contain overlap from a file A, it will report all entries in A. There are also a number of parameters, parameter options that look at how to
qualify, how to modulate the output. For instance, by default,
two features are reported as overlapping. The overlap is at least one base pair. These can be changed with
the command line -f to be a fraction of the length of the featuring A so
50% of the length. And then there's also
the option -r that comes with -f which requires that
the fraction of overlap be applied equally to A and B, so
50% should be 50% of the A feature containing the overlap as well as 50%
of the features containing the overlap. And these are some of those that I will
be illustrating try to remember them. Perhaps one more that
is very important split in case we have a BED entry
BED12 it's called here, corresponding to one genome to one
transfer that contains multiple blocks. In this case multiple exons. Then each one of those blocks or exons should be considered a different
annotation in the intersection and same thing for
spliced alignments in the SAN file. The default option with the C and
alignment as a single segment starting at the start coordinate and
ending at the end coordinate and also containing the intervening features,
intervening features. So we definitely want to use split
when we're looking at BAM files, or BED lines that contain corrections. So let's try now to answer
the question of how many exons transcripts slash
transcripts and slash genes. In the reference connotation contain Alus,
using the vectors to intersect from the end let's
get the file names first. Let's say RefSeq in gtf format. The second one is
compared to the Alus.bed, now let's see what we
want to have reported. And let's assume that we want to have
reported only the lines that contain the overlaps and we would also like
to know the extent of the overlap. The number of business
that contain the overlap. So just running this, okay, and if we look at the output, the first
nine columns that I'm highlighting, refer to the feature in the A file
in the RefSeq.gtf file. You will recognize the characteristic
format, chromosome, source, feature type, which is x and y coordinates, and so on. Three more columns. Followed by information about the gene and
transcript. Then the second set of columns refer to
the overlapping feature in the B file. So that's the Alus. One, two, three, four,
five, six, six columns. Chromosome location within
the chromosome will start end Alus, the numerical value of. And lastly, we have the number
of base pairs in the overlaps. So, 309 pairs on the overlap. So let's see how many
such features we have. And we have 452 exons that
overlap on this feature. Now let's see how many genes
do they correspond to. And to do so, you might recall that
the gene ID is located in column nine. So we're going to cut using
the tab as delimiter, which is the default delimiter,
we're going to cut column nine. Now within column nine,
we're going to again identify column two, which contains the gene information. And we'll use the separator,
a space as a separator, a single space, then column two,
and let's see what we get. So these are all the genes,
sometimes specified twice or three times depending on the number
of exons that overlap Okay, but the genes that had overlapped with exons. So now we can, to identify to
determine the number of genes, we're going to sort uniquely,
and then count. So we have 452 exons corresponding
to 259 genes that overlap exons. And we can answer the question
on transcripts in a similar way. So this is how we could use
the vectors intersect command for a simple intersection analysis. Now, let's assume,
let's use, in this case, in the gtf format, every line was
a separate feature, separate exon. Now let's use the RefSeq BD. The BED format where one gene
is represented by one line with multiple intervals and see what we get. So we will recognize the BED format,
okay theres one, two, three. Twelve entries here,
12 columns followed by the six columns corresponding to the Alus and
finally the amount of the overlap. What you might recall, however, was that
in this case the entire span of the genome is going to be considered for the overlap. So let's see just. For information purposes
how many lines we have. And we have 33,607. So we definitely want to split this, we want to add the common
line option split so each exon is going to be
considered as a separate interval. And that brings it down to 432 feature, which is much closer to the ones
that we noticed earlier. So if you consider that as
being a split interval. One more option here. What happens if we're adding wao. I like to show you. So in this case, if you're looking
at the last, in this case, we have all the features in A represented
whether they do have an overlap or not. And you will see that why the first
line shows an overlap feature. The second line here
will show you the gene, followed by a no entry in the alu file, which is represented by a .,
-1, -1, and so on. So that's a way of
representing no features. So in most of the cases you
will be interested in using the -wo overlap only lines. So this concludes the illustration on
how we can use betters intersect to generate the intersection
of two sets of allocations. In the next session we'll be looking
other functionality provided by BEDtools."
