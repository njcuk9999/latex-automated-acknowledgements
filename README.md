# latex-automated-acknowledgements
A tex file that if included manages acknowledgements (i.e. like bibtex for acknowledgements)

## How to in a latex/tex document

In any tex file you wish to use this add:
\input{ {PATH} + /acknowledgement_refs}

where {PATH} is the location where acknowledgement_refs.tex is located
i.e. for same folder ./acknowledgement_refs will suffice

This file will allow use of the /acknowledge command

## Command structure

Use in the following form:
```
\acknowledge{2MASS}
```

Displays the following in text:

```
This paper makes use of data products from the Two Micron All Sky Survey\citep{Skrutskie2006}, which is a joint project of the University of Massachusetts and the Infrared Processing and Analysis Center/California Institute of Technology, funded by the National Aeronautics and Space Administration and the National Science Foundation.
```

## Writing new acknowledgements

add key as follows to \pgfkeys{}
```
\pgfkeys{/key/.code = {value}}
```
### Example
```
\pgfkeys{/ADS/.code = {This \acknowledgetype made use of NASA's Astrophysics Data System.}}
```
cited in text as:
```
\acknowledge{ADS}
```
and displays the following in text:
```
This paper made use of NASA's Astrophysics Data System.
```

### Acknowledgement type

Note most acknowledgements use "This paper..." or "This work..." or "This Thesis..." to remove this as a problem in writing references there is a command 
```
\acknowledgetype
```
use this in place of "paper", "work" or "Thesis" is the value

for example:
```
\pgfkeys{/ADS/.code = {This \acknowledgetype made use of NASA's Astrophysics Data System.}}
```

To set which word this goes to set the 
```
\newcommand{\acknowledgetype}{thesis\,\,}
```
in acknowledgement_refs.tex

### Warnings

1) Some of the example acknowledgements will need hyperref package to use /url

2) Some will have a reference
   - the references are commented out below (in standard bibtex format) for convience
   - copy these into your bib file to use these (or edit the references to remove the \cite


### Some more Examples of acknowledgements

```
\pgfkeys{/MAST/.code = {Some/all of the data presented in this \acknowledgetype were obtained from the Mikulski Archive for Space Telescopes (MAST). STScI is operated by the Association of Universities for Research in Astronomy, Inc., under NASA contract NAS5-26555. Support for MAST for non-HST data is provided by the NASA Office of Space Science via grant NNX13AC07G and by other grants and contracts.}}

\pgfkeys{/SIMBAD/.code = {This \acknowledgetype made use of the SIMBAD database, operated at CDS, Strasbourg, France.}}

\pgfkeys{/SpeX/.code = {This \acknowledgetype has benefitted from the SpeX Prism Spectral Libraries, maintained by Adam Burgasser at \url{http://pono.ucsd.edu/~adam/browndwarfs/spexprism}.}}

\pgfkeys{/VizieR/.code = {This \acknowledgetype made use of the VizieR catalogue access tool, CDS, Strasbourg, France. }}

\pgfkeys{/WebPlotDigitizer/.code = {This \acknowledgetype made use of WebPlotDigitizer (\url{http://arohatgi.info/WebPlotDigitizer/}) by Ankit Rohatgi.}}
```
