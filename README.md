Simple Video Corpus
===================
This is a simple video corpus created for my friend Nik at the office of the
[Swedish Sign Language Lexicon].

It is inspired by the [Swedish Sign Language Corpus] that was built by myself
and Patrick Hansson, but this version is far simpler and more experimental. It
features vertically scrolling annotations (similar to movie end credits), and
very few dependencies.

[Swedish Sign Language Lexicon]: https://teckensprakslexikon.su.se/
[Swedish Sign Language Corpus]: https://teckensprakskorpus.su.se/


Data Structures
===============
Data is stored in the `x/` directory. This script also contains a couple of
scripts for converting .eaf files (ELAN annotation files) to the format needed
for this little web corpus. (The tools are named 'annot' and 'cheaf', have a
look at 'annot' for info on how to use them.)

For each video there's a bunch of files. There's a `x/VIDEO` directory, which
contains the annotations in .tsv (tab-separated value) file format (which each
ELAN tier in a separate file), belonging to that dir is a `x/VIDEO.tsv` index
file indicating which annotations which annotations and video files are
available. It looks something like this:

    x/sslc01_003.tsv
    x/sslc01_003
      tier_1.tsv
      tier_2.tsv
      ...
    x/sslc01_003_s001_b.mp4
    x/sslc01_003_s002_b.mp4


The Format of `sslc01_003.tsv`
==============================
The first line contains the names of video files, separated by tabs. All
subsequent lines contain three values:

  1. The ELAN tier name
  2. The name of the .tsv file containing the annotations
  3. The number of annotations in the file

Note that fields are tab separated, while values may contain space, they cannot
contain tab or newline. An example (`x/sslc01_003.tsv`):

    sslc01_003_s001_b.mp4	sslc01_003_s002_b.mp4
    Artikulator_DH S2	sslc01_003/artikulator_dh_s2.tsv	623
    Munrörelse S1	sslc01_003/munrorelse_s1.tsv	266
    ...

And here's an annotation file example (`x/sslc01_003/glosa_dh_s1.tsv`):

    10.47	1.18	PU@g[G]
    11.83	0.05	PI[AB]
    12.05	0.13	LÄNGESEDAN[AB]
    12.3	0.08	LITE[AB]
    12.58	0.48	DÅLIG[JJ]
    13.28	0.15	LÄNGESEDAN[AB]
    ...

The start and length time values are expressed in seconds. The annotations
(above gloss). There is no header line in the file.

<!--[eof]-->
