![Version](https://img.shields.io/github/v/release/DCMLab/beethoven_piano_sonatas?display_name=tag)
[![DOI](https://zenodo.org/badge/383397003.svg)](https://zenodo.org/badge/latestdoi/383397003)
![GitHub repo size](https://img.shields.io/github/repo-size/DCMLab/beethoven_piano_sonatas)
![License](https://img.shields.io/badge/license-CC%20BY--NC--SA%204.0-9cf)

This is a README file for a data repository originating from the [DCML corpus initiative](https://github.com/DCMLab/dcml_corpora)
and serves as welcome page for both 

* the GitHub repo [https://github.com/DCMLab/beethoven_piano_sonatas](https://github.com/DCMLab/beethoven_piano_sonatas) and the corresponding
* documentation page [https://dcmlab.github.io/beethoven_piano_sonatas](https://dcmlab.github.io/beethoven_piano_sonatas)

For information on how to obtain and use the dataset, please refer to [this documentation page](https://dcmlab.github.io/beethoven_piano_sonatas/introduction).


<!-- TOC -->
* [Ludwig van Beethoven - Piano Sonatas (A corpus of annotated scores)](#ludwig-van-beethoven---piano-sonatas-a-corpus-of-annotated-scores)
  * [Version history](#version-history)
  * [Getting the data](#getting-the-data)
    * [With full version history](#with-full-version-history)
    * [Without full version history](#without-full-version-history)
  * [Data Formats](#data-formats)
    * [Opening Scores](#opening-scores)
    * [Opening TSV files in a spreadsheet](#opening-tsv-files-in-a-spreadsheet)
    * [Loading TSV files in Python](#loading-tsv-files-in-python)
  * [How to read `metadata.tsv`](#how-to-read-metadatatsv)
    * [File information](#file-information)
    * [Composition information](#composition-information)
    * [Score information](#score-information)
    * [Identifiers](#identifiers)
  * [Generating all TSV files from the scores](#generating-all-tsv-files-from-the-scores)
  * [Questions, Suggestions, Corrections, Bug Reports](#questions-suggestions-corrections-bug-reports)
  * [License](#license)
  * [Naming convention](#naming-convention)
  * [Overview](#overview)
<!-- TOC -->

# Ludwig van Beethoven - Piano Sonatas (A corpus of annotated scores)

This corpus of annotated [MuseScore](https://musescore.org) files has been created within
the [DCML corpus initiative](https://github.com/DCMLab/dcml_corpora) and employs
the [DCML harmony annotation standard](https://github.com/DCMLab/standards). It is one out of nine similar corpora that
have been grouped together
to [An Annotated Corpus of Tonal Piano Music from the Long 19th Century](https://doi.org/10.5281/zenodo.7483349)
which comes with a data report that is currently in press at Empirical Musicology Review.

## Version history

See the [GitHub releases](https://github.com/DCMLab/beethoven_piano_sonatas/releases).

## Getting the data

### With full version history

The dataset is version-controlled via [git](https://git-scm.com/). In order to download the files with all
revisions they have gone through, git needs to be installed on your machine. Then you can clone this 
repository using the command

```bash
git clone https://github.com/DCMLab/beethoven_piano_sonatas.git
```

### Without full version history

If you are only interested in the current version of the corpus, you can simply download and unpack
[this ZIP file](https://github.com/DCMLab/beethoven_piano_sonatas/archive/refs/heads/main.zip).


## Data Formats

Each piece in this corpus is represented by four files with identical names, each in its own folder. For example, the
first movement of the first sonata Op. 2 no. 1 has the following files:

* `MS3/01-1.mscx`: Uncompressed MuseScore file including the music and annotation labels.
* `notes/01-1.tsv`: A table of all note heads contained in the score and their relevant features (not each of them represents an onset, some are tied together)
* `measures/01-1.tsv`: A table with relevant information about the measures in the score.
* `harmonies/01-1.tsv`: A list of the included harmony labels (including cadences and phrases) with their positions in
  the score.

### Opening Scores

After navigating to your local copy, you can open the scores in the folder `MS3` with the free and open source score
editor [MuseScore](https://musescore.org). Please note that the scores have been edited, annotated and tested with
[MuseScore 3.6.2](https://github.com/musescore/MuseScore/releases/tag/v3.6.2). 
MuseScore 4 has since been released and preliminary tests suggest that it renders them correctly.

### Opening TSV files in a spreadsheet

Tab-separated value (TSV) files are like Comma-separated value (CSV) files and can be opened with most modern text
editors. However, for correctly displaying the columns, you might want to use a spreadsheet or an addon for your
favourite text editor. When you use a spreadsheet such as Excel, it might annoy you by interpreting fractions as
dates. This can be circumvented by using `Data --> From Text/CSV` or the free alternative
[LibreOffice Calc](https://www.libreoffice.org/download/download/). Other than that, TSV data can be loaded with
every modern programming language.

### Loading TSV files in Python

Since the TSV files contain null values, lists, fractions, and numbers that are to be treated as strings, you may want
to use this code to load any TSV files related to this repository (provided you're doing it in Python). After a quick
`pip install -U ms3` (requires Python 3.10) you'll be able to load any TSV like this:

```python
import ms3

labels = ms3.load_tsv('harmonies/01-1.tsv')
notes = ms3.load_tsv('notes/01-1.tsv')
```

## How to read `metadata.tsv`

This section explains the meaning of the columns contained in `metadata.tsv`.

### File information

| column                 | content                                                    |
|------------------------|------------------------------------------------------------|
| **fname**              | name without extension (for referencing related files)     |
| **rel_path**           | relative file path of the score, including extension       |
| **subdirectory**       | folder where the score is located                          |    
| **last_mn**            | last measure number                                        |
| **last_mn_unfolded**   | number of measures when playing all repeats                |
| **length_qb**          | length of the piece, measured in quarter notes             |
| **length_qb_unfolded** | length of the piece when playing all repeats               |
| **volta_mcs**          | measure counts of first and second endings                 |
| **all_notes_qb**       | summed up duration of all notes, measured in quarter notes |
| **n_onsets**           | number of note onsets                                      |
| **n_onset_positions**  | number of unique note onsets ("slices")                    |


### Composition information

| column             | content                   |
|--------------------|---------------------------|
| **composer**       | composer name             |
| **workTitle**      | work title                |
| **composed_start** | earliest composition date |
| **composed_end**   | latest composition date   |
| **workNumber**     | Catalogue number(s)       |
| **movementNumber** | 1, 2, or 3                |
| **movementTitle**  | title of the movement     |

### Score information

| column          | content                                                |
|-----------------|--------------------------------------------------------|
| **label_count** | number of chord labels                                 |
| **KeySig**      | key signature(s) (negative = flats, positive = sharps) |
| **TimeSig**     | time signature(s)                                      |
| **musescore**   | MuseScore version                                      |
| **source**      | URL to the first typesetter's file                     |
| **typesetter**  | first typesetter                                       |
| **annotators**  | creator(s) of the chord labels                         |
| **reviewers**   | reviewer(s) of the chord labels                        |

### Identifiers

These columns provide a mapping between multiple identifiers for the sonatas (not for individual movements).

| column          | content                                                                                                 |
|-----------------|---------------------------------------------------------------------------------------------------------|
| **wikidata**    | URL of the [WikiData](https://www.wikidata.org/) item                                                   |
| **viaf**        | URL of the Virtual International Authority File ([VIAF](http://viaf.org/)) entry                        |
| **musicbrainz** | [MusicBrainz](https://musicbrainz.org/) identifier                                                      |
| **imslp**       | URL to the wiki page within the International Music Score Library Project ([IMSLP](https://imslp.org/)) |


## Generating all TSV files from the scores

When you have made changes to the scores and want to update the TSV files accordingly, you can use the following
command (provided you have pip-installed [ms3](https://github.com/johentsch/ms3)):

```python
ms3 extract -M -N -X -D # for measures, notes, expanded annotations, and metadata
```

If, in addition, you want to generate the reviewed scores with out-of-label notes colored in red, you can do

```python
ms3 review -M -N -X -D # for extracting measures, notes, expanded annotations, and metadata
```

By adding the flag `-c` to the review command, it will additionally compare the (potentially modified) annotations in the score
with the ones currently present in the harmonies TSV files and reflect the comparison in the reviewed scores.

## Questions, Suggestions, Corrections, Bug Reports

For questions, remarks etc., please create an issue and feel free to fork and submit pull requests.

## License

Creative Commons Attribution-ShareAlike 4.0 International License ([CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/)).


## Naming convention

The file names listed in the [Overview](#overview) below refer to the following numbering of the sonatas from 1-32.
For example, the four movements of sonata no. 1 are named `01-1`, `01-2`, `01-3`, and `01-4`.

| Number                              | Opus (Name)                       |
|-------------------------------------|-----------------------------------|
| Piano Sonata No.1 in F minor        | Op.2 No.1                         |
| Piano Sonata No.2 in A major        | Op.2 No.2                         |
| Piano Sonata No.3 in C major        | Op.2 No.3                         |
| Piano Sonata No.4 in E-flat major   | Op.7 ("Grand Sonata")             |
| Piano Sonata No.5 in C minor        | Op.10 No.1 ("Little Pathétique")  |
| Piano Sonata No.6 in F major        | Op.10 No.2                        |
| Piano Sonata No.7 in D major        | Op.10 No.3                        |
| Piano Sonata No.8 in C minor        | Op.13 ("Pathétique")              |
| Piano Sonata No.9 in E major        | Op.14 No.1                        |
| Piano Sonata No.10 in G major       | Op.14 No.2                        |
| Piano Sonata No.11 in B-flat major  | Op.22                             |
| Piano Sonata No.12 in A-flat major  | Op.26 ("Funeral March")           |
| Piano Sonata No.13 in E-flat major  | Op.27 No.1 ("Quasi una fantasia") |
| Piano Sonata No.14 in C-sharp minor | Op.27 No.2 ("Moonlight")          |
| Piano Sonata No.15 in D major       | Op.28 ("Pastoral")                |
| Piano Sonata No.16 in G major       | Op.31 No.1                        |
| Piano Sonata No.17 in D minor       | Op.31 No.2 ("The Tempest")        |
| Piano Sonata No.18 in E-flat major  | Op.31 No.3 ("The Hunt")           |
| Piano Sonata No.19 in G minor       | Op.49 No.1 ("Leichte Sonata")     |
| Piano Sonata No.20 in G major       | Op.49 No.2 ("Leichte Sonata")     |
| Piano Sonata No.21 in C major       | Op.53 ("Waldstein")               |
| Piano Sonata No.22 in F major       | Op.54                             |
| Piano Sonata No.23 in F minor       | Op.57 ("Appassionata")            |
| Piano Sonata No.24 in F-sharp major | Op.78 ("A Thérèse")               |
| Piano Sonata No.25 in G major       | Op.79 ("Cuckoo")                  |
| Piano Sonata No.26 in E-flat major  | Op.81a ("Les adieux")             |
| Piano Sonata No.27 in E minor       | Op.90                             |
| Piano Sonata No.28 in A major       | Op.101                            |
| Piano Sonata No.29 in B-flat major  | Op.106 ("Hammerklavier")          |
| Piano Sonata No.30 in E major       | Op.109                            |
| Piano Sonata No.31 in A-flat major  | Op.110                            |
| Piano Sonata No.32 in C minor       | Op.111                            |


## Overview
|file_name|measures|labels|standard|                    annotators                    |           reviewers            |
|---------|-------:|-----:|--------|--------------------------------------------------|--------------------------------|
|01-1     |     152|   241|2.3.0   |Lars & Ya-Chuan (2.2.0), John Heilig (2.3.0)      |AN                              |
|01-2     |      61|   200|2.3.0   |Lars & Ya-Chuan                                   |Adrian Nagel, Victor Zheng      |
|01-3     |      73|   132|2.3.0   |Daniel Grote (2.2.0), Adrian Nagel (2.3.0)        |Adrian Nagel, Victor Zheng      |
|01-4     |     196|   355|2.3.0   |Daniel Grote (2.2.0), Adrian Nagel (2.3.0)        |Adrian Nagel, Victor Zheng      |
|02-1     |     336|   479|2.3.0   |Lydia Carlisi (2.2.0), Victor Zheng (2.3.0)       |AN, VZ                          |
|02-2     |      80|   244|2.3.0   |Lydia Carlisi (2.2.0), Victor Zheng (2.3.0)       |AN, VZ                          |
|02-3     |      68|   124|2.3.0   |Lydia Carlisi (2.2.0), Victor Zheng (2.3.0)       |AN, VZ                          |
|02-4     |     187|   339|2.3.0   |Lydia Carlisi (2.2.0), Victor Zheng (2.3.0)       |AN, VZ                          |
|03-1     |     257|   487|2.3.0   |Lydia Carlisi (2.2.0), John Heilig (2.3.0)        |AN                              |
|03-2     |      82|   233|2.3.0   |Lydia Carlisi (2.2.0), Adrian Nagel (2.3.0)       |Victor Zheng                    |
|03-3     |     127|   198|2.3.0   |Lydia Carlisi (2.2.0), Adrian Nagel (2.3.0)       |Victor Zheng                    |
|03-4     |     312|   793|2.3.0   |Lydia Carlisi (2.2.0), Adrian Nagel (2.3.0)       |Victor Zheng                    |
|04-1     |     362|     0|        |                                                  |                                |
|04-2     |      90|     0|        |                                                  |                                |
|04-3     |     150|     0|        |                                                  |                                |
|04-4     |     186|     0|        |                                                  |                                |
|05-1     |     284|   310|2.3.0   |Adrian Nagel (2.2.0), Hanné Becker (2.3.0)        |AN                              |
|05-2     |     112|   252|2.3.0   |Adrian Nagel (2.3.0)                              |Victor Zheng                    |
|05-3     |     122|   313|2.3.0   |Adrian Nagel (2.3.0)                              |Victor Zheng                    |
|06-1     |     202|   338|2.3.0   |Adrian Nagel (2.2.0), Amelia Brey (2.3.0)         |AB, AN                          |
|06-2     |     170|   236|2.3.0   |Gabriele Ortiz Würth (2.2.0), Adrian Nagel (2.3.0)|Johannes Hentschel, Victor Zheng|
|06-3     |     150|   308|2.3.0   |Adrian Nagel (2.3.0)                              |Victor Zheng                    |
|07-1     |     344|   527|2.3.0   |Lydia Carlisi (2.2.0), Amelia Brey (2.3.0)        |AB                              |
|07-2     |      87|   218|2.3.0   |Lydia Carlisi (2.2.0), Adrian Nagel (2.3.0)       |Victor Zheng                    |
|07-3     |      86|    92|2.3.0   |Lydia Carlisi (2.2.0), Adrian Nagel (2.3.0)       |Victor Zheng                    |
|07-4     |     113|   266|2.3.0   |Lydia Carlisi (2.2.0), Adrian Nagel (2.3.0)       |Victor Zheng                    |
|08-1     |     310|   503|2.3.0   |Lydia Carlisi (2.2.0), John Heilig (2.3.0)        |AN                              |
|08-2     |      73|   143|2.3.0   |Lydia Carlisi (2.2.0), Adrian Nagel (2.3.0)       |Victor Zheng                    |
|08-3     |     210|   365|2.3.0   |Lydia Carlisi (2.2.0), Adrian Nagel (2.3.0)       |Victor Zheng                    |
|09-1     |     161|   351|2.3.0   |Lydia Carlisi (2.2.0), Amelia Brey (2.3.0)        |AB, AN                          |
|09-2     |     178|   235|2.3.0   |Lydia Carlisi (2.2.0), Adrian Nagel (2.3.0)       |Victor Zheng                    |
|09-3     |     131|   262|2.3.0   |Lydia Carlisi (2.2.0), Adrian Nagel (2.3.0)       |Victor Zheng                    |
|10-1     |     200|   355|2.3.0   |Daniel Grote (2.2.0), John Heilig (2.3.0)         |AN                              |
|10-2     |      90|   330|2.3.0   |Daniel Grote (2.2.0), Adrian Nagel (2.3.0)        |Victor Zheng (2.3.0)            |
|10-3     |     254|   318|2.3.0   |Adrian Nagel (2.3.0)                              |Victor Zheng                    |
|11-1     |     199|     0|        |                                                  |                                |
|11-2     |      77|     0|        |                                                  |                                |
|11-3     |      46|     0|        |                                                  |                                |
|11-4     |     199|     0|        |                                                  |                                |
|12-1     |     219|     0|        |                                                  |                                |
|12-2     |      95|     0|        |                                                  |                                |
|12-3     |      75|     0|        |                                                  |                                |
|12-4     |     170|     0|        |                                                  |                                |
|13-1     |      86|     0|        |                                                  |                                |
|13-2     |     140|     0|        |                                                  |                                |
|13-3     |      26|     0|        |                                                  |                                |
|13-4     |     285|     0|        |                                                  |                                |
|14-1     |      69|     0|        |                                                  |                                |
|14-2     |      60|     0|        |                                                  |                                |
|14-3     |     201|     0|        |                                                  |                                |
|15-1     |     462|     0|        |                                                  |                                |
|15-2     |     103|     0|        |                                                  |                                |
|15-3     |      94|     0|        |                                                  |                                |
|15-4     |     210|     0|        |                                                  |                                |
|16-1     |     325|   303|2.3.0   |Adrian Nagel (2.2.0), Hanné Becker (2.3.0)        |AN                              |
|16-2     |     119|   285|2.3.0   |Adrian Nagel (2.2.0), Amelia Brey (2.3.0)         |VZ, AB                          |
|16-3     |     275|   703|2.3.0   |Adrian Nagel (2.3.0)                              |VZ                              |
|17-1     |     228|   352|2.3.0   |Adrian Nagel (2.2.0), Hanné Becker (2.3.0)        |AN                              |
|17-2     |     103|   223|2.3.0   |Adrian Nagel (2.3.0)                              |Victor Zheng                    |
|17-3     |     399|   460|2.3.0   |Adrian Nagel (2.3.0)                              |Victor Zheng                    |
|18-1     |     253|   269|2.3.0   |Adrian Nagel (2.2.0), Hanné Becker (2.3.0)        |AN                              |
|18-2     |     169|   273|2.3.0   |Adrian Nagel (2.3.0)                              |Victor Zheng                    |
|18-3     |      61|   178|2.3.0   |Adrian Nagel (2.3.0)                              |Victor Zheng                    |
|18-4     |     333|   410|2.3.0   |Adrian Nagel (2.3.0)                              |Victor Zheng                    |
|19-1     |     110|   193|2.3.0   |Daniel Grote (2.2.0), Hanné Becker (2.3.0)        |AN (2.2.0 + 2.3.0)              |
|19-2     |     164|   384|2.3.0   |Daniel Grote (2.2.0), Adrian Nagel (2.3.0)        |Adrian Nagel, Victor Zheng      |
|20-1     |     122|   286|2.3.0   |Lydia Carlisi (2.2.0), John Heilig (2.3.0)        |AN                              |
|20-2     |     120|   169|2.3.0   |Lydia Carlisi (2.2.0), Adrian Nagel (2.3.0)       |Victor Zheng                    |
|21-1     |     302|   616|2.3.0   |Adrian Nagel (2.2.0), Amelia Brey (2.3.0)         |AB, AN                          |
|21-2     |      28|    82|2.3.0   |Adrian Nagel (2.3.0)                              |VZ                              |
|21-3     |     543|   739|2.3.0   |Adrian Nagel (2.3.0)                              |Victor Zheng                    |
|23-1     |     262|   434|2.3.0   |Daniel Grote (2.2.0), Hanné Becker (2.3.0)        |AN                              |
|23-2     |      97|   220|2.3.0   |Daniel Grote (2.2.0), Adrian Nagel (2.3.0)        |Victor Zheng                    |
|23-3     |     361|   395|2.3.0   |Daniel Grote (2.2.0), Adrian Nagel (2.3.0)        |Victor Zheng                    |
|24-1     |     105|   286|2.3.0   |Adrian Nagel (2.2.0), Hanné Becker (2.3.0)        |AN                              |
|24-2     |     183|   317|2.3.0   |Adrian Nagel (2.3.0)                              |Victor Zheng                    |
|26-1     |     255|   537|2.3.0   |Adrian Nagel (2.2.0), John Heilig (2.3.0)         |AN                              |
|26-2     |      42|   127|2.3.0   |Adrian Nagel (2.2.0), Amelia Brey (2.3.0)         |AB, Victor Zheng                |
|26-3     |     196|   317|2.3.0   |Adrian Nagel (2.3.0)                              |VZ                              |
|30-1     |      99|   252|2.3.0   |Adrian Nagel (2.2.0), Amelia Brey (2.3.0)         |AB, AN                          |
|30-2     |     177|   320|2.3.0   |Adrian Nagel (2.3.0)                              |Victor Zheng                    |
|30-3     |     203|   656|2.3.0   |Adrian Nagel (2.3.0)                              |Victor Zheng                    |
|31-1     |     116|   339|2.3.0   |Adrian Nagel (2.2.0), John Heilig (2.3.0)         |AN                              |
|31-2     |     158|   201|2.3.0   |Adrian Nagel, Victor Zheng (2.3.0)                |AN                              |
|31-3     |     212|   644|2.3.0   |Adrian Nagel (2.2.0), Victor Zheng (2.3.0)        |AN                              |
|32-1     |     157|   576|2.3.0   |Adrian Nagel (2.2.0), Amelia Brey (2.3.0)         |AB, AN                          |
|32-2     |     177|   869|2.3.0   |Adrian Nagel (2.2.0), Victor Zheng (2.3.0)        |AN                              |


*Overview table automatically updated using [ms3](https://ms3.readthedocs.io/).*
