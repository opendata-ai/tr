# Introduction

About datasets for information retrieval and recommendation tasks

## Sources

1. **arXiv.** This dataset comes from the public data source of arxiv<sup>[1]</sup>, which contains a total of 1,180,081 papers. All papers contain titles, abstracts, authors, publication time, subject, and 1,031,734 papers without MSC classification. We use subject as classification information. In order to evaluate the paper search task, we randomly selected 1000 papers to be queried and 20,000 candidate papers from the arXiv dataset. Table 1 describes the dataset in detail. Candidate papers with the same classification as the paper to be queried as groundtruth. Under this setup, there are 22 to 95 real candidate papers for each paper to be queried.

2. **DBLP.** This dataset comes from the public data source of  DBLP<sup>[4]</sup>. We use the v10 version<sup>[2]</sup>, which includes a total of 3,079,007 papers (including 2,229,296 papers with all attributes). We use titles, abstracts, publication times, and citations in this dataset. In order to evaluate the citation recommendation task, we randomly select 1000 papers to be recommended and 20,000 candidate papers from the DBLP dataset. Table 2 describes the dataset in detail. There are 15 to 16 citations for each paper to be recommended.

3. **USPTO.** This dataset comes from the public data source of the PatentsView database<sup>[3]</sup> (a total of 6,424,534 patents) which is sourced from USPTO-provided text and XML data on published patent applications (2001-most recent update) and granted patents (1976-most recent update). We extracte the title, abstract, year, first paragraph of the claim, and the citation cited by examiner from the dataset ("claim.tsv", "patent.tsv", "uspatentcitation.tsv"). In order to evaluate the patent recommendation task, we randomly select 1000 patents to be recommended and 20,000 candidate patents from the USPTO dataset. Table 3 describes the dataset in detail. There are 8 to 29 citations for each patent to be recommended.

[1] ftp://3lib.org//oai_dc/arxiv

[2] https://aminer.org/citation

[3] http://www.patentsview.org/download

[4] Tang J, Zhang J, Yao L, et al. Arnetminer: extraction and mining of academic social networks[C]//Proceedings of the 14th ACM SIGKDD international conference on Knowledge discovery and data mining. ACM, 2008: 990-998.

## Preprocessing

1. Convert all text to lowercase;
2. Remove HTML labels;
3. Restore HTML escape characters;
4. Split text with punctuation;
5. Remove tokens without letters. 

## Result

Table 1: arXiv20000

|                 | Query papers | Candidate papers |
| --------------- | ------------ | ---------------- |
| Papers          | 1000         | 20000            |
| Years           | 2016         | 1991-2015        |
| Words           | 205-418      | 205-425          |
| Classifications | 146          | 331              |
| Candidates      | 22-95        | -                |

Table 2: DBLP20000

|           | Recommended papers | Candidate papers |
| --------- | ------------------ | ---------------- |
| Papers    | 1000               | 20000            |
| Years     | 2017               | 1967-2016        |
| Words     | 156-412            | 155-421          |
| Citations | 15-16              | -                |

Table 3: USPTO20000

|           | Recommended patents | Candidate patents |
| --------- | ------------------- | ----------------- |
| Patents   | 1000                | 20000             |
| Years     | 2017-2018           | 2002-2016         |
| Words     | 255-629             | 250-680           |
| Citations | 8-29                | -                 |

## Format

- First line: {'text ID of candidates or citations':{'text ID of papers or patents',..},..}
- Other line: text ID of papers or patents \t title \t abstract
