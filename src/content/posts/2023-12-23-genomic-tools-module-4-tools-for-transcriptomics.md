---
template: blog-post
title: Genomic Tools Module 4 Tools for Transcriptomics
slug: genomic_4
date: 2023-12-24 04:07
description: Genomic Tools Module 4 Tools for Transcriptomics
---
"Welcome to Command Line Tools for
Genomic Data Science. Today, we'll be talking about Tools for Transcriptomics as part
of lecture number four. Well, we'll start with a brief overview
of the molecular biology concepts, primarily talk about genes and
transcripts, then represent the standard workflow for
a transcript [INAUDIBLE] analysis. And lastly, we will do a hands on analysis
using basic command line tools of transcript [INAUDIBLE] data. So let's get started. They occupy a specific location with an initial point, an initiator and an ending point. When one of the two strands of DNA and
they have a very specific organization. They are formed of informative
blocks between core exons and interspersed with uninformative
blocks which we call introns. Now where they are located,
where they are housed in the genome. Genes also take a body of their own and
they do so during the process of gene expression or
saying that the gene is expressed. The process of gene expression is complex
and it starts with transcription. During which an polymerase
creates a copy of the gene. Nucleotide by nucleotide from the
beginning to the end is a single stranded RNA molecule, we call this as pre-mRNA. This contains the information
the exons interferes with the introns. This molecules still located in the
nucleus is highly unstable and it suffers a number of modifications to stabilize
it before it gets to the next step. There is first capping
at the five prime end, then the cleavage of the 3 prime end and
addition of a long poly(A) tail. But perhaps, the most important for
our work today is the process of splicing. During splicing, exons are being splice,
are being adjoined together and introns are being spliced out and the result
is a so-called messenger RNA molecule. Messenger RNA now travels
from the nucleus into the cytoplasm where it is later
translated into a protein. So overall,
this is called gene expression. As you can see here, we have one gene and one mRNA with three axons and
these form one protein. However, under different circumstances,
for instance, in different tissues or different conditions of
diseased versus healthy tissue, we might have the different combinations
of the genes exons might be used to form the messenger RNA. We also call the messenger
RNAs transcripts. So in this particular case at the bottom,
you'll see a messenger RNA that only contains exons one and
three, exon two escaped. We call the process of exon escaping and
the process by which a gene can express different combination
of exons alternative splicing. So we have genes and each gene can
produce multiple splice variance, multiple transcripts or
so-called isoforms. And we would be using this terms,
isoforms, splice, variance and transcripts interchangeably
throughout today's presentation. The examples that I've shown
you is a very simple one. It's the case in which one
exon can be present or can be excluded from the messenger RNA. What I'm showing you here is a much more
complicated example at the BRCA1 gene. You will see a view from
the UCSC browser and on the line you see a representation
of a different transcript of this gene. The vertical bars are used
to represent exons, whereas the horizontal bars or
lines that connect them are introns. Obviously, introns are much
larger than exons. What you see here is that every
transcript represents a different combination of exon. For instance, you will see that
the transcript that this exon, exon number eight appears in only one
transcript, the third one from the bottom. You also see that the transcript at the
very bottom skips a large number of exons. Exon two, three, four and
all the way through to the last one. So there is a large
variety of transcripts and to look at how daunting alternative
splicing is consider that 90% of the human genes are alternatively
spliced to form two or more isoforms up to potentially thousands. Many of the aberrant isoforms has
been associated with diseases. So determining the repertoire genes and
determining the repertoires of isoforms in general species order under particular
cellular condition is very important. Let's look at the very high level state
of the cell in the content of the cell. At any given time,
there is one copy of the genome and then both in the nucleus and in
the cytoplasm, we'll have multiple genes being expressed, each genes would
potentially multiple copies of mRNA's and with multiple possible
transcript variants. So any biological or clinical analysis, we
try to interrogate the status of the sell, particular the status of the transcripto
by asking the following questions. What genes are expressed in the sample? What transcripts are expressed for
every gene? Then for each gene,
how many copies of the gene do we have? And how many copies of
each type of transcript? And lastly, assuming that the analysis
is trying to compare disease versus healthy tissue or any other two different
conditions, how do the expression levels and splicing patterns
differ between the two conditions? So these are the questions that
are being tackled by typical RNAC or analysis and
we're going to be looking at that next."
"A transcriptomic analysis would
survey the state of the transcript done within a particular cell and it would
try to answer the following questions. First, what are the genes that
are expressing in the sample? And for every gene,
what are its transcript variants? We call that assembly. Then, what are the expression levels
of the genes and of the transcripts? We call that quantification. And lastly, we might want to perform
a differential analysis looking at how do expression levels and splicing patterns
differ between two particular conditions? Say healthy versus disease tissue. So let me walk you through
a typical work flow for a transcriptomic or
so-called RNA-seq analysis. RNA-seq because this refers to analyzing
next generation sequencing data of similar RNA. It starts with the RNA-seq
experiments that generates reads as we described
a couple of lectures ago. Then the short reads that are typically
between 50 and 250 base pairs long, are being mapped to the genome, or
using another word, aligned to the genome. Then, their alignments,
the realignments on the genome are being clustered in gene-oriented groups
to form a basic structure for the gene and for these transcripts. In the following step,
a number of transcripts are being read or decoded from the structure and quantified,
meaning rates are being assigned to them. And lastly, if we have two or
multiple conditions and possibly with multiple replicas,
then the analysis would continue with a differential
analysis at the expression level or at the splicing level
between the two conditions. What I'm showing you
here is two conditions, test versus control,
each one of them with three replicates. A crucial step in this analysis is the
part that assembles the transcripts and then quantifies them. So I'm going to spend a little
bit more time explaining those. What you see here on the left hand
side is the computational process that creates a representation of
a gene and its splice variants. So we start with an RNA molecule,
shown at the top. You see it organizes in an RNA, and
as it's exons locations along the genome, and, the portions that are alternatively
spliced are shown in red. So, you see here that we have an exon
skipping event, exon two escaped, that is included in some transcripts,
and excluded from others, and we also have another event
that we call intron rotation. That particular intron is sometimes
included in the exon, sometimes not. Once the RNA molecule is sequenced,
then we have a number of reads, which we show underneath. The reads are being mapped to the genome. If a read falls right inside,
entirely inside an exon, then it's going to be aligned
as a contiguous fragment. However, if the read spans the boundary
between two different exons, it's going to have to be spliced. So we talked already
about spliced alignments. Now this type of information when
seen along the genome give us two particular types of clues that
can inform transcript assemblers in gene-finding methods as to how they can
build the most likely gene structure. The first type of information comes
from the bulk of the alignments. Because the rates that are coming
along the exons means that when viewed along the genome the
alignments are going to cluster in columns at the location of the exons. So the bulk of the alignments
are going to tell us roughly where the exons are located. The other type of information
comes from the splice reads, and they are going to give us
information about the introns. The introns connecting the exons. So that's what you see in the next two
pictures, the levels of the reads along the genome, and the splice junctions that
can be obtained from the splice reads. The next stage of transcript
assembly methods typically creates a graph representation
that combines the gene and the transcript together
into a compact form. There are a variety of graph
representations, overlap graph, exon graph, sub exon graph,
connectivity graph. But the one that you have shown
here is a very simple exon graph. Let me put it simply. Exons are represented
as nodes in the graph, and you see them here represented
with bars, red or blue. And then we connect two exons or two nodes by an edge if there
is an intron that connects them. So that's what we see here. Now we can reverse the graph from
a node that has no incoming edge all the way to the end to the node
that has no outgoing edge, and we can obtain all the possible splice
variants or transfers for the gene. See, if you're looking at our example,
we can have four possible splice variants. So the splice graph and other graph
representations present information and collect information about the gene and
splice variants in a compact form. However, the information that they encode
might be much more than what we need, because oftentimes, the number of splice
variants that are encoding in the graph far exceeds the number of
truth splice variants. So a very challenging
question is how do we identify the most likely splice
variants the guiding coded in the graph based on the information
that we have from reads? So what we see here on the right hand side
is how this process is being addressed. We start, let's say,
by enumerating all splice variants and in this case we had four, and
then by assigning reads back to them, using usually some
sophisticated algorithm. Let's say it can be expectation
maximization, or a linear program. Once we identify what it is that we
transcript, we can calculate and expression level for the transcript,
and then we select the top variants as being the most likely to be
expressed in that particular sample. So there it is, the two stage process, the graph representation, followed by
transcript selection and quantification. So that's the transcript assembly. Now let's look at the entire workflow, and I will point out along the way
what are some of the tools, the basic command line tools,
that can be used to perform a restage. So we start by mapping the reads
to the genome, and we can do so with the tools such as Tophat, STAR or
Hisat, for example, but there are others. The next stage is to
take this alignments and assemble the realignments
into transcripts, using the transcript assembler,
such as Cufflinks, CLASS or iReckon. In the third stage, we would reconcile
transcripts across multiple samples in case we have multiple samples,
and it is necessary because there might not be enough reads in every
sample to assemble the transcript fully. And then we would like to know for each
fragment, what transcript it comes from. So lastly, once we have a unified
reference for what transcripts are being expressed in a set of samples,
we can quantify the isoform expression and we can finally perform a differential
analysis among the samples. And this can be done with a tool such as
Cuffdiff or the more recent Ballgown. So in the next sections, I will illustrate how we can use
representative tools from this week. In particular,
I will focus on the Tuxedo Suite, shown here with the stock Tophat,
Cufflinks, Cuffmerge and Cuffdiff."
"We will start our transcriptomic
analysis with the first tool, Top Hat. Top Hat is being used to align reads
against a general reference genome, allowing for spliced alignments. And in doing so, we will illustrate with
a data set, which I'm going to show you. The dataset that consists
of three replicates, each for the dataset and for a test. Let's call it the disease dataset. Each one of them,
each one of these samples consists of and. Let's see how long. Zcat Data/Ctrl1_1.fastq.gz. And let's look only at the top ten line. So these are fairly short ones. They are 48 base pairs long. So we have two conditions,
we have two replicates each. They are then. And we will have to
align them with Top Hat. So first,
let's see what are the options, and what is the command line usage for
Top Hat. And we do so, just like we done
during the previous lecture. So we'll run Top Hat and
we'll store the output into a log file. So we can view it. Okay. As you can see here, so the basic idea is
you use Top Hat followed by a number of options followed by a bowtie index just
as we used with bowtie and the reset. Resets for my number one, for
my number two, and so on. Some of these options that one might
find relevant are options related to, for instance, minimum length, maximum
length, minimum length of an anchor. So they refer to the alignment. Then useful options,
particularly useful, are for instance the number of threads by default,
Top Hat is single threaded. So if you want to spit
out the calculation, we're going to use multiple threads. Then we can keep it a transcript on index,
with- g gtf. Is if annotations as well as the index. As if if spurs junctions to help guide the
discovery of additional splice junctions, and then if we have information
about the insert distance. The distance between the mate pairs, and we can provide that for
increased specificity as well. So- R is the average N of
distance between mates, and then we can specify
the standard deviation as well. In general,
the defaults are fairly well suited. And then some options for finding supply junctions and so on. So there's a fairly large set of options. However, in general,
we only need a few because most of these options have already been calibrated for
the best performance. So let's see what we can remember. So I'm going to say head tophat.log. We would like to align
selection you are near. And let's try to do that for this one. We would have to write tophat, or tophat2. A number of options, let's say p 10. Then maybe we would like to write
a directory, an output directory and let's say that we would like
Test1.tophat is just the name. Then the [INAUDIBLE]
index, /Data1/ign2 and so on. And as you can see,
it's very easy to get lost in the details, especially when we start putting the read
files and we have to write the full task. So, an alternative to just type in
the comment from the comment line is to create a batch file,
a very simple shell script. So, let me show you how you can do that. So let's type something
that's called com.tophat, so it'll load ShowScript, and
we would like to write a comment here. So, first of all,
let's create the output directory. Make Directory. We would like to create a directory that's called, let's say test bot. First of all,
let me show you where we are. We're in Coursera which is data and results, a little bit of cheating there. And then,
I'm going to make a directory top hat. Okay, and that's where I'm
going to put the results for each of the six samples, separately,
in a separate directory. Okay. So we're going to make this directory This one on the top Help. And now we'll record tophot2. And make the directory -b, in case it
already exists, then we make it again. Then, the output directory would be this directory Okay. We would like ten threads to
make this multi-threading. Let's say that we want
the maximum number of kids. Four max. Okay? Let's say that the number
ten by default it is 40. We can split the line
if it becomes too long. We want to give it an annotation file. And then remember that Okay. data1/gn3 These are fairly long file as you can see. So that's the annotation. We also have to provide an index. [INAUDIBLE]
index. And that comes from the same location. Okay. As you can tell, it is very tedious
to just write these things down, to type them down. If we know the information
about the inner mate distance, the average, let's put it here. Let's say that it's 120. And the next standard deviation. Let's say that that's 30, but
these are generally not needed. Okay? We have to give the Bowtie index. data1 and I remember this one igm3. Okay, and lastly,
we're going to give the data sets, Okay? And this going to be test1_1.fastq.gz,
and the second file. So then we're going to take a look at
this, and see how we can improve it. How we can make it easier."
"So we're saying create another
directory for sample test one. So there's going to be under the Tophat
directory and we're getting the full path. So we can run this transcript
from anywhere on our file system. And then we're running
the command tophat2. We're saying put the output. In this directory, Test1. Run ten threads. Report at most ten results for each read. Use the information, the genome and
transfer allocations in this data file. And with transcript of index. To inform your alignment process. Use this information, if available,
about the distance between mate. Use this bolder index. And by the way, if a bolder index
is not ready on the system, then you can create one
using bolder by build. Just like I've shown you last time. And lastly, these are the two files
containing reads, mate one and mate two. So this is fairly long, and
we can make this a little bit easier. So first of all, let's observe
that we have a base directory. Which is data1 igm to my name,
or Sara L4, Okay? And, from those we can
create a data directory. We can name a data directory,
and a working directory. So, data directory, for instance, is a name that we're giving to
the directory that contains our data. So, this data1 for Sara. And I just found a mistake now,
so it should be in data. Okay, so now I can simply go and replace the string here with $DATADIR. And the same thing for the second file. So that was simple. The other name that is being typed multiple times here,
is the working directory. So let's see that again. Working directory. So it's data one and so
on all the way to top hat. Now we can simply replace the string here with work directory. Tophat test one. And now, we can write work directory,
test one. Finally we can also give
the information about the annotation. So we can replace all of
these with just a node. And the same for the transcript index. And lastly, we can do so for
the bowtie index as well. That's back in bowtie, too. So there's a much easier way of
representing the amount of information. And it also ensures that any changes
are going to be encapsulated at the top. So any change we need to make,
we can make in the datasets at the top. And once we have this file,
all we need to do is to say, sh com.tophat. We put nohup at the beginning because we
don't want the process to be interrupted once we log out. Where this is being done remotely. And we can save whatever errors,
we do com.tophat.log. And we can put that in the background. So we wrote a very simple shell script
that could show us how we can run TopHat. I'm not going to do that. And as I told you,
I'm going to cheat a little bit. Because all of the data files that
I've selected are fairly large. They have about 120 million reads each. So instead I'm going to go and
show you what the result looks like. So the output for
Test1 will look as follows. In the directory Test1,
we have a number of files. We have. The primary alignment part
is accepted_hits.bam and you might recall that we can use
santools viewer to look at the content. So the sequences are fairly short for
the basis one. And then we have a file,
a bed file showing the deletions, insertions, junctions. These are are displayed junctions. You might record the bed format. Of the unmapped, which should one
be interesting performing any further operations, filtering,
screening, and so on. And then, a summary file that tells us, that gives us basic information
about the mapping base, and so on. So for instance,
this tells us that of all the left reads. Of the 16,586,968 input weights. Left weights, or make one. 96% of them could be mapped. And that those 11.7%
have not pull alignment. Of which 359,000 had
more than ten alignments, and would not have been reported. Similar values are being reported for
the right reads. So for made number 2, 94% mapping rate. For an overall mapping rate of 95%. So we have this many aligned pairs. Of which 6.5 roughly, millon. Or 11.6% have multiple alignments. And some other,
5% on this concordant alignment. So the concurrent alignment rate,
in which the mates are mapped in the correct orientation,
and at a proper distance. Is 87.6%, which is a fairly high rate. So we can obtain, for instance, we can
very easily grep for the information. For the overall read mapping rate,
in the other files as well. To see if we have similarly mapped Levels. So we have six directories
containing this type of information. Add this in a line summary. .txt. And you can see that all of
them have very high rates. Between 89%, between 9.5% and 97%. So these are the bam files containing
read alignments that will be used in the final stage. To perform transcript assembly. So this concludes our illustration
on how to use command line tools for transcript commits. And we're also at the end of our
course on command line tools for genomic data science. Thanks for joining me,
and happy computing."
"Once bits are aligned to the genome, the next step is to assemble
them into transcripts. And for that purpose,
we'll illustrate how we can use Cufflinks. So go back to our dataset. And we have alignments in
a directory called Tophat. And now we want to run Cufflinks. Cufflinks uses an overlap graph, in order
to represent in a compact way, a gene. And then it finds the minimum number of
pass through, through the overlap graph, that can explain all the weights,
or rather all the splicing paths. So that's, in a nutshell, the algorithm. Now let's see how we can use it. Again, I'm going to just call Cufflinks. To see the command line usage. All of this tools have fairly
complicated command line arguments, and that's why like them in a file, and
you can do so too, cufflinks.log. Okay, so just like before,
we need to create a directory ideally for
the output to be placed in. So we're calling Cufflinks,
a list of options, and then the list of alignments,
read alignments, the BAM file. Okay.
So we have to create a directory for the output. We can specify the number of threads. We can give it a reference, but
then it couldn't perform an assembly. Some information about
the inner mate distance. But again, this is not necessary,
it can be estimated from the input read. One that I found very
useful is to give a label. So this is going to be used as
the prefix for the name of the genes and transcripts that we assemble. And it's very useful to differentiate from isoforms from transcripts
assembled from another sample. And then there are a couple of parameters,
such as -F/--min-isoform-fraction, that I found particularly useful. By default -F is ten percent, which means
that for a gene all the transcripts, only transcripts that are above ten
percent of the transcript level, expression level, of the most abundant one
for the gene are going to be reported. And similarly, -j/--pre-mrna-fraction to suppress
intra-intronic transfer below this level. It provides a way to interpret the
intronic reads as being either pre-MRNA fraction or being. And the default here is 15 percent,
and I usually leave it as is. But it can be modified, for instance,
when working with total RNA. So, these are some of the basic commands. In the case of strand specific libraries,
one can use one of the options here, depending on the library. So, let's give it a try. First of all, we're going to create
a directory called Cufflinks, and we would like for
the outputs to be in Cufflinks. And we'll create one subdirectory for
every sample. So just like before, let's create
a little command or batch file. com.cufflinks. And now we pretty much know what we need. We're probably going to need
the location of the same files, so I'm going to say THDIR. And I already know what that is,
but it's easy to copy and paste. L4/Tophat. And then, we need to create a directory. We're going to create a directory. So let's create DATADIR as being, actually, WORKDIR,
because that's where we're going to be working, and there's
going to be our Cufflinks directory. So under WORKDIR, we're going to create for the first sample, directory Test1. And Cufflinks creates transcripts and
intermediate files in the directory where it's being called, so
we're going to go to the directory. Okay, once we are located there,
we can call Cufflinks, cufflinks2. We're going to tell it a label. I'm just going to come up with that one. So I happen to know this,
these are patient identifier, for the particular data set. We would like, say 8 threads, and then we will be using
the BAM file in THDIR, in the Tophat directory,
this one set accepted_hits.bat. So that's it. And these will create a set of
files in the Cufflinks directory, Cufflinks and subdirectory Test1. And again, I'm going to show how
you can call this command line. Command5, nohup sh shell com.cufflinks, and we'll save all the standard error to com.cufflinks.log. And put this in the background so
we can exit without a comment. And this might take up to one day, or
maybe sometimes longer to execute, and in the mean time,
we can perform other operations. But now I'm going to check again,
and instead of waiting for a day, I'm going to show you
what the output looks like. So, let's go to results, and
we're going to go to Cufflinks. And there's one directory for
each of the samples. Let's go to Test1. And as you can see,
the main file here is transcripts.gtf. These are assembled
transcripts in gtf format. And you will recognize the format. So it's chromosome, the source,
which is the program that's reading those, whether it's a transcript or
exome, so the type of feature. Beginning of the feature, end of the
feature, a score that can be represented graphically, the information
about the strand, if none, and the coding sequence,
the frame, and finally, the ninth column gives
information about the gene ID, transcript ID, estimated expression level. And either below our bond
of the confidence interval, higher bond, and so on. So a variety of types of
informations that can be added. So this is the main file, transcripts.gtf. And you will see that there are a number
of other files, for instance, a number of skipped transcripts. That usually contains a small number of
transcripts that could not be processed, because there was some sort of exception. For instance,
there were too many reads at the logs. And then, together with those, we have
two files that give us the estimates, the expression estimates, fpkm. Let's take a look at genes.fpkm_tracking,
and similarly for transcripts, or for isoforms. So the label, as you might recall,
we asked for the label bja0z2. So all the gene names, and the transfer
name are going to have this prefix. Class code not known,
nearest preference, gene identifier, the same one,
the location on the genome, and then information about the FPKM,
the confidence intervals, and the FPKM status, whether it could
be calculated or not, and why. So let's count how many genes and how many transcripts we have
in the trascripts.gtf file. So we can find that
information in column nine. So cut -f9,
using the tools that were described in the first lecture, transcripts.gtf. Again, cut, but now we're going to have
to separate the fields by a space. -F, I'm looking at column number 24G9B. F2, let's see what this looks like. And now we're going to call this unique,
so that we have only, among consecutive records of
the same type, we'll only keep one. We sort that uniquely,
and then we're counting. So we have 43,983 genes. And if we want to identify
the number of transcripts, then, you might recall,
let's do another more, or rather, a head. So we can find that in column nine,
one, two, three, four, so it's field number four. So, again,
cut column nine from transcript, and cut by space -F4 uniq, and
lets see how many we get. So, mostly we have one transcript
per gene, in this particular case, but many of them might be single exon,
and therefore, cannot have alternative variants. So this concludes
the section on Cufflinks. And next, we're going to be looking at how
we can perform differential expression with Cuffdiff."
"So next we're going to be looking at how
we can perform a differential expression and splicing analysis using Cuffdiff
between our two conditions. Test and control You might recall that
we have three replicates for each. Let's start again by just looking
at what is the basic command line usage for Cuffdiff. And actually before even doing so. Many times it is very
useful to first reconcile the organization, the gene names and gene
organization across the multiple samples. This is because in some of the samples,
there might not be enough risk to be able to put together to
assemble a transcript end to end. So Cuff Merge,
which is also part of the Tuxedo Suite. Is designed to achieve particularly this, to reconcile the gene
structure across the samples. And to combine it, and compare it with the
reference annotation and do so seriously. So what we're going to be doing in
the first stage is to run cuffmerge. So let's see how we can use cuffmerge
just like we've done before. cuffmerge.log. Okay, so it's cuffmerge options,
and then a file that contains a list of the transcript annotations for
each of the samples. And there are a number of options so dash out just like before directory where
we would like to write the March assembly. Then if you want to give it reference
annotation, you might remember annotation from our top half column, min isoform
fraction, the number of threads and so on. So we're going to remember
a few of these options here. Active directory we're going to
give it a reference annotation. And we're going to give
it a number of threads. So similarly, we're going to write. First let's make a directory cuffmerge. And we would like to put the output there. And then we're going to write
similarly a file that's called com. And I'm going to make it a combined
cuf.dif.cuf merge, okay. So the first thing we're going to
say is cufmerge, we're going to give it a reference file, I'm going to do this
by prepping, so let's find out from here. There's the annotation. Let's denote this annotation. So cuffmerge options, but
then I give it the annotation. Let's say that we want
to use eight threads. We want the output to
go into the directory. Let's call it WORKDIR and
then cuffmerge, okay? This where we'd like the output to go. And now we have to create a little
text file that would list The files, the transcript files created
by Cufflinks for these examples. So, there's going to be GTFs.txt, and let's put that in the directory
WORKDIR/Cuffmerge. So we're going to keep it there,
keep them all encapsulated. And for that purpose. Let's create the file. You might remember, in the directory Cuffmerge/GTFs.txt. So the first file was in a Cufflinks,
lets start with test, test one. Transcripts, go gtf. So this is one file per line Cufflinks were listing, we're listing Cufflinks transfers for
samples, test samples one two and three, followed by the contour
samples one two and three. And essentially what Cufflinks does it
calls because Cufflinks to assemble this together with reference annotation
and create four transcript models. So we've created the file. Okay, let me show it again. Now we're going to go back, sorry, to com. Cuffdiff. And we have everything we need. So, the results are going to be
reported in the directory cuff merge. And I'm not going to,
just like before, you can simply call a stage com, perhaps will no hop,
com.cuffdiff, and save the standard error
to cuffdiff The log and so on, but I'm not going to run it and
I'm going to show you what the result is. This in fact the command cuff merge
creates a single file, merge GTF which is the result of merging the transcripts and
reconciling them across these examples. The results, Cuff merge/merge.gtf and a look at this file is going
to show me it's a gtf file, basically every logos is
assigned a new gene ID and now we have the same multipliers
across these examples and the transcript receive new IDs as well. But you also have, for every line and for every transcript the corresponding
gene name and the old name. For instance in this case in
the annotation, but it could also have been one of those that we labeled
from among the Cufflinks transcripts. Cross code them and so on, by comparison
to the reference on patient, and so on. So it's a GTF file that contains
the reconciled genes and transcripts across the six cell samples. Now, once we have that we're
going to run Cuffdiff, and Cuffdiff will run in two stages. In the first stage it will assign reads. To this set of transcripts for
each of the samples to quantify them. Or pay expression levels for
transports and genes in each of the five, six samples. And then the second stages will perform
the financial expression in differentials plus analyses. So let's continue writing
our comment five. So once we create the fimers we're
going to use it in cuffdiff. So let's create a directory
called cuffdiff as well. And that's where we're
going to see the output. And we're going to mark that as Okay. Yeah, we should have put here, data one. Which is our directory. Coursera/L4, okay, and
let's read it there. For the directory and now cuffdiff. And now we don't need one
subdirectory per sample because they are all going into one directory. Cuffdiff2. We want the output to be
sent to WORKDIR/Cuffdiff. We want to use say ten we want to use, actually,
cuffdiff, let's see what we need. And that's a very long list again. So the basic format is cuffdiff for
list of options, transcript of GTF so these are reference transcript
the merge file that we used and then the [INAUDIBLE]
files. So this would be
WORKDIR/CuffMerge/merge.gtf and enough for that line. And now we have a list, we have two parameters that specify
the [INAUDIBLE] corresponding to the replicates in the two foundations so
first lets start with the test. We know that those are in
the top hot directory. Let's make that clear, here. Top hat directory, is top hat. So we're going to write that here,THDIR/Test1/accepted_hits.ban [SOUND]
And we'll do so for the other two replicates. [SOUND] Wrong paste [TYPING] So, we're going to copy these. [TYPING] Replica three, replica two. And then for the control set. So, let's take a look at
the command as a whole. We're calling CuffDiff,
the output reporter will be saved in the directory CuffDiff from
the working directory. It will use ten threads it will use
as the reference file the merged file that was produced by Cuff merge, and then
we have two sets of files of replicates, the first corresponding
to the test condition and the second corresponding
to the control condition. And again, we're going to run
that with nohup sh com.cuffdiff. And save the standard
error to cuffdiff.log. So that in case something happens we
would know what they are and so on. And just like before,
because this is this takes a while. Sometimes a long while. We're going to just cheat again and
look at go to results and see what the output looks like. Cuffdiff, so there's a set of files here. So there are the diff files, that show the differential expression,
okay? The most important of them, and
the most frequently used is gene_exp.diff. So you'll see that there
are two types of files here. So they are the ones that
refer to the expression. So, for instance,
if a gene's expression is different, significantly different, that
the secret between the two conditions. Or with an isoform expression is significantly different
between the two conditions. The same thing with
the groups of transcripts. And then we also have CDS.dif,
and promoters.dif and splicing.dif, which
refers to the splicing. So whether the the split, the percentage
of the various transcripts within that group, for instance, for splicing
within a gene group is the same or not or is rather significantly
different between the conditions. But as I said the most important one, the most frequently used is
the expression of an analysis and let's take a look at gene expression
dot diff with the understanding that the other, dot diff files
have a singular organization. So we have the locals,
which was the one assigned by cuff merge. Gene ID, which is the same. The name of the gene and
we start from the reference annotation. The locus chromosome and
location within the genome. Sample one and sample two these are some
values one through two unless specified. And then we have a column that tells
us something about the status, so we have one line for
every locus for every gene. And then we have here, the status. It tells us whether the test
quickly performed or not. So notice,
it means that it could not be performed. There are other parameters such as okay. This probably going to see, so
the test could be performed there, there are enough reads. High data means that there are too
many reads for the test to be precise. Low data means that there were not
enough reads for the test to be precise. And then there's also
a label that's called fill, that will be the first format for
mathematical exception in the calculation. And then we have, following this column,
we have the value one, so the average, let's pick one here. If became for the gene in
the first data set in the test, then the average in the control data set,
then the log two fold change. So that's log two of this,
of the second versus the first. So control over test. Followed by another column
that shows the test value, and that it's interpretation in
terms of P value and Q value. And finally, the last one tells us
whether the difference is a physical significance or not. So, in a very simple way to obtain the list of genes that
are differentially expressed, signficantly differentially expressed between the two
conditions, we just have to do grep yes. So we're grepping by yes on
the last column in gene_exp.diff. And we can look at them. [SOUND] And we can even count them. In this case we have 169 genes that were
identified as signficantly differentially expressed. And we can perform the same analysis
on the Isoform level and so on. There's one difference when looking
at splicing pattern differences. In that case we're looking at
the distribution of the values as percentages of the total distribution for
a gene. So in one case, for instance, we might
have three different transcripts and the relative FPK and
expression values might be 50%, 30%, 20% in one case and 80%, 10%,
10% in the control data set. And that's why this pricing
dot diff file will show us. So I'm not going to go through that,
I would just like to select one gene for further analysis and for illustration,
and I'm going to check here, I'm going to look at chromosome 9 because it has a
small number of genes and I can pick one. So let's keep this in mind. Let's look at the gene
215 on chromosome 9. Okay.
And we have in the test we have
6.8776 as the average of. In the controls we only have 0.18,
so a significant fold change and this is a statistically significant and
we're going to illustrate that next. And we're going to visual that in IGV. So this is in a nutshell how we can
use Cuff merge and Cuffdiff to perform a differential expression analysis and
how we can interpret the basic results. Next we're going to be looking at how we
can visualize and manually annotate or understand, curate the results
of these analyses. Using the IGV. The integrate."
"So, next we're going to look at how we
can use the Integrated Genomics Viewer in order to visualize the results and
to them. There are two types of files
that we can visualize and that we need to visualize in IGB. The first ones are the top of alignment,
and the second ones are the transfer. The GTF files of transcript assemble with. Both types of files will
need to be indexed, however, to allow easy access to random
locations in the visualization tool. So first I'm going to illustrate how we
can sort and then index these files, and then I'm going to show you how you can
load them and analyze them in the IGB. For the purposes of illustration,
we're going to use one of those examples. As you might recall, The gene TMEM 215,
which we identified as being deferentially expressed between
control and test samples via. So we're going to remember
the name TMEM 215 on chromosome 9. As well as the logos name assigned
by S lock 057616 might be needed. We'll start with the transcripts files
because that's slightly easier to handle. So, we have the transcripts file
in the directory Cufflinks. And you might recall that each
sub-directory contained a transcript assembled from that particular sample. So now, let's make a smaller file, let's only expand the transcripts
corresponding to chromosome nine. And I'm going to do that
using a simple trick. Starting with control, cufflinks, like that. Cufflinks/Ctrl1. The name of the file was transcripts.gtf. I'm going to use here
a problem that's called awk. So I'm going to cheat here a little bit. And I'm going to say, I'm only going to repeat those lines
that show chromosome nine in column one. Save con 1 yes, sets chromosome nine,
I'm going to save that. Usually, you should be able to
work with the entire file, but this further narrows down the input
to the visualization tool. So let's check that, below there. So, indeed, we're getting only chromosome
nine, and I'm going to save that into a file that I'm going to call crtl1.gtf,
and I know that those are the transcripts. And I can do that with the second file and
so on. And then similarly, we would test. This one. Now, we need these files to be indexed,
but in order to be indexed, they need to be sorted. Which they are not. We will use for both sorting and for
indexing a tool that's called IGV tools. You can only access them from
with in the IGV environment but in this case the actual I shall
demonstrate it from the command line. So IGV tools sort. Okay. Oh.
Okay. Simply Test1.gtf. Test1.sorted.gtf. So it's IGV tools sort name
of the first file, and the input file, and
name of the output file. And let's see what we get. And it's very simple,
the same thing for the other files. That's three. Then we're going to do that for
the controls. And now we can finally indexed them, again using IGV tools,
to index Ctrl1.sorted.gtf. And let's take a look. So this created the file
Ctrl1.sorted.gtf.idx and we can continue that with the other files. And test three. So this creates the sets of files. Gtf files. As well as the sets of Indexes for
these files. That we'll need for the visualization. So here they are. Those are the gtf files. Now we also have to create smaller files,
sorted and index files for the alignments. Now the alignment files are all ready
sorted and knowing that I was supposed to extract ranges from them,
I've all ready indexed them. So if we're looking at Tophat/Test1/. Okay. So we have. In addition to the alignment file
accepted we also have the index. So now with the index we
can use some tools view, just like I demonstrated in the previous
lecture, and extract only those [INAUDIBLE] could belong to chromosome,
chromosome nine. So to do that, we would say samtools view, test Tophat/Test1accepted heat. But you understand that I
already have the index there. And give me anything that is
located on chromosome nine, and I want that as a band file. So I'm going to show that
as I'm going to add -b. And save that into,
let's say chr9.test1.ban. And I'm going to run this and
this is going to take awhile so I will only demonstrate this for
Test1 with the understanding that you can repeat this analysis and you can repeat
this comment for the other five files So, we can now view the file. Samtools view, chr9.Test1. Just to make sure everything is in order. Okay?
And indeed, all of the matches are on chromosome nine. Now we will index the file
because it's already sorted. And we'll repeat this analysis,
this processing for the other five files. Now we have a set of alignment files and
their indices. This is Test1 but we should have for all these examples as well as a set of
gtf files that represent annotations and we're ready to view them in
the integrated genomic viewer."
"So now that we have created the annotation
files, as well as the alignment files that can be viewed and
curated in the integrated genomics viewer. We are ready to load them into the viewer. But first, a couple of words about
where you can find this tool. You can go and
Google integrated genomics viewer, and you can either run it from
the Broad Institute's website, or we can download a copy. So downloads here, and you can have
your own copy after registration. So now that you downloaded your own copy, all you have to do is
to click on the icon. This will open IGV. And then, we're going to load into IGV,
our data sets. And let's start with the transcripts. Let's start with a test. So first of all we want
the human genome H19. That's the one that we used. But if we're wanting another genome,
we could find it here in the list. Or we could even load a genome from
a FASTA genome file that we could provide. But let's start with human genome, HG19. And now we're going to load,
let's start with the annotations. So in this case,
Desktop > Coursera > IGV > GTFs and start with Test1.sorted. Okay, you also have a listing, these are the RefSeq
reference gene annotations, so we've loaded Test1. Load from File, Test2. We won't see anything until we locate and we narrow down the region and
zoom down to see the features. And now let's also load the controls. And just for the purposes of illustration,
let's go to our gene TMEM215. So now as you can see in the viewer,
we have one panel. And we have stacked panels with each panel
corresponding to one of the annotation sets that we provided. And we can view these annotation in
the Collapsed form that is projected along the genomic axis and
collapsed, Expanded and Squished. I usually like to see Squished so
they are extended but not too much so. And we squish the alignments for
each of these. One can also change the track color. So for instance, in this particular case,
let's make this red, and so on. And now you can see that the pattern that
emerges is that of a gene with two exons. And there's an additional single exon
transcript that might be a transcript, or might be in 24 other type of noise. As are these. But what you will observe is
that the top three panels, corresponding to the test examples,
have a clear definition of the gene. Whereas the bottom three, where only one of them has enough reads
to allow reconstruction of the gene. So the other two barely show any signal. And you might recall that the average
gene expression level was 0.18 compared to about 6 for the test examples. So now let's look at the alignments to
verify that this indeed is the case. So we're going to Load from File now,
let's load an alignment file. We're going to go to IGV > BAMs. Let's load the alignments for
the control, for one control, and we can load the alignments for
one test file. And I might actually want to move
them around to have the test there. Okay, followed by the controls. But for every alignment file,
we have three sub tracks. We have one showing the coverage. So that's calculating at every
position on the genome the number of reads that align at that position,
and you can see the coverage varies. Then we have the junctions track, this shows the splice junctions
coming from the splice reads. And some information about the depth,
how many reads are supporting that. In this case, 37. And then we have a detailed view
of the alignments in the BAM file. And here you see this horizontal
line representing the spliced exon. So as you can tell there is significant
coverage, the maximum number of reads is 139, I'm assuming at this point for
the test file. Whereas if we're going
to the control file, we barely have any reads and
the coverage is up to ten reads. So, and if we load the remaining files,
Test2, Test3, versus Control2 and Control3,
we will see a similar example. So as you tell,
we identify that this is a two exon gene. That is significantly,
we can validate that is significantly more expressed in the test samples
compared to the control samples. So this is one illustration on how we
can perform a very simple analysis and curation, verification of results
with a Tuxedo pipeline using the integrated genomics viewer, IGV."
