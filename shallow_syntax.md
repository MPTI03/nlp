# Shallow syntax

Tugas shallow syntactic memberikan analisis dari sebuah teks pada tingkat struktur syntactic dari teks tersebut. 

## Chunking

Chunking, juga dikenal sebagai penguraian shallow, mengidentifikasi jangka waktu yang berkelanjutan yang membentuk unit syntactic seperti frasa kata benda atau frasa kata kerja.

Example:

| Vinken | , | 61 | years | old |
| --- | ---| --- | --- | --- |
| B-NLP| I-NP | I-NP | I-NP | I-NP |

### Penn Treebank

[Penn Treebank](https://catalog.ldc.upenn.edu/LDC99T42) biasanya digunakan untuk mengevaluasi chunking. Bagian 15-18 digunakan untuk pelatihan, bagian 19 untuk pengembangan, dan bagian 20 untuk pengujian. Model yang dievaluasi berdasarkan F1.

| Model           | F1 score  |  Paper / Source |
| ------------- | :-----:| --- |
| Flair embeddings (Akbik et al., 2018) | 96.72 | [Contextual String Embeddings for Sequence Labeling](http://aclweb.org/anthology/C18-1139) |
| JMT (Hashimoto et al., 2017) | 95.77 | [A Joint Many-Task Model: Growing a Neural Network for Multiple NLP Tasks](https://www.aclweb.org/anthology/D17-1206) |
| Low supervision (Søgaard and Goldberg, 2016) | 95.57 | [Deep multi-task learning with low level tasks supervised at lower layers](http://anthology.aclweb.org/P16-2038) |
| Suzuki and Isozaki (2008) | 95.15 | [Semi-Supervised Sequential Labeling and Segmentation using Giga-word Scale Unlabeled Data](https://aclanthology.info/pdf/P/P08/P08-1076.pdf) | 
| NCRF++ (Yang and Zhang, 2018)| 95.06 | [NCRF++: An Open-source Neural Sequence Labeling Toolkit](http://www.aclweb.org/anthology/P18-4013) | [NCRF++](https://github.com/jiesutd/NCRFpp) |

## Resolving the Scope and focus of negation

Scope of negation adalah bagian dari arti yang dinegasikan dan fokus pada bagian dari scope  yang paling jelas dinegasikan (Huddleston dan Pullum 2002).

Example:

`[John had] never [said %as much% before].`

scope yang tertutup dalam tanda kurung dan fokus ditandai antara tanda %.

The [CD-SCO (Conan Doyle Scope) dataset](https://www.clips.uantwerpen.be/sem2012-st-neg/data.html) is for scope detection.
 The [PB-FOC (PropBank Focus) dataset](https://www.clips.uantwerpen.be/sem2012-st-neg/data.html) is for focus detection.
The public leaderboard is available on the [*SEM Shared Task 2012 website](https://www.clips.uantwerpen.be/sem2012-st-neg/results.html).

[Go back to the README](../README.md)
