---
template: blog-post
title: "Genomic Tools Module 3 Alignment & Sequence Variation "
slug: "Genomic_Tools_Module_3_Alignment_Sequence_Variation "
date: 2023-12-23 22:21
description: "Genomic Tools Module 3 Alignment & Sequence Variation "
---
"Welcome to the course, Command Line Tools
for Genomic Data Science. Today we'll be talking in lecture three
about Alignment and Sequence Variation. We'll start with the definition of
sequence variation, what it is, how it manifests itself, and
what are the consequences. Then we're going to look at
what is the work flow for determining sequence variations
in genomes and exomes. And lastly, we will conclude
that in the administration of relevant genomic tools for
alignment and for calling variants. So let's get started. Each individual's genome
sequence is unique. The differences in the DNA sequences of
individuals are ultimately responsible for differences in observable traits,
such as height or such as eye color, as well as for the hidden ones. For instance, susceptibility to a disease,
or how the cell functions. There are about 1% differences
between the genomes of humans and the genomes of chimps. And there's 0.1% differences between the
genomes of any two individuals, humans. But if you're thinking about it,
out of a three billion base sequence, that amounts to roughly three million
differences between any two individuals. Now there have been a number of
international projects, very large projects, that aim to sequence the genomes
of thousands of individuals and to create a map of all the sequence
variation along the human genome. And I should say those include HabMap and
The 1000 Genomes Project. But these projects capture most of
the sequence variation along the genome that are common to
a large number of people. Nevertheless, each person will still have
a relatively small number of variants that are going to be rare,
or relatively unique. And I should say at this point that
a variant that occurs in at least 1% of the population is called
the polymorphisms. So we will be looking at sequence
variation in this lecture. And by that, we mean relatively small
differences such as substitutions, insertions, or the relations,
either of one base, or maybe at a level of small
blocks up to a thousand bases. There can also be structural variance
that goes from about one kilobase to up to megabases of sequence, but
they will not be addressed here. So how do we identify sequence
variation in an individual? We start by taking a sample,
for instance a blood sample. Extracting the DNA, sequencing it
with an instrument such as Illumina, which will produce a large
number typically of reads. The reads are then mapped to the genome
using an alignment algorithm, and then the sequences are being analyzed. Essentially, at every
position in the genome, we're looking at all the reads that
line up above it, that align to it. And we're looking at the base that's
contained at that particular position. So if you're looking here on the left hand
side, you'll see that this individual has two alleles, an A allele, which is
the same as the reference, and a C allele. And by the way, the number of reads
that line up at the given position in the genome, give the so-called depth or
depth of coverage. Now it might be expensive to sequence
the genome from one end to the next, a procedure that is by shotgun sequencing. So, a procedure that we usually
refer to as whole genome shotgun. In most of the cases, we expect that
the variants that are going to be disease causing will be contained within genes. More specifically within the protein
holding portions of the genes. Therefore, one other strategy
would be to only sequence the DNA within the portions of
the genome that correspond to genes, and we call that whole exome
shotgun sequencing. In either case, the bioinformatics
workflow for handling and for detecting sequence variations would start
with alignment of reads to the genome, followed by what we call variant calling. In the following sections, people will
be looking at the genomic tools that are employed to detect sequence variation."
"We will start looking at the genomic tools
for alignment and for varying detection, and we will first look at the standard
best formats for files and data. So let's start with the alignment format
which I presented in the previous section, so I'm only going to go over it briefly. The standard for representing alignment of next generation
sequencing data is the SAM format. And if you look here, it consists of a header at the top
followed by a number of lines, each of which represents an alignment
of one read to the genome. In the header, we have some
information about the file, but it's sorted for instance and
by [INAUDIBLE] followed by a number of sequence lines that show us the sequences
that are present in the reference genome. And then lastly one line
that tells us the program in the command line options that
were used to create this file. And then we have as I've said,
one line for each alignment. And let's look at that more closely. It has a number of
columns separated by tabs where the first one gives
us the Read identifier. The second one is a FLAG that gives us
comprehensive information about this particular match and the mate,
if we have paired end reads. The location given by chromosome and
start position, mapping quality, and alignment stream that we call CIGAR, and then some information about
where the mate is matched. Whether it's on the same chromosome or
it's unmapped on a different chromosome, the main start position and the distance, the insert between the two lists
that's inferred from the alignment. These are followed by the query sequence,
and then by the base qualities for each of the bases, and
a number of optional fields that give us information about the alignment, such
as the edit distance to the reference, number of hits, whether this is
the primary alignment, strand and so on. So this is basically in
a nutshell the SAM format. Now I'd like to talk about one type
of format that is being used for representing variants, so
the SAMtools in the mpileup format. In the mpileup format, each line represents one position along
the genome at which we have reads aligned. And then we have a number of fields
that are again separated by caps. The first one gives us the chromosome
number, in this case chromosome 17. The second gives us the position that
we're looking at in one base coordinate. The third column tells us what
the letter is, what the base is, and their position in the genome. The fourth one gives us
the number of reads at the line, or the depth, at that position. The fifth column gives us a string
of characters that tell us something about the bases in each
of the 19 reads at their position. And we have a number of codes that
can represent the options here. So for instance, a dot is used to represent
a match in the forward direction. A comma is just to represent the match, however, the read must have
been inverse complemented. A capital T or capital A, or
in this case a C or a T for instance, would represent a mismatch where the read
aligns in the forward direction, and T in this case would be
the letter in the read. A lowercase t would mean a mismatch,
where t is a letter in the read, again. However, the read has to be
reverse complemented to match. There are characters to represent letters
that are at the beginning of a read, given that those positions are usually
lower quality than the rest of the read, and also to represent the end of the read,
and this is the dollar sign. In case there are insertions or
deletions, with respect to the reference, those can be marked by a plus or minus
sign, respectively, followed by a number, and then followed by the string that was
inserted and, respectively, deleted. And lastly, a greater than sign
represents a reference skip, so jumping over a portion of this sequence. Following the bases in the reads,
the sixth column gives the qualitities of those bases in the corresponding reads,
and lastly, an optional column gives us the specific position of that
particular letter in the read. So for instance, the first read had
a match on the fourth strand, and that occurred at position
74 within the read. Next we'll be taking about
another standard for representing a sequence variation,
WCF format."
"The VCF format or variant code format describes
information about sequence variation. It can also be compressed to
create BCF format to save space. Unlike the mpileup format,
which showed one line for every base in the genome at
which we had beats alike. The VCF format gives detailed information
about only those positions at which we mark variation, we identify variation. So as you can see here,
it is a fairly dense file that starts in a file
beginning with a preamble. We recognize the preamble because
every line starts with two # signs. And then at the beginning of the preamble,
we have some information about the format. So this here is VCFv4 version 2, about
the source, about the reference file, that is the genome file and perhaps
the URL where it was extracted from. And in sequence, it's chromosome,
scaffolds, or context sequences. This portion of the preamble is followed
by a set of so called info lines. Followed itself by a set of filter lines
that we're applied to produce the variant and a set of format lines. And then lastly, following this
information we have the header line and one line for each sequence variant. And I going to describe
each one of these shortly. So let's look at the lines here, and see what kind of information
we have in the VCF format. The first column is easy,
we have the chromosome. In this case, we have five new patients. We have five variants,
all of them on chromosome 20. The second column gives us
the position in the genome. The third column gives us an identifier, if one has been identified in database
such as dbSNP or maybe the 1000 Genomes. The fourth column gives us the letter
that's in the reference, or the variant that is present
in the reference genome. Whereas the next column
gives us the alternate. So the letter, the variation that
is present in the sequencing grid. We then have the quality
of the variant core. A filter, so that tells us whether
the sequence with the variant pass the filters or not, and
if it hasn't, why it has not. Followed by a column that gives us
information so that information about the beat that support the core
at the particular position. And then by format,
in Genotype information. The FORMAT column, gives us a template for how the genotype information will be
represented in one or multiple samples. You can find more
information about this and this particular example in the address
that I listed here, listed here. So let's look first at the INFO lines. In the info lines,
we have a definition of what the info, what the particular field it would be and
characteristics about that field. So, for instance, we have the field NS,
the number of sequences, which would be represented by
just one value of integer type. And which represents the number of
samples, that contain the data. Another example of the second one,
DP, again, is an integer value, just a single one. And the description is total depth,
and so on. All of these that you can see here, NS,
DP, AF, which stands for allele frequency. AA which stands for ancestral allele. DP for dbSNP membership, and
H2 [INAUDIBLE] HapMap2 membership. Along with a few others, represent
standard fields that are recognizable among different programs and
different file representations. However, one can define
new fields as well. Some examples that were shown here are,
for instance, for our variance NS = 3, so
we have three samples here. The depth is 14 reads, and
the other frequency is 0.5. Let's look at the third position, we have
that it is present in 2 samples, NS is 2. The total depth of reads there
at that position is 10, and you might recall from the previous slide,
that it has two possible variations. And their corresponding real
frequencies are 0.333 and 0.667 which optimal. So now, we presented the information
let's move on and describe the format. So as you might remember,
the format simply gives the template for representing genotype information. Just like before, we first define what
are the fields that belong to the format. So for instance here,
we have four different types of entities, which are coded GT, GQ, DP, and HQ. And just like before, every format line
tells us how many values we expect, what type of address, which can
be streamed, integer float, flag. And they give us some description
about what the field represent. For instance, GT stands for
Genotype, GQ for Genotype Quality, DP Read Depth,
and HQ for Haplotype. Just like we mentioned on the previous
slide about the info data, there are a number of standard fields but
others can be defined as well. And let's take a look at our example,
and we look at the format, and also at one of the samples, the NA00001. So the template here for the first SNP. Because that's why we have
a single nucleotide polymorphism, a substitution, is GT separated
by a column from GQ separated by another column from DP, and then from HQ. And if we're looking at the string that
corresponds to this format in the sample, we have that the 0 in real is
present in the two samples. We have that the quality is 48,
that there's only one read mapping. And then that haplotype, and
we need to have two values here, haplotype quality is 51 and 51, and so on. Now, let's take a look at the field
that describes the actual type of sequence variation. In the simplest case, this is a SNP or
a single nucleotide polymorphism. That's a case of a substitution when
the letter in the reference is modified, has a different variation
substituted in the sequencing reads. So let's assume that the reference here,
it has the sequence g c a G g t. And let's assume that the sequencing
read show the pattern g c a A g t, how would we represent this? We will have one line on which
we're showing first the chromosome, say chromosome 14. Followed by the position four, because G occurs at position
four in the reference sequence. Followed by a dot, because we don't have
this variant identified in the dbSNP or some. Followed by g which shows us the letter, the base in the reference genome,
the alternate of real is A. The quality is unknown, so we leave it as a dot, let's assume
that this variant pass the filter. And then the number of supporting read
is 100, so that was a simple example. Let's try another one,
a deletion from the reference. The reference stays the same, g c a G g t. And let's assume that the variant now,
shows the same sequence, except that the G at position
four is removed, g c a g t. But would show this as one line with the
first field, 14, as the chromosome number. We will mark that the change
notation starts at position three, there's, now,
no known identifier in the databases. The reference genome variant is AG, and
that becomes an A in the alternate. Notice that AG starts at position three. Then we have no information about
the quality, assume that the variant has passed the filter, and
the number of supporting reads is 100. And lastly, a more complex example in
which let's assume that we have three different alleles that may come
from multiple individuals. The reference genome is the same,
g c a G g t, the variant one shows a deletion
of G at the fourth position. Variant two shows a substitution,
a single nucleotide polymorphism, where G is replaced by A. Variant three shows an insertion of a t at that position, so how do we
represent all of these in one line? Well, we show the chromosome
at the end 14, we show that the mutation
starts at position 3. Again, no identifier given, that
the reference genome has the sequence AG. And this is replaced by A for
variant one, AA for variant two, and AGT for variant three. This variant pass the filter, and
the depth at that position was 100. So these are ways in which we can
represent sequence variation. Structure variance which are defined
as those variance that start somewhere between 1000 basis and a few mega basis,
can also be represented. But we will not be covering that here. So let's put this all together, and try to decode the entries in
the VCF file that I've shown you. So we have in column one,
the chromosome and all of these five variants
are located on chromosome 20. Then the position,
as explained on the previous slide. The identifier, and
you can see that we have two that had been previously identified and stored in dbSNP,
as well as a microsatellite. Then we have the reference allele,
and we have SNP for the first variance, SNP for the second. We have two possibilities for the
alternate allele for the third position, for the third variant, and so on. We have the qualities, the filter,
and we can see that all except for variant number two pass the filters. And various number two do not pass,
because there is no quality above 10. Then the input field, which gives us the number of samples
in which we can see the variant, the total read depth, and the haplotype
quality, as well as the other frequency. And lastly, the format, the template,
and then correspondingly, the little presentation the genotype, which we've
shown on one of the previous slides. So that's how we put it all together. In the next section, we'll be looking at
how we can actually use genomic tools for producing alignments,
naming both I and bwa. And then how we can analyze your
alignments with tools such SAMtools and BCFtools, in order to
produce variant costs."
"We'll start talking about genomic
tools for producing alignments, and we'll discuss Bowtie and BWA. Note that both of these
are very fast tools for mapping very large numbers of sequences,
and they do so by using a compressed
representation of the genome as an index. That is called either Burrows
winner index, or an FM index. So that at matching time, at mapping time,
each read is searched against the genome, against the genome index to
identify precise matches. And then, in a very fast way, and then more complex alignment algorithms
are used to create the entire map. And let me also mention that both
Bowtie and BWA are looking for contiguous matches that only have a small
number of insertions and deletions. So in this section we're going to
be looking at Bowtie, and in the next session we're
going to analyze BWA. In most of the cases, for instance,
if you're working with one of the model organisms such as for instance,
a human or mouse, you can go and you can download a copy of the genome
index, the Bowtie index from the Bowtie. Location of the source code. However let's assume you wish
to look at different organism or maybe you only want to map to
a strict number of regions. In that case the first step
would be to create an index and you can do so
with boat time two build connect. So let's type the command and
see what is the format. So the format says that it's bowtie2-build
followed by a number of options, which are obviously null,
followed by the reference fasta sequence, and then the prefix for the index. Including the full path. In general, you won't be needing
to use any of the options. So in our case, I'm going to
simply say bowtie2-build HPV or and I'm going to create it in the local
directory that I'm going to call HPV. So for that reason I'm going to
first create the directory HPV. So now bowl.2-build HPV_all.fasta, directory HPV, and then I'm going to to be also HPV. So let's look now, let's look at
the content of the directory HPV. And you see that there are a number
of files with the extension bz2, which collectively represent the genome
index for this new Genome or rather, separate genomes. Now assume that we have an index given,
and I'm going to be doing my next example using that human genome index or
that we've all ready created one. The next step is to actually
map reads to the genome. So I've selected here a subset of
an Exome data data set, a very small set. Exome.fastq. So let's see how many sequences they are. You might recall that was wc -l 40000 and
four lines per record. That means 10,000 reads. And now I'd like to map it. Again, we would like to see what are the
common line options that we can use. But if I just type it's a very,
very long message. So I'd like to save this to be directed, to redirect the [INAUDIBLE],
and put it in the farthest. So let's look briefly at
what your options are. First of all, the usage is BOWtie2,
a number of options listed below. The index, the preface to the index. Then, if we have pair of [INAUDIBLE],
we have to specify the file separately. If we have unpaired single end
then they can specify with -U. And lastly, the format for the alignment. -S to produce sound formatting alignment. And if you're looking
at the set of options, We have some information about the input, how which to specify the base
qualities in the system, your system. Then important,
we can specify whether we want alignments to go from one end of
the read to the other end. So those are global alignments. Or, what I can also produce, local alignments that only match
a portion of the input read. There's some information
about string UCFE alignment. You can modify the number of
mismatches in the scene and so on. Some parameters that
control the scoring scheme, generally you shouldn't
need to touch these. And then options for reporting for
specifying the insert, the minimum insert length, and maximum,
and defaults are usually sufficient. And lastly for the output. So let's try to run bow tie to align
the exon beats to the human genome. We'll do that with bow
tie too We want four grades to make the process run faster. We specify the location of the genome and I'm going to give the location of the
human genome index on my system, data1. For by the actual fos queue reads, and we want the output to be
specified in sand format. So exon.bd2. And we wait a bit. And we obtain a summary of the alignment. We have 10,000 reads,
all of which were unpaired. We had 1.11%,
111 that did not align at all. We had 78% that aligned exactly one time. And we had 20.59% that
aligned more than one time. So let's take a look at
xsom.bt2.sam format file. And you see,
we have the sequences here, and then followed by one line for each match. And obviously, we could transform these
into a format with, samtools_view, just as we have shown in
a previous section, -bt Data1. The reference fasta fi for the genome. We need to hg38. And we can move that to exome.bt2.bam. And now we can verify that we
have the same information and that the file has been
written with Samtools U. [SOUND] So now let's look a little
bit at the difference between using the option versus
the end to end option. The end to end option was the default and
that's why we were in the previous one. So let's run the command again. And let's file it with. So here, we give the option local,
let's see what we obtain. And you'll see that we have more sequences
that align more than one time and fewer sequences that
align exactly one time. Because you can find more matches
[INAUDIBLE] partial matches for every [INAUDIBLE]. So that's how we can use
Bowtie to map reads, exome or whole-genome shotgun sequencing
reads to the genome. Next, we will be looking at
BWA in the following section."
"In this section, we will illustrate how
we can use BWA to create alignments. So, the same as before,
if we have a new genome, for which we need to create an index. We can do so with one of the BWA commands. So lets try BWA, and
to see which are the options. So it has a number of
commands that can be used, index, mem, aln, bwasw and so on. And there's some information at the bottom
that tells us that you at first, need to index the genome. Then you can use one of the three
possible alignment algorithms and so on. So let's go back to our HPV or
the file which contains a collection of human papillomavirus genomes, and
let's try to create an index for that. We would do so with BWA index, and followed by HPV on. And it's that simple. And now we have a number of files that
were created that contain the index. Now lets try to map the reads and there are three options for alignment but the one that is the most
applicable is BWA mem. To see what the command line
options are for BWA mem, we simply have to type this BWA mem and
again that is fairly long. So I'm going to save
the output into bwa.log. So I can look at it with my text editor. So we're looking at this. So the format, the usage is bwa,
followed by mem for the command line. A number of options listed below. The index base which is
the reference past this sequence. And lastly, the first two reads. So if you're looking at the algorithm
option, just as before, we have the number of threads with -d. Some information about the alignment
that can be changed minimum seed length, look for internal seeds, and so on. Some scoring option for
substitutions in Dells, and so on. Some information about input,
output, and so on. But in the vast majority of the cases, just using BWA with the default
parameter is going to do the job. So now, to map the exome
reads to the human genome, I'm simply going to type,
bwa mem to do the alignment. I'm going to use four
threads to make this faster, I have an index on my system
which I shall be using. Okay, and then the fastq. And within a safety output, which would be in same format,
in exome.bwa.san. So now that we have the san file, we can look within more exome.bwa.san, just like we've done before. And we have the genome sequences
here in one alignment for each read, or line for each read. And just as before,
we can very simply descend towards view with the fastest sequence
of the reference genome. To transform this, to convert this file
into a bam file for further analysis. And now santools view, And this will show us the information. And that concludes this section. Next we're going to be looking
at tools for varying points."
Next, let's look at the suite of tools to perform variant calling. The first one is sent tools with it's option mpileup. We've already looked at a number of command line options and a number of commands for samtools, but this is different. So the samtools mpileup command creates at every base in the genome which we have a line reads, a tally of the information that is present reads at that position. And it optionally also calculates a genotype likelihood which can be used by other tools further down the pipeline in order to produce the actual variant calls. The format for the output file is usually the specific mpileup output. However, it can also produce VCF and BCF format. So let's take a quick look. I'm gonna say samtools and i'll say samtools1, because I have multiple versions on my system, this are most recent mpileup and just like before I would like to look at the options, so I'm gonna just save them in a log file for easy viewing. So you can see that the comment is samtools mpileup, a number of options then the BAM file and bump to BAM file if that's the case. There are a number of options for the input, for instance the system for representing qualities, whether a long list of repairs should be discarded or not and so on, whether we should be looking at the entire genome or maybe only within a region or a set of regions, this file here. Then there are output options. And here's one important set, actually of important options -g will produce a BCF format, and it invokes the procedure for calculating the genotype likelihoods. The same for -v, but the output will be in VCF format. Each of these can be further compressed gzip. The -O option allows us to see the output based positions on reads, this corresponds to the last column that we have on the format slide, and lastly, there are a number of parameters that can be used to control the calculation of the genotype likelihoods. And one option that I would be using here -f for specifying the fast day reference file for the genome. I have a file here, sample.bam. We can visualize it with samtools view. And we can get how many alignments it contains. samtoolsfax.sample.bam to apply some of the commands that we've learned in the previous lecture. So then it could be small, small number, and now let's use samtools to produce a pileup format to start with samtools mpileup -f and we're specifying the reference genome and in this case is hg19, dot fa. And then lastly the bamfile. And I should make one observation- the file needs to be sorted in index, so let's see what we get. So I couldn't open the FASTA index. Typically, we need to sort the file, however this is file is already sorted, so all we need to do is to do samtools index sample.bam, and this will create a sample.bam.bai.index file. So now let's repeat that operation. And I couldn't find the fa file, because the extension was fast a, sorry. So now as you see that went by quite fast, so I'm going to capture that output into sample.mpileup. And we can do more on this file sample.mpileup. And you'll recognize the output that I showed you earlier. So these are all matches to chromosome 17. This is the positioning the genome, every position on which they are aligned is listed there, the reference genome letter. And then we have information about the number of reads, followed by information about the letters in those reads, where dots represent a match and then the qualities. So that's the amount of information that we have in this mpileup format. However often times, and actually, usually in order to produce variant coarse with the tools such as vcf tools or maybe jdk. One we need to use the vcf format or maybe the bcf format, and for that we give the option, let's try -v -u for vcf, -v says, "this u", -u says, "i'll compress" and were going to save that into a vcf file. More sample.vcf, and you can see so there is a sequence for every counting, then you'll recognise the info lines, the format lines and then, every base here had shown as one line. And if I wanted to produce vcf format, then we would really just have to put a g here. So that is a compress simple.vcf format. So let me show you sample.vcf. Okay, so that's it. So this concludes the section on samtools and mpileup. Next we'll be talking about how we can make variant calls with bcf tools.
"Next, we will be looking at the tool for
variant calling, namely bcftools. bcftools usually operates
on the output from the tool and up program and
uses that information to make a call as to whether assembly position
contains a little variation or not. So let's look at bcftools package and
again I'm going to use bcftools one, because I have multiple ones on
the system and these the most recent one. So bcftools common argument
that's the usage line. And just like SAMtools,
this is a suite of packages for manipulating VCF files including for
variant coding. And this one include operations for
indexing, for manipulating vcf and bcf files Reheader. An important one that we're going
to look at more closely is view. And then we also have
the very important part, the VCF/BCF analysis, and
particularly the call function. So we'll be looking to start with,
in the view command and the call command. To obtain more information
about view comment, we simply type just like
before bcftools one view. And this gives us the option for
this particular package. There are a number of, so if you're
looking at the usage its BCF tools view a number of options,
a VCF which can be compressed or not and then a number of regions from which to
do analysis only on a restricted region. There are a number of options that are in
common to all of the BCF tools and most of them are listed
here in the beginning. They refer to the input and output. For instance the output file
the type of the output and therefore options here, Bis for
compressed BCF, U is for uncompressed BCF, Z is for compressed VCF,
and V for uncompressed VCF. So that's fairly important then dash r can
specify the regions from the command and the dash capital R can allow the program
to read the regions from a file. And so on. So let's try one more example, the view, the bcftools is used to convert from
one format to another primarily. So in this scale you might recall
that we have the sample BCF file. And we would like to see what's inside,
because as you might remember, it is all in binary. So let's just bcftools1. View sample.bcf. And that transforms it into a form of CFR. You will see the quantity information so
that's for every genomic sequence,
then followed by an odd information, a presentation for
the allele or alternate allele. A set of info lines. A format line and then one line for every position in the genome for
which we have reads. Recall this was produced by empire so that's how we can use view
in a very simple way. The second package from
the VCF 2 suite that we are interested in is
the actual genotype quantum pack. Package so that bcftools1 call. And let's look at the common
like options for this package. Call.log So we're using just bcftools call,
a number of options, followed by the bcf file
in compressed form or not. And again, we have a number of
options that refer to the input and output and which I mentioned
are common to all the bcftool packages. Some additional ones here, and then some options we learned in
the variant column algorithm. So one can specify one of two algorithms,
a -c, the consensus caller. However, this method is now obsolete. And the other one is -m for
multi [INAUDIBLE] and rare variant column. And this one is currently being used
in most practical applications. So let's try now,
using the [INAUDIBLE] output. With information on every location in
the genome within lien base, and looking at that information and the summary to
make variant calls using bcftools1. We're going to save bcftools1,
with the option core. And then we have a number of comments
like parameters, dash v would say then we should only write the license
corresponding to fairness, dash m which says let's use the mortgage in any corner,
the the mortgage and version. Dash o which says use these formula for the output, so l am going to use Z for bcf compressed, dash o to lower case to specify that the output should be put into sample.vcf.gzz and lastly sample.bcf. So that is the output that
we produce from the package. So now we can look at a sample,
the vcf.gz, and we can do so
without having to unzip the file, so we can do it with z cap sample vcf.gz. And use information, so we have the preamble with information
about the reference genome. We have the ALT template
specifying the alternate alleles. The informants, which gives information
about the algorithms that were used for variant coding. The format lines again,
scores reproduced in variant coding. And then lastly we have one line for
every variant that has been called. And if you're counting here you are going
to see that there are eight variants so. Let me just do these. Just saying wrap dash v. So we're going to move all the lines
that start with a double pound sign. And we're going to see, actually just a pound sign to remove the header as
well and that's how many variants. And that's eight. Then we have represented here. Most of these are substitutions of snips,
T to C, C to G, and so on. But then, we also have a deletion here and
the more complex substitution. Then, you can see the qualities,
no information about the filter, and then information about the depth 36 bs for the
first variant, 22, 3, 1, 101 and so on. So this concludes our demonstration on how to use bcftools to
produce variant cause. And next we are going to show
how to put this together so that way we have a pipeline for a very
simple pipeline for variant calling from a"
"In this section, we're going to
show how to put it all together and to write the various simple
application for doing variant calling. Let's start with our sample, load file. The first operation was to sort and index
the file, and this file is already sorted. So I'm going to use same
tools index sample.ban. Which creates an index
file sample.ban.bak. In the next step, I will use CentOS
one with the empire op module, in order to create a BCF file. That has one line for every position in
the genome that contains a line read. And that also has genotypes likelihood
that are going to be used by. So that was a long sentence,
let's make it short. One, and I map. We want to have genotype likelihood values
-g, the output would be nbcf, or map. The reference sequence is the one
that we used earlier on the system. Gino's a human HG19, last name, Sample dot down. And we want this to be output
into a compressed BCF file. Now we will be using BCF tools
on the sample dot BCF file. To call variance. bcftools1, with the comment call, -v to report variance only. -m for the multiallelic core. -O, we want the output to be
specified in compressed VCF format. -o, we want the output to
go into VCF sample.vcf.gz. And then finally, the input file will be sample.bcf. And this produces the sample.vcf.gz file. Which, as we've shown, has a variance. Now, next one can perform
a number of field tests, which I'm not going to demonstrate here. And or one might want to
visually inspect the quality and number of alignments at
one particular position. So let's look at this variant here,
which is a more complex variant. And position 7579643. And we can visualize that with same tools, 1 keyview. Let's look at the command line options for
these. Okay. We can give you the position. So on chromosome 17, at the position 75796 and let's say it's 00. So that we have a little bit of context. And then Sample.ban. -dT. And with -dT we're selecting
the display to be simple text, and lastly we have to specify
the fasta sequence for the genome and
that's again the long swing. Ign/prev. So the text file, we can save this
into a file or we can pop it. And you'll see, here,
the location of completion. We can view these,
we see this as the HTML. Or we can see them in the terminal,
without deploying that. There it is. So the location of the 7579641 is here
at this location and then as you might recall, the variant started collision
at 7579643 so, and each location here. And so on, So this concludes our demonstration
on how we can use alignment tools, and then the combination of SAMtools and BCFtools in order to produce
varying costs from sequencing data. Or the shotgun data from. Or exome sequencing beta. And that concludes this section and
this lecture."
