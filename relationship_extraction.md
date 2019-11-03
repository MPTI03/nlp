# Relationship Extraction

Ekstraksi hubungan adalah tugas mengekstraksi hubungan semantik dari sebuah teks. Hubungan yang diekstraksi biasanya terjadi antara dua atau lebih entitas dari jenis tertentu (mis. Orang, Organisasi, Lokasi) dan jatuh ke dalam sejumlah kategori semantik (mis. Menikah dengan, dipekerjakan oleh, tinggal).

### Capturing discriminative attributes (SemEval 2018 Task 10)

**Capturing discriminative attributes (SemEval 2018 Task 10)** Menangkap atribut diskriminatif (SemEval 2018 Tugas 10) adalah tugas klasifikasi biner di mana peserta diminta untuk mengidentifikasi apakah suatu atribut dapat membantu membedakan antara dua konsep. Tidak seperti tugas prediksi kesamaan kata lainnya, tugas ini berfokus pada perbedaan semantik antara kata-kata.

Misalnya merah (atribut) dapat digunakan untuk membedakan apel (concept1) dari pisang (concept2) -> label 1

Lebih banyak contoh :

| Attribute | concept1 | concept2 | label |
| --------- | -------- | -------- | ----- |
| bookcase | fridge | wood | 1 |
| bucket | mug | round | 0 |
| angle | curve | sharp | 1 |
| pelican | turtle | water | 0 |
| wire | coil | metal | 0 |

Task paper: [https://www.aclweb.org/anthology/S18-1117](https://www.aclweb.org/anthology/S18-1117)

Task Codalab: [https://competitions.codalab.org/competitions/17326](https://competitions.codalab.org/competitions/17326)

| Model | Explainability | F1 Score | Paper / Source | Code |
| ----- | -------------- | -------- | -------------- | ---- |
| **SVM** with GloVe                                                                            | **None**           | **0.76** | [SUNNYNLP at SemEval-2018 Task 10: A Support-Vector-Machine-Based Method for Detecting Semantic Difference using Taxonomy and Word Embedding Features](https://aclweb.org/anthology/S18-1118) | [Author's](https://github.com/Yermouth/sunnynlp)                    |
| **SVM** with ConceptNet, Wikipedia articles and WordNet synonyms                              | None               | 0.74     | [Luminoso at SemEval-2018 Task 10: Distinguishing Attributes Using Text Corpora and Relational Knowledge](https://aclweb.org/anthology/S18-1162)                                              | [Author's](https://github.com/LuminosoInsight/semeval-discriminatt) |
| **MLP** combining information from various DSMs, PMI, and ConceptNet                          | None               | 0.73     | [THU NGN at SemEval-2018 Task 10: Capturing Discriminative Attributes with MLP-CNN model](https://aclweb.org/anthology/S18-1157)                                                              |                                                                     |
| **Gradient boosting** with co-occurrence count features and JoBimText features                | None               | 0.73     | [BomJi at SemEval-2018 Task 10: Combining Vector-, Pattern- and Graph-based Information to Identify Discriminative Attributes](https://aclweb.org/anthology/S18-1163)                         |                                                                     |
| LexVec, word co-occurrence, and ConceptNet data combined using **maximum entropy classifier** | None               | 0.72     | [UWB at SemEval-2018 Task 10: Capturing Discriminative Attributes from Word Distributions](https://aclweb.org/anthology/S18-1153)                                                             | [Author's](https://github.com/dpaperno/DiscriminAtt)                |
| Composes explicit **vector spaces** from WordNet Definitions, ConceptNet and Visual Genome    | **Fully Explainable**  | **0.69** | [Identifying and Explaining Discriminative Attributes](https://arxiv.org/abs/1909.05363)                                                                                                      | [Author's](https://github.com/ab-10/Hawk)                           |
| **Word2Vec** cosine similarities of WordNet glosses Transp. (No expl.)                        | Transp. (No expl.) | 0.69     | [Meaning space at SemEval-2018 Task 10: Combining explicitly encoded knowledge with information extracted from word embeddings](https://aclweb.org/anthology/S18-1154)                        | [Author's](https://github.com/cltl/meaning_space)                   |
| Use of Wikipedia and ConceptNet Transp. (No expl.)                                            | Transp. (No expl.) | 0.69     | [ELiRF-UPV at SemEval-2018 Task 10: Capturing Discriminative Attributes with Knowledge Graphs and Wikipedia](https://aclweb.org/anthology/S18-1159)                                           |                                                                     |

### FewRel

Dataset Few-Shot Relation Classification (FewRel) adalah pengaturan yang berbeda dari kumpulan data sebelumnya. Dataset ini terdiri dari 70 ribu kalimat yang mengungkapkan 100 hubungan yang dianotasi oleh crowdworkers di Wikipedia corpus. Tugas belajar beberapa-shot mengikuti pengaturan pembelajaran meta K-shot N-arah. Ini adalah dataset klasifikasi hubungan terawasi terbesar serta dataset pembelajaran beberapa-shot terbesar hingga sekarang.

Papan publik tersedia di [FewRel website](http://www.zhuhao.me/fewrel/).

### Multi-Way Classification of Semantic Relations Between Pairs of Nominals (SemEval 2010 Task 8)

[SemEval-2010](http://www.aclweb.org/anthology/S10-1006) diperkenalkan ‘Tugas 8 - Klasifikasi Multi-Arah Hubungan Semantik Antar Pasangan Nominal '. Tugasnya adalah, diberi satu kalimat dan dua nomina yang ditandai, untuk memprediksi hubungan antara nomina-nomina tersebut dan arah hubungannya. Dataset berisi sembilan hubungan semantik umum bersama dengan hubungan kesepuluh 'LAINNYA'.

Contoh:
 > There were apples, **pears** and oranges in the **bowl**.

 `(content-container, pears, bowl)`

Metrik evaluasi utama yang digunakan adalah makro rata-rata F1, rata-rata di sembilan hubungan yang tepat (mis. Tidak termasuk hubungan OTHER), dengan mempertimbangkan arah hubungan itu.

Beberapa makalah telah menggunakan data tambahan (mis. Embeddings kata pra-terlatih, WordNet) untuk meningkatkan kinerja. Angka-angka yang dilaporkan di sini adalah yang tertinggi yang dicapai oleh model dengan menggunakan sumber daya eksternal apa pun.

#### End-to-End Models

| Model                                  | F1    | Paper / Source  | Code           |
| -------------------------------------- | ----- | --------------- | -------------- |
| *BERT-based Models* |
| Matching-the-Blanks (Baldini Soares et al., 2019) | **89.5** | [Matching the Blanks: Distributional Similarity for Relation Learning](https://www.aclweb.org/anthology/P19-1279) |
| R-BERT (Wu et al. 2019) | **89.25** | [Enriching Pre-trained Language Model with Entity Information for Relation Classification](https://arxiv.org/abs/1905.08284) |
| *CNN-based Models* |
| Multi-Attention CNN (Wang et al. 2016) | **88.0** | [Relation Classification via Multi-Level Attention CNNs](http://aclweb.org/anthology/P16-1123) | [lawlietAi's Reimplementation](https://github.com/lawlietAi/relation-classification-via-attention-model) |
| Attention CNN (Huang and Y Shen, 2016) | 84.3<br>85.9<sup>[\*](#footnote)</sup> | [Attention-Based Convolutional Neural Network for Semantic Relation Extraction](http://www.aclweb.org/anthology/C16-1238) |
| CR-CNN (dos Santos et al., 2015)       | 84.1  | [Classifying Relations by Ranking with Convolutional Neural Network](https://www.aclweb.org/anthology/P15-1061) | [pratapbhanu's Reimplementation](https://github.com/pratapbhanu/CRCNN) |
| CNN (Zeng et al., 2014)                | 82.7  | [Relation Classification via Convolutional Deep Neural Network](http://www.aclweb.org/anthology/C14-1220) | [roomylee's Reimplementation](https://github.com/roomylee/cnn-relation-extraction) |
| *RNN-based Models* |
| Entity Attention Bi-LSTM (Lee et al., 2019) | **85.2** | [Semantic Relation Classification via Bidirectional LSTM Networks with Entity-aware Attention using Latent Entity Typing](https://arxiv.org/abs/1901.08163) | [Official](https://github.com/roomylee/entity-aware-relation-classification) |
| Hierarchical Attention Bi-LSTM (Xiao and C Liu, 2016) | 84.3 | [Semantic Relation Classification via Hierarchical Recurrent Neural Network with Attention](http://www.aclweb.org/anthology/C16-1119) |
| Attention Bi-LSTM (Zhou et al., 2016)  | 84.0 | [Attention-Based Bidirectional Long Short-Term Memory Networks for Relation Classification](http://www.aclweb.org/anthology/P16-2034) | [SeoSangwoo's Reimplementation](https://github.com/SeoSangwoo/Attention-Based-BiLSTM-relation-extraction) |
| Bi-LSTM (Zhang et al., 2015)           | 82.7<br>84.3<sup>[\*](#footnote)</sup> | [Bidirectional long short-term memory networks for relation classification](http://www.aclweb.org/anthology/Y15-1009) |

<a name="footnote">*</a>: It uses external lexical resources, such as WordNet, part-of-speech tags, dependency tags, and named entity tags.

#### Dependency Models

| Model                               | F1    | Paper / Source  | Code           |
| ----------------------------------- | ----- | --------------- | -------------- |
| BRCNN (Cai et al., 2016)            | **86.3**  | [Bidirectional Recurrent Convolutional Neural Network for Relation Classification](http://www.aclweb.org/anthology/P16-1072) |
| DRNNs (Xu et al., 2016)             | 86.1  | [Improved Relation Classification by Deep Recurrent Neural Networks with Data Augmentation](https://arxiv.org/abs/1601.03651) |
| depLCNN + NS (Xu et al., 2015a)     | 85.6 | [Semantic Relation Classification via Convolutional Neural Networks with Simple Negative Sampling](https://www.aclweb.org/anthology/D/D15/D15-1062.pdf) |
| SDP-LSTM (Xu et al., 2015b)         | 83.7  | [Classifying Relations via Long Short Term Memory Networks along Shortest Dependency Path](https://arxiv.org/abs/1508.03720) | [Sshanu's Reimplementation](https://github.com/Sshanu/Relation-Classification) |
| DepNN (Liu et al., 2015)            | 83.6  | [A Dependency-Based Neural Network for Relation Classification](http://www.aclweb.org/anthology/P15-2047) |
| FCN (Yu et al., 2014)               | 83.0  | [Factor-based compositional embedding models](https://www.cs.cmu.edu/~mgormley/papers/yu+gormley+dredze.nipsw.2014.pdf) |
| MVRNN (Socher et al., 2012)         | 82.4  | [Semantic Compositionality through Recursive Matrix-Vector Spaces](http://aclweb.org/anthology/D12-1110) | [pratapbhanu's Reimplementation](https://github.com/pratapbhanu/MVRNN) |

### New York Times Corpus

Korpus standar untuk ekstraksi hubungan yang diawasi secara jauh adalah korpus New York Times (NYT), yang diterbitkan dalam [Riedel et al, 2010](http://www.riedelcastro.org//publications/papers/riedel10modeling.pdf).

Ini berisi teks dari [New York Times Annotated Corpus](https://catalog.ldc.upenn.edu/ldc2008t19) dengan entitas bernama yang diekstraksi dari teks menggunakan sistem NER Stanford dan secara otomatis ditautkan ke entitas di basis pengetahuan Freebase. Pasangan entitas bernama diberi label dengan tipe hubungan dengan menyelaraskannya dengan fakta di basis pengetahuan Freebase. (Proses menggunakan database terpisah untuk memberikan label dikenal sebagai 'pengawasan jauh')

Contoh:
 > **Elevation Partners**, the $1.9 billion private equity group that was founded by **Roger McNamee**

 `(founded_by, Elevation_Partners, Roger_McNamee)`

Makalah yang berbeda telah melaporkan berbagai metrik sejak rilis dataset, sehingga sulit untuk membandingkan sistem secara langsung. Metrik utama yang digunakan adalah presisi pada hasil N atau plot presisi-recall. Kisaran penarikan telah meningkat selama bertahun-tahun karena sistem membaik, dengan sistem sebelumnya memiliki presisi sangat rendah pada penarikan 30%.


| Model                               | P@10% | P@30% | Paper / Source | Code           |
| ----------------------------------- | ----- | ----- | --------------- | -------------- |
| HRERE (Xu et al., 2019) | 84.9 | 72.8 | [Connecting Language and Knowledge with Heterogeneous Representations for Neural Relation Extraction](https://arxiv.org/abs/1903.10126) | [HRERE](https://github.com/billy-inn/HRERE) |
| PCNN+noise_convert+cond_opt (Wu et al., 2019)         | 81.7   | 61.8   | [Improving Distantly Supervised Relation Extraction with Neural Noise Converter and Conditional Optimal Selector](https://arxiv.org/pdf/1811.05616.pdf) |  |
| Intra- and Inter-Bag (Ye and Ling, 2019)         | 78.9   | 62.4   | [Distant Supervision Relation Extraction with Intra-Bag and Inter-Bag Attentions](https://arxiv.org/pdf/1904.00143.pdf) | [Code](https://github.com/ZhixiuYe/Intra-Bag-and-Inter-Bag-Attentions) |
| RESIDE (Vashishth et al., 2018)         | 73.6   | 59.5   | [RESIDE: Improving Distantly-Supervised Neural Relation Extraction using Side Information](http://malllabiisc.github.io/publications/papers/reside_emnlp18.pdf) | [RESIDE](https://github.com/malllabiisc/RESIDE) |
| PCNN+ATT (Lin et al., 2016)         | 69.4   | 51.8   | [Neural Relation Extraction with Selective Attention over Instances](http://www.aclweb.org/anthology/P16-1200) | [OpenNRE](https://github.com/thunlp/OpenNRE/) |
| MIML-RE (Surdeneau et al., 2012)    | 60.7+  |   -   | [Multi-instance Multi-label Learning for Relation Extraction](http://www.aclweb.org/anthology/D12-1042) | [Mimlre](https://nlp.stanford.edu/software/mimlre.shtml) |
| MultiR (Hoffman et al., 2011)       | 60.9+  |   -   | [Knowledge-Based Weak Supervision for Information Extraction of Overlapping Relations](http://www.aclweb.org/anthology/P11-1055) | [MultiR](http://aiweb.cs.washington.edu/ai/raphaelh/mr/) |
| (Mintz et al., 2009)                | 39.9+  |   -   | [Distant supervision for relation extraction without labeled data](http://www.aclweb.org/anthology/P09-1113) | |

(+) Diperoleh dari hasil dalam makalah “Ekstraksi Relasi Saraf dengan Perhatian Selektif terhadap Mesin Virtual”

### TACRED

[TACRED](https://nlp.stanford.edu/projects/tacred/) adalah dataset ekstraksi relasi skala besar dengan 106.264 contoh dibangun di atas berita dan teks web dari [corpus](https://catalog.ldc.upenn.edu/LDC2018T03) yang digunakan dalam tantangan [TAC Knowledge Base Population (TAC KBP) challenges](https://tac.nist.gov/2017/KBP/index.html) tahunan. Contoh dalam TACRED mencakup 41 jenis hubungan seperti yang digunakan dalam tantangan TAC KBP  (misal , _per:schools_attended_ and _org:members_) atau dilabeli as _no_relation_ jika tidak ada hubungan yang pasti dipegang. Contoh-contoh ini dibuat dengan menggabungkan anotasi manusia yang tersedia dari tantangan TAC KBP dan crowdsourcing.

Contoh :
 > *Billy Mays*, the bearded, boisterious pitchman who, as the undisputed king of TV yell and sell, became an inlikely pop culture icon, died at his home in *Tampa*, Fla, on Sunday. 

 `(per:city_of_death, Billy Mays, Tampa)`

Metrik evaluasi utama yang digunakan adalah mikro-rata-rata F1 atas instance dengan hubungan yang tepat (mis. Tidak termasuk tipe no_relation).

| Model                                  | F1    | Paper / Source  | Code           |
| -------------------------------------- | ----- | --------------- | -------------- |
| Matching-the-Blanks (Baldini Soares et al., 2019) | **71.5** | [Matching the Blanks: Distributional Similarity for Relation Learning](https://www.aclweb.org/anthology/P19-1279) |
| C-GCN + PA-LSTM (Zhang et al. 2018) | **68.2** | [Graph Convolution over Pruned Dependency Trees Improves Relation Extraction](http://aclweb.org/anthology/D18-1244) | [Offical](https://github.com/qipeng/gcn-over-pruned-trees) |
| PA-LSTM (Zhang et al, 2017) | 65.1 | [Position-aware Attention and Supervised Data Improve Slot Filling](http://aclweb.org/anthology/D17-1004) | [Official](https://github.com/yuhaozhang/tacred-relation) |

[Kembali ke README](../README.md)
