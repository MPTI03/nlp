# Semantic textual similarity

Semantic textual similarity berkaitan dengan menentukan seberapa mirip dua keping teks itu.
Ini dapat berupa pemberian skor dari 1 hingga 5. 
Tugas terkait adalah parafrase atau duplikasi identifikasi.

### SentEval

[SentEval](https://arxiv.org/abs/1803.05449) adalah perangkat evaluasi untuk mengevaluasi representasi kalimat. Ini mencakup 17 tugas hilir, termasuk tugas kesamaan teks semantik yang umum. Tugas tolok ukur kemiripan semantik (STS) 2012-2016 (STS12, STS13, STS14, STS15, STS16, STS-B) mengukur keterkaitan dua kalimat berdasarkan kesamaan cosinus dari dua representasi. Kriteria evaluasi adalah korelasi Pearson.

SICK relatedness (SICK-R) melatih model linier untuk menghasilkan skor dari 1 hingga 5 yang mengindikasikan keterkaitan dua kalimat. Untuk dataset yang sama (SICK-E) dapat diperlakukan sebagai masalah klasifikasi tiga kelas menggunakan label entailment (kelas adalah 'entailment', 'kontradiksi', dan 'netral'). Metrik evaluasi untuk SICK-R adalah korelasi Pearson dan akurasi klasifikasi untuk SICK-E.

Microsoft Research Paraphrase Corpus (MRPC) corpus adalah dataset identifikasi parafrase, di mana sistem bertujuan untuk mengidentifikasi apakah dua kalimat adalah parafrase satu sama lain. Metrik evaluasi adalah akurasi klasifikasi dan F1.

Data dapat diunduh dari [sini](https://github.com/facebookresearch/SentEval).

| Model           | MRPC | SICK-R | SICK-E | STS | Paper / Source | Code |
| ------------- | :-----:| :-----:| :-----:| :-----:| --- | --- |
| XLNet-Large (ensemble) (Yang et al., 2019) | 93.0/90.7 | - | - | 91.6/91.1* | [XLNet: Generalized Autoregressive Pretraining for Language Understanding](https://arxiv.org/pdf/1906.08237.pdf) | [Official](https://github.com/zihangdai/xlnet/) |
| MT-DNN-ensemble (Liu et al., 2019) | 92.7/90.3 | - | - | 91.1/90.7* | [Improving Multi-Task Deep Neural Networks via Knowledge Distillation for Natural Language Understanding](https://arxiv.org/pdf/1904.09482.pdf) | [Official](https://github.com/namisan/mt-dnn/) |
| Snorkel MeTaL(ensemble) (Ratner et al., 2018) | 91.5/88.5 | - | - | 90.1/89.7* | [Training Complex Models with Multi-Task Weak Supervision](https://arxiv.org/pdf/1810.02840.pdf) | [Official](https://github.com/HazyResearch/metal) |
| GenSen (Subramanian et al., 2018) | 78.6/84.4 | 0.888 | 87.8 | 78.9/78.6 | [Learning General Purpose Distributed Sentence Representations via Large Scale Multi-task Learning](https://arxiv.org/abs/1804.00079) | [Official](https://github.com/Maluuba/gensen) |
| InferSent (Conneau et al., 2017) | 76.2/83.1 | 0.884 | 86.3 | 75.8/75.5 | [Supervised Learning of Universal Sentence Representations from Natural Language Inference Data](https://arxiv.org/abs/1705.02364) | [Official](https://github.com/facebookresearch/InferSent) |
| TF-KLD (Ji and Eisenstein, 2013) | 80.4/85.9 | - | - | - | [Discriminative Improvements to Distributional Sentence Similarity](http://www.aclweb.org/anthology/D/D13/D13-1090.pdf) |  |

\* hanya pada evaluasi STS-B

## Paraphrase identification

### Quora Question Pairs

[Quora Question Pairs dataset](https://data.quora.com/First-Quora-Dataset-Release-Question-Pairs)
terdiri dari lebih dari 400.000 pasangan pertanyaan di Quora. Sistem harus mengidentifikasi apakah satu pertanyaan merupakan duplikat dari yang lain. Model dievaluasi berdasarkan akurasi.

| Model           | F1 | Accuracy  |  Paper / Source | Code |
| ------------- | :-----: | :-----:| --- | --- |
| XLNet-Large (ensemble) (Yang et al., 2019) | 74.2 | 90.3 | [XLNet: Generalized Autoregressive Pretraining for Language Understanding](https://arxiv.org/pdf/1906.08237.pdf) | [Official](https://github.com/zihangdai/xlnet/) |
| MT-DNN-ensemble (Liu et al., 2019) | 73.7 | 89.9 | [Improving Multi-Task Deep Neural Networks via Knowledge Distillation for Natural Language Understanding](https://arxiv.org/pdf/1904.09482.pdf) | [Official](https://github.com/namisan/mt-dnn/) |
| Snorkel MeTaL(ensemble) (Ratner et al., 2018) | 73.1 | 89.9 | [Training Complex Models with Multi-Task Weak Supervision](https://arxiv.org/pdf/1810.02840.pdf) | [Official](https://github.com/HazyResearch/metal) |
| MwAN (Tan et al., 2018) | | 89.12 | [Multiway Attention Networks for Modeling Sentence Pairs](https://www.ijcai.org/proceedings/2018/0613.pdf) | |
| DIIN (Gong et al., 2018) | | 89.06 | [Natural Language Inference Over Interaction Space](https://arxiv.org/pdf/1709.04348.pdf) | [Official](https://github.com/YichenGong/Densely-Interactive-Inference-Network) |
| pt-DecAtt (Char) (Tomar et al., 2017) | | 88.40 | [Neural Paraphrase Identification of Questions with Noisy Pretraining](https://arxiv.org/abs/1704.04565) | |
| BiMPM (Wang et al., 2017) | | 88.17 | [Bilateral Multi-Perspective Matching for Natural Language Sentences](https://arxiv.org/abs/1702.03814) | [Official](https://github.com/zhiguowang/BiMPM) |
| GenSen (Subramanian et al., 2018) | | 87.01 | [Learning General Purpose Distributed Sentence Representations via Large Scale Multi-task Learning](https://arxiv.org/abs/1804.00079) | [Official](https://github.com/Maluuba/gensen) |

[Go back to the README](../README.md)
