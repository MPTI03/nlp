# Ekstraksi Informasi

### Grafik Pengetahuan Canonicalization

Pendekatan Ekstraksi Informasi Terbuka mengarah pada pembuatan Basis  Pengetahuan (KB) besar dari web. Masalah dengan metode tersebut adalah bahwa entitas dan hubungan mereka tidak dikanonikalisasi, yang mengarah pada penyimpanan fakta yang berlebihan dan ambigu. Misalnya, penyimpanan Open KB*\<Barack Obama, lahir di, Honolulu\>* and *\<Obama, lahir di, Honolulu\>* tidak tahu itu *Barack Obama* and *Obama* berarti entitas yang sama. Demikian pula, *lahir di* dan *lahir di* juga merujuk pada hubungan yang sama. Masalah kanonikisasi KB Terbuka melibatkan identifikasi kelompok entitas yang setara dan hubungan dalam KB.

### Dataset 

| Datasets                                 | # Gold Entities | #NPs  | #Relations | #Triples |
| ---------------------------------------- | :-------------: | ----- | ---------- | -------- |
| [Base](https://suchanek.name/work/publications/cikm2014.pdf) |       150       | 290   | 3K         | 9K       |
| [Ambiguous](https://suchanek.name/work/publications/cikm2014.pdf) |       446       | 717   | 11K        | 37K      |
| [ReVerb45K](https://github.com/malllabiisc/cesi) |      7.5K       | 15.5K | 22K        | 45K      |

### Noun Phrase Canonicalization

| **Model**                     |               | Base Dataset |        |               | Ambiguous dataset |        |               | ReVerb45k  |        | **Paper**/Source                         |
| :---------------------------- | :-----------: | :----------: | :----: | :-----------: | :---------------: | ------ | :-----------: | :--------: | :----: | ---------------------------------------- |
|                               | **Precision** |  **Recall**  | **F1** | **Precision** |    **Recall**     | **F1** | **Precision** | **Recall** | **F1** |                                          |
| CESI (Vashishth et al., 2018) |     98.2      |     99.8     |  99.9  |     66.2      |       92.4        | 91.9   |     62.7      |    84.4    |  81.9  | [CESI: Canonicalizing Open Knowledge Bases using Embeddings and Side Information](https://github.com/malllabiisc/cesi) |
| Galárraga et al., 2014 ( IDF) |     94.8      |     97.9     |  98.3  |     67.9      |       82.9        | 79.3   |     71.6      |    50.8    |  0.5   | [Canonicalizing Open Knowledge Bases](https://suchanek.name/work/publications/cikm2014.pdf) |

[Go back to the README](../README.md)
