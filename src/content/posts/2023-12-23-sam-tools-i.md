---
template: blog-post
title: SAM Tools I
slug: sam_1
date: 2023-12-24 05:22
description: SAM Tools I
---
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
