# Relation Prediction

## Tugas

Relation Prediction adalah tugas mengenali relasi bernama antara dua entitas semantik bernama. Pengaturan tes umum adalah untuk menyembunyikan satu entitas dari triplet relasi, meminta sistem untuk memulihkannya berdasarkan entitas lain dan jenis relasi.

Misalnya, mengingat triple \<*Roman Jakobson*, *born-in-city*, *?*\>, sistem diperlukan untuk mengganti tanda tanya dengan *Moscow*.

Relation Prediction datasets biasanya diekstraksi dari dua jenis sumber daya:
* *Knowledge Bases*: KBs seperti [FreeBase](https://developers.google.com/freebase/)berisi ratusan atau ribuan jenis hubungan yang berkaitan dengan pengetahuan dunia yang diperoleh secara otomatis atau semi-otomatis dari berbagai sumber daya pada jutaan entitas. Hubungan-hubungan ini mencakup *born-in*, *nationality*, *is-in* (untuk entitas geografis), *part-of* (funtuk organisasi, antara lain), dan banyak lagi.
* *Semantic Graphs*: SGs seperti [WordNet](https://wordnet.princeton.edu/) seringkali merupakan sumber daya yang dikuratori secara manual dari konsep semantik, terbatas pada hubungan yang lebih “linguistik” dibandingkan dengan pengetahuan dunia nyata yang bebas. Relasi semantik yang paling umum adalah *hypernym*, juga dikenal sebagai relasi *is-a* relasi (example: \<*cat*, *hypernym*, *feline*\>).

## Evaluation

Evaluation dalam Relasi Prediksi bergantung pada daftar kandidat peringkat yang diberikan oleh sistem untuk contoh uji. Metrik di bawah ini berasal dari lokasi kandidat yang benar dalam daftar itu.

Tindakan umum yang dilakukan sebelum evaluasi pada daftar yang diberikan adalah *filtering*, di mana daftar tersebut dibersihkan dari entitas yang triples yang sesuai ada dalam grafik pengetahuan. Kecuali ditentukan lain, hasil di sini berasal dari daftar yang difilter.

### Metrics

#### Mean Reciprocal Rank (MRR):

Rerata dari semua peringkat timbal balik untuk kandidat sejati selama set tes (1 / peringkat).

#### Hits at k (H@k):

Tingkat entitas yang benar muncul di entri k atas untuk setiap daftar instance. Angka ini dapat melebihi 1,00 jika daftar *k*-terpotong rata-rata berisi lebih dari satu entitas sebenarnya.

### Datasets

#### Freebase-15K-237 (FB15K-237)
Dataset FB15K diperkenalkan di [Bordes et al., 2013](http://papers.nips.cc/paper/5071-translating-embeddings-for-modeling-multi-relational-data.pdf). Ini adalah subset dari Freebase yang berisi sekitar 14.951 entitas dengan 1.345 relasi berbeda. Dataset ini ditemukan menderita kebocoran uji utama melalui hubungan terbalik dan sejumlah besar tripel tes dapat diperoleh hanya dengan membalikkan triples dalam pelatihan yang awalnya ditetapkan oleh [Toutanova et al.](http://aclweb.org/anthology/D15-1174). Untuk membuat dataset tanpa properti ini, [Toutanova et al.](http://aclweb.org/anthology/D15-1174) memperkenalkan FB15k-237 - bagian dari FB15k di mana hubungan terbalik dihapus.

#### WordNet-18-RR (WN18RR)

Dataset WN18 juga diperkenalkan[Bordes et al., 2013](http://papers.nips.cc/paper/5071-translating-embeddings-for-modeling-multi-relational-data.pdf). Ini termasuk 18 hubungan penuh yang diambil dari WordNet untuk sekitar 41.000 sinkronisasi. Mirip dengan FB15K, dataset ini ditemukan menderita kebocoran uji oleh [Dettmers et al. (2018)](https://arxiv.org/abs/1707.01476) memperkenalkan [WN18RR](https://github.com/villmow/datasets_knowledge_embedding). 

Sebagai cara untuk mengatasi masalah ini, [Dettmers et al. (2018)](https://arxiv.org/abs/1707.01476) memperkenalkan dataset [WN18RR](https://github.com/villmow/datasets_knowledge_embedding) yang berasal dari WN18, yang hanya menampilkan 11 relasi, tidak ada pasangan yang timbal balik (tetapi masih menyertakan empat relasi simetris internal seperti verb_group, yang memungkinkan sistem berbasis aturan mencapai 35 pada ketiga metrik).

### Experimental Results

#### WN18RR

Set tes terdiri dari kembar tiga, masing-masing digunakan untuk membuat dua contoh uji, satu untuk setiap entitas yang akan diprediksi. Karena setiap instance dikaitkan dengan satu entitas benar tunggal, nilai maksimum untuk semua metrik adalah 1,00.
   
| Model           | H@10 | H@1 | MRR | Paper / Source | Code | 
| ------------- | :-----:| :-----:| :-----:| --- | --- | 
| Max-Margin Markov Graph Models (Pinter & Eisenstein, 2018) | 59.02 | 45.37 | 49.83 | [Predicting Semantic Relations using Global Graph Properties](https://arxiv.org/abs/1808.08644) | [Official](http://www.github.com/yuvalpinter/m3gm) |
| KBAT(Deepak et al., 2019) | 58.1 | 36.1 | 44 | [Learning Attention Based Embeddings for Relation Prediction](https://arxiv.org/pdf/1906.01195.pdf) | [Official](https://github.com/deepakn97/relationPrediction)
| TransE (reimplementation by Pinter & Eisenstein, 2018) | 55.55 | 42.26 | 46.59 | [Translating Embeddings for Modeling Multi-relational Data. ](http://papers.nips.cc/paper/5071-translating-embeddings-for-modeling-multi-relational-data.pdf) | [OpenKE](https://github.com/thunlp/OpenKE) |
| ConvKB (Nguyen et al., 2018) | 52.50 | - | 24.80 | [A Novel Embedding Model for Knowledge Base Completion Based on Convolutional Neural Network](http://www.aclweb.org/anthology/N18-2053) | [Official](https://github.com/daiquocnguyen/ConvKB) |
| ConvE (v6; Dettmers et al., 2018) | 52.00 | 40.00 | 43.00 | [Convolutional 2D Knowledge Graph Embeddings](https://arxiv.org/abs/1707.01476) | [Official](https://github.com/TimDettmers/ConvE) |
| ComplEx (Trouillon et al., 2016) | 51.00 | 41.00 | 44.00 | [Complex Embeddings for Simple Link Prediction](http://www.jmlr.org/proceedings/papers/v48/trouillon16.pdf) | [Official](https://github.com/ttrouill/complex) | 
| DistMult (reimplementation by Dettmers et al., 2018) | 49.00 | 40.00 | 43.00 | [Embedding Entities and Relations for Learning and Inference in Knowledge Bases.](https://arxiv.org/pdf/1412.6575) | [Link](https://github.com/thunlp/OpenKE) |

#### FB15K-237

| Model           | H@10 | H@1 | MRR | Paper / Source | Code | 
| ------------- | :-----:| :-----:| :-----:| --- | --- | 
| KBAT(Deepak et al., 2019) | 62.6 | 46 | 51.8 | [Learning Attention Based Embeddings for Relation Prediction](https://arxiv.org/pdf/1906.01195.pdf) | [Official](https://github.com/deepakn97/relationPrediction)
| TransE (reimplementation by Han et al., 2018) | 47.09 | 19.87 | 29.04 | [Translating Embeddings for Modeling Multi-relational Data. ](http://papers.nips.cc/paper/5071-translating-embeddings-for-modeling-multi-relational-data.pdf) | [OpenKE](https://github.com/thunlp/OpenKE) |
| TransH (reimplementation by Han et al., 2018) | 41.32 | 5.79 | 17.66 | [Knowledge Graph Embedding by Translating on Hyperplanes.](http://www.aaai.org/ocs/index.php/AAAI/AAAI14/paper/viewFile/8531/8546) | [OpenKE](https://github.com/thunlp/OpenKE) |
| TransR (reimplementation by Han et al., 2018) | 40.67 | 16.35 | 24.44 | [ Learning Entity and Relation Embeddings for Knowledge Graph Completion.](http://www.aaai.org/ocs/index.php/AAAI/AAAI15/paper/download/9571/9523/) | [OpenKE](https://github.com/thunlp/OpenKE) |
| TransD (reimplementation by Han et al., 2018) | 46.05 | 14.83 | 25.27 | [Knowledge Graph Embedding via Dynamic Mapping Matrix.](http://anthology.aclweb.org/P/P15/P15-1067.pdf) | [OpenKE](https://github.com/thunlp/OpenKE) |
| ConvKB (Nguyen et al., 2018) | 51.70 | - | 39.60 | [A Novel Embedding Model for Knowledge Base Completion Based on Convolutional Neural Network](http://www.aclweb.org/anthology/N18-2053) | [Official](https://github.com/daiquocnguyen/ConvKB) |
| ConvE (v6; Dettmers et al., 2018) | 50.10 | 23.70 | 32.50 | [Convolutional 2D Knowledge Graph Embeddings](https://arxiv.org/abs/1707.01476) | [Official](https://github.com/TimDettmers/ConvE) |
| ComplEx (reimplementation by Dettmers et al., 2018) | 42.80 | 15.80 | 24.70 | [Complex Embeddings for Simple Link Prediction](http://www.jmlr.org/proceedings/papers/v48/trouillon16.pdf) | [Official](https://github.com/ttrouill/complex) | 
| DistMult (reimplementation by Dettmers et al., 2018) | 41.90 | 15.50 | 24.10 | [Embedding Entities and Relations for Learning and Inference in Knowledge Bases.](https://arxiv.org/pdf/1412.6575) | [Link](https://github.com/thunlp/OpenKE) |

## Resources
[OpenKE](http://aclweb.org/anthology/D18-2024) adalah toolkit terbuka untuk pembelajaran relasional yang menyediakan pelatihan standar dan kerangka kerja pengujian. Saat ini, model yang diterapkan di OpenKE termasuk TransE, TransH, TransR, TransD, RESCAL, DistMult, ComplEx dan HolE.

[KRLPapers](https://github.com/thunlp/KRLPapers) adalah daftar kertas yang harus dibaca untuk pembelajaran relasional.

[Kembali ke README](../README.md)
