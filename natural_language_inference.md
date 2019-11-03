# Natural language inference

Natural language inference adalah tugas untuk menentukan apakah "hipotesis" itu benar (entailment), false (kontradiksi), atau tidak ditentukan (netral) diberi "premis".

Example:

| Premise | Label | Hypothesis |
| --- | ---| --- |
| A man inspects the uniform of a figure in some East Asian country. | contradiction | The man is sleeping. |
| An older and younger man smiling. | neutral  | Two men are smiling and laughing at the cats playing on the floor. |
| A soccer game with multiple males playing. | entailment | Some men are playing a sport. |

### SNLI

The [Stanford Natural Language Inference (SNLI) Corpus](https://arxiv.org/abs/1508.05326)
Corpus berisi sekitar 550 ribu pasang hipotesis / premis. Model dievaluasi berdasarkan akurasi.

Hasil mutakhir dapat dilihat di [SNLI website](https://nlp.stanford.edu/projects/snli/).

### MultiNLI

The [Multi-Genre Natural Language Inference (MultiNLI) corpus](https://arxiv.org/abs/1704.05426)
corpus berisi sekitar 433k pasangan hipotesis / premis. Ini mirip dengan corpus SNLI, tetapi mencakup berbagai genre teks lisan dan tulisan dan mendukung evaluasi lintas-genre. Data dapat diunduh dari [MultiNLI](https://www.nyu.edu/projects/bowman/multinli/) website.

Papan peringkat publik [in-genre (matched)](https://www.kaggle.com/c/multinli-matched-open-evaluation/leaderboard) 
and [cross-genre (mismatched)](https://www.kaggle.com/c/multinli-mismatched-open-evaluation/leaderboard)
evaluasi tersedia, tetapi entri tidak sesuai dengan model yang diterbitkan.

| Model           | Matched  | Mismatched | Makalah / Sumber | Code | 
| ------------- | :-----:| :-----:| --- | --- |
| RoBERTa (Liu et al., 2019) | 90.8 | 90.2 | [RoBERTa: A Robustly Optimized BERT Pretraining Approach](https://arxiv.org/pdf/1907.11692.pdf) | [Official](https://github.com/pytorch/fairseq/blob/master/examples/roberta/README.md) |
| XLNet-Large (ensemble) (Yang et al., 2019) | 90.2 | 89.8 | [XLNet: Generalized Autoregressive Pretraining for Language Understanding](https://arxiv.org/pdf/1906.08237.pdf) | [Official](https://github.com/zihangdai/xlnet/) |
| MT-DNN-ensemble (Liu et al., 2019) | 87.9 | 87.4 | [Improving Multi-Task Deep Neural Networks via Knowledge Distillation for Natural Language Understanding](https://arxiv.org/pdf/1904.09482.pdf) | [Official](https://github.com/namisan/mt-dnn/) |
| Snorkel MeTaL(ensemble) (Ratner et al., 2018) | 87.6 | 87.2 | [Training Complex Models with Multi-Task Weak Supervision](https://arxiv.org/pdf/1810.02840.pdf) | [Official](https://github.com/HazyResearch/metal) |
| Finetuned Transformer LM (Radford et al., 2018) | 82.1 | 81.4 | [Improving Language Understanding by Generative Pre-Training](https://s3-us-west-2.amazonaws.com/openai-assets/research-covers/language-unsupervised/language_understanding_paper.pdf) | |
| Multi-task BiLSTM + Attn (Wang et al., 2018) | 72.2 | 72.1 | [GLUE: A Multi-Task Benchmark and Analysis Platform for Natural Language Understanding](https://arxiv.org/abs/1804.07461) | |
| GenSen (Subramanian et al., 2018) | 71.4 | 71.3 | [Learning General Purpose Distributed Sentence Representations via Large Scale Multi-task Learning](https://arxiv.org/abs/1804.00079) | |

### SciTail

[SciTail](http://ai2-website.s3.amazonaws.com/publications/scitail-aaai-2018_cameraready.pdf)
dataset entailment SciTail terdiri dari 27 ribu. Berbeda dengan SNLI dan MultiNLI, itu tidak bersumber dari orang banyak tetapi dibuat dari kalimat yang sudah ada "di alam liar". Hipotesis dibuat dari pertanyaan sains dan kandidat jawaban yang sesuai, sedangkan kalimat web yang relevan dari sebuah korpus besar digunakan sebagai tempat. Model dievaluasi berdasarkan akurasi.



| Model           | Akurasi   |  Makalah / Sumber |
| ------------- | :-----:| --- |
| Finetuned Transformer LM (Radford et al., 2018) | 88.3 | [Improving Language Understanding by Generative Pre-Training](https://s3-us-west-2.amazonaws.com/openai-assets/research-covers/language-unsupervised/language_understanding_paper.pdf) 
| Hierarchical BiLSTM Max Pooling (Talman et al., 2018) | 86.0 | [Natural Language Inference with Hierarchical BiLSTM Max Pooling](https://arxiv.org/abs/1808.08762)
| CAFE (Tay et al., 2018) | 83.3 | [A Compare-Propagate Architecture with Alignment Factorization for Natural Language Inference](https://arxiv.org/abs/1801.00102) |

[Kembali ke README](../README.md)
