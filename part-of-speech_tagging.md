# Part-of-speech tagging

Part-of-speech tagging (POS tagging) adalah tugas penandaan kata dalam teks dengan bagian bicaranya. Bagian dari pidato adalah kategori kata dengan sifat gramatikal yang serupa. Bagian Bahasa Inggris yang umum digunakan adalah kata benda, kata kerja, kata sifat, kata keterangan, kata ganti, kata depan, kata sambung, dll.

Contoh : 

| Vinken | , | 61 | years | old |
| --- | ---| --- | --- | --- |
| NNP | , | CD | NNS | JJ |

### Penn Treebank

Dataset standar untuk penandaan POS adalah bagian Wall Street Journal (WSJ) dari Penn Treebank, yang berisi 45 tag POS berbeda. Bagian 0-18 digunakan untuk pelatihan, bagian 19-21 untuk pengembangan, dan bagian 22-24 untuk pengujian. Model dievaluasi berdasarkan akurasi.

| Model           | Accuracy  |  Paper / Source | Code |
| ------------- | :-----:| --- | --- |
| Meta BiLSTM (Bohnet et al., 2018) | 97.96 | [Morphosyntactic Tagging with a Meta-BiLSTM Model over Context Sensitive Token Encodings](https://arxiv.org/abs/1805.08237) | |
| Flair embeddings (Akbik et al., 2018) | 97.85 | [Contextual String Embeddings for Sequence Labeling](http://aclweb.org/anthology/C18-1139) | [Flair framework](https://github.com/zalandoresearch/flair) |
| Char Bi-LSTM (Ling et al., 2015) | 97.78 | [Finding Function in Form: Compositional Character Models for Open Vocabulary Word Representation](https://www.aclweb.org/anthology/D/D15/D15-1176.pdf) | |
| Adversarial Bi-LSTM (Yasunaga et al., 2018) | 97.59 | [Robust Multilingual Part-of-Speech Tagging via Adversarial Training](https://arxiv.org/abs/1711.04903) | |
| Yang et al. (2017) | 97.55 | [Transfer Learning for Sequence Tagging with Hierarchical Recurrent Networks](https://arxiv.org/abs/1703.06345) | |
| Ma and Hovy (2016) | 97.55 | [End-to-end Sequence Labeling via Bi-directional LSTM-CNNs-CRF](https://arxiv.org/abs/1603.01354) | |
| LM-LSTM-CRF (Liu et al., 2018)| 97.53 | [Empowering Character-aware Sequence Labeling with Task-Aware Neural Language Model](https://arxiv.org/pdf/1709.04109.pdf) | |
| NCRF++ (Yang and Zhang, 2018)| 97.49 | [NCRF++: An Open-source Neural Sequence Labeling Toolkit](http://www.aclweb.org/anthology/P18-4013) | [NCRF++](https://github.com/jiesutd/NCRFpp) |
| Feed Forward (Vaswani et a. 2016) | 97.4 | [Supertagging with LSTMs](https://aclweb.org/anthology/N/N16/N16-1027.pdf) | |
| Bi-LSTM (Ling et al., 2017) | 97.36 | [Finding Function in Form: Compositional Character Models for Open Vocabulary Word Representation](https://www.aclweb.org/anthology/D/D15/D15-1176.pdf) | | 
| Bi-LSTM (Plank et al., 2016) | 97.22 | [Multilingual Part-of-Speech Tagging with Bidirectional Long Short-Term Memory Models and Auxiliary Loss](https://arxiv.org/abs/1604.05529) | |


### Social media

[Ritter (2011)](https://www.aclweb.org/anthology/D11-1141) dataset Ritter (2011) telah menjadi tolok ukur untuk penandaan part-of-speech media sosial. Ini terdiri dari sekitar 50 ribu token media sosial Inggris yang diambil sampelnya pada akhir 2011, dan ditandai menggunakan versi diperpanjang dari tagset PTB.

| Model | Akurasi  | Makalah  |
| --- | --- | ---|
| FastText + CNN + CRF | 90.53 | [Twitter word embeddings (Godin et al. 2019 (Chapter 3))](https://fredericgodin.com/research/twitter-word-embeddings/) | 
| CMU | 90.0 ± 0.5 | [Improved Part-of-Speech Tagging for Online Conversational Text with Word Clusters](http://www.cs.cmu.edu/~ark/TweetNLP/owoputi+etal.naacl13.pdf) | 
| GATE  | 88.69 | [Twitter Part-of-Speech Tagging for All: Overcoming Sparse and Noisy Data](https://www.aclweb.org/anthology/R13-1026) | 

### UD

[Universal Dependencies (UD)](http://universaldependencies.org/) adalah kerangka kerja untuk anotasi tata bahasa lintas-bahasa, yang berisi lebih dari 100 treebanks dalam lebih dari 60 bahasa. Model biasanya dievaluasi berdasarkan akurasi pengujian rata-rata di 21 bahasa sumber daya tinggi (♦ dievaluasi pada 17 bahasa).

| Model           | Avg akurasi  |  Makalah / Sumber |
| ------------- | :-----:| --- |
| Multilingual BERT and BPEmb (Heinzerling and Strube, 2019) | 96.77 | [Sequence Tagging with Contextual and Non-Contextual Subword Representations: A Multilingual Evaluation](https://arxiv.org/abs/1906.01569) |
| Adversarial Bi-LSTM (Yasunaga et al., 2018) | 96.65 | [Robust Multilingual Part-of-Speech Tagging via Adversarial Training](https://arxiv.org/abs/1711.04903) | 
| MultiBPEmb (Heinzerling and Strube, 2019) | 96.62 | [Sequence Tagging with Contextual and Non-Contextual Subword Representations: A Multilingual Evaluation](https://arxiv.org/abs/1906.01569) |
| Bi-LSTM (Plank et al., 2016) | 96.40 | [Multilingual Part-of-Speech Tagging with Bidirectional Long Short-Term Memory Models and Auxiliary Loss](https://arxiv.org/abs/1604.05529) |
| Joint Bi-LSTM (Nguyen et al., 2017)♦ | 95.55 | [A Novel Neural Network Model for Joint POS Tagging and Graph-based Dependency Parsing](https://arxiv.org/abs/1705.05952) |

[Kembali ke README](../README.md)
