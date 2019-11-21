# Dependency parsing

Dependency parsing parsing adalah tugas mengekstraksi parse dependensi dari kalimat yang merepresentasikan struktur gramatikal dan mendefinisikan hubungan antara kata-kata dan kata-kata "kepala", yang memodifikasi kepala-kepala itu

Contoh:

```
     root
      |
      | +-------dobj---------+
      | |                    |
nsubj | |   +------det-----+ | +-----nmod------+
+--+  | |   |              | | |               |
|  |  | |   |      +-nmod-+| | |      +-case-+ |
+  |  + |   +      +      || + |      +      | |
I  prefer  the  morning   flight  through  Denver
```

Hubungan antar kata diilustrasikan di atas kalimat dengan terarah, berlabel
busur dari kepala ke tanggungan (+ menunjukkan ketergantungan).

### Penn Treebank

Model dievaluasi pada [Stanford Dependency](https://nlp.stanford.edu/software/dependencies_manual.pdf)
konversi (**v3.3.0**) dari Penn Treebank dengan  __predicted__ POS-tag. Simbol tanda baca dikecualikan dari evaluasi.  Metrik evaluasi adalah skor lampiran tidak berlabel (UAS) dan skor lampiran berlabel (LAS).  UAS tidak mempertimbangkan hubungan semantik (mis. Subj) yang digunakan untuk memberi label lampiran antara kepala dan anak, sementara LAS memerlukan label semantik yang benar untuk setiap lampiran. Di sini, kami juga menyebutkan akurasi penandaan POS yang diprediksi.

| Model                                                         |  POS  |  UAS  |  LAS  | Paper / Source                                                                                                                   | Code                                                                           |
| ------------------------------------------------------------- | :---: | :---: | :---: | -------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------ |
| HPSG Parser (Joint) + XLNet (Zhou and Zhao, 2019)                         | 97.3 | 97.20 | 95.72 | [Head-Driven Phrase Structure Grammar Parsing on Penn Treebank](https://www.aclweb.org/anthology/P19-1230)                                   | [Official](https://github.com/DoodleJZ/HPSG-Neural-Parser) |
| HPSG Parser (Joint) + BERT (Zhou and Zhao, 2019)                         | 97.3 | 97.00 | 95.43 | [Head-Driven Phrase Structure Grammar Parsing on Penn Treebank](https://www.aclweb.org/anthology/P19-1230)                                   | [Official](https://github.com/DoodleJZ/HPSG-Neural-Parser) |
| CVT + Multi-Task (Clark et al., 2018)                         | 97.74 | 96.61 | 95.02 | [Semi-Supervised Sequence Modeling with Cross-View Training](https://arxiv.org/abs/1809.08370)                                   | [Official](https://github.com/tensorflow/models/tree/master/research/cvt_text) |
| Graph-based parser with GNNs (Ji et al., 2019)                | 97.3  | 95.97 | 94.31 | [Graph-based Dependency Parsing with Graph Neural Networks](https://www.aclweb.org/anthology/P19-1237)                           |                                                                                |
| Deep Biaffine (Dozat and Manning, 2017)                       | 97.3  | 95.74 | 94.08 | [Deep Biaffine Attention for Neural Dependency Parsing](https://arxiv.org/abs/1611.01734)                                        | [Official](https://github.com/tdozat/Parser-v1)                                |
| jPTDP (Nguyen and Verspoor, 2018)                             | 97.97 | 94.51 | 92.87 | [An improved neural network model for joint POS tagging and dependency parsing](https://arxiv.org/abs/1807.03955)                | [Official](https://github.com/datquocnguyen/jPTDP)                             |
| Andor et al. (2016)                                           | 97.44 | 94.61 | 92.79 | [Globally Normalized Transition-Based Neural Networks](https://www.aclweb.org/anthology/P16-1231)                                |                                                                                |
| Distilled neural FOG (Kuncoro et al., 2016)                   | 97.3  | 94.26 | 92.06 | [Distilling an Ensemble of Greedy Dependency Parsers into One MST Parser](https://arxiv.org/abs/1609.07561)                      |                                                                                |
| Distilled transition-based parser (Liu et al., 2018)          | 97.3  | 94.05 | 92.14 | [Distilling Knowledge for Search-based Structured Prediction](http://aclweb.org/anthology/P18-1129)                              | [Official](https://github.com/Oneplus/twpipe)                                  |
| Weiss et al. (2015)                                           | 97.44 | 93.99 | 92.05 | [Structured Training for Neural Network Transition-Based Parsing](http://anthology.aclweb.org/P/P15/P15-1032.pdf)                |                                                                                |
| BIST transition-based parser (Kiperwasser and Goldberg, 2016) | 97.3  | 93.9  | 91.9  | [Simple and Accurate Dependency Parsing Using Bidirectional LSTM Feature Representations](https://aclweb.org/anthology/Q16-1023) | [Official](https://github.com/elikip/bist-parser/tree/master/barchybrid/src)   |
| Arc-hybrid (Ballesteros et al., 2016)                         | 97.3  | 93.56 | 91.42 | [Training with Exploration Improves a Greedy Stack-LSTM Parser](https://arxiv.org/abs/1603.03793)                                |                                                                                |
| BIST graph-based parser (Kiperwasser and Goldberg, 2016)      | 97.3  | 93.1  | 91.0  | [Simple and Accurate Dependency Parsing Using Bidirectional LSTM Feature Representations](https://aclweb.org/anthology/Q16-1023) | [Official](https://github.com/elikip/bist-parser/tree/master/bmstparser/src)   |

### Universal Dependencies

Fokus dari tugas ini adalah mempelajari parser dependensi sintaksis yang dapat bekerja dalam pengaturan dunia nyata, mulai dari teks mentah, dan yang dapat bekerja pada banyak bahasa yang berbeda secara tipologis, bahkan bahasa sumber daya rendah yang hanya memiliki sedikit atau tidak ada data pelatihan,  dengan mengeksploitasi standar anotasi sintaksis yang umum.  Tugas ini dimungkinkan oleh inisiatif  (UD, http://universaldependencies.org/), yang telah mengembangkan bank-bank untuk 60+ bahasa dengan anotasi yang konsisten secara lintas-bahasa dan pemulihan dari teks mentah asli.

Sistem yang berpartisipasi harus menemukan ketergantungan sintaksis berlabel di antara kata-kata, mis. Kepala sintaksis untuk setiap kata, dan label yang mengelompokkan jenis hubungan ketergantungan.  Selain dependensi sintaksis, prediksi morfologi dan lemmatization akan dievaluasi.  Akan ada beberapa set tes dalam berbagai bahasa tetapi semua set data akan mematuhi gaya penjelasan umum UD.  Peserta akan diminta untuk mem-parsing teks mentah di mana tidak ada pra-pemrosesan standar emas (tokenization, lemmas, morfologi) tersedia.  Data yang diolah sebelumnya oleh sistem dasar (UDPipe, https://ufal.mff.cuni.cz/udpipe/) disediakan sehingga para peserta dapat fokus pada peningkatan hanya satu bagian dari pipa pemrosesan.  Penyelenggara percaya bahwa ini membuat tugas itu cukup mudah diakses untuk semua orang.

| Model                     |  LAS  | MLAS  | BLEX  | Paper / Source                                                                                                                                              | Code                                                                 |
| ------------------------- | :---: | :---: | :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------- |
| Stanford (Qi et al.)      | 74.16 | 62.08 | 65.28 | [Universal Dependency Parsing from Scratch](https://arxiv.org/pdf/1901.10457.pdf)                                                                           | [Official](https://github.com/stanfordnlp/stanfordnlp)               |
| UDPipe Future (Straka)    | 73.11 | 61.25 | 64.49 | [UDPipe 2.0 Prototype at CoNLL 2018 UD Shared Task](https://www.aclweb.org/anthology/K18-2020)                                                              | [Official](https://github.com/CoNLL-UD-2018/UDPipe-Future)           |
| HIT-SCIR (Che et al.)     | 75.84 | 59.78 | 65.33 | [Towards Better UD Parsing: Deep Contextualized Word Embeddings, Ensemble, and Treebank Concatenation](https://arxiv.org/abs/1807.03121)                    |                                                                      |
| TurkuNLP (Kanerva et al.) | 73.28 | 60.99 | 66.09 | [Turku Neural Parser Pipeline: An End-to-End System for the CoNLL 2018 Shared Task](https://universaldependencies.org/conll18/proceedings/pdf/K18-2013.pdf) | [Official](https://github.com/TurkuNLP/Turku-neural-parser-pipeline) |

Hasil berikut ini hanya untuk referensi:

| Model                                                                  |  UAS  |  LAS  | Note                           | Paper / Source                                                                                    |
| ---------------------------------------------------------------------- | :---: | :---: | ------------------------------ | ------------------------------------------------------------------------------------------------- |
| Stack-only RNNG (Kuncoro et al., 2017)                                 | 95.8  | 94.6  | Constituent parser             | [What Do Recurrent Neural Network Grammars Learn About Syntax?](https://arxiv.org/abs/1611.05774) |
| Deep Biaffine (Dozat and Manning, 2017)                                | 95.75 | 94.22 | Stanford conversion **v3.5.0** | [Deep Biaffine Attention for Neural Dependency Parsing](https://arxiv.org/abs/1611.01734)         |
| Semi-supervised LSTM-LM (Choe and Charniak, 2016) (Constituent parser) | 95.9  | 94.1  | Constituent parser             | [Parsing as Language Modeling](http://www.aclweb.org/anthology/D16-1257)                          |

# Cross-lingual zero-shot dependency parsing

Cross-lingual zero-shot parsing adalah tugas untuk menyimpulkan parsing dependensi kalimat dari satu bahasa tanpa pohon pelatihan yang diberi label untuk bahasa itu.

## Universal Dependency Treebank

Model dievaluasi terhadap [Universal Dependency Treebank v2.0](https://github.com/ryanmcd/uni-dep-tb/). .  Untuk masing-masing dari 6 bahasa target, model dapat menggunakan pohon dari semua bahasa lain dan bahasa Inggris dan dievaluasi oleh UAS dan LAS pada target.  Skor akhir adalah skor rata-rata di 6 bahasa target.  Pengaturan evaluasi yang paling umum adalah dengan menggunakan tag-POS emas.

| Model                                      |  UAS  |  LAS  | Paper / Source                                                                                                                               | Code                                                          |
| ------------------------------------------ | :---: | :---: | -------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------- |
| Cross-Lingual ELMo (Schuster et al., 2019) | 84.2  | 77.3  | [Cross-Lingual Alignment of Contextual Word Embeddings, with Applications to Zero-shot Dependency Parsing](https://arxiv.org/abs/1902.09492) | [Official](https://github.com/TalSchuster/CrossLingualELMo)   |
| MALOPA (Ammar et al., 2016)                |       | 70.5  | [Many Languages, One Parser](https://www.transacl.org/ojs/index.php/tacl/article/view/892)                                                   | [Official](https://github.com/clab/language-universal-parser) |
| Guo et al. (2016)                          | 76.7  | 69.9  | [A representation learning framework for multi-source transfer parsing](https://dl.acm.org/citation.cfm?id=3016100.3016284)                  |

# Unsupervised dependency parsing

Unsupervised dependency parsing adalah tugas untuk menyimpulkan parsing dependensi dari kalimat tanpa data pelatihan yang diberi label.

## Penn Treebank

Seperti parsing yang diawasi, model dievaluasi terhadap Penn Treebank.  Pengaturan evaluasi yang paling umum adalah menggunakan tag-POS emas sebagai input dan untuk mengevaluasi sistem menggunakan skor lampiran yang tidak berlabel (juga disebut 'akurasi ketergantungan terarah').

| Model                                                |  UAS  | Paper / Source                                                                                                                                        |
| ---------------------------------------------------- | :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------- |
| Iterative reranking (Le & Zuidema, 2015)             | 66.2  | [Unsupervised Dependency Parsing - Let’s Use Supervised Parsers](http://www.aclweb.org/anthology/N15-1067)                                            |
| Combined System (Spitkovsky et al., 2013)            | 64.4  | [Breaking Out of Local Optima with Count Transforms and Model Recombination - A Study in Grammar Induction](http://www.aclweb.org/anthology/D13-1204) |
| Tree Substitution Grammar DMV (Blunsom & Cohn, 2010) | 55.7  | [Unsupervised Induction of Tree Substitution Grammars for Dependency Parsing](http://www.aclweb.org/anthology/D10-1117)                               |
| Shared Logistic Normal DMV (Cohen & Smith, 2009)     | 41.4  | [Shared Logistic Normal Distributions for Soft Parameter Tying in Unsupervised Grammar Induction](http://www.aclweb.org/anthology/N09-1009)           |
| DMV (Klein & Manning, 2004)                          | 35.9  | [Corpus-Based Induction of Syntactic Structure - Models of Dependency and Constituency](http://www.aclweb.org/anthology/P04-1061)                     |

[Kembali ke README](../README.md)
