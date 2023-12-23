---
template: blog-post
title: Genomic Tools Module 2 Sequences and Genomic Features
slug: genomic_2
date: 2023-12-24 04:03
description: Genomic Tools Module 2 Sequences and Genomic Features
---
"Let's start again by thinking about all the various molecules
in the context of the cell. So we have the cell, we have its nucleus,
a number of organelles. If you think about the genetic material, we have at any given time one copy of the
genome shown in this green squiggly line. We have for every gene or for
the genes that are being expressed one or several copies of the mRNA
either in the nucleus or in the cytosol you see those
represented with blue squiggly lines. And similarly have a number of copies for
every protein both in the nucleus and in the cytosol. And the question is, what do these
sequences look like, what do they do, and how many of them there are? And we'll address the question of sequence
representation and generation here. So, you probably know by now,
but I will say, nevertheless, Genomic sequences, we can think about
them as being unidimensional objects of strings that are formed of
combinations of four nucleotides, adenine, cytosine, guanine and
thymine, and very simply said, ACGT. The mRNA gene, or gene sequences are strings over
an alphabet of four letters, A C G U, where A is adenine,
cytosine, guanine, and U is uracil. However, for convenience,
we shall simply use T to represent U. And proteins are words or
strings over a 20 letter alphabet, but we will not be addressing
proteins in our presentation. So, this is the representation,
the question is, how do we generate this sequence? How do we figure out
what those strings are? Well, ideally we would like to
have an instrument, let's call it a sequencing instrument that starts
at the beginning of the sequence and tells us every letter
all the way to the end. Unfortunately that is not possible
with current technologies. So instead, what happens is current
technologies would sheer, or split, the substrate, whether its DNA or RNA,
into a number of pieces, so call fragments and then every fragment gets sequenced and
those pieces get put together. So there are two processes embedded here. The first one is the sequencing. The biological, with the lab, or experimental part,
which represents isolating the DNA or the RNA, then fragmenting in and
then sequencing. The second part is the bioinformatics
part which means assembly. So, let me go a little
bit to each one of them. For the sequencing once we have
the substrate it usually gets sheared into a number of fragments that
are roughly the same in length. Roughly the same means that actually
we can characterize it statistically by a normal distribution with a given. Average and the given standard deviation. Now, each one of those
fragments is in turn, can be amplified if there's
not enough material or not. And each one of them is sequenced either
from both ends and that's what you're seeing there with the red arrows pointing
towards each other, or from one end only. If sequencing happens from both ends, we
call the resulting reads paired-end reads. If it happens from only one end, we're
going to call that a single-end read. So that's, in a nutshell, the process. Once the sequences are produced,
we have to put them together. We have to use them to reconstruct
the sequence of the original molecule and not only going to give you a flavor of
what's in the bioinformatics world. So imagine that you have two segments
that are co-locating on the genome and they share a common portion. Well, by looking at the common portion for
instance, the fact that the N sequence of one read Is very, very similar to the
beginning sequence of another read that tells us they belong to a same position
to the same location on the genome and it all also tells us
something about the order. That read number one should
come before read number two. So just imagine if you're putting all this
information together for all the reads and what you create is a data structure
that is called an assembly graph. In which the nodes, shown here in yellow,
are the reads and in which we can establish a connection whenever
we have an overlap like I've described. And the task of the bioinformatician is to
write an algorithm to traverse this graph so that all the reads are being included. By putting that information together, then one can create a consensus
sequence for the genome. So those are the two steps. Now how do we generate the sequences? Up until 2008 the prevailing
method was sanger sequencing. So in sanger sequencing will
produce relatively short reads. Relatively long reads 500 to 800 bp but
it was expensive, it was slow and it required
amplification into a cloning vector. It was also medium to relatively high
throughput, especially in its last years. However, in 2008, Next Generation
Sequencing marked a revolution in our ability to produce reads. At this point,
new sequencing instruments, particularly Illumina sequencing instruments have
started being able to produce shorter, much shorter fragments somewhere
between 50 and 450 base pairs. However, at much reduced cost. I'm t about less than one
dime per megabase, and very, very fast to the point
where we can generate hundreds of millions of feeds within
a matter of days on one instrument. But clearly, the next generation
sequencing will produce a revolution in terms of our ability to generate sequences
It also brought major challenging, especially for
the biome of mapping genome assembly. So there's a story of how
we generate sequences. Now how do we represent sequences? For Sanger sequences,
the prevailing format is Fasta, or Pearson format and
it's very simple, you can see it here. So there's one line that starts
with a greater than sign that represents the header
of the sequence. So you have the greater than
sign followed by an identifier that very importantly uniquely
identifies the sequence and followed optionally by some
information about the sequence itself. In this case it tells us that
this is the interlocking tool receptor gene in homosapiens and
that it's an mRNA. The hidden line is then followed by one or
multiple lines containing the actual sequences and one has to be very
careful to not include any blank lines. Now clearly we might want to put
multiple of such sequences together especially if we're
talking about the genome. As we said there are many chromosomes,
22 plus x and y. In order to do so all we have to do
is to attach these records together. So we have one header line followed by the
actual sequence followed immediately by another header line, fasta header,
and it's sequence and so on. Again, importantly, there cannot be any blank sequences or
any lines that start with a space. So that's the multi-fasta format which was
used and is still being used for Sanger sequences as well as for a presentations
of genes Genomic chromosomes and so on. With the advent of next generation
sequencing technologies, we started adding more information to
the sequences, which becomes important in bioinformatics applications that need
to take into account the quality. So how much can we rely on
the sequences being produced. And what I'm showing you here is in fact
not one but two so called fast a records. So let's break that into pieces. The first line, so
every record contains four lines. The first line us a header line, and always start with an at sign followed by
an identifier which can be fairly long. Usually these identifiers give information
about the precise location and geometry of the cluster within
the sequencing instrument. Often times you will see
that the last two digits, the last two letters will be
a slash followed by a one or two. That one or
two tells us what is in the pair. In case we have paired. More recent formats also show additional
information such as length at the end of the header. Now following the header
is the actual sequence. You want to see A's, C's, G's, and D's, and occasionally an N,
lower quality sequence or no. The third line starts with a plus sign and item repeats information in the header
precisely or is just a plus sign. And lastly, the fourth line is a so
called line of quality, of base qualities. So there's one, letter here or one symbol. For every single one of the bases
that you see in line 2. And that tells us how much we can rely. So how much can we trust the reading, the automatic reading of the base
calling at that particular position. As you can see, just like we've
done with multify stay sequences, we can stack together many, many such
records and we can create a Fastq file. Now I'd like to look a little bit more
closely at the base quality scores and to explain to you what those mean. So let's assume that we have
a mathematical model in base calling, and we have a probability to see a base b,
let's call it the probability p b. Probability that the core
at base b is correct, then the quality value
is simple an integer that is obtained with a formula given
here minus ten, log base ten of PB. There are a variety of systems for
establishing quality scores, but systems now tend to converse
to one set of criteria, one system, which is Sanger and
started from the Phred quality scores. In this you can have a quality score associated with a base as a value
that ranges between zero and 93. Obviously larger values
will mean higher quality, lower values will mean poorer quality. These correspond, if you're writing them
to ASCII characters between 33 and 126. And just to take a look at them,
I listed them there. So you're going to see 94 positions where
the lowest quality is represented as the exclamation point to
the left hand side and the highest quality is that squiggly
line that I showed you earlier. Now in practice you're not going to
have quality values over 40. Lastly in terms of interpreting this data, quality values that are below 20 or
sometimes even 25, depending on the application,
are generally considered to be low. So, this concludes our first
section on sequence generation and sequence representation. Next, we're going to
look at genomic features."
"So, suppose that we already have
the sequence of the genome. Now, what is the next step? That would be to go along the genome and
to annotate important features. So essentially we would like to
determine the precise location and structure, meaning intervals or
lists of intervals. Think about exons or maybe genes and your associated biological
information all along the genome. We call it Genome Annotation. What can these genomic features be? They can be genes as I said,
they can be exons, they can be promoters, protein binding sites, translation start
and stop sites of DNA cutting and so on. So a variety of features. I'm going to give you one example
that's going to come in handy which is Genome Annotations. So what do we call Gene Annotation? Well, when we're annotating genes
we would like to know a variety of types of information. We would like to know
where the gene is located. And how it's structured into Exon and
Introns? So if you're looking at this example here,
there are two genes. One of them is in red,
the other one in green. The first one has three exons. We know the precise
coordinates of th exons. For instance, the first exon for the red
gene is started position 10,135 and goes to 10,600 and so on. And similarly for the red and
for the green gene. We would like to know the strand, and you can see we have an arrow showing that
the red gene is on the forward strand, whereas the green gene is
on the reverse strand. And maybe you want to know something
more about the gene structure. So for instance where does
the translation start and where does it stop within every gene and
so on? So that is what we call Annotation. Now of course we have a representation or multiple ways of representing
genomic features. And the first type of representation
that I'm going to tell you about is the BED format. It is the Browser Extensible Data
format and B-E-D, BED is obviously an abbreviation. In the basic forma,t BED files only need
to represent the data in three columns. Basically signifying
the location within the genome. The first column gives the chromosome or
the scaffold as the genomic substrate. The second and the third column
shows the start of the feature and the end of the feature. And I'm going to say something
important here, they are zero based. Which means the first base in
the genome is considered to be zero. So there's the minimum that we
need to specify in a BED format. However, we can add more fields
to show more information. So in the representation here at
the bottom, you'll see that in addition to the chromosome number, start, and end,
we've also added a name for the feature. Exon one, exon two, exon three and so on. Escort, Strand, data values to numerical values that
indicate thick_start and thick_end. And then finally an rgb
cover representation. So what are these? I should point out that this really
mimics, this refers to the example of gene annotations, the two genes that
I've shown you on the previous slide. So, as you might see, we have three exons,
Exon one, Exon two, and Exon three, which correspond to the three
exons in the red gene. And then we have exon four and five, which have features corresponding
to the two exons in the green gene. Now the score is typically a value
between zero and a thousand, it simply indicates to a browser or visualization
tool how intense the color should be. The strength can be plus or
can be minus or reverse, depending on what strand of
the genome the feature is located. And then the thick_start and
think_end mark a visualization feature. Basically they tell the browser where the direct handle representing
the feature can become thick. So these are common way of representing
the start of the protein coding, of the coding portion within a gene. Lastly, column nine is an rgb, Red, Green,
Blue, representation for the color. So, as you can see there,
the first gene is shown in red, whereas the second gene is shown here,
well, in blue. Now, I want to go a little bit more over the concept of zero based
versus one based notation. On the previous slide you
might look at the coordinates. And you might have seen that
the coordinate of the first exon, the start coordinate, is 10,135. Whereas in this here presentation
the first coordinate is 10,134. The end coordinates however
match between the two slides. So let me explain a simple way of
thinking about this representation. Let's assume that we have a sequence that
is called, that reads A C A G C T A C A G. You can think about zero based
coordinates is being in a system that counts the spaces. So there's one space,
space number zero before the first letter. Space number one is between
letters one and two and so on. So we have ten spaces here zero to ten. In contrast we can count basis,
which is usually what systems do. We start with the first letter
A corresponding to letter one, C two and so on up to G ten. So in a zero base system we count
the space right before the first letter in the string we're interested in. And we're counting all
the way to the space that immediately follows the last
letter of the string we're looking at. So if we're looking to
represent the string C, A, G, B in zero base coordinates. This will be listed as
the interval between one and five. Whereas in one base coordinates, this will represent the interval
between two and five. So that's it about how we represent
intervals in the BED format. Now what I've shown you referred
to the case where each interval was a separate entity or rather each
entity was a separate interval. So we talked about exons
as being separate entities. However, most often we would like to show
exons that belong to a same gene together. So we would like to have a concept
of clustering intervals, or features that belong to
the same larger feature. And we can do so by putting additional fields at the end
of the already existing BED record. So here's how we do it. We have two lines here. The first one corresponding
to the first gene, the second one corresponding
to the green gene. And you can see there, in bold font. Additionally we're giving the block count,
where a block will correspond to an exon. So we have three exons in the first case,
two exons in the second case. The sizes of each block,
that is the size of each exon. In this case for the first gene 466,
basis for exon one, 31 for exon two, and 903 for exon three. And lastly we give the coordinates
in the relative system, the start coordinates of the features,
the block. In the coordinates system where
zero marks the beginning of the G, the beginning of the first exon. So this diagram at the bottom
actually represents shows you the correspondence between
the two notation systems. So you start, now, instead of on 10,135, we're marking that as position
zero in the new system. You see the lengths of the three axons,
466, 31 and 903. And you see what the start
coordinates are, 843 and 3,275 for exons two and three. So, that's fairly simple. In addition to the BED format, several other types of formats have
evolved for representing genomic features. And some of them, especially the next
two that I'm going to be talking about, were geared to representing gene
information and transcript information. So, the GTF format,
in the GTF format, let me just say, GTF stands for Genomic Transfer Format,
we have more columns. It is structured, perhaps, in more. In the first column, just like in BED
format, we show the chromosome or the scaffold. So there's the genomic access,
an identifier for it. The second one tells us the source
which can be a program or it can be a website or
anything that you can think of. The third column tells
us the type of feature. The fourth and fifth numerical
columns simply tell us the beginning of the feature along the genomic axis,
along chromosome seven and the end of the feature. Then we have the score, just like before,
that represents the shading and perhaps represents the confidence that
we have in that particular feature. This strand signifying the forward or the
reverse trend that features locating on. The dot here, so
almost anytime we can place a dot if the feature is not applicable or
we don't have the information. But this column, had we had
the information would represent the frame. Particularly for
coding sequences frames zero, one, or two. And then comes the ninth column,
and the ninth column is typically a composite column that has
at least two different types of fields. The first one gives the gene
identification, gene identifier. And it's preceded by gen_id. Followed by the actual name of the gene. Then the second piece of
information is the transcript ID. In this case genA.1 meaning
it's variant number one. There can be additional fields
that refer to the abundance, to the exon number and so on. And within column nine the fields
are being separated by spaces. As you can see for the GTF format as
well as for the BED format, BED format. The columns themselves
are separated by types. Now as to how genes are structured here. So, all the exons corresponding
to one gene are grouped together. So, you might see here that the first
three lines correspond to the three exons in genA, in that particular order. And you might see that the last two
lines correspond to the two exons that form genB. Another important distinction
from that format is the coordinates here are one base. So, we're going back to one base notation. So, the first position for the gene
along chromosome seven would be 10,135. So that's the genomic transfer format. A format that is next, a format that is closely related to the GTF format and
that also evolved from gene representation is the so called GFF now in
its version number three. So GFF stands for Genomic Feature Format
and usually needs to be preceded at the top of the line by a line that
specifies the version, GFF version three. Then just like with the GDF format we
have one line for every exon in the gene. We have column one representing the exon,
representing sorry, the genomic substrate,
whether it's a chromosome or a scaffold. Followed by the source, let's say the GF
stands for some generic gene finder but it can be Cufflinks,
it can be GenMark, it can be C4. Followed then by the type of feature
in the exemplifying with mrna and exon. But other features can be there as well. Followed by in columns four and
five numerical values that represent the start and end coordinates
of the feature along the genome. A score in the following column, the strand, the common frame or
a dot if we don't know that. And then in the last column some
information about the feature and the cluster that it belongs to,
the upper-level entity. So they are specific
fields are identifier. So we're giving a name that
uniquely represents this feature. For instance, our two genes are going
to be named, mrna001 and mrna002. And then we're also giving
the name of the gene, in this case genA and genB. Other fields can be included there as
well, but that's a minimum representation. Now as you can see, so
after the mrna line, that gives one line representing a summary of the gene,
we have in the first case. Three exon lines,
that each corresponds to one of the exons. Here, we have an ID for
every feature, exon 0001, 0002, 0003. But, we also have a parent feature that identifies this as being a feature
that's part of the parent mrna. So the parent for
all the three is mrna0001. So, that's the way we can represent
genes in the GFF3 format. And that concludes our brief section
on representation of genomic features. In the next section, we'll talk about
the specific type of feature, alignment."
"In this section, we will be talking about
a special type of a genomic feature, alleles. Think about a particular application. This can be a clinical investigator
who wish to sample all the sequence of a number of patients and control. To identify and analyze the,
to identify DNA or RNA variations, or this could be sequencing of a new
species, plant species for instance. In either case,
this will start by isolating the DNA or the RNA sequencing it. And the next step would be to try
to place it into genomic context, in other words to map it to the genome. And we call this an alignment. Intuitively if you're thinking
that particular read, that particular sequence,
came from some place on the genome. So they're should be somewhere
on the genome a sequence of new strongly resembles it. I'm saying resembles it, and it is not that it is identical because
there can be a number of differences. This can be polymorphisms, or they can
be errors introduced by sequencing. And our task is to find an alignment. An alignment is, essentially a mapping
between the letters of the read and the letters of the genomic sequence
at the particular location of origin. Where we're matching each base that is
identical between the two, and we're using some spacers in order to fill in the gaps,
or for the portions that do not match. So I'm showing you one example here
at the bottom with two sequences, sequence one and sequence two. And just for reference, let's think
that sequence one is the reference and generally is the genome, and
sequence two represent the read. We talked about letters
bases that match and those are shown here with vertical bars. But there are also a number of
positions that do not match, and they need to be filled in. And we have three types of so called edit operations that we can
use to fill in these positions. The simplest one perhaps is substitutions,
assuming a substitution, we have one letter in the genome and
another letter in the read. We have three substitutions here marked
with the red, and in the third one, for instance, we have a G in the genome,
and an A in the read. This might be a mark of polymorphism or it could simply be a sequencing error,
as I said earlier. Now there might be cases in which
a letter is present in the genome, but is missing from the read. So we say that, that's a deletion,
and that's shown here in blue. And yet there may be another case here in
which there's a letter in the read for which we have no
correspondence in the genome. And that's shown here in green, and
we're going to call it insertion. So it's insertion
corresponding to the genome. All this notation refers to the genome
as being the reference sequence. So let's think a little bit about
alignment as segments in genomic features. If we start with the DNA shown
here on the left-hand side, we produce a number of
reads represented in red. And then every read,
the vast majority of the cases, each read can be mapped continuously
along the genomic region of its origin. So we have three reads and their
corresponding locations along the genome. In the case of an mRNA however,
the mRNA splices together information that is located at different positions at
different intervals within the genome, as the exons. The exons are separated by introns. So if a read belongs
entirely within an exons and that's the way you're
seeing these red read here, then they will be located then we
will have a continuous alignment. The alignment will be in one piece. However if our read in
this case shown in green, spans the boundary between two exons. Then they would have to be
divided along the genome, and the points of divisions
would be particularly the boundaries of the exons or
the starting end of the intron. So that's what you're
seeing here in green, and we call such an alignment
the spliced alignment. So those are the two types of
alignment structure that we can find when we're sequencing DNA and
mRNA respectively. A couple more concepts
related to alignments, especially as it relates to alignments
of next generation sequences. You may recall that the DNA or
the RNA will shear into fragments, and the fragment sizes followed a fairly
well characterized distribution. A normal distribution with a given
average and a given standard deviation. So we'd expect that anywhere we find
these two reads along the genome is the originating sequence, they will follow the same rules we
got this the distance between them. If they do, and this is the case here
in cartoon on the left-hand side. So if they're mapped on the genome where
the reads are in opposite directions and facing each other, the alignments. And the distance between them
is within the boundaries that are specified for
the original set of fragments, then we call that particular
mapping as being properly paired. So we're saying that these are properly
paired or that they are concordant. Now of course, if any of those
conditions is being violated, we're going to say that
the mapping is non-concordant. So what does it mean that
it is being violated? For instance, the reads are not mapping
in the corresponding orientations. They might be mapping
both looking outside or they might be mapping both
looking in the same direction. So that's one case, or
another case might be when the distance, so when the mapping does not
meet the requirements for the distance between the reads. In this example that I'm showing
in column number three at the top, when the reads are mapped in
the proper orientation, however, they are too far apart to be concordant. And one variation here might
be that the might actually map to different chromosomes. So we have properly paired or
concordant mappings, and we can have non-concordant
mappings as well. And we shall see how these are being
used in the following sections. Now as I said, these are very
special types of genomic features. And they have their own
way of being represented. The standard format for representing alignments of next
generation sequences is SAM. We can also obtain by compression,
a compressed format that's called BAM. But over the next few slides,
I will be talking about the SAM format and what the information here represents. In a SAM file,
the first portion of the file, the first few lines,
represents the header. Every line in the header will
start with an x sign, and then by very short code that tells
us what kind of line that is. So the first one is an HD line and
a header. So it tells us something about
whether this is sorted or not. We have here a file that is sorted
by coordinates for instance. The following few lines,
marked with an SQ code, are lines that correspond to sequences,
particularly to genomic sequences. And you'll see the identifier for
each one of them, in the order in which they
are listed in the genome. So we're starting with chromosome one,
followed by chromosome ten, eleven, and so on. So now we said they are listed
here alphabetically, but other orders can be used. And then we have an indicator of
the length, LN, and that's the name, 248 mega bases and so on. Following the sequence one we have a PG
line that tells us the program, or the way this file was generated. So in this case it was called, it was generated by a program
that's called TopHat. And just to get ahead to look forward,
to some of the future lectures, TopHat is a spliced alignment program. We talked about spliced
alignment on the previous slide. So following the TopHat, we have
the version as well as some information about the command line parameters
that were used to produce this file. So that's the header. And following the header, we have the
alignments and there would be one line for each alignment. And everything that is shown here at
the bottom, is actually just one line. So there's a lot of information,
let's go through it. The first item in one line,
and by the way, all fields picking a line
are separated by terms. So the first one is to read the read ID. So that's taken from the FASTQ header. You might recall that from
the FASTQ representation. The second one is a FLAG,
and it's a complicated and complex entity which I'm going to
explain on the next slide. The third one just like with other
genomic feature representations, gives us the scaffold
of the chromosome ID. So the substrate genomic axis. Followed by the start of the alignment,
in this case the position of 10,021. The following field gives
us the mapping quality and the next one marked here as a 50M,
tells us something about the alignment. Basically it's a compact, a compress representation of the alignment
and is called a CIGAR string. We'll be talking about this
in a couple of slides. The following line, the following field,
tells us about where the mate of this particular read is located,
on what chromosome. If the chromosome is the same
as the current chromosome, we're going to see an equal sign. If it's a different chromosome, we're
going to see the name of that chromosome, or if the mate is not mapped,
then we're going to see a star sign. So that can give us some information
as to, in a very restricted sense, as to whether this pair has
the chance of being concordant. The next column looks at where
the next mate would start. So in this case at position 10,151,
as I said on the same chromosome. And then is followed by the mate distance
measured along the genomic axis. The next field is a stream field and gives the actual sequence
of the query of the read. And immediately followed by
the query base qualities, as I've shown you on the FASTQ format. And lastly,
we have a number of features that are all separated by tags, that give us some
further information about the alignment. And there are variety of such fields and
tags, and some of them are standard and some of them are user specified. So all the tags that start with
an x point are user specified, or rather they are program specific. A tag, as you can see here,
has three components. The first component is a two letter code,
followed by and separated by a column by a letter that
tells us what kind of field it is. For instance, A marks a character,
I marks an integer field, F a float, Z a string, and H a hex string. And then lastly, we have the value for
that particular attribute. So we have a tag a code, followed by the
type, and followed by the attribute value. And you're going to see only
a few of them represented here. So AS here is the alignment score and
it's an integer value. NM here is again an integer value, and is used to denote the edit
distance to the reference. In other words it tells us,
how many of those edit operations, how many substitutions, insertions, and
deletions we needed to include to equalize to do the mapping between the query and
the corresponding genomic sequence. Then we have NH which gives
us the number of hits. So you can see that
this read has ten hits. We have the strand, the predicted strand,
in the field XS and you might notice that
it's program specific. And then we have the hit index for
this alignment. So if we have multiple matches and each
one of them has a different quality or a different alignment score,
what is the order, the position of this alignment within that particular
hierarchy, that particular list? So that's the SAM format in a nutshell,
but I would like to spend a bit more time on the flag and cigar strings,
because they are complex fields."
"So flag represents a combination of multiple pieces of information. All of which are represented in binary. So at the level of bits. So what we're seeing is
a base ten representation, a number that represents this
collection of information. So for instance, imagine that
you're writing these in binary. And then the right most bit, 0x1, tells
you whether there are multiple segments. In other words, the formula reads
whether these are pairs of reads, pair then reads, or single end reads. Another piece of information that
is contoured by the second bit form the write, is whether the segments
are properly aligned. So this is the concordant information
that I mentioned previously. The next piece of information is whether
the segment is mapped or unmapped. Often times, FLAGs may contain red words
for the sequences that cannot be mapped, just for the purposes of
providing a unified view and a complete view of the original data set. The next bit, moving again from the right
to the left, tells us whether the next segment in the template, basically
its mate in the pair, is unmapped. Following this, we have some information
as to the sequence for the current read have to be reverse complimented
to be aligned to match the genome. Or whether the sequence of the next mate,
or the next segment,
had to be reverse complimented to match. The next two bits marked
here with 0x40 and 0x80 in hex tell us whether these
degrees that we're looking at is the first segment in a pair of reads or
whether this is the last segment. Moving on, 0x100 tells us, so
looking at that particular bit, tells us whether it is a secondary
versus a primary alignment for that read, based on the equality of
the mapping, the alignment score. 0x200, if that bit is set, then that means the read is not
passing the quality checks. Maybe the base quality values are not high
enough or maybe there are too many ends. On the line that's marked 0x400, the bit
will tell us whether this is a PCR or optical duplicate. And lastly,
the left-most bit in the representation will tell us whether this is
a supplementary alignment. So let's take one example. Let's say on the previous
slide we saw the code of 99. So 99 is a representation in base 10,
which is what we use for numerical representations
in day to day life. We're going to write that in basic still,
decompose it, and then what you see on the right-hand side is
a sequence of blocks in green, black, and red,
you will see a binary representation. So we have 12 bits. We're going to start from the right and
move to the left, and we're going to read. We're going to interpret
the meaning of the flag 99 using the individual meanings of the bits
as reflected in the table above. Remember, we're moving from
the right to the left. So the 0011 or rather,
moving from the right to the left, 1100 marked in red, gives us information that
would reading on the first four lines. Multiple segments,
segments are properly aligned, and so on. So 0011, or rather 1100,
tells us that these are paired end reads. That the pair is properly aligned,
the bit is set to one, that this segment is mapped,
and its mate is unmapped. That's because we would have had
one if the statement was unmapped. So that was easy,
now let's check the next block. Again we're moving from
the right to the left, but in this case it's a palindrome so
it makes it easier. So what this information tells us that the sequence was matching
the forward direction. Basically that it did not need
to be reverse complemented. And that it's mate, on the other hand, had to be reverse complemented
to match the genome. It tells us that this read
is the first in the pair. I'm reading the line that
corresponds to 0x40 first segment. It is not the second or
not the last in the pair. So that's the second block. As for the third block, its all zeros and it tells us that they read
past the quality check. It is not a PCR duplicate and
it is not a supplementary FLAG. So that's how you can interpret
each one of the codes. And there are specific ways in which
you can use, for instance, Python or Perl commands to extract
information automatically. Now the next and
last piece of information, the last field that I will be
talking about is the cigar field. Which is used to represent
the alignment in a very compressed and rather lengthy form,
longer form, a CIGAR-like form. The CIGAR from can be represented
as a sequence of short strings. Each string,
there's a number followed by a letter. The letter marks edit operations, and the number tell us how many
such edit operations we have. And here are the types of
editing operations that expand on the set that I gave you earlier. So M, for instance,
says that it's one nucleotide match. I means insertion to the reference,
just as we talked earlier. D, a deletion from the reference. N, it's a very special case
that represents an intron. S marks a portion that is soft clipped. For instance, the sequence, the start of the end of
the sequence could not be aligned. And it tells us how many
bases were clipped. However, these bases will still be shown
in the sequence field in the SAM format. H marks a hard clipping. So it's just like soft clipping except
that this time those letters will not be shown in the sequence
field in the SAM format. P is a padding for the first segment. Equal in some cases the M value
which it was marked as a match is further identified
as either an identity, a sequence match, so
an A matches an A in the genome. Or is a sequence mismatched, for instance,
an A is different from a C, in the genome. So that will be a substitution. And here are two examples. In the first example, I'm giving
you the reference at the top, and then the read, and how the two align. If you're looking at the alignments
starting from the left to the right, you will see that A C T map or
match between the two sequences. So we're going to mark those at three M. Then we have one insertion, so
one letter that is present in the read but not in the genome, so
it's inserted to the reference. Followed by three letters, G A A,
that again match between the read and the genome. We're marking that the three M. Now you notice that there is a C, a letter
that is present in the reference, genome, but not the read. And that one marks a deletion
from the reference. And, lastly,
we have a block of five letters that are either matches or substitutions,
and we mark those at 5 Ms. So M does not distinguish between
substitution and identity. And in the second example, we're showing
a spliced alignment where we have the read expanding two different exons. So we have that the first two letters, A C
T will match at the end of the first exon and will have 3M, then that there
will be a long intron, a long jump or gap of 1000 bases in the reference
that are not present in the read. We mark that with 1000n
followed by five matches, five Ms, for five bases at
the beginning of the next exon. That's how we represent
a spliced alignment. So this concludes our presentation
of alignments as specific genomic features and
of genomic features in general. And in the following few sections we
will be looking at how we retrieve this information, and how we can manipulate it
using basic or not so basic UNIX commands."
"So far we've talked about sequences and
genomic features. What they are, what they look like,
how they are being represented. And right now we're going to be talking
about, how we can retrieve the sequences, and how we can retrieve the features. Because once sequences
are being generated, they are being deposited into databases,
for the use of us all. I'll show you two different
larger pool stories. The first one is GenBank. How to access sequencing,
the sequences from GenBank. And in the second section, we'll talk about we can retrieve genomic
features from the UCSC Table Browser. So let's get started with GenBank. So I'm going to ncbi.nln.nih.gov,
and then we make the point that it is the primary report story
of genomic information in the US, and it contains a variety
of types of information. In a variety of databases,
which are listed here. So Assembly, BioProject, Clone,
EST, Epigenomics, Gene, and so on. So first let's assume that we would like
to retrieve the sequence of one gene. And let's take the IL-2 gene in human,
which is the example that I gave for a FASTA format, as you might recall
in one of the previous sections. So, I'm going to go in the box here, and
text box ,and I'm going to type IL-2, or Interleukin 2. I'm going to say that I
want it in homo sapiens, and I want the mRNA, okay and
let's see what happens. I have to select the appropriate database,
and the appropriate database for extracting the Nucleotide
sequences would be, Nucleotide. Let's see what happens, so it's a string based search, and you can see I am
getting the number of results 226. And if you're looking at the first ones, you will notice that this
is not very specific. The first sequence is a mouse sequence,
followed by a frog, and so on genomic sequencing,
that's not what I want. However, right here at the edit top,
in a summary, it shows me that perhaps what I'm interested in, might be
one of the genomic sequences either two. Transcript or Proteins, so
I'm going to select Transcript. Let's run again. There are other ways, in which I can fill up the formation to
reach particularly what I need to obtain. So, we have the Homo
sapiens Interleukin 2 mRNA. This is shown here in the general format,
which I had not described. So in addition to the sequence, which is
listed at the bottom, there's information about papers that refer the sequence
about the perfect log post, about the identifier, a specific
identifier from the sequence and so on. Length and many others. So what I want to do is fix
from the FASTA sequence so I'm going to click the little button that
says FASTA Which will give me a rendition of the sequence in FASTA format,
just like I've shown you earlier. And these I can now cut and
paste since it's a fairly short sequence. For longer ones,
we can just send the complete record, for instance, or
just portions of it to a file. And this will download,
the item in FASTA format. I just click that and
it will save it into a text file. That's fairly simple, I can do cell, or
there is already a number of databases of sequences that can be directly
downloaded from NCPI, and which you can access from
the entry page of NCPI. It's fairly simple so
I'm not even going to show you that. I'd like to show you how
to access one particular, one other type of sequences, and
those are the FASTQ sequences. Let's say now that we would
like to find something very specific data let's say strawberry. So I'm going to type strawberry and I'm going to type RNA-seq to
make sure that it's RNA-seq. Then I'm going to go to SRA,
short with archive. Let's see what we get. Search. And I have a number of results, 66. Which I can further filter down. You can see that there are three different
species being represented, fragaria vesca, 37, fragaria ananassa, and one more. And I'm really interested in woodland
strawberry, which is fragaria vesca. So I'm going to narrow it down to the 37. And that all of them,
as we see here, are RNA sequences. So I'm going to pick one set here
that is relatively short and it's going to be transferred
in a short time. So lets look at this illumina sequencing
of floral transcriptomes woodland strawberries. It's produced with 2000 and
it has 15.5 million spots, that is 15.5 million bits, so
that's not that much data. Now clicking on this is going
to take me to a page that describes the particular
experiment in that sample. So the experiment number is SRX,
identify SRX 426518, we have some information about the run,
the number of reads, the number of bases and how much they
represent in downloads in binary. Followed by more information
about the project because a project might have multiple
samples and they usually do. The scope, or the goal of the project,
larger bio project, or experiments and so on. Also, what this tells us is that
these are single end weight. You only see one four here. And then we have in the table information
and links to the actual data. So let's click on this number here and
it brings us to a page that allows us to access various types of information about
this particular experiment and sample. At the surface on this tab there's
metadata, number of reads and so on. If we click on reads we are going to see
that there is going to be one entry for each read but
that's particularly the identifier and some information about where it came from,
the sequencing configuration. What we're mostly interested
in here is the download. And there are ways we can download this
information by clicking and dragging. But what I'm going to show you
will be a way to download this SRA data using command line utilities,
which I found to be much more useful. So first let's write down some
information which will come in handy. First of all, this experiment and
the sample identifier. SRR1107997. And then you see that these also
determined by the experiment, sample, and study identifiers,
which are listed here. And which normally is a good idea to
write on the piece of paper as well. Let's follow the link to information
on how to download SRA data. This takes us to a help page on NCBI with a variety of ways using [INAUDIBLE] and
so on. One command line utility that I've
found to be very, very useful is WGet. I have to find that. Here's one example, So Wget can be
typed from any UNIX type interface, and it will go and it will fetch,
it will download the data, from the Internet address that's listed here,
as the second common line argument. So I'm going to copy this,
I'm going to go to a terminal And I'm going to modify this slightly. So the benefits of the Wget comment
are that you can do the transfer remotely. It is convenient, it can happen
in the background while you're running other commands, and most
importantly because it deposits the data precisely in the directory where
you want it to be located. So we have some fixed string here. Then we have SRR followed by
the first three digits in the sample number which
was 110 which were 110 and SRR followed by the entire identifier and
digits, 1107997. This is the identifer
I've asked you to write down on a piece of paper, SRR1107997. And let's see what's happening. So you see that it connects to NCBI and
then it starts a transfer. And then we have a nice report port of
the progress on the left hand side. And it's going fairly fast. We're downloading 554 MB, of sequence, of data and almost there. So we're downloading the SRA5. And obviously the time will depend
on the speed of the download. So we save the file, but now let's
take a look a little bit so SRR, so, remember that head will
give us the top ten lines. And this is definitely not something
that we can understand, and definitely not what we expected. So in order to produce the appropriate
format, we have to run a new utility that's called fastq dump. Name of the file and
because I know it's going to take a while, I'm going to write it in the background. To do so, I'm going to start with
the comment NoHoc, which means No Hangup. That means, even if I'm going to
close my environment on my laptop, this is still going to run on the remote
terminal if I walk some place else. Followed by fastq-dump command and the SRA
file and I wish this to be happening in the background while I have access
to the shell for other commands. So I'm going to put an & at the end. So while command is being executed in
the background any errors, any problems, are reported, are being written to
automatically to the file nohow.out. Where, and in the meantime
I can write other comments. So, I've done this previously,
I know it takes a while, so I'm going to just show you the result,
the final result. And the output, actually this one
other head again, the top ten lines. And I've done this previously so
this is what the output looks like. So it's the identifier, the header line,
which contains the length, and so on. Now these were single [INAUDIBLE]. In case you have to
process pair then weights, then you need to use a command
line modifier, an option. And that would be fastq
dump dash sleep three.. But here's another way in which you can
usually see what the possible options are and use them accordingly. You can always type
the command line fast-dump and typically help with a dash dash,
and that can give you information about what other command like
parameters are available there. So in this particular case. The split-3 would split the SRA files into mate one and
mate two for paired end rates. So, as you can see,
we were able to retrieve sequences produced with the Sanger technology,
so maybe genes or genomic sequences. From the and I've also shown you
can download fast queue type data, next generation sequencing data. And this concludes this section. In the next section we'll
be looking at where and how we can download genomic features or
annotations."
"In this section,
we'll be looking at where and how we can retrieve information
about genomic features. And this can be gene allocations,
promoters, and so on. And the primary two places, I will
consider will be the UCSC Table Browser, that comes together with the Geno Browser,
and the Ensembi. And that will be
demonstrated the first one. So let's go to the UCSC website,
genome.ucsc.edu. And while we usually might be using
the Genome browser, this time we're going to go to the Table Browser
to identify and download the features. So let's see that we would like
to download a set of human genes. So we have a number of fields
here that we have to fill in. Mammal, we want human. We want to have the latest
version of the human genome. So that's December, 2013, hg38. We want the group genes and
gene predictions in this query. And Refgenes, as might see
there are a number of tracks or a number of data sets that all
relate to gene type of information. But were going to stick with refseq. Many of them,
most of them are human created sequences. So we can specify the entire genome, but
for the purposes of this demonstration, let's just specify a range or
rather, a chromosome. Chromosome 22, I'm picking it
because it's the shortest one. So it's relatively easy to download. We have a number of filters,
we won't be using this at this point. Output format. As you can see, there are a number of
output formats we can extract GPF. And we're also going to do it for BD, and then we want the five to be
returned to us as plain text. So let's get the output And you can see, we have the genes, and we have
the features, exons, coding sequencing. And so on, in the GTA format
that we already mentioned. So we can simply go to File > Save As. Save as text, we're going to
give it an informative name. So let's say RF Sig, and
we're going to say GTF.DAC, and we're going to save the graphic. Now, I'm goona go back and, by just changing this filter,
we can we can do BD back. So again, let's get in the output. And we have more information here. We want the whole gene so we're not
interested in all the additional features. But, you can evaluate that depending
on your particular problem. So push the button to get that data. Sometimes we have to wait. Here's the information in Bed format. Again, you might recognize this
as being multi-intervals or multi-axon records with
the number of blocks here. And the lengths of each blocks. And then finally, with the relative start position
of each block within the ten bank. So it's the same thing, File > Save As. We're going to save it as refSeek, And we're going to specify that it's BD and
save. So for the purposes of demonstration,
I'm going to show one other type of genomic features namely repeats,
arrow repeats in particular. So the genome is the same, human. The version is the same, ng38. Instead of genes and gene predictions,
now I'm going to to go to repeats. Keep repeat master here. There are a few other options. Positions, I'm interested in
chromosome 22 and it's the full length. And now, there are several classes
of repeats, so I'm going to select our repeats because those
are the only one's I'm interested in. So repeat name. I'm going to say that match is and
I'm going to put the star there for anything else that might come as a suffix. So let's submit this. More information on the filter. We can always edit the filter
using this button here. We want it as BED,
Browser Expendable Data. In a plain text, just so
we can look at it. And get the output. Again, we can ask for context information
or just the features themselves. And here they are. All the our repeats and their names. Chromosome, start, end, and so on. And we save this information just like
we saved the previous text files. So, I'm going to say that this. So this is how we can download the
features from the UCSC payment browser. You can also go to the ensemble website,
ensemble.org, and download the entire data
sites of our locations. But, we won't be covering
that in this presentation. So this concludes the section on how
we can retrieve sequences and features."
"We're going to now illustrate the use
of SAMtools, a package that was design by Hangley, to manipulate SAM formatted,
and BAM formatted files. We're going to start by looking at
the possible command line options. And modules implemented,
and then testing of view. So let's see what's in
the samples package. Samples 1. That will give us a listing. First of all, the usage is same
towards the type of comment. And we have a number of comments that
I have worked into the packages. And then a number of options,
that depend on the verse command. So as you can see here,
there are recommends for indexing both the alignment,
and the reference box 85. There a recommends for editing the files,
for instance, changing the header, updating the header, or
removing PCR duplicates. Which can be useful for
some operations, for some applications. Then operations on file
such as concatenate files merge, sort, and
convert a BAM to as FASTQ file. Another package or a suite of packages, for
extracting information about the files. For instance, the depth information
in position in the genome. The face header was on logs, and some simple statistics about the file,
about the alignments in the file. And for viewing and converting the file. So, we're going to start with a number of
these, particularly the flags that sort, index, and merge operations and
then, in the next session, we will be looking at the command
view which is more complicated. So, let's assume that we have,
for instance, a file example.bam, that's going to serve as the substrate for
our illustration. And the simplest operation, the simplest
question that we might have is, how many alignments does it contain? And we can do so, we can find it out so with Santours1 Flagstat and example.bam. And the output tells us
that there are roughly 2.4 million alignments in the file. That of those,
about 577,000 are secondary alignments. It tells us how many of those
alignments are alignments mapped? They can also be records that do
not correspond to an alignment, but rather just to the input fasting
sequence not in this case. How many of those are paired in sequences,
in sequencing, that is, they are properly paired
the way we defined earlier? How many week one alignments to we have,
how many week two? How many have themselves and
the mate mapped, the number of singletons? And then the number of alignments, for which the mate was mapped to
a different chromosome and among those, the number that had the mate
mapped to different chromosomes, and additional they had a mapping
quality greater than five. So, the unbreakable alignment those
just separate parentheses could be, good candidates to identify fusion
events or other types of translocations. So, that was the flag stat operation. Let's illustrate another operation,
that'll be the sort sends towards one the sort operation. Often times we may need to sort
the file for instance to index it. And then use it for the purposes of visualization, so
that one can quickly locate and can quickly extract the information
from a particular range in the genome. So send tools Sort. We can always type the comment,
SAMtools1 in the comment line, and then we can view the usage and
the particular options, and in most cases you probably
won't need most of the options. So SAMtools sort, we have the options and
then the input down file. We can compress it or not. But in most of the cases,
all we need to say is SAMtool1, sort, and then example.back. The sort operation is fairly extensive. Let's visualize that. It is a very expensive operation and
therefore, we would like to be able to
execute it in the background, while allowing other processes
to happen in the foreground. And therefore we can
test the other comment. So SAMtools, we can do so by running the comments SAMtool1 sort. And we want to sort the file example.bam,
and we want the prefix the output
to be example.sorted, and then to receive the extension value. To be able to run this in the background,
we have to specify no hangups. So that means,
that's to prevent any interruption from the current terminal
to be transmitted. And to kill the SAMtools1 process. So no hangup. Which will allow, the program to run
even if we close the current terminal. And then at the end, we want to say that it's going to take place in
the background so we put the index on. So this is going to be running. We have a process number, 20120. While in the meantime I will
illustrate some of the other commands. So let's look at SAMtool1 index. Actually that requires a sorted file, so we can try SAMtool merge,
while we're waiting for the output from the sorting algorithm. And for
this purpose I have two files NA128141. Okay, so the same tools sort
operation has finished. Maybe we can go back to that and index it. So, we can index the sorted file. Let's look at what
the command would look like. Clear, to make some room. SAMtools index, and that's very simple, so
we just have to specify the index file. Example.sorted.bam. And let's look at the files, and the most
recent file is example.sorted.bam.bai, which is the index file corresponding
to the example.sorted.bam file. So now, let's illustrate
the use of the merge command, which allows us to merge together
multiple alignment files. And to illustrate that I've
created two different bam files. NA12814_1.bam NA12814_2.bam and I also have the corresponding .fasq, but so we see how many sequences we have. We can do so with a zcat, so that it allows us get the content of
the file without unzipping the file. And we can that and
count the number of lines, using some of the basic Unix comments
that we showed in the first lecture. So there are 4,000 lines which
corresponds to 4 million lines, which corresponds to 1
million FastQ records. And we're going to have the same
number in the In the second file. So, let's run a samples merge first, samples merge without any arguments,
to show us the command line. And there are a number of options here. We shall specify, in it's simplest form, all that one is to specify
is SAMtools1 merge. Followed by the name of the output file. And followed by the two input files. So let's get going, SAMtools1 merge NA12814_1. Actually, let's put
the output into NA12814.BAM. Now we're giving it to input files. The first file, and then the second file. Then we're going to send it
in the background as well. In the meantime, we can look at the number of alignments
with the command samtools.flagstat. On each one of those files. So, the first file contains, 1.1 million alignments. You may recall that we had
1 million sequences, so there might be a number of sequences
that have multiple alignments. So then, running the common centers
one flagstad on the resulting file. Will tell us that we have 2.3 million,
which is basically just the sum of the numbers [INAUDIBLE] in those
two files, which is what we expected. So we've illustrated how we can use
the SAMtools flags, sort, index, and [INAUDIBLE] packages in order
to manipulate some formatted and bam formatted files. And next we will be talking about another
command, another package of SAMtools, which is View."
In this section we will be talking about the SAMtools command view which performs three different kinds of operations. The first one is to view alignment. To allow one to view alignment. The second one is to allow conversion between the BAM and the SAM format. And the third one is to allow extraction of alignments only within a range of the genome. So let's illustrate each one of these. The viewing operation. So if we just invoke SAMtools with the package with a command view. And we give it our example.bam file as input. So that's our file, that we are going to use to illustrate the operations. And we're typing that for more. We're going to see basically all the lines the alignment file in the bam file. So we're going to see the SAM format. So automatically, it converts in to a SAM format. But you might notice that there was no header information. So let's say that we wish to see the alignments and the header which would form the full SAM file. So we do so by adding the dash h lowercase. Let's see what we get. So indeed, we have the header line which specifies that the file is sorted by coordinates so this we do know. Then, it has one line for every sequence in the reference genome, one line for the program, followed by the actual alignment file. And this looks like a complete alignment file. So we are going to save this input file example.sam Now we will say that maybe under some circumstances we might only wish to see the header. Perhaps we can save it and we can we can prepend it to another file. So SAMtools view dash capital H example.bam will give us precisely the header of the file. So thats the viewing operation. A second type of function that SAMtools performs is the conversion and we've already seen that conversion from the BAM format to the SAM format. But how can you convert from SAM to BAM? So, we can always specify samtools1 with the name of the command, in order to obtain more information about the particular command line parameters for that command. So, just type in samtools1 view, it give us the general usage of samtools view options followed by the input bam file and then potentially by the region. Which we are going get to in our next session. If we wish even more information, more specific information. We can also type help. So in this file, I'm looking particularly at the SAM to BAM conversion. So we're going to use this particular line. We want to convert from the SAM format to the BAM format. So we need to say, samtools1, Am calling it samtools1 because I get multiple versions of the program and this is most recent. View dash b which means the output should be in binary. T which gives the reference, indicates there's going to be a reference file. Then the reference file which is in my genome file on the system, hg38, hg38c. And finally the BAM file to the SAM file, example.sam And we're going to send that in to a file. Thats example.sam.bam. So that we dont override the example of the bam. So that's a conversion operation. And to make sure that they're succeeding we're going to take a look at the file samtools view example.sam.bam. Or we could also run flag stats to make sure that we have the same number of records as in the original file. So, that was really the second type of function which was to convert from the BAM format and to SAM and conversely from the SAM format to the BAM format. And next I am going to illustrate how we can use SAMtools with the command view in order to extract alignments within a range. So let's say that we're interested in just looking at alignments on chromosome 22 between location 24 million and location 25 million. And how will we do that? We can actually do it two ways. So let me remind you of the command samtools1 view. You probably have noticed that we have sam tools view, options input bam. And then there's an optional parameter at the end that allows us to specify the region. So that's one way. But we can also specify especially if we have multiple search regions on the genome, we can also specify the input regions in a file in for instance in BED format. Dash L, so with the dash L only includes reads overlapping these BED file. which will contain intervals. So let's try both options. So in the first option, we just type samtools1 view, will give the alignment file example.bam and then the range chromosome 22, 24 million to 25 million. So, let's see what happens. So notice that 'm simplifying to use example.bam. Oh and it then tells me that my file has to be indexed. Now normally a file in order to be indexed, has to be sorted. But in this case if we're looking at our alignment file, samtools, view example.bam and put it only at the header line. We don't need more than that. You are going see that the file is already sorted by coordinates. So we can simply apply the index just like we have demonstrated in the previous section samtool1, index example.bam And this creating the file example.bam.bai And now we can proceed with our range extraction, samtools view example.bam and then we are giving it the range. Then now, we can actually apply the same set of parameters to specify the type of the output. In this case the output will be in the SAM format. So let's look at what it looks like. One option will be with head. So you will notice that this are alignments and the start position is following position 24 million and let's also use tail to look at the last lines and make sure that they are also within the range that we asked for. So indeed the start position for the last alignments in the file. All alignments being sorted by their coordinates. So the last one is 24 million, nine hundred seventy one and so on. So just a little bit shorter than 25 million boundary. So, this shows one of the algorithms which we can use samtools view to extract alignments within a range. And let's try the next one. For this purpose, I have created a file, that's example.bed. It contains just one line. You might recall from the BED format that it requires at least columns. The chromosome number, start position and then end position interval. And I only have one interval here but then we have multiple lines. So let's now perform the same operation, samtools1 view, dash Capital L which says, extract only alignments within a range. And the range is specified by the example.bed file and then we don't need this region in here. Then this would produce sam file. In the same way we can use head to look at the first 10 lines and look at the coordinates, its not shown me after the position 24 million But we are also going to look at the tail and the last alignment will stop just short of the 25 million boundary. So, this concludes the presentation of SAMtools in particular samtools view.
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
