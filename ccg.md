# Combinatory Categorical Grammar

Combinatory Categorical Grammar (CCG; [Steedman, 2000](http://www.citeulike.org/group/14833/article/8971002)) adalah formalisme yang sangat kompleks. Model parsing standar [Clark and Curran (2007)](https://www.mitpressjournals.org/doi/abs/10.1162/coli.2007.33.4.493)
menggunakan lebih dari 400 kategori leksikal (atau supertag), dibandingkan dengan sekitar 50 tag bagian-of-speech untuk parser biasa.

Contoh :

| Vinken | , | 61 | years | old |
| --- | ---| --- | --- | --- |
| N| , | N/N | N | (S[adj]\ NP)\ NP |

## Parsing

### CCGBank

CCGBank adalah kumpulan derivasi  CCG dan struktur ketergantungan yang diekstraksi dari Penn Treebank oleh Hockenmaier dan Steedman (2007)](http://www.aclweb.org/anthology/J07-3004).Bagian 2-21 digunakan untuk pelatihan, bagian 00 untuk pengembangan, dan bagian 23 sebagai set uji in-domain.  Beberapa pekerjaan

| Model           | Accuracy |  Paper / Source |
| ------------- | :-----:| --- |
| Vaswani et al. (2016) | 88.32 | [Supertagging with LSTMs](https://aclweb.org/anthology/N/N16/N16-1027.pdf) |
| Lewis et al. (2016) | 88.1 | [LSTM CCG Parsing](https://aclweb.org/anthology/N/N16/N16-1026.pdf) |
| Xu et al. (2015) | 87.04 | [CCG Supertagging with a Recurrent Neural Network](http://www.aclweb.org/anthology/P15-2041) |
| Kummerfeld et al. (2010), with additional unlabeled data | 85.95 | [Faster Parsing by Supertagger Adaptation](https://www.aclweb.org/anthology/papers/P/P10/P10-1036/) |
| Clark and Curran (2007) | 85.45 | [Wide-Coverage Efficient Statistical Parsing with CCG and Log-Linear Models](https://www.aclweb.org/anthology/J07-4004) |

### Wikipedia

| Model           | Accuracy |  Paper / Source |
| ------------- | :-----:| --- |
| Xu et al. (2015) | 82.49 | [CCG Supertagging with a Recurrent Neural Network](http://www.aclweb.org/anthology/P15-2041) |
| Kummerfeld et al. (2010), with additional unlabeled data | 81.7 | [Faster Parsing by Supertagger Adaptation](https://www.aclweb.org/anthology/papers/P/P10/P10-1036/) |

### Bioinfer

| Model         | Bio specifc taggers? | Accuracy |  Paper / Source |
| ------------- | -------------------- | :-------:| --- |
| Kummerfeld et al. (2010), with additional unlabeled data | Yes | 82.3 | [Faster Parsing by Supertagger Adaptation](https://www.aclweb.org/anthology/papers/P/P10/P10-1036/) |
| Rimell and Clark (2008) | Yes | 81.5 | [Adapting a Lexicalized-Grammar Parser to Contrasting Domains](https://aclweb.org/anthology/papers/D/D08/D08-1050/) |
| Xu et al. (2015) | No | 77.74 | [CCG Supertagging with a Recurrent Neural Network](http://www.aclweb.org/anthology/P15-2041) |
| Kummerfeld et al. (2010), with additional unlabeled data | No | 76.1 | [Faster Parsing by Supertagger Adaptation](https://www.aclweb.org/anthology/papers/P/P10/P10-1036/) |
| Rimell and Clark (2008) | No | 76.0 | [Adapting a Lexicalized-Grammar Parser to Contrasting Domains](https://aclweb.org/anthology/papers/D/D08/D08-1050/) |

## Supertagging

### CCGBank

Untuk evaluasi Supertagging pada CCGBank, kinerja hanya dihitung selama 425 label yang paling sering.  Model dievaluasi berdasarkan akurasi.

| Model           | Accuracy |  Paper / Source |
| ------------- | :-----:| --- |
| Clark et al. (2018) | 96.1 | [Semi-Supervised Sequence Modeling with Cross-View Training](https://arxiv.org/abs/1809.08370) |
| Lewis et al. (2016) | 94.7 | [LSTM CCG Parsing](https://aclweb.org/anthology/N/N16/N16-1026.pdf) |
| Vaswani et al. (2016) | 94.24 | [Supertagging with LSTMs](https://aclweb.org/anthology/N/N16/N16-1027.pdf) |
| Low supervision (Søgaard and Goldberg, 2016) | 93.26 | [Deep multi-task learning with low level tasks supervised at lower layers](http://anthology.aclweb.org/P16-2038) |
| Xu et al. (2015) | 93.00 | [CCG Supertagging with a Recurrent Neural Network](http://www.aclweb.org/anthology/P15-2041) |
| Clark and Curran (2004) | 92.00 | [The Importance of Supertagging for Wide-Coverage CCG Parsing](https://aclweb.org/anthology/papers/C/C04/C04-1041/) (result from Lewis et al. (2016)) |

## Conversion to PTB

Ada minat dalam mengkonversi derivasi CCG ke parsing struktur frasa untuk dibandingkan dengan parser struktur frasa (karena CCGBank didasarkan pada PTB).

| Model           | Accuracy |  Paper / Source |
| ------------- | :-----:| --- |
| Kummerfeld et al. (2012) | 96.30 | [Robust Conversion of CCG Derivations to Phrase Structure Trees](https://www.aclweb.org/anthology/P12-2021) |
| Zhang et al. (2012) | 95.71 | [A Machine Learning Approach to Convert CCGbank to Penn Treebank](https://www.aclweb.org/anthology/C12-3067)
| Clark and Curran (2009) | 94.64 | [Comparing the Accuracy of CCG and Penn Treebank Parsers](https://aclweb.org/anthology/papers/P/P09/P09-2014/) |

[Kembali ke README](../README.md)
