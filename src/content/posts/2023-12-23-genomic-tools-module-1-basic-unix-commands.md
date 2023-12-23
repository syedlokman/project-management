---
template: blog-post
title: Genomic Tools Module 1 Basic Unix Commands
slug: genomic_1
date: 2023-12-24 04:05
description: Genomic Tools Module 1 Basic Unix Commands
---
Hi, I'm a Liliana Florea. I am an assistant professor in the McKusick-Nathans Institute of Genetic Medicine in the Johns Hopkins University School of Medicine. I'm a competition biologist which means that I design algorithms and methods to solve biological problems. I also use other people's software and tools in order to analyze genomic data which is what I'm going to show you how to do today. So I will start the course "Command Line Tools for Genomic Data Science". It is structured in four different lectures and today we will start with the basic Unix commands. Before going into lectures we'll look at sequence and genome feature representation after which we will start looking at tools for performing alignments and identifying sequence variation and lastly we're going to get tools for doing transcript [inaudible] analysis. So let's get started. Think about the content that you have represented in your computer. You have files and you have them organized in directories. Directories can be themselves part of bigger directories. So if you're looking at that and what I'm showing is what you can see on my Mac machine. You have a tree structure. At the very top is what we call the wood. And then there are a number of directories, for instance, here I have in the Macintosh hard drive I have directories, applications, library system, and so on. And these directories can have further subdirectories such as Library under System or it can have files such as mach_kernel. When you communicate with your computer you communicate via the operating system. So this can be OS, for instance on the Mac, or it can be Windows on your typical Windows machine or it can be Unix which is the system that we're going to be learning about. And you're doing so via an interpreter. In a system such as Mac or in Windows your files have certain types of fixed pages when you click on a file your operating system will know automatically what kind of program to use to open the file and to perform operations on it. However, if you're thinking about it the range of operations that you can perform on a particular file is quite limited. And under some circumstances, for instance for general analyses, you might want to do your own set of operations which is what Unix is for and that's what we're going to be doing. I'm going to illustrate some of the basic Unix commands in this lecture and in doing so I'm also going to show that for a particular genomic application. For our application let's consider that we have one directory that's called "Plants" which contains genomic information on three current day plant systems. However, they're on planet toy. So we have toy apple, toy pear, toy peach. We also have two ancient plant systems, let's say, toy agathis and toy araucaria. What kind of information do we have? We have genomes, we have annotation of genes and I'm assuming at this point that we have taken a course on genes and we have the list of samples from each species. So, with this information let's embark the point at looking at the command line in Unix which will be the following section.
"In this section we will be looking at
how we represent content in Unix and some of the basic commands in Unix. So let's start by opening a terminal. The way we communicate with
the Unix operating system is via an interpreter or shell. And we give it commands, and then it
responds back if it understands it. So in this case let's start
with some basic Unix commands. Let's type date, and then it responds
with Tuesday, March 24, 2015. Let's try echo hello, and it echoes hello. So it understand that particular comment. Now let's try foo, and the interpreter, the shell language, does not recognize
the command and it says command not found. So there's a basic language
of commands that is being recognized by the interpreter. One very useful command is pwd,
this print working directory. And it gives us the current
location within the file system. As you may recall, content is
organized into files in the computer, and the files are themselves located
in two directories, which may be part of other directories, and so
on, until we reach the root directory. So any particular location within
the file system can be represented by its direct path from that
location to the root of the system, which is what we have represented here. In Unix, every level in
the hierarchy is marked by a slash. So we have a slash here, which represents
the root, then the directory users, then its sub-directory, lilianaflorea,
with sub-directory Desktop, sub-directory Coursera, and then Plants
and that's our current location. We can go from this location or any other location to any other one in
the file system by using the comment cd. That's change directory. So, for instance, we can change directory to /Users/lilianaflorea/Desktop/. And then we can move on from that
location to Coursera/Plants. As you've noticed, I used two types of
referent to get to the directories. The first type is by
using the absolute path from the root to the current location. The other way was a relative way of moving around the file system by
moving from the current directory. So once I was in the current directory,
I changed it to its subdirectory, Coursera, and
subdirectory within it is called plants. There are two special directories for
which we have abbreviations. One of them is the current directory,
which is represented as a dot. And another one is the parent directory
which is represented as dot dot. Before we do so,
before we move into the parent directory, I would like to show you how we
can look at the file content and the directory content within
a particular location. So we are in the directory Plants. Typing ls, then,
will give us a list of all the files that we have represented
in this particular directory. And as you can see here, we have files
that are associated with the tree species that we mentioned in the previous
section, with apple, peach and pear. We also have a few additional files. Let's say that we wish to
go to the parent directory. We would use cd..,
which represents the parent directory. Let's see what directory that is. pwd, print working directory. And we are in
Users/LilianaFlorea/Desktop/Coursera. Just like before,
we can see its file content with ls. We have a PowerPoint file, the Plants
directory that we were in previously, and an archive. We want to go back to our Plants
directory and we do so with cd Plants. And then ls will convince us that we're
tooling the directory we wish to be in. So when I'm typing ls, you might
notice that the files are listed in alphabetical order, with files
starting with an uppercase character being listed before files
that start with lowercase. Sometimes we might wish to have additional
information about the files and there are several command line
parameters that can be used. One very useful one is the- l,
ls -l would list additional information about the files. So you might notice here that each each
file is listed with the first digit. The information as to whether
it is a directory or a file. D here marks a directory
whereas the dash marks a file. Then the set of permissions which we will
not cover in this particular section. Then the number of links to the file,
the user name and owner name of the file, the group that the owner belongs to,
the file size in bytes, the date when it was last modified,
and lastly the filename. As I mentioned, the files
are listed in alphabetical order. A very useful option is to see them in
the order in which they were created or rather, reverse chronological order. So type in ls -lt in
the current directory would show pear.samples, months,
orchard, and so on. And you can look at the modification type. You can view other options for
these commands and others at any time by looking
at the manual pages, so man ls would give us the information
about the command ls and so on. So this concludes our first part
of the section on how we represent content in Unix. For the next section, we will look at
how we can handle representing and listing content when we have
a very large number of files."
"In this section, we will continue to talk
about content representation in Unix, and we will look at how we can
effectively name files, particularly, when we have large numbers of files
that are of a particular type. So, if we're looking at the content of
the current directory for our application, LS would show us that we have three types
of files for each of the three species. The three species are apple,
peach, and pear, and for each of the species, we have a genome
file, a genes file and a samples file. So that's simple, right? But now, let's imagine that
we have 100 species, and that we have 1,000 files for each one. Well, how can we represent, or how can we
least files, in that case efficiently? We can use the so called naming patterns. We can use wild cards. For instance, one very popular wild card,
and very useful one, is the star. So star represents any combination of
letters and numbers, so any string. So we can very simply type now,
list all the fives that are associated with the species apple,
apple.star, and that would give us the three files that correspond
to the species apple, apple.genes, apple.genome, and apple.samples. And we can do so
with the other species as well. Another wild card, that now stands for just one character,
is marked with a question mark. So, for instance, we can say ls ?pple.genome, and this will return apple.genome. So, as you can see,
the question mark stands for the a at the beginning of file name. We can also represent a range of
characters in square brackets. So we can say, square brackets, any lower case letter between A and
Z, multiple times, and this what star stands for, .genome. So this is a representation that will give
us all the files that have the extension genome. Apple.genome, peach.genome, and pear.genome. We can also do combinations. So for instance, we can look at all the genomes files
whose name starts with the letter P. LS p star .genome, and that will give us peach.genome and pear.genome. Lastly, there's one more way
of representing one more naming pattern that I would like to
show you, which is the curly brackets. So in curly brackets,
we can specify a number of options. So we can say, ls open curly bracket pear, peach.genome, and
it will list all the files that have either pear or
peach at the beginning of the file name, followed by .genome. So in this case,
peach.genome and pear.genome. So this way we can represent a very large
number of files that share a common naming pattern in a very effective way."
"In this session we will be looking
at how we create content and how we remove content in UNIX. So let's start from the current directory. An ls will give us the directory content. And we have files for apple,
for peach and for pear. We would like to have them
organized by species. To do so, we will create a directory for
each of the species and transfer the content corresponding to
the species into those directories. Let's start by creating a directory for
apple. We do so
with a command called make directory, mkdir, and
then the name of the directory, apple. We now have to populate the directory
apple with its corresponding files, the genome, genes and samples file. We can do so by copying a file, or multiple files, from the current
location to the apple directory. Let's start by copying,
with the command cp, the file apple.genome
into the apple directory. If we now list the content of the apple
directory we will see apple.genome. There's still a copy of the apple.genome
file in the current directory as well. ls apple.genome. So it's here. We can copy one file with a cp command,
or we can copy multiple files. So we can copy apple.genes and apple.samples into the apple directory. And now if we list the content
of the apple directory it will show all the three files. We could also have used
the naming conventions and wild cards we showed in
the previous section to copy all the apple-related
files into the apple directory. And we can do so with cp, copy, apple.* into the directory apple. And the apple directory now
reflects the three files. We can also move files,
simply transfer the content, from the current directory
to the target directory. For instance, we can move the pear.genome file into the pear directory. So if we now list the content
of the pear directory. We have first to create the directory. So we can create directories for pear and
we can create another directory for peach. And as you notice we can put both
of them on the same command line. We can now move the pear.genome
file into the pear directory. And listing the content of the pear
directory will show pear.genome. We can move several files at one time. For instance, move pear.*, all the files in the current directory,
into the directory pear. Now listing the content of the pear
directory will show us that all the three files are represented there, pear.genes,
pear.genome and pear.samples. Let's check to see, are there any more
pear files into the current directory? Ls pear.*, and theres no such file of
directory, so these files have been effectively transferred or
moved into that particular directory. And we can apply the same to the peach files. And we shall move them
into the peach directory. The peach directory
then place peach.genes, peach.genome and peach.samples. And now let's check to
see if any peach files have been left in the current directory. And there's none.
So let's survey the content
of the current directory. We still have the files apples.genes,
apple.genome and apple.samples, which, you might recall,
we simply copied into the apple directory. We want to remove these duplicates, and we can do so with the comment rm,
remove file. So we can remove the file apple.genome. To verify, ls apple.genome. And indeed, it has been removed. In a similar way we can remove
the other two apple files. However, we want to be very careful when removing files,
because this operation is final. So one common line option for rm, -i,
will allow us to change our minds. So if we type rm -i apple.genes, the prompt will ask us whether we indeed
want to remove the file apple.genes. If we type y the file will be removed. If we type any other letter,
the file will stay where it is. So let's type n, ls apple.genes,
and the file is still there. Let's try now rm -i apple.genes. And we'll say y, yes, confirm. Now we can see that the apple.genes
file has been removed indeed. And now we simply remove
apple.samples in the same way. In addition to removing files, we might
want to remove entire directories. For instance, our application mentioned
two ancient species which are listed and have files in the directory Old.stuff. If we're looking at Old.stuff,
it contains genome files for two species, agathis and araucaria. We want to remove these. So let's try the command rmdir,
which is one command for removing empty directories. rmdir Old.stuff. And it cannot remove the directory
since the directory is not empty. So we can first delete all the files and subdirectories, if applicable,
from the directory Old.stuff. For instance,
remove Old.stuff/agathis.genome and so on, and
then try to remove our directory. That's one way of doing things. Another way is to just type rm -r,
which stands for recursively, so remove recursively Old.stuff, which starts
by removing all the subdirectories and their subdirectories and so
on from the Old.stuff directory, and then removing the directory itself. So let's apply this. And let's look at the current content. So we have apple, peach, pear, and then
the Old.stuff directory has been removed. Let's list the files again,
now with all of your operations, and we can see we have now three directories,
peach, pear and apple. And two files, months and orchard, which
we'll be using in subsequent sections. This concludes our session on content
creation and removal in UNIX."
"In this section we will be
looking at Unix commands for accessing content In files,
in directories. This will also give us an opportunity
to explore the content of the files for the three species for
our particular application. So let's start with apple. Now all of our files are located
in the apple directory so we're going to change
the directory to apple. One easy way of looking at the content
of each file is with a command more. More apple.genome. So this will allow us to look at the
content of the file one page at a time, or one line at a time, by pressing Return. We can also press the Space bar and
that will move ahead one full screen. We'll do this again to
demonstrate another option. You will notice that the genome
file has a specific structure. We call this a file,
which is used to represent sequences. We'll be talking about this in more
detail in our following lecture. A file is represented with one header for
each sequence. In this case, that is marked with a greater than sign followed by
an identifier unique to that sequence. Here it is chromosome one and then followed by one
are multiple lines of strings. Over the A, C, D, G alphabet. Sequences can be quite long and we might not be able to scroll
to the end of the sequence. So under certain circumstances,
we might want to see where the start of the next sequence in the file is,
and we can do so by with a slash, and then looking for
the limiter, the greater than sign. So these will take us in the file to
the location of the next sequence. The next sequence is named chromosome two,
and the sequence itself follows. And we can repeat this looking for
the next sequence. Chromosome three. Chromosome four. Chromosome five. And then the pattern is not found. So this is a fast file containing
five different sequences. Chromosome one, chromosome two, chromosome
three, chromosome four, and then five. And we shall call this a multi-fast file. So that's what the genome file looks like. We can view the same information. With a command less. Less apple.genome. So it starts from the beginning. We can recognize chromosome one, the first sequence followed by
this string of nucleotides. And spacebar will move
us forward in the file. But unlike more, which only allowed
us to move forward in the file, less also allows us to go backward. So pushing the up arrow would allow
us to go backward in the file. So we can move
bidirectionally in this case. That was the apple.genome file. We can now use the more and
less commands in a similar fashion to look at the other types of files
that we have in this directory. So let's take a look at the genes file,
more apple.genes. The genes file will contain annotation,
which is information about the genes and where they are located within
the general mix sequence. It is organized in columns, and here for
instance in the first column we have the gene name,
in the second column we have the variant. And that explains a little bit. The chromosome where it's located,
the start location on the chromosome, end location,
whether it's located on the fourth, or plus, versus the reverse or
minus trend of the genome. And then a string that uniquely
characterizes this gene and this variant. Namely its structure along the genome. So the gene seen in this particular
case might be genes such as smell, size, color, taste, shape but
their might be other genes that do not correspond to a particular trait or
collectively correspond to some traits. And here those are indicated with appl4,
appl5, 8, 9, and 10. And to think of variance for instance you
might think about the color of an apple as being red, yellow, or green. We just mark them color one,
two and three. So we use more which allowed us to view
the content of the file apple.genes. Of course we can illustrate with less, and we will obtain the same
information in a similar manner. Lastly, let's take a look at the last
type of files which is apple.samples. So we will say apple.samples. And it simply tells us what
are the portions of the that were sampled by a particular experiment,
in this case root, leaf, and foot. We can observe the information in
a similar way for the peach and the pear directories which I am
now going to illustrate here. So more or less are basic commands for
accessing content in Unix."
"In this section, we will look
at a few more Unix commands for how to access content in files. We are now in the peach directory, in the previous section we
looked at more and less. If the file is very long, though, we might
only want to see a portion of the file, let's say the portion at the top. The command head,
followed by the name of the file, would give us the top ten lines in a file. So you might know this,
that in the peach genome, our sequences are named scaffold one and
perhaps, scaffold two and so on. Followed by the sequence of a's, c's,
g's and d's, the genomic sequence. If I want to change the number of lines
that we see from the top of the file, we can do so by specifying head,
let's say, -50. Peach.genome, return, and
that's going to show us the 50 lines. And similarly, head-20 peach.genome. Obviously, we can use the same command to look at the genes five head peach.genes, which will list the top ten lines. And similarly peach.samples. Now just as an observation as we're
exploring this particular file structure, you will see that the peach.genes
include among others, shape, smell, taste, and size, and they each of
them having a number of variants. And that our experiment only
sampled the fruit from the peach. So, head would give us a number of
lines from the beginning of the file. Sometimes we might want to extract
a number of files to test a particular procedure, rather than use the entire,
very large file. In a similar way, we can use tail to look at the last
few lines at the end of a file. For instance, those might be some statistics that
are attached at the end of the file. So tail peach.genome,
in this particular case, would give us the last ten lines, which
only show the end of the genomic sequence. We can similarly do tail-15, for instance, to extract the last fifteen
lines from the genome file, and we can do so with the genes file. And with a samples file. One last command for accessing content
that I want to show you is cat. Cat actually stands for concatenate. So we can concatenate
multiple files using cat, or we can simply show
the content of one file. So in this case, I'm going to show you
the content of the file peach.genes. Catpeach.genes. I'm going change to the parent directory,
and now, let's concatenate the content
of all the genes files. Cat star, to mark any directory,
p star .genes. So as you can see, this put together
the content of the genes files across the three directories apple,
aeach, and pear. Let's also try to do this with the gnome
files, and that went very fast. So when the file is large, cat is going
to show the entire content of the file. It is not going to give us the time to
stop and look at how it's represented. So perhaps, we need a way of capturing
the output from this program so we can view it at our leisure and this
is what the next section will be about. So for the time being, this concludes
this section on accessing content."
"In this section we will be talking about
how we can redirect content in Unix. You may recall that sometimes the output
from one command for instance, cat, can be very large. Too large for
the human mind to be able to see it. At the speed at which it is displayed. So, cat */*.genome. Showing the genome files. Will only allow us to view the last
few lines of the last file. In Unix, content is organized in files. And the files are organized
in directories. And the files have a particular location
within the directory structure. However, there are three
additional types of files. Three standard files that are used for
input and output. So these are the standard input,
standard output, and standard L. So, for instances, lets take the command,
when we're typing the command cat apple/apple.genome. The comment cat takes it's content
from the file apple/apple.genome. Or when we're typing echo hello,
the command echo is taking it's input. Is being, but in this case it's taking
its input from the command line. And namely it's hello. Let's give one more example of a comment,
WC. WC word count, is another way of
accessing the content within a file. So if we wish to see, for
instance, how many lines or how many characters we have in one file,
we can use wc. wc apple/apple.genome. Would give us four pieces
of information.The first one will be the number
of lines in the file. The second one will be
the number of words in the file. Recall that each line here was one word. So it makes sense for the number of words,
and the number of lines to be the same. Then we have the number of
characters in the file. And followed by the name
of the file itself. We can use wc-l to view just
the number of lines in the file. So apple/apple.genome gives us 1083 lines. In this case, that we see -l took it's input from the file apple/apple.genome. We can redirect files,
in standard input into standard output. For instance,
instead typing wc -l apple/apple.genome, the output was presented to the terminal. So, there's a standard output. We can redirect the output
using the greater than sign. Into a file that will give us, for
instance, nlines, the number of lines. So, now the file nlines would
show us the output that we previously saw at the standard output. And we can do similarly, with the input
file with the less than sign. So for instance we can say wc -l. And we apply that to the file,
apple/apple.genes, and we get 16. So we can use the greater than sign to redirect the output from a command
line, from the terminal to a file. And we can use the less than sign. In order to redirect the standard input
from the terminal, to a particular file. One other redirect operation that
is very very useful is the piping. With this vertical bar. That essentially takes the output from
one program, in the list of commands. And pipes it to become
the input of another program. So in this case,
we will illustrate with, let's say, ls. Let's show ls, we have one, two,
three, four, five, six items. We type ls. And then we pipe the output,
which would be these six words. To become the input of the command wc -l. So this will show six. And you have seen how the output of
one command, becomes the input for the next command. Similarly, going back to our command, cat. We can use the command cat, */*.genome. Which was appending the call cat. The content of the three genomes file. And we can pipe it to the command more. Which allows us to see
it one page at a time. So this is chromosome one, spacebar, chromosome two. Chromosome three, four, five. And we should soon see scaffold 1,
scaffold 2 and so on. You don't need to go to the next file. We will see more examples on
how to redirect output, and redirect input in the following section."
"So in the previous sections,
we talked about how we organize content, how we create, remove, how we access,
and how we direct content in uniqs. And in the current section we're going
talk about how we can query content more closely. So, let's go back to our
example in our directory. So, we're in the plants directory and we
have our three directories with files for the peach, pear and apple species. And we also have two files,
months and orchard. We will demonstrate in the current
section how to sort the files and how to obtain basic information
from fields contained in the files. So let's start with sort. The months file which I will use for
the purposes of demonstration contains simply a listing
of the months of the year. January, February, March, April,
May, and so on through December. We can sort the files, this file,
using the command sort. Sort months. And this will list the items in the file. April, August, December, February,
January, July, and so on. Perhaps you expected to see
the names in the order of January, February, March, and so on. However, sort by default
sorts alphabetically. So April comes before August
before December and so on. We can also sort in a reverse
alphabetical order, sort -R reverse months. And that will start in
September because S is the last among the letters at the beginning of
the words, among those represented here. October, November and so on. So how can we sort them in
the order of the calendar year? Let's add a little bit more
information to the file. And while we're not
going to cover it here, you can use any kind of text
editor to edit your file. I'm going to be using vi, vi.months. So let's add one more font that gives the month during the year. From 1 to 12. And let's add the season as well. So March, April, and
May we're going to put spring. Summer, fall for September, October, November, and winter again for December. We can sort the file instead of sorting
it by the content of an entire line. Which is what we have done,
what we did before. We can sort it by column. So we can sort months by column two,
which was the numerical column. Okay?
So let's sort it by the numerical column, by column number two. So in this case look at column number two,
that's going to show, they're going to be listed in the order
of 1, 10, 11, 12, 2, 3, 4 and so on. So, you might wonder why? We would have expected to see the order 1,
2, 3, 4 through 12. Well. And that's because again
sorting alphabetical order. And 1 comes before 10. Before the string 1.1,
1.2, and 2 and so on. In order to sort by counting numerals, we have to specifically indicate
that on the command line. So we're going to indicate that with an N. We're going to say dash k,
column two, and N numerically. And now, indeed, the records are sorted
in the order in which we expected them. January 1, before 2 February, before March
3, and so on all the way to December 12. We can also sort them in reverse order. So sort -k 2, which is a common number, n, which tells us that the command is
numeric, and we should sort numerically. Nr says to sort in reverse order and
we can sort them. As you can see,
December is the first month, number 12. Followed by November number 11,
October number 10, and so on, all the way to January number 1. Let's sort by column number three. And then the three fall months
are going to be listed first. Because f, fall, alphabetically is
before spring and summer and winter. We might want to sort by multiple columns. So, for instance we might want to sort by
the season which would be column three and then within each season. So, we're going to say -k3, and
within each season you want to sort the months in their numerical
order within the card. So -K LB2 N. So first we have the four, and within the four months we have September,
October, November, 9, 10, and 11. Followed by Spring, with March,
April, May being 3, 4, and 5. Summer, with June, July, August, 6, 7, 8. Then we have Winter, which shows January,
February, and December, so 1, 2, 12. We can also sort those in
reverse numerical order. So we're going to have them
alphabetically by the season. And then sorting within each season in the reverse order
numerical order of the month. So let's see what we get. We have four again and within four we
start with November and then October, September, 11, 10, 9. In reverse order. [COUGH] Spring, again,
the order is five, four, three. Summer eight, seven, six. August, July, and June. And winter,
starting with December number 12. February two, and January one. So that's how we can sort by multiple,
multiple keys by multiple fields. One other very useful command here that
would allow us to look at particular, at individual fields within the file,
is the command cut. The command cut takes one file and it extracts a particular range or
of kinds or a particular kind. I'm going to make one small
modification to the file mass. And then I'm going to change all
the spaces into caps and you'll see why. So the cut command by
default delimits the field at the tabs mark. So we can say cut column
number one from the file mask. And that's going to give us
just the list of of months. We can say cut columns one and two,
and we can separate them by a comma. And we're going to see January 1,
February 2 and so on. And we can similarly cut a range of
columns, so we can cut columns between one and three, so columns one, two, and
three, and we'll mark that with a dash. So that's going to show
us the entire file. January 1 winter, February 2 winter, and
so on all the way to December 12 winter. However, we might have files, or we might want to count by
different types of delimiters. So I'm going to go into my mans file, and I'm going to change it back,
all the tabs into simple spaces. So now if I wish to cut just the first
column from the file months, it will be looking for the tab delimiter. Doesn't find it so
the entire line becomes column number one. To specify a different delimiter,
we use cut -D and then we specify the character
between quotes. And then the number of the column. So now when we specify this, cutting the
first column will show us only the month. We can similarly cut the first two columns
so now we see the month and the number. It's order within the calendar year or
we can show all three columns with one or three. Let's look at another command. And for that particular application, I'm going to cut the third
column here of months. And I'm going to put it in
a file that's called seasons. So the file seasons, Looks like this. It starts with two winter lines
corresponding to the first two months of winter, January February, three spring,
three summer, three fall, and another winter. So I might want to know the number
of unique types of seasons. So as you can see I have 12 months. I'm going to sort the file and
I have the option to say sort -u seasons. So, if there are multiple occurrences
of a line, it will only list one. And all of these distinct lines
will be listed alphabetically. And indeed we see fall,
spring, summer, winter. There's another command that has a similar
meaning and that is called uniq. Uniq, however, looks at the file and analyzes all old lines
one after the other. So whenever there is a number of
continuous lines, that is following one another, of the same type uniq
will only replace them with one line. Let's apply that to our seasons file. You might recall that we had two lines
that said Winter at the beginning, which have now been replaced
with just one line, Winter. Then we had the three spring lines
replace with just one spring, summer, fall and then we had December the winter
might correspond to December at the end. So you can see that winter now appears
twice because it was stated two distinct places within the file. So lets assume now that we would like
to use uniq, but we would like now to have a distinct representation
of all the four seasons alone. So we double the duplicate of winter. Then we can pipe this. Remember, we talked about pipes
in the previous section, so we can redirect the output
into sort dash u and that will give us what we expected,
fall, spring, summer, winter. There is however,
another benefit of the uniq command, which is to tell us how
many times the word or lines appears in a certain context. And we can do that with uniq -c. So let's apply uniq -c
to our five seasons. In the first column, you'll have
the number of consecutive occurrences. And then in the second column
you will have the line. So we can see that at the beginning of the
file we had two occurrences of the winter line, followed by three lines of spring,
three lines of summer, three lines of fall and
followed by at the end one line of winter. So that allows us to assess counts,
as I said, the number of occurrences. One last comment that I would like to
mention to you in querying file is grep. So we might, for instance, want to know if which of the three plans have samples
from the root of the plant system? So for that purpose, we can say grep root in all the samples files. And the output will show us the file and
then the appearance of the line containing
the pattern that they look for. So we see that only Apple and Pear
contain samples extracted from the root. Another application might be to look. So we might be looking for
instance, for a pattern of where we need to insert spaces and
we would delimit that by quotes. So, we want to look for 12 winter,
for instance, in our file mice. And indeed it appears there and
it gives us the line December 12 winter. Now let's try grep "" 7 winter"" months. And it couldn't find it in the find
months, which is expected. One last option is we can also retrieve the number of the line within the file
on which the plant was identified. And that can be done with the option, n. Grep -n "" 12 winter"" months, will give us the content of the line
preceded by the line number. Number 12. So we have looked at the number
of commands, particularly sort, uniq, cut, and grep, which allows
us to query the content of a file. In the following section we will look
at how we can compare content between two files."
"In this section we will be looking
at how we can compare content in two files in Unix. In particular we will be looking
at the commands diff and comm. Let me go straight there. So we are in our plans directory In which,
just to remind you, we have one directory
containing information for each of the tree species,
apple, pear, and peach. And then we have a number of files that we
will we use to illustrate some of these concepts and commands. The first command that we're going to
look at is diff which allows us to compare files, line by line. For the purposes of this illustrations,
I would like to show you the file orchard. More, orchard. And I quote,
under the evening stars I walk, the smell of cool damp air beneath my
feet on a summer night in the orchard. Tiger army in the orchard. So these are not my lyrics and now let's make a slightly
modified version of this file. So I'm going to just copy
the file orchard into orchard.1. This for instance, might happen when you have to make
changes to a particular file, to a text file, or when you might have a
program that modifies slightly and now you have just slightly different versions of
the output and you would like to compare. So we're going to try
to illustrate it there. Again, I'm going to involve my editor and
let's say that I don't want a second line. So now the second line
I'm going to save it You see the content of the first
file which is four lines and now let's take a look at
the newly created file. Which was just slightly edited. Under the evening stars I walk on
a summer night in the orchard by tiger army in the orchard. So we're missing the second line. Lets do a diff on the two fives. Diff orchard and orchard.1. So the command diff is going to tell us
all the differences between those two files and their location and type. So the location within the first file and
the second file. So here this indicator tells
us that line number two, in the first file was deleted right after
line number one in the second file. Then it shows us the line, and at the
beginning of the line it shows us the less than sign which is used to mark all the
changes as they occur in the first file. And indeed, as you might recall, we simply remove the second
line in the file orchard. Now let's make a view more changes in orchard.1 to illustrate
some other types of changes. So let's say that instead of
under the evening stars I walk, I'm going to say under the bright
night stars I walk, okay? So now as you may recall,
this file differs from the first one in the first where we changed
evening with bright night, and by not having the second line,
the second verse. And let's again invoke diff orchard orchard.1 So we have a longer report now because we
have more changes, more differences. So now it shows us that the minimum number
of changes that you can, that you can use to transform the first file into
the second one is to simply change the c. Lines One and
two underline one in the second file. So under the evening stars I walk, the smell of cool damp underneath my
feet into the third line and so on. Just as a parentheses here,
I should say that the algorithms that were used to implement, that were using
the diff method are the ones that also started the field of alignment. Of sequence alignment for
computational biology. So there you have it. I'm now going to move to illustrate
the next comment, which is comp. So com simply submits or rejects line
without any comment to different files, and for the purposes of illustrating
this first I'm going to show you the experiment, the sample files for
for our species. So apple, apple.samples, so root, leaf and food. And let's look at pear and then peach. So one practical question might be what
is the difference between the samples that we have from apple versus
the samples that we have from pear? So from apple we have root,
leaf, fruit, and we have flower, leaf and root for pear. So first we're going to just type comm. Apple. And then followed by the name of
the two files that we want compared. And that shows the output and
I also measured the carry out. Okay, so if you're looking at the output,
just the weight structure you're going to see it has three counts and each line that
the files is shown among the columns. So if the line appears
only in the first file, it's going to be listed in column one. If the file is going to
appear in the second file only is going to be
listed in the second column. And if it appears in both of them
it's going to be listed in the third. So according to this output, root is the only organ that has been
sampled in both apple and pear. However, you might be looking
at this output and ask me why? It appears that leaf is listed
individually for apple and for pear so
why was it not reported as being common? And here's the caveat In order to be able
to apply com, the files need to be sorted. So, the lines have to be sorted,
have to appear in the same order. So, let's do that first. You might remember the comment sort. So, we're going to sort apple.samples. Do a-p-p. Actually apple.samples.sorted and let's put that in the Apple
directory as well. And we'll do the same with pear. We're just modifying the previous comment. So we're sorting the pair.samples
file in the pair directory and we're saving that as the pair.samples.sorting
file in that same directory. And now let's apply the command
com to our sorted versions. And now you might see that food appears
only in the first file, only in Apple. So, food was only sampled from apples. The flower was only sampled from pear. And that leaf and root were both
sampled from both apple and pear. So, this makes sense. There are several options that
allow us to simply carve out and see only one of these coms. So, let's apply the same comment, com, and now let's say that we only want to see how
many organs were sampled in both of these. The way to do that is Sorry. So the way to do that is to simply ignore the lines that appear only in
the first line which is dash one and to ignore the lines that appear only in
the second In the second box, dash two. And that gives us leaf and root. Of course, we can, for instance, pipe
this through a comment such as, sorry, WCL, so we can get the number of such
ordinals, or teachers, if you wish. And that's two. We can also use these command
line arguments, -1, -2, and -3, in different combinations to
obtain those tissues or those lines that are represented only in the
first file, or only in the second file. So for instance if we want
to see only the lines that appear in the apple file
then we should ignore those lines that appear only in the second,
in the pear file and that appear in both. So -2, -3 and then gives us food
which is only sampled in apple. And similarly, we can ignore those lines
that appear only in the first file, that's Apple-1, or
that appear in both files -3. And that will give us. So four is the line that is specific
to the file pair dot samples, and pair dot samples dot sorted. So, this tool comments, diff and com, can be used effectively
to compare two files in UNIX. Which concludes this section."
"In the current section we'll be talking
about how we can archive content in Unix. And we might want to do that for
several purposes. For instance we might have very large data
files that we would like to compressed. Or we might have several data files that
might all belong to a common project. Or we might just want to exchange
information with a collaborator. So the commands that we'll be talking
about today will gzip, gunzip, bzip2, bunzip2 and tar, and
perhaps another one, zcat. Let's get started. Within our directory, Coursera,
we'll move into Plants. And for illustration purposes,
let's say that we wish to compress the content of the apple.genome
file, which can be quite much. So let's look at the file
of the apple.genome file. And we can compress that,
we can create an archive. Using the command gzip, gzip apple,genome. And these are two examples. So the operation was very fast. Let's look big comparison at the current size of the apple files. Actually, let's look at one of them. One observation is that you won't
see the file apple.genome anymore, it has been compressed to a file
that's called apple.genome.gz. And you can compare the size of
the original apple.genome file. Which was 65 kilobases, to its current
file current size compressed, 90. So that was a compression of about
3.5-fold, which will become very useful. I should mention that gzip uses
a particular compression algorithm which is Lempel-Ziv Once you've compressed the file,
we can obviously uncompress it and the command to do so, for
gzip compress file is gunzip. Simply type gunzip apple.genome.gz, and this will reverse the operation. So now when you were releasing
the files in this directory -dl. We will have retrieved your
original apple.genome file. So there's no loss of information to
the compression and then decompression. There's another one we used algorithm that
perhaps have even more compressive power. Especially, for genomic data sets. And that is bzip2. So we can similarly type
bzip2 apple.genome. And now we can view. This has created a file
with the extension bz2. And we can look at the size of
the new file and that 18kilob so that's sightly smaller than the one
that you're paying with the Compression. Just for
your information the bzip algorithm uses the Burrows-Wheeler compress
representation of strings. In a similar way once we have the file
zipped if we want to uncompress it we would use bunzip2
Apple.genome.visit2 and this will simply reverse the operation. So, now we retrieve the apple.genome
file with it's original size and it's original content. So as I've shown you gzip and
bzip only compress one file at a time. But sometimes we might want to
compress multiple files together. To do so, first we have to create
an archive that simply chains together, links together, all the files. And then a second operation would
be to compress the resulting file. In order to create the archive
we would simply tar, we would use the command tar,
to put together several files. So, in this case [COUGH] let's
say that we want to archive. All the parts in this directory. For actually apple.genes, apple.genome, and apple.samples. The command tar takes as arguments
first a number of options. I will explain each one of them. CVF followed by the name
of the target archive. So, let's call it apple, right,
.tar, with the extension tar. And followed by the list of names,
the list of files and or directories that will be included
in this particular archive. Going back to the commands,
back to the options, C specifies that tar is used
to pull together and archive. V is for
verbose to tell us the list of files, at one time that will be
included in the archive. And -F simply means that
there's going to be a file that indicates to the target file,
that follows apple dot tar. So let's perform this archiving in
which the three files, apple.genes, apple.genome, apple.samples, are going to
be put together in one unique archive. So you can see the v option gave us that
apple.genes has been added to the archive. Apple.genome has been added and
apple.samples. And looking at the list of files,
we have apple.tar. If we're looking at the list If
were looking at the sizes you can see that apple.tar contains
roughly the content and the size, the cumulative size of apple.genome,
genes and sample. So there hasn't been any
compression per say. For the compression part we are going
to type gzip the command that we just We just analyzed. Apple.tar. And that will give us apple dot tar dot gz which is now much reduced in size so
it's only 19 only 20 kilobytes. So, now we have an archive as I said
you might want to use this when you use the compress files on your,
in a systematic way on your system. When you want to share
data with collaborators or simply when you're preparing
a distribution software. But how do we open it up? Let's go back one directory And let's create a little directory
that I'm going to call sandbox and we're going to put a copy, copy apple. A copy of the archive in
the sandbox directory. We don't want to overwrite
the previous files. Now let's change to sandbox and
illustrate how we can open the archive. So first of all we have to unzip the file,
gunzup apple.tar.gz. And that happens quietly and the result is the apple.tar
file that we just looked at. Which has the same size as we saw earlier,
17 kilobytes. Now we use the tar command with
a different set of options to untar to open your archive. Tar-x which tells to extract
the files from the archive. B which says B for bows, so
list all the names of the files that were included in the archive, and
F that says from the following file apple.tar. And let's see what we get. So it says that it extracted
the files apple.genes, apple.genome, and apple.samples. And we can verify that by listing
the content of the current. And indeed we have apple.genes,
apple.genome, and apple.samples. And we still have a copy of the apple.tar. So we were able to retrieve
the content from the archive. I'm going to show you one more trick. So far we archived files along. So let me show you how we can tar and
we can archive entire directories. And for that operation, first I'm going
to clean up the current directory. So I'm going to remove
everything in this directory. That's one operation you
have to do carefully, but now I know that I don't need anything
in the current directory, so rm start. We're going to remove everything
in the local directory. Ls, okay, I want to move back to
the plants directory and from there on. From which I can see the apple,
peach, and pear directory. And let's say that I want to archive
everything that's in the apple directory, in it's directory structure. I can do it in a similar way with tar. Tar.-c, which says archive, put together. V, which says be verbose,
tell me everything that you're putting in. And f, which says now follows
the name of the target file. I'm going to call this appled.tar. So everything will be stored
in the appled.tar file. And then the name of the apple directory. So the content of the apple directory, including it's structure will be
stored in the AppleD.tar file. And you can see that, so
we open apple apple/apple.genes, and so on, including our previous tar. We can similarly, let's say basic to now
the apple, first let's look at the size. Ok. And now let's bzip2 appleD.tar which produced the appleD.tar.bz2 5. We remove these into sandbox. And in the sandbox, I'm going to
demonstrate how we open the archive and what we obtain. Cd to sandbox. The first operation again will
be to decompress the file. And we're typing bunzip2. AppleD.tar.bz2. And now we can enter the file,
tar -x, which means extract, v, be verbose, and f, from this file. AppleD.tar and this tells us that it takes after
the directory apple and its contents. Apple genes, apple genomes,
apple samples, apple samples sorted and the kind of genes. And indeed we can now look
at the directory apple and we can see all those files represent. One last operation for
working with archived content which becomes very convenient is ZCad. So that allows us to look inside a file
that has already been compressed. So for
that operation Let me gzip again just the apple.genome file. So now we have in the directory apple,
the file apple.genome .gz. Which is compressed. So a simple look at this file will probably not show it once,
it's a binary file. So this concludes our section
on archiving content in Unix."
"In this section we will start with some
practical applications and exercises that will allow you to go through some
of the commands that we've shown. Let's go back to our data example. As you might recall, we were talking about
three plant systems, toy apple, toy pear, and toy peach, and all the relevant
data was stored in the directory plants. And we have three types of information,
genome files which were multi-faceted files of
sequences of chromosomes or scaffolds. The second type of genomic information
was annotations of genes and their potential variants, these genes
could have one or multiple variants. And then we had the list of samples
that had been collected for each of the species. So these are the three
types of information corresponding to the three types of files
that we'll be performing operations on. And we'll try to answer a list
of practical questions. The first set of questions which
I will be showing in this section will refer to operations on the data
set pertaining to a single species. And for the following section, we'll be talking about operations that
apply to cross-species comparisons. So let's get started. Some examples of questions would be, how
many chromosomes are there in the genome? That would be one question. Another one would be, how many genes and
how many transcripts? How many variations of the genes
are there in each of the genomes? And we can further qualify this
last section by asking, for how many genes do we
have a single variant? For how many genes,
we have more than one variable. You might recall I was talking about
color was potentially being yellow, green or red. So let's see how we would try to answer
this samples given our dataset and we're going to exemplify with apple. We're in the core directory plants. And we're going to move on with
cd to the apple directory. And we'll try to answer
the first question, how many chromosomes
are there in the genome? You might recall that using the comment
more, we were able to visualize the content of the file apple.genome. And it revealed a multi fast eight
structure where each fast eight five, each fast eight sequence, each chromosomal
sequence was introduced by a header, a fast eight header line. It started with a greater dense
sign followed by identifier, and then everything was followed
by the actual sequence itself. In other words one easy way to determine
how many chromosomes we have or how many scaffolds we have in
the genome is to simply count how many header lines we have. Now, I'm going to point out
that one distinctive item in a fast header lines is the greater
than sign that precedes the header line. So, what we can do is,
we can simply do a grab. So, count how many times lines that start with the greater
than sign appear in the genome file. This is simply typed as grab in
quotes the greater than sign, which is the marker for
a header, a sequence header. In the genome, sorry,
in the apple.genome file. And this will simply list all of those. Going back and so
it shows us all of those. But it only shows us the listing. We want the number. To do the number we can apply one
of two different commands in UNIX. We can tie this to the wc-l which gives us the number of lines that get read from
the standard input, so tied it to. And it's going to tell us five. Alternatively, one option
of the grep command is to put grep-c,
which gives us the count, apple.genome. Which will be five. So that's a simple way of looking at how
many chromosomes we can find in a file. Let's try to answer the next question. How many genes are there
in the apple species? And how many variants there are. And we can find that information
in the file apple.genes. Let's remind ourselves. So, the gene name is
listed in column one and the variant name is listed in column two. Observe that there might
be multiple lines for the same gene because there might
be multiple variants of the gene. So simply cutting the first
column of the file. Cut -f1 apple.genes. The column that contains the gene
names and pipe in the tool more so we can look at it, will give us
two listings of the gene smell. Two listings of size,
three listing of color and so on. So what kind of comment can you use at this point to create only one copy for
each gene name? So we can count the number of genes. If you thought about unique then
that is a good option because gene names are actually
sorted within the list. So unique, so pipe in the output of the cut
F1 apple.genes to unique. Within it gives us a listing of the genes. And now piping that to a WC-L to give
us the number will give us that. So there are ten different
genes in the apple genome. Another way of doing this instead of using
the command unique would be sort uniquely. So sort and only report one occurrence for
each one nine for a number of occurrences of the same item. So that would give us color and
they're listed alphabetically. Color, shape, size, smell,
taste, with uppercase words being listed before the lowercase
words as I mentioned in the beginning. And we can again pipe that to
wc -l to see how many of them. And indeed,
we're replicating the answer which is ten. So now, we will do a similar operation
to identify the number of variants. To find the number of variants,
we're looking at column number two. So cot -F2 apple.genes, gives us the list of variances. Let's sort this uniquely,
actually first let's hide that and find the number, which is 16. Piped to wc-l. And now let's also sort uniquely to
see the number of distinct variants. And if you count those you're
going to see that it is 16. So, every variant was independently. And that's true, because indeed
the file contains only one line for each variant of a gene. So, the number of genes is 10,
and the number of variants is 60. Now, let's address the more
complicated option of how many genes have a single variant. And then the related question of how
many genes have multiple variants. So the information, Pertains to genes and variants and
is found in columns one and two. So, let's first cut just columns one and
two from the file apple.genes. Now, for each gene, we can obtain the
number of variants that are related to it. So the way we can do that is
by looking at column one, and every thing will be listed as many times
as the number of variants that it has. So if we now cut only the column one. We will have smell twice, size twice, color three times, and for instance
apple ten showing up just one time. So how do we extract that information
which will allow us to identify which genes have multiple variance versus
which genes have only one variant? A simple way is to use unique
just as we have done before. But instead of just listing
the nine you are going to count how many times it appears in
one particular location in the file. In the c file. So unique/c. So let's see what it gives us. So that shows smell, that smell appears
two times, size appears two times, color three times, appl4 one time,
appl5 one time, and so on. So from this listing, so as you've seen,
we already wrote a series a commands. From this listing we can
apply one more command to identify first all the Gs
that have one variant. We recognize them because they
would one listed in the column. So doing a graph of the pattern space,
one, and space, will give us only those lines
that have a single variant. We can further pipe that to a wc-l and
get 5. Or equivalently we can use the -c option
with grep and that's going to give us 5. So the number of genes that
have a single variant is five. Now we can simply say ten genes
that have ten total genes, minus five genes that
have a single variant, would leave us with exactly five
genes that have multiple variants. Or, we could do it the hard but
interesting way. So let's see what pipe of commands,
pipeline of commands, would allow us to retrieve
that information. Again we're copying column number one. We're using ""uniq-C"" to see how
many times the G name appears, which is the equivalent to
the number of variance it has. Now we want all lines except for
those that are listed just once. So one option to the common grep is -v. So -v says ignore the pattern and
report everything else. So grip-v open quotes,
one and another space, so that says take away, ignore,
all the lines that have this pattern. And that will show us, indeed, the five
genes that have at least two variants. And these are smell, size,
color, taste, and shape. And to make sure that
there are five of them, we can pipe the result through wc-l And
the result is five. So we answered some simple questions
related to the structure and organization of genes and genomes. Specifically we answered the question how
many chromosomes are there in the genome, starting from the fast eight file. And then how many genes and
transcript variants and how many genes have a single variant
versus how many have multiple variants. Which are simple and practical
questions in your general analysis. In the following section, we will
be addressing a couple of questions that relate to the too late
information across the species."
"In this section,
we will continue a list of exercises, or practical applications, and
this time we'll look at questions, that relate information
across the species. Across the three species that we
have represented in our example. So we are in our client's directory, and we would like to answer
the following questions. What plant systems contain a Smell gene? Or any other main gene? The second question would be,
what genes are in common, between toy apple, and toy pear? And what genes are specific to each? So let's try to answer these two,
or rather three, questions. You might recall that information
about the particular gene name, is stored in the species, that's
a star .genes file for each species. So to determine whether
the smell gene is present, in the two species all we have to
do is to apply a GREP operation. GREP. We're grepping from the word,
we're looking for the word smell, and it has to be capitalized. And were looking for
that in all directories, in the files that have
the extension genes. And then the output then shows us,
that it is present in apple, and that it's also present in peach. And that it has, just for
the information, so it has two variants. Looks like I got one. It has two variants in apple, and it has three variants in peach. And now we notice that just by mistake, it also retrieved the line
corresponding to the gene shape. For which smell one was
listed as one variant. So the GREB command, will give us all the lines that contain
somewhere within the line, the word smell. So we identified that smell, the gene
smell, appears in apple and peach. That's for the first question. Let's look at the other two questions. What genes are in common between,
toy apple and toy pear? And there are several ways
in which we can do this. The information that we're interested in,
is clearly in the genes file. And more precisely in the first column,
which is the gene name. So first, let's make some simpler files
that contain only the genes listed once, for each of those two species. So we'll type cut, if you remember, -F1 because we have tab delimited files. Apple, so apple.genes, and this operation will retrieve the first
column, so the names of the genes, each one of them listed, the same ones for
each variant that it has. You might recall that to obtain simply the
list of names, we can sort those uniquely. And we can create them, we can redirect
the output into a file that's simply called applegenes in
the current directory. Let's do the same, with the pear genes. I simply modify the above command line,
but you can type cut-f1 pear/pear.genes, pipe that to sort -u, and
save them in peargenes. And now there are two ways in
which we can compare them. A simple comparison would be
to apply the command COMM. Notice here, that we specifically
sorted the files which was one of the requirements for
applying the command COMM. So, now. If we're listing COMM, and
we want to see what genes are in common, then we want to ignore the genes, that
are unique to the first file apple genes. And also ignore the genes that are unique, the lines that are unique to
the second file, pear genes. Followed by the names of the files. And this gives us color,
shape, size and paste, as being the four genes that
are shared by the two species. So that's four. Another way to obtain this information, will be to simply notice that
each gene is listed once. So if we concatenate the two files,
apple genes and pear genes, we now have each gene
listed once for every species. We can simply sort the file to
bring the gene names together. So, now color shows up together one for
apple, one time for apple, and one time for pear. Shapes shows up in both species and so on. Whereas, articles such as,
genes such as apple10, apple4, appear only one time or pyres. Pyr1, just one time. So now that they are sorted, we can use
uniq-c, just as you've used before, to know how many times, the line appears
in this list at one particular location. And you'll see that
color appears two times, which means it was present
in both directories. Shape, again,
was present in both apple and pear. Whereas smell only appeared in one. And now finally, looking for
the pattern of two, so quotes space 2, and piping through more, will give us only those
genes that appear in both, that have two occurrences in our list. And that, what you see here would
tell us that there are four of them. Let's go to the next question,
or sub question, which is what genes
are specifically to each? So back to our COMM command. You might recall that we can play, we can
choose specific command line options, that can select or
reject certain combinations, or that can print some combinations. So for instance, if we want genes that
are specific to the apple species. We would say COMM, ignore all the lines
that appear only in the second, in the pear file. Ignore all the lines that
are in common to both files. And then we give that the list of files,
apple genes and pear genes. Pear genes. And this list smell apple10,
apple4, 5, 8 and 9 as appearing specifically in apple,
so those are apple specific genes. Conversely we can ignore all the entries, that appear only in the apple
file in the first file, and all the entries that
appear in both files, which will give us all
the pear specific genes. And those are pyr1, pyr2, 3, and 4. So I've demonstrated some ways,
we can obtain basic information about genomic data,
by using the command line arguments, that the basic UNIX commands
that we've illustrated before. You have a more extensive list of
exercises at the end of this chapter. At the end of this chapter. I encourage you apply them to each of
the systems, apple, pear and peach, and then to look at the last set of questions,
that apply across the three systems. Additional exercises will be
provided in the on-line supplement. Thank you very much."
