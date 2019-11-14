# Summarization

Summarization adalah tugas menghasilkan versi yang lebih pendek dari satu atau beberapa dokumen yang mempertahankan sebagian besar makna input.

### Warning: Evaluation Metrics

Untuk summarization, metrik otomatis seperti ROUGE dan METEOR memiliki batasan serius:
1. Mereka hanya menilai pemilihan konten dan tidak memperhitungkan aspek kualitas lainnya, seperti kelancaran, tata bahasa, koherensi, dll. 
2. Untuk menilai pemilihan konten, mereka sebagian besar bergantung pada tumpang tindih leksikal, meskipun ringkasan abstraktif dapat mengekspresikan konten yang sama sebagai referensi tanpa tumpang tindih leksikal.
3. Mengingat subjektivitas ringkasan dan kesepakatan yang sama rendahnya antara annotator, metrik dirancang untuk digunakan dengan beberapa rujukan referensi per input. Namun, kumpulan data terbaru seperti CNN / DailyMail dan Gigaword hanya menyediakan satu referensi.

Oleh karena itu, melacak kemajuan dan mengklaim canggih hanya berdasarkan pada metrik ini dipertanyakan. Sebagian besar makalah melakukan perbandingan manual rangkuman alternatif. Sayangnya, percobaan seperti itu sulit untuk dibandingkan di berbagai makalah. Jika Anda memiliki ide tentang bagaimana melakukan itu, silakan berkontribusi.

### CNN / Daily Mail

[CNN / Daily Mail dataset](https://arxiv.org/abs/1506.03340) diproses oleh
[Nallapati et al. (2016)](http://www.aclweb.org/anthology/K16-1028) telah digunakan untuk mengevaluasi peringkasan. Dataset berisi artikel berita online (rata-rata 781 token) dipasangkan dengan ringkasan multi-kalimat (rata-rata 3,75 kalimat atau 56 token). Versi yang diproses berisi 287.226 pasangan pelatihan, 13.368 pasangan validasi dan 11.490 pasangan uji. Model dievaluasi dengan skor F1 panjang penuh ROUGE-1, ROUGE-2, ROUGE-L, dan METEOR (opsional).

#### Anonymized version

Model-model berikut telah dievaluasi pada versi entitas-anonim dari dataset yang diperkenalkan oleh [Nallapati et al. (2016)](http://www.aclweb.org/anthology/K16-1028).

| Model           | ROUGE-1 | ROUGE-2 | ROUGE-L | METEOR | Paper / Source | Code |
| --------------- | :-----: | :-----: | :-----: | :----: | -------------- | ---- |
| RNES w/o coherence (Wu and Hu, 2018) | 41.25 | 18.87 | 37.75 | - | [Learning to Extract Coherent Summary via Deep Reinforcement Learning](https://www.aaai.org/ocs/index.php/AAAI/AAAI18/paper/view/16838/16118) | |
| SWAP-NET (Jadhav and Rajan, 2018) | 41.6 | 18.3 | 37.7 | - | [Extractive Summarization with SWAP-NET: Sentences and Words from Alternating Pointer Networks](http://aclweb.org/anthology/P18-1014) | |
| HSASS (Al-Sabahi et al., 2018) | 42.3 | 17.8 | 37.6 | - | [A Hierarchical Structured Self-Attentive Model for Extractive Document Summarization (HSSAS)](https://ieeexplore.ieee.org/stamp/stamp.jsp?arnumber=8344797) | |
| GAN (Liu et al., 2018) | 39.92 | 17.65 | 36.71 | - | [Generative Adversarial Network for Abstractive Text Summarization](https://aaai.org/ocs/index.php/AAAI/AAAI18/paper/view/16238/16492) | |
| KIGN+Prediction-guide (Li et al., 2018) | 38.95| 17.12 | 35.68 | - | [Guiding Generation for Abstractive Text Summarization based on Key Information Guide Network](http://aclweb.org/anthology/N18-2009) | |
| SummaRuNNer (Nallapati et al., 2017) | ﻿39.6 | 16.2 | 35.3 | - | [SummaRuNNer: A Recurrent Neural Network based Sequence Model for Extractive Summarization of Documents](https://arxiv.org/abs/1611.04230) | |
| rnn-ext + abs + RL + rerank (Chen and Bansal, 2018) | 39.66 | 15.85 | 37.34 | - | [Fast Abstractive Summarization with Reinforce-Selected Sentence Rewriting](http://aclweb.org/anthology/P18-1063) | [Official](https://github.com/ChenRocks/fast_abs_rl) |
| ML+RL, with intra-attention (Paulus et al., 2018) | 39.87 | 15.82 | 36.90 | - | [A Deep Reinforced Model for Abstractive Summarization](https://openreview.net/pdf?id=HkAClQgA-) | |
| Lead-3 baseline (Nallapati et al., 2017) | 39.2 | 15.7 | 35.5 | - | [SummaRuNNer: A Recurrent Neural Network based Sequence Model for Extractive Summarization of Documents](https://arxiv.org/abs/1611.04230) | |
| ML+RL ROUGE+Novel, with LM (Kryscinski et al., 2018) | 40.02 | 15.53 | 37.44 | - | [Improving Abstraction in Text Summarization](http://aclweb.org/anthology/D18-1207) |  |
| (Tan et al., 2017) | 38.1 | 13.9 | 34.0 | - | [Abstractive Document Summarization with a Graph-Based Attentional Neural Model](http://aclweb.org/anthology/P17-1108) | |
| words-lvt2k-temp-att (Nallapti et al., 2016) | 35.46 | 13.30 | 32.65 | - | [Abstractive Text Summarization using Sequence-to-sequence RNNs and Beyond](http://www.aclweb.org/anthology/K16-1028) | |


#### Non-Anonymized Version: Extractive Models


Model-model berikut telah dievaluasi pada versi non-anonim dari dataset yang diperkenalkan oleh [lihat di et al. (2017)](http://aclweb.org/anthology/P17-1099).

Tabel pertama mencakup Model Ekstraktif, sedangkan yang kedua mencakup pendekatan abstraktif.

| Model           | ROUGE-1 | ROUGE-2 | ROUGE-L | METEOR | Paper / Source | Code |
| --------------- | :-----: | :-----: | :-----: | :----: | -------------- | ---- |
| BertSumExt (Liu and Lapata 2019) | 43.85 | 20.34 | 39.90 | - | [Text Summarization with Pretrained Encoders](https://arxiv.org/abs/1908.08345) |[Official](https://github.com/nlpyang/PreSumm) | 
| BERT-ext + RL (Bae et al., 2019) | 42.76 | 19.87 | 39.11 | - | [Summary Level Training of Sentence Rewriting for Abstractive Summarization](https://arxiv.org/abs/1909.08752) | |
| HIBERT (Zhang et al., 2019) | 42.37 | 19.95 | 38.83 | - | [HIBERT: Document Level Pre-training of Hierarchical Bidirectional Transformers for Document Summarization](https://arxiv.org/abs/1905.06566) | |
| NeuSUM (Zhou et al., 2018) | 41.59 | 19.01 | 37.98 | - | [Neural Document Summarization by Jointly Learning to Score and Select Sentences](http://aclweb.org/anthology/P18-1061) | [Official](https://github.com/magic282/NeuSum) |
| Latent (Zhang et al., 2018) | 41.05 | 18.77 | 37.54 | - | [Neural Latent Extractive Document Summarization](http://aclweb.org/anthology/D18-1088) | | 
| BanditSum (Dong et al., 2018) | 41.5 | 18.7 | 37.6 | - | [BANDITSUM: Extractive Summarization as a Contextual Bandit](https://aclweb.org/anthology/D18-1409) | [Official](https://github.com/yuedongP/BanditSum)|
| REFRESH (Narayan et al., 2018) | 40.0 | 18.2 | 36.6 | - | [Ranking Sentences for Extractive Summarization with Reinforcement Learning](http://aclweb.org/anthology/N18-1158) | [Official](https://github.com/EdinburghNLP/Refresh) |
| Lead-3 baseline (See et al., 2017) | 40.34 | 17.70 | 36.57 | 22.21 | [Get To The Point: Summarization with Pointer-Generator Networks](http://aclweb.org/anthology/P17-1099) | [Official](https://github.com/abisee/pointer-generator) |

#### Non-Anonymized: Abstractive Models & Mixed Models

| Model           | ROUGE-1 | ROUGE-2 | ROUGE-L | METEOR | Paper / Source | Code |
| --------------- | :-----: | :-----: | :-----: | :----: | -------------- | ---- |
| CNN-2sent-hieco-RBM (Zhang et al., 2019) | 42.04 | 19.77 | 39.42 | - |[Abstract Text Summarization with a Convolutional Seq2Seq Model](https://www.mdpi.com/2076-3417/9/8/1665/pdf) | |
| BertSumExtAbs (Liu and Lapata 2019) | 42.13 | 19.60 | 39.18 | - | [Text Summarization with Pretrained Encoders](https://arxiv.org/abs/1908.08345) |[Official](https://github.com/nlpyang/PreSumm) |
| BERT-ext + abs + RL + rerank (Bae et al., 2019) | 41.90 | 19.08 | 39.64 | - | [Summary Level Training of Sentence Rewriting for Abstractive Summarization](https://arxiv.org/abs/1909.08752) | |
| Two-Stage + RL (Zhang et al., 2019) | 41.71 | 19.49 | 38.79 | - | [Pretraining-Based Natural Language Generation for Text Summarization](https://arxiv.org/abs/1902.09243) | |
| DCA (Celikyilmaz et al., 2018) | 41.69 | 19.47 | 37.92 | - | [Deep Communicating Agents for Abstractive Summarization](http://aclweb.org/anthology/N18-1150) | |
| EditNet (Moroshko et al., 2018) | 41.42 | 19.03 | 38.36 | - | [An Editorial Network for Enhanced Document Summarization](https://arxiv.org/abs/1902.10360) | |
| rnn-ext + RL (Chen and Bansal, 2018) | 41.47 | 18.72 | 37.76 | 22.35 | [Fast Abstractive Summarization with Reinforce-Selected Sentence Rewriting](http://aclweb.org/anthology/P18-1061) | [Official](https://github.com/chenrocks/fast_abs_rl) |
| Bottom-Up Summarization (Gehrmann et al., 2018) | 41.22 | 18.68 | 38.34 | - | [Bottom-Up Abstractive Summarization](https://arxiv.org/abs/1808.10792) | [Official](https://github.com/sebastianGehrmann/bottom-up-summary) |
| (Li et al., 2018a) | 41.54 | 18.18 | 36.47 | - | [Improving Neural Abstractive Document Summarization with Explicit Information Selection Modeling](http://aclweb.org/anthology/D18-1205) | |
| (Li et al., 2018b) | 40.30 | 18.02 | 37.36 | - | [Improving Neural Abstractive Document Summarization with Structural Regularization](http://aclweb.org/anthology/D18-1441) | |
| ROUGESal+Ent RL (Pasunuru and Bansal, 2018) | 40.43 | 18.00 | 37.10 | 20.02 | [Multi-Reward Reinforced Summarization with Saliency and Entailment](http://aclweb.org/anthology/N18-2102) | |
| end2end w/ inconsistency loss (Hsu et al., 2018) | 40.68 | 17.97 | 37.13 | - | [A Unified Model for Extractive and Abstractive Summarization using Inconsistency Loss](http://aclweb.org/anthology/P18-1013) | |
| RL + pg + cbdec (Jiang and Bansal, 2018) | 40.66 | 17.87 | 37.06 | 20.51 | [Closed-Book Training to Improve Summarization Encoder Memory](http://aclweb.org/anthology/D18-1440) | |
| rnn-ext + abs + RL + rerank (Chen and Bansal, 2018) | 40.88 | 17.80 | 38.54 | 20.38 | [Fast Abstractive Summarization with Reinforce-Selected Sentence Rewriting](http://aclweb.org/anthology/P18-1061) | [Official](https://github.com/chenrocks/fast_abs_rl) |
| Pointer + Coverage + EntailmentGen + QuestionGen (Guo et al., 2018) | 39.81 | 17.64 | 36.54 | 18.54 | [Soft Layer-Specific Multi-Task Summarization with Entailment and Question Generation](http://aclweb.org/anthology/P18-1064) | |
| ML+RL ROUGE+Novel, with LM (Kryscinski et al., 2018) | 40.19 | 17.38 | 37.52 | - | [Improving Abstraction in Text Summarization](http://aclweb.org/anthology/D18-1207) | |
| Pointer-generator + coverage (See et al., 2017) | 39.53 | 17.28 | 36.38 | 18.72 | [Get To The Point: Summarization with Pointer-Generator Networks](http://aclweb.org/anthology/P17-1099) | [Official](https://github.com/abisee/pointer-generator) |



### Gigaword


Dataset ringkasan Gigaword telah digunakan pertama kali oleh [Rush et al., 2015](https://www.aclweb.org/anthology/D/D15/D15-1044.pdf) dan mewakili tugas pembuatan ringkasan / informasi utama kalimat dengan dokumen masukan yang sangat singkat (31,4 token) dan ringkasan (8,3 token). Ini berisi pelatihan 3,8 juta, pengembangan 189 ribu dan contoh uji 1951. Model dievaluasi dengan ROUGE-1, ROUGE-2 dan ROUGE-L menggunakan skor F1 panjang penuh.

| Model           | ROUGE-1 | ROUGE-2 | ROUGE-L | Paper / Source | Code |
| --------------- | :-----: | :-----: | :-----: | -------------- | ---- |
| BiSET (Wang et al., 2019) | 39.11 | 19.78 | 36.87 | [BiSET: Bi-directional Selective Encoding with Template for Abstractive Summarization](https://www.aclweb.org/anthology/P19-1207) | [Official](https://github.com/InitialBug/BiSET) |
| MASS (Song et al., 2019) | 38.73 | 19.71 | 35.96 | [MASS: Masked Sequence to Sequence Pre-training for Language Generation](https://arxiv.org/pdf/1905.02450v5.pdf) | [Official](https://github.com/microsoft/MASS) |
| CNN-2sent-hieco-RBM (Zhang et al., 2019) | 37.95 | 18.64 | 35.11 | [Abstract Text Summarization with a Convolutional Seq2Seq Model](https://www.mdpi.com/2076-3417/9/8/1665/pdf) | | |
| Re^3 Sum (Cao et al., 2018) | 37.04 | 19.03 | 34.46 | [Retrieve, Rerank and Rewrite: Soft Template Based Neural Summarization](http://aclweb.org/anthology/P18-1015) | |
| FTSum_g (Cao et al., 2018) | 37.27 | 17.65 | 34.24 | [Faithful to the Original: Fact Aware Neural Abstractive Summarization](https://arxiv.org/pdf/1711.04434.pdf) | |
| Seq2seq + E2T_cnn (Amplayo et al., 2018) | 37.04 | 16.66 | 34.93 | [Entity Commonsense Representation for Neural Abstractive Summarization](http://aclweb.org/anthology/N18-1064) | |
| Reinforced-Topic-ConvS2S (Wang et al., 2018) | 36.92 | 18.29 | 34.58 | [A Reinforced Topic-Aware Convolutional Sequence-to-Sequence Model for Abstractive Text Summarization](https://www.ijcai.org/proceedings/2018/0619.pdf) | |
| CGU (Lin et al., 2018) | 36.3 | 18.0 | 33.8 | [Global Encoding for Abstractive Summarization](http://aclweb.org/anthology/P18-2027) | [Official](https://www.github.com/lancopku/Global-Encoding) |
| DRGD (Li et al., 2017) | 36.27 | 17.57 | 33.62 | [Deep Recurrent Generative Decoder for Abstractive Text Summarization](http://aclweb.org/anthology/D17-1222) | |
| SEASS (Zhou et al., 2017) | 36.15 | 17.54 | 33.63 | [Selective Encoding for Abstractive Sentence Summarization](http://aclweb.org/anthology/P17-1101) | [Official](https://github.com/magic282/SEASS) |
| EndDec+WFE (Suzuki and Nagata, 2017) | 36.30 | 17.31 | 33.88 | [Cutting-off Redundant Repeating Generations for Neural Abstractive Summarization](http://aclweb.org/anthology/E17-2047) | |
| Pointer + Coverage + EntailmentGen + QuestionGen (Guo et al., 2018) | 35.98 | 17.76 | 33.63 | [Soft Layer-Specific Multi-Task Summarization with Entailment and Question Generation](http://aclweb.org/anthology/P18-1064) | |
| Struct+2Way+Word (Song et al., 2018) | 35.47 | 17.66 | 33.52 | [Structure-Infused Copy Mechanisms for Abstractive Summarization](http://aclweb.org/anthology/C18-1146) | [Official](https://github.com/KaiQiangSong/struct_infused_summ)|
| Seq2seq + selective + MTL + ERAM (Li et al., 2018) | 35.33 | 17.27 | 33.19 | [Ensure the Correctness of the Summary: Incorporate Entailment Knowledge into Abstractive Sentence Summarization](http://aclweb.org/anthology/C18-1121) | |
| RAS-Elman (Chopra et al., 2016) | 33.78 | 15.97 | 31.15 | [Abstractive Sentence Summarization with Attentive Recurrent Neural Networks](http://www.aclweb.org/anthology/N16-1012) | |
| words-lvt5k-1sent (Nallapti et al., 2016) | 32.67 | 15.59 | 30.64 | [Abstractive Text Summarization using Sequence-to-sequence RNNs and Beyond](http://www.aclweb.org/anthology/K16-1028) | |
| ABS+ (Rush et al., 2015) | 29.76 | 11.88 | 26.96 | [A Neural Attention Model for Sentence Summarization](https://www.aclweb.org/anthology/D/D15/D15-1044.pdf) * | |
| ABS (Rush et al., 2015) | 29.55 | 11.32 | 26.42 | [A Neural Attention Model for Sentence Summarization](https://www.aclweb.org/anthology/D/D15/D15-1044.pdf) * | |

(*) [Rush et al., 2015](https://www.aclweb.org/anthology/D/D15/D15-1044.pdf)  report ROUGE recall, the table here contains ROUGE F1-scores for Rush's model reported by [Chopra et al., 2016](http://www.aclweb.org/anthology/N16-1012)

### DUC 2004 Task 1

Mirip dengan Gigaword, tugas 1 dari [DUC 2004](https://duc.nist.gov/duc2004/) adalah tugas meringkas kalimat. Dataset berisi 500 dokumen dengan rata-rata 35,6 token dan ringkasan dengan 10,4 token. Karena ukurannya, model saraf biasanya dilatih pada dataset lain dan hanya diuji pada DUC 2004. Metrik evaluasi adalah ROUGE-1, ROUGE-2 dan ROUGE-L recall @ 75 byte.

| Model           | ROUGE-1 | ROUGE-2 | ROUGE-L | Paper / Source | Code |
| --------------- | :-----: | :-----: | :-----: | -------------- | ---- |
| Transformer + LRPE + PE + Re-ranking (Takase and Okazaki, 2019) | 32.29 | 11.49 | 28.03 | [Positional Encoding to Control Output Sequence Length](https://arxiv.org/abs/1904.07418) | [Official](https://github.com/takase/control-length) |
| DRGD (Li et al., 2017) | 31.79 | 10.75 | 27.48 | [Deep Recurrent Generative Decoder for Abstractive Text Summarization](http://aclweb.org/anthology/D17-1222) | |
| EndDec+WFE (Suzuki and Nagata, 2017) | 32.28 | 10.54 | 27.8 | [Cutting-off Redundant Repeating Generations for Neural Abstractive Summarization](http://aclweb.org/anthology/E17-2047) | |
| Reinforced-Topic-ConvS2S (Wang et al., 2018) | 31.15 | 10.85 | 27.68 | [A Reinforced Topic-Aware Convolutional Sequence-to-Sequence Model for Abstractive Text Summarization](https://www.ijcai.org/proceedings/2018/0619.pdf) | |
| CNN-2sent-hieco-RBM (Zhang et al., 2019) | 29.74 | 9.85 | 25.81 | [Abstract Text Summarization with a Convolutional Seq2Seq Model](https://www.mdpi.com/2076-3417/9/8/1665/pdf) |
| Seq2seq + selective + MTL + ERAM (Li et al., 2018) | 29.33 | 10.24 | 25.24 | [Ensure the Correctness of the Summary: Incorporate Entailment Knowledge into Abstractive Sentence Summarization](http://aclweb.org/anthology/C18-1121) | |
| SEASS (Zhou et al., 2017) | 29.21 | 9.56 | 25.51 | [Selective Encoding for Abstractive Sentence Summarization](http://aclweb.org/anthology/P17-1101) | |
| words-lvt5k-1sent (Nallapti et al., 2016) | 28.61 | 9.42 | 25.24 | [Abstractive Text Summarization using Sequence-to-sequence RNNs and Beyond](http://www.aclweb.org/anthology/K16-1028) | |
| ABS+ (Rush et al., 2015) | 28.18 | 8.49 | 23.81 | [A Neural Attention Model for Sentence Summarization](https://www.aclweb.org/anthology/D/D15/D15-1044.pdf) | |
| RAS-Elman (Chopra et al., 2016) | 28.97 | 8.26 | 24.06 | [Abstractive Sentence Summarization with Attentive Recurrent Neural Networks](http://www.aclweb.org/anthology/N16-1012) | |
| ABS (Rush et al., 2015) | 26.55 | 7.06 | 22.05 | [A Neural Attention Model for Sentence Summarization](https://www.aclweb.org/anthology/D/D15/D15-1044.pdf) | |

## Webis-TLDR-17 Corpus

[dataset] ini (https://zenodo.org/record/1168855) berisi 3 Juta pasangan konten dan ringkasan yang ditulis sendiri yang ditambang dari Reddit. Ini adalah salah satu set data rangkuman berskala besar pertama dari domain media sosial. Untuk detail lebih lanjut, lihat [TL; DR: Menambang Reddit untuk Mempelajari Peringkasan Otomatis](https://aclweb.org/anthology/W17-4508)

## Sentence Compression

Sentence compression menghasilkan kalimat yang lebih pendek dengan menghapus informasi yang berlebihan, menjaga tata bahasa dan konten penting dari kalimat asli.

### Google Dataset

[Google Dataset](https://github.com/google-research-datasets/sentence-compression) dibangun oleh Filippova et al., 2013([Mengatasi Kurangnya Data Paralel dalam Kompresi Kalimat](https://www.aclweb.org/anthology/D/D13/D13-1155.pdf)). Dataset pertama yang dirilis hanya berisi 10.000 pasangan kompresi-kalimat, tetapi tahun lalu dirilis 200.000 pasangan tambahan.

Contoh dari pasangan kompresi kalimat:
> Kalimat: Floyd Mayweather terbuka untuk bertarung melawan Amir Khan di masa depan, meskipun menolak petinju kelahiran Bolton itu demi pertarungan Mei dengan pemain Argentina Marcos Maidana, menurut promotor Golden Boy

> Kompresi: Floyd Mayweather terbuka untuk memerangi Amir Khan di masa depan.

Singkatnya, ini adalah tugas berbasis penghapusan di mana compression adalah hasil dari kalimat aslinya. Dari 10.000 pasangan bagian eval([repository](https://github.com/google-research-datasets/sentence-compression/tree/master/data)) digunakan 1.000 kalimat pertama untuk evaluasi otomatis dan 200.000 pasangan untuk pelatihan.

Model dievaluasi menggunakan metrik berikut:
* F1 - hitung daya ingat dan presisi dalam hal token yang disimpan dalam emas dan kompresi yang dihasilkan.
* Tingkat kompresi (CR) - panjang kompresi dalam karakter dibagi atas panjang kalimat.

| Model           | F1 | CR |Paper / Source | Code |
| -------------   | :-----:| --- | --- | --- |
| BiRNN + LM Evaluator (Zhao et al. 2018) | 0.851 | 0.39 | [A Language Model based Evaluator for Sentence Compression](https://aclweb.org/anthology/P18-2028) | https://github.com/code4conference/code4sc |
| LSTM (Filippova et al., 2015) | 0.82 | 0.38 | [Sentence Compression by Deletion with LSTMs](https://research.google.com/pubs/archive/43852.pdf) | |
| BiLSTM (Wang et al., 2017) | 0.8 | 0.43 | [Can Syntax Help? Improving an LSTM-based Sentence Compression Model for New Domains](http://www.aclweb.org/anthology/P17-1127) |  |

[Go back to the README](../README.md)
