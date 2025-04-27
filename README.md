![Version](https://img.shields.io/github/v/release/DCMLab/beethoven_piano_sonatas?display_name=tag)
[![DOI](https://zenodo.org/badge/383397003.svg)](https://doi.org/10.5281/zenodo.7473560)
![GitHub repo size](https://img.shields.io/github/repo-size/DCMLab/beethoven_piano_sonatas)
![License](https://img.shields.io/badge/license-CC%20BY--NC--SA%204.0-9cf)


This is a README file for a data repository originating from the [DCML corpus initiative](https://github.com/DCMLab/dcml_corpora)
and serves as welcome page for both 

* the GitHub repo [https://github.com/DCMLab/beethoven_piano_sonatas](https://github.com/DCMLab/beethoven_piano_sonatas) and the corresponding
* documentation page [https://dcmlab.github.io/beethoven_piano_sonatas](https://dcmlab.github.io/beethoven_piano_sonatas)

For information on how to obtain and use the dataset, please refer to [this documentation page](https://dcmlab.github.io/beethoven_piano_sonatas/introduction).

When you use (parts of) this dataset in your work, please read and cite the accompanying data report:

_Hentschel, J., Rammos, Y., Neuwirth, M., Moss, F. C., & Rohrmeier, M. (2024). An annotated corpus of tonal piano music 
from the long 19th century. Empirical Musicology Review, 18(1), 84–95. https://doi.org/10.18061/emr.v18i1.8903_

This corpus forms part of the larger [Distant Listening Corpus](https://github.com/DCMLab/distant_listening_corpus)
which constitutes a data infrastructure the data report of which has implications for the present corpus, too:

_Hentschel, J., Rammos, Y., Neuwirth, M., & Rohrmeier, M. (2025). A corpus and a modular infrastructure for the 
empirical study of (an)notated music. Scientific Data, 12(1), 685. https://doi.org/10.1038/s41597-025-04976-z_

# Ludwig van Beethoven – Piano Sonatas


## Getting the data

* download repository as a [ZIP file](https://github.com/DCMLab/beethoven_piano_sonatas/archive/main.zip)
* download a [Frictionless Datapackage](https://specs.frictionlessdata.io/data-package/) that includes concatenations
  of the TSV files in the four folders (`measures`, `notes`, `chords`, and `harmonies`) and a JSON descriptor:
  * [beethoven_piano_sonatas.zip](https://github.com/DCMLab/beethoven_piano_sonatas/releases/latest/download/beethoven_piano_sonatas.zip)
  * [beethoven_piano_sonatas.datapackage.json](https://github.com/DCMLab/beethoven_piano_sonatas/releases/latest/download/beethoven_piano_sonatas.datapackage.json)
* clone the repo: `git clone https://github.com/DCMLab/beethoven_piano_sonatas.git` 


## Data Formats

Each piece in this corpus is represented by five files with identical name prefixes, each in its own folder. 
For example, the first movement of the first sonata Op. 2 no. 1 has the following files:

* `MS3/01-1.mscx`: Uncompressed MuseScore 3.6.2 file including the music and annotation labels.
* `notes/01-1.notes.tsv`: A table of all note heads contained in the score and their relevant features (not each of them represents an onset, some are tied together)
* `measures/01-1.measures.tsv`: A table with relevant information about the measures in the score.
* `chords/01-1.chords.tsv`: A table containing layer-wise unique onset positions with the musical markup (such as dynamics, articulation, lyrics, figured bass, etc.).
* `harmonies/01-1.harmonies.tsv`: A table of the included harmony labels (including cadences and phrases) with their positions in the score.

Each TSV file comes with its own JSON descriptor that describes the meanings and datatypes of the columns ("fields") it contains,
follows the [Frictionless specification](https://specs.frictionlessdata.io/tabular-data-resource/),
and can be used to validate and correctly load the described file. 

### Opening Scores

After navigating to your local copy, you can open the scores in the folder `MS3` with the free and open source score
editor [MuseScore](https://musescore.org). Please note that the scores have been edited, annotated and tested with
[MuseScore 3.6.2](https://github.com/musescore/MuseScore/releases/tag/v3.6.2). 
MuseScore 4 has since been released which renders them correctly but cannot store them back in the same format.

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

labels = ms3.load_tsv("harmonies/01-1.harmonies.tsv")
notes = ms3.load_tsv("notes/01-1.notes.tsv"")
```


## Version history

See the [GitHub releases](https://github.com/DCMLab/beethoven_piano_sonatas/releases).

## Questions, Suggestions, Corrections, Bug Reports

Please [create an issue](https://github.com/DCMLab/beethoven_piano_sonatas/issues) and/or feel free to fork and submit pull requests.

## Cite as

> Hentschel, J., Rammos, Y., Neuwirth, M., Moss, F. C., & Rohrmeier, M. (2024). An annotated corpus of tonal piano music from the long 19th century. Empirical Musicology Review, 18(1), 84–95. https://doi.org/10.18061/emr.v18i1.8903

## License

Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License ([CC BY-NC-SA 4.0](https://creativecommons.org/licenses/by-nc-sa/4.0/)).

![cc-by-nc-sa-image](https://licensebuttons.net/l/by-nc-sa/4.0/88x31.png)

## File naming convention

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
|07-4     |     113|   268|2.3.0   |Lydia Carlisi (2.2.0), Adrian Nagel (2.3.0)       |Victor Zheng                    |
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
|18-1     |     253|   268|2.3.0   |Adrian Nagel (2.2.0), Hanné Becker (2.3.0)        |AN                              |
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
|29-1     |     405|     0|        |                                                  |                                |
|29-2     |     175|     0|        |                                                  |                                |
|29-3     |     187|     0|        |                                                  |                                |
|29-4     |     400|     0|        |                                                  |                                |
|30-1     |      99|   252|2.3.0   |Adrian Nagel (2.2.0), Amelia Brey (2.3.0)         |AB, AN                          |
|30-2     |     177|   320|2.3.0   |Adrian Nagel (2.3.0)                              |Victor Zheng                    |
|30-3     |     203|   656|2.3.0   |Adrian Nagel (2.3.0)                              |Victor Zheng                    |
|31-1     |     116|   339|2.3.0   |Adrian Nagel (2.2.0), John Heilig (2.3.0)         |AN                              |
|31-2     |     158|   201|2.3.0   |Adrian Nagel, Victor Zheng (2.3.0)                |AN                              |
|31-3     |     212|   644|2.3.0   |Adrian Nagel (2.2.0), Victor Zheng (2.3.0)        |AN                              |
|32-1     |     157|   576|2.3.0   |Adrian Nagel (2.2.0), Amelia Brey (2.3.0)         |AB, AN                          |
|32-2     |     177|   869|2.3.0   |Adrian Nagel (2.2.0), Victor Zheng (2.3.0)        |AN                              |


*Overview table automatically updated using [ms3](https://ms3.readthedocs.io/).*
