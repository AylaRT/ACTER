# ACTER Annotated Corpora for Term Extraction Research, version 1.4

ACTER is a manually annotated dataset for term extraction, covering 3 languages (English, French, and Dutch), 
and 4 domains (corruption, dressage, heart failure, and wind energy).

**Readme structure:**
1. General
2. Abbreviations
3. Data Structure
4. Annotations
5. Additional Information
6. Updates
7. Error Reporting
8. License



## 1. General

* **Creator**: Ayla Rigouts Terryn 
* **Association**: LT3 Language and Translation Technology Team, Ghent University
* **Date of creation version 1.0**: 17/12/2019
* **Date of creation current version 1.4**: 15/07/2020 
* **Last updated**: 13/05/2020
* **Contact**: ayla.rigoutsterryn@ugent.be
* **Context**: Ayla Rigouts Terryn's PhD project + first TermEval shared task (CompuTerm2020)
* **Shared Task**: see https://termeval.ugent.be; workshop proceedings with overview paper at 
                    https://lrec2020.lrec-conf.org/media/proceedings/Workshops/Books/COMPUTERM2020book.pdf)
* **Annotation Guidelines**: http://hdl.handle.net/1854/LU-8503113
* **Source**: https://github.com/AylaRT/ACTER
* **License**: Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International (CC BY-NC-SA 4.0) 
                    (https://creativecommons.org/licenses/by-nc-sa/4.0/)
* **Reference**: Please cite the following Open Access paper if you use this dataset 
                    https://doi.org/10.1007/s10579-019-09453-9
    * Authors: Ayla Rigouts Terryn, Véronique Hoste, Els Lefever
    * Title: In no uncertain terms: a dataset for monolingual and multilingual automatic term extraction from comparable corpora
    * Date of online publication: 26 March 2019
    * Date of print publication: 2020 (Volume 54, Issue 2, pages 385-418)
    * Journal: Language Resources and Evaluation (LRE)
    * Publisher: Springer



## 2. Abbreviations

**Languages and domains**:
* "en" = English
* "fr" = French
* "nl" = Dutch
* "corp" = corruption
* "equi" = equitation (dressage)
* "htfl" = heart failure
* "wind" = wind energy

**Types of terms/annotations**:
* "Spec" or "Specific": Specific Terms
* "Com" or "Common": Common Terms
* "OOD": Out-of-Domain Terms
* "NE(s)": Named Entities



## 3. Data Structure

File structure under each language folder ("en", "fr", and "en") is identical:

```
ACTER
│   README.md
│   sources.txt
│
└───en
│   └───corp
│   |   └───annotations
│   |   |   |   corp_en_terms.ann
│   |   |   |   corp_en_terms_nes.ann
│   |   | 
│   |   └───texts
|   |       └───annotated
│   |       |   corp_en_01.txt
│   |       |   corp_en_02.txt
│   |       |   ...
│   |       |
|   |       └───unannotated
│   |           |   corp_en_03.txt
│   |           |   ...
|   |
│   └───equi (equivalent to "corp")
|   |
│   └───htfl (equivalent to "corp")
|   |
│   └───wind (equivalent to "corp")
|
└───fr (equivalent to "en")
└───nl (equivalent to "en")
```

As can be seen, there are corpora in three languages and four domains.
All domains are available in all languages and they are comparable across these languages,
meaning that they are not only about the same domain, but also have a similar style and size.
However, they are not parallel corpora, so they cannot be aligned (not even on document level).
The file names always mention the subject, language, and a unique id (e.g. corp_en_01.txt).

For each part of the corpus, both the plain text files and the annotations are included. 
There are two annotation files: one with only the term annotations (Specific Terms, Common Terms, and OOD Terms), 
and one with both term and Named Entity annotations. The labels are mentioned for each annotation (see also section 4).

The plain text files are split into those which have been annotated and those that have not been annotated. 
This means that all annotations were found in the parts of the corpora labelled as "annotated" 
and that the "unannotated" parts of the corpora may contain many more terms which are not (yet) in the gold standard. 
Currently, around 50k words in each corpus (combination language/domain) have been manually annotated.

There is a single case where a text has been annotated only partially: wind_fr_06; 
therefore the text has been split and the unannotated part is called wind_fr_06bis.

In addition, there is this readme file and a txt-file with the sources of all corpora.



## 4. Annotations

### 4.1 Format

The annotations are provided in simple UTF-8 encoded plain text files, with one annotation per line.

The term annotation files include all the term annotations (Specific, Common, and OOD Terms have been combined).
A separate file (terms_nes) includes both terms and NEs. Since version 1.2, the labels are added to each annotation.
 
This means that the "terms.amm" and "terms_nes.ann" files now contain two types of information per line: 
the annotation (lowercased, unlemmatised, see further), followed by a tab and 
the label of this annotation ("Specific_Term", "Common_Term", "OOD_Term", or "Named_Entity"). 
In cases where a single annotation received different labels depending on the context, 
the most frequently given label is provided.


### 4.2 Casing, POS-tagging, and Lemmatisation
 
True-casing, POS-tagging & lemmatisation are non-trivial tasks but not the focus of this edition of TermEval. 
Therefore, all data will be lower-cased, non-lemmatised, and with only one entry per term. 

For example, the English corpus on dressage contains the term “bent” (verb – past tense of “to bend”), 
but also “Bent” (proper noun – person name). While both capitalisation and POS differ, 
and “bent” is not the lemmatised form, there will be only one entry: “bent” (lowercased) in the gold standard 
(other full forms of the verb “to bend” have separate entries, if they are present and annotated in the corpus). 



## 5. Additional Information

**Websites**:
* For more information about the TermEval shared task, visit: https://termeval.ugent.be
* For more information about the CompuTerm workshop, visit: https://sites.google.com/view/computerm2020/
* For more information about the annotation guidelines, visit: http://hdl.handle.net/1854/LU-8503113

**Publications**:
* Rigouts Terryn, A., Hoste, V., & Lefever, E. (2018). A Gold Standard for Multilingual Automatic Term Extraction from Comparable Corpora: Term Structure and Translation Equivalents. Proceedings of LREC 2018.
* Rigouts Terryn, A., Hoste, V., & Lefever, E. (2019). In No Uncertain Terms: A Dataset for Monolingual and Multilingual Automatic Term Extraction from Comparable Corpora. Language Resources and Evaluation, 54(2), 385–418. https://doi.org/10.1007/s10579-019-09453-9
* Rigouts Terryn, A., Hoste, V., Drouin, P., & Lefever, E. (2020). TermEval 2020: Shared Task on Automatic Term Extraction Using the Annotated Corpora for Term Extraction Research (ACTER) Dataset. Proceedings of the 6th International Workshop on Computational Terminology (COMPUTERM 2020), 85–94.

The dataset has been updated since the publication of the former two papers.
These papers also discuss aspects of the data which have not been made available yet,
such as cross-lingual annotations and information on the span of the annotations.

**Number of annotations per corpus**: 

Domain  Language    # term annotations  # term + Named Entity annotations   # Specific Terms    # Common Terms  # OOD Terms # Named Entities:
* corp	en	927	    1173    278 642 6   247
* equi	en	1155	1575    777 309 69  420
* htfl	en	2361	2585    1883    319 157 226
* wind	en	1091	1534    781 296 14  443
* corp	fr	979	    1207    298 675 5   229
* equi	fr	961	    1181    701 234 26  220
* htfl	fr	2228	2374    1684    487 57  146
* wind	fr	773	    968 444 308 21  195
* corp	nl	1047	1295    310 730 6   249
* equi	nl	1393	1544    1022    330 41  151
* htfl	nl	2074	2254    1559    449 66  180
* wind	nl	940	    1245    577 342 21  305


**Normalisation**:

The following normalisation procedures are applied to both the original text files and the annotations:
* unicodedata.normalize("NFC", text)
* normalising all dashes to "-", all single quotes to "'" and all double quotes to '"'


## 6. Updates

**Changes version 1.0 > version 1.1**

* English corpora:
    * corruption
        * Removed 1 NE: 'com(2007) 805 final'
    * wind energy
        * Removed 2 terms: 'variable pitch blades', 'renewable sources'
        * Removed 1 NE: 'skuodas'
* French corpora:
    * corruption:
        * Removed 2 terms: 'indélicat', 'loi relative à la corruption'
    * equitation-dressage
        * Removed 2 terms: 'canons', 'équilibration'
    * wind energy
        * Added 1 term: 'systèmes mutisources-multistockages'
        * Removed 4 terms: 'systèmes mutisources', 'quadrature', 'inductance directe', 'résistance statorique'
        * Removed 98 NEs: 'bar', 'esk', 'akh', 'tht', 'enbw', 'rich', 'kama', 'man', 'sab', 'mer', 'deg', 'mor', 'aba', 'abo', 'ana', 'azm', 'joo', 'jen', 'pri', 'han', 'ree', 'dav', 'cou', 'hol', 'sau', 'lal', 'lei', 'vet', 'pur', 'per', 'her', 'hau', 'ans', 'slo', 'win', 'thi', 'ela', 'stem', 'cer', 'lav', 'ack', 'e.on', 'cim', 'luo', 'wik', 'ds1103', 'fag', 'and', 'alm', 'pan', 'rap', 'ric', 'saa', 'reb', 'bor', 'kin', 'sem', 'ecr', 'fau', 'ukt', 'kun', 'creg', 'sal', 'bou', 'crap', 'mog', 'nget', 'stu', 'sei', 'lec', 'dir', 'nor', 'abb', 'doh', 'rwe', 'mul', 'oud', 'bea', '96/92/ce', 'gar', 'eri', 'cal', 'goi', 'ish', 'fra', 'cra', 'bna', 'ull', 'des', 'ips', 'dro', 'uct', 'mat', 'ds 1104', 'mar', 'svk', 'bla', 'buh'
* Dutch corpora:
    * corruption
        * Added 1 term: 'anticorruptie-eenheid'
        * Removed 4 terms: 'verslagen corruptiebestrijding', 'auditdiensten', 'anticorruptie', 'wet betreffende de omkoping'
    * equitation-dressage
        * Removed 2 terms: 'promotie', 'stuw'
    * wind energy
        * Removed 2 terms: 'windturbines een horizontale as', 'power coefficient'


**Changes version 1.1 > version 1.2**

* Included domain of heart failure (test domain for TermEval shared task)
 

**Changes version 1.2 > version 1.3**

* corrected wrong sources in htfl_nl
* changed heart failure abbreviation to "htfl" to be consistent with four-letter domain abbreviations
* created Github repository for data + submitted it to CLARIN


**Changes version 1.3 > version 1.4**

* applied limited normalisation on both texts and annotations:
    * unicodedata.normalize("NFC", text)
    * normalising all dashes to "-", all single quotes to "'" and all double quotes to '"'



## 7. Error Reporting

The ACTER dataset is an ongoing project, so we are always looking to improve the data.
Any questions or issues regarding this dataset may be reported via the Github repository at:
https://github.com/AylaRT/ACTER and will be addressed asap.



## 8. License

* *License*: Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International (CC BY-NC-SA 4.0) 
                (https://creativecommons.org/licenses/by-nc-sa/4.0/)
* *Reference*: Please cite the following Open Access paper if you use this dataset for your research 
                (https://doi.org/10.1007/s10579-019-09453-9)
    * Authors: Ayla Rigouts Terryn, Véronique Hoste, Els Lefever
    * Title: In no uncertain terms: a dataset for monolingual and multilingual automatic term extraction from comparable corpora
    * Date of online publication: 26 March 2019
    * Date of print publication: 2020 (Volume 54, Issue 2, pages 385-418)
    * Journal: Language Resources and Evaluation (LRE)
    * Publisher: Springer

The data can be freely used and adapted for non-commercial purposes, provided the above mentioned paper is cited 
and any changes made to the data are clearly stated.

