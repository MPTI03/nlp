# Text classification

Text classification adalah tugas menetapkan kalimat atau mendokumentasikan kategori yang sesuai. Kategori bergantung pada dataset yang dipilih dan dapat berkisar dari topik

### AG News

[AG News corpus](https://papers.nips.cc/paper/5782-character-level-convolutional-networks-for-text-classification.pdf)
terdiri dari artikel berita dari korpus artikel berita AG di web(http://www.di.unipi.it/~gulli/AG_corpus_of_news_articles.html)
yang berkaitan dengan 4 kelas terbesar. Dataset berisi 30.000 pelatihan dan 1.900 contoh pengujian untuk setiap kelas. Model dievaluasi berdasarkan tingkat kesalahan (lebih rendah lebih baik).

| Model           | Error  |  Paper / Source | Code |
| ------------- | :-----:| --- | :-----: |
| XLNet (Yang et al., 2019) | 4.49 | [XLNet: Generalized Autoregressive Pretraining for Language Understanding](https://arxiv.org/pdf/1906.08237.pdf) | [Official](https://github.com/zihangdai/xlnet/) |
| ULMFiT (Howard and Ruder, 2018) | 5.01 | [Universal Language Model Fine-tuning for Text Classification](https://arxiv.org/abs/1801.06146) | [Official](http://nlp.fast.ai/ulmfit ) |
| CNN (Johnson and Zhang, 2016) * | 6.57 | [Supervised and Semi-Supervised Text Categorization using LSTM for Region Embeddings](https://arxiv.org/abs/1602.02373) | [Official](https://github.com/riejohnson/ConText ) |
| DPCNN (Johnson and Zhang, 2017) | 6.87 | [Deep Pyramid Convolutional Neural Networks for Text Categorization](http://aclweb.org/anthology/P17-1052) | [Official](https://github.com/riejohnson/ConText ) |
| VDCN (Alexis et al., 2016) | 8.67 | [Very Deep Convolutional Networks for Text Classification](https://arxiv.org/abs/1606.01781) | [Non Official](https://github.com/ArdalanM/nlp-benchmarks/tree/master/src/vdcnn) |
| Char-level CNN (Zhang et al., 2015) | 9.51 | [Character-level Convolutional Networks for Text Classification](https://papers.nips.cc/paper/5782-character-level-convolutional-networks-for-text-classification.pdf) | [Non Official](https://github.com/ArdalanM/nlp-benchmarks/tree/master/src/cnn) |

\* Hasil dilaporkan oleh Johnson and Zhang, 2017

### DBpedia

[DBpedia ontology](https://papers.nips.cc/paper/5782-character-level-convolutional-networks-for-text-classification.pdf) 
dataset berisi 560.000 sampel pelatihan dan 70.000 sampel pengujian untuk masing-masing dari 14 kelas yang tidak tumpang tindih dari DBpedia. Model dievaluasi berdasarkan tingkat kesalahan (lebih rendah lebih baik).
| Model           | Error  |  Paper / Source | Code |
| ------------- | :-----:| --- | :-----: |
| XLNet (Yang et al., 2019) | 0.62 | [XLNet: Generalized Autoregressive Pretraining for Language Understanding](https://arxiv.org/pdf/1906.08237.pdf) | [Official](https://github.com/zihangdai/xlnet/) |
| Bidirectional Encoder Representations from Transformers (Devlin et al., 2018) | 0.64 | [BERT: Pre-training of Deep Bidirectional Transformers for Language Understanding](https://arxiv.org/abs/1810.04805) | [Official](https://github.com/google-research/bert) |
| ULMFiT (Howard and Ruder, 2018) | 0.80 | [Universal Language Model Fine-tuning for Text Classification](https://arxiv.org/abs/1801.06146)  | [Official](http://nlp.fast.ai/ulmfit ) |
| CNN (Johnson and Zhang, 2016) | 0.84 | [Supervised and Semi-Supervised Text Categorization using LSTM for Region Embeddings](https://arxiv.org/abs/1602.02373) | [Official](https://github.com/riejohnson/ConText ) |
| DPCNN (Johnson and Zhang, 2017) | 0.88 | [Deep Pyramid Convolutional Neural Networks for Text Categorization](http://aclweb.org/anthology/P17-1052) | [Official](https://github.com/riejohnson/ConText ) |
| VDCN (Alexis et al., 2016) | 1.29 | [Very Deep Convolutional Networks for Text Classification](https://arxiv.org/abs/1606.01781) |  [Non Official](https://github.com/ArdalanM/nlp-benchmarks/tree/master/src/vdcnn) |
| Char-level CNN (Zhang et al., 2015) | 1.55 | [Character-level Convolutional Networks for Text Classification](https://papers.nips.cc/paper/5782-character-level-convolutional-networks-for-text-classification.pdf) | [Non Official](https://github.com/ArdalanM/nlp-benchmarks/tree/master/src/cnn) |

### TREC

[TREC dataset](http://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.11.2766&rep=rep1&type=pdf) adalah dataset untuk klasifikasi pertanyaan yang terdiri dari domain terbuka, pertanyaan berbasis fakta yang dibagi ke dalam kategori semantik luas. Ini memiliki versi enam kelas (TREC-6) dan lima puluh kelas (TREC-50). Keduanya memiliki 5.452 contoh pelatihan dan 500 contoh uji, tetapi TREC-50 memiliki label yang lebih halus. Model dievaluasi berdasarkan akurasi.

TREC-6:

| Model           | Error  |  Paper / Source | Code |
| ------------- | :-----:| --- | :-----: |
| USE_T+CNN (Cer et al., 2018) | 1.93 | [Universal Sentence Encoder](https://arxiv.org/pdf/1803.11175.pdf) | [Official](https://tfhub.dev/google/universal-sentence-encoder/1) |
| ULMFiT (Howard and Ruder, 2018) | 3.6 | [Universal Language Model Fine-tuning for Text Classification](https://arxiv.org/abs/1801.06146) | [Official](http://nlp.fast.ai/ulmfit ) |
| LSTM-CNN (Zhou et al., 2016) | 3.9 | [Text Classification Improved by Integrating Bidirectional LSTM with Two-dimensional Max Pooling](http://www.aclweb.org/anthology/C16-1329) |
| CNN+MCFA (Amplayo et al., 2018) | 4 | [Translations as Additional Contexts for Sentence Classification](https://arxiv.org/pdf/1806.05516.pdf) |
| TBCNN (Mou et al., 2015) | 4 | [Discriminative Neural Sentence Modeling by Tree-Based Convolution](http://aclweb.org/anthology/D15-1279) |
| CoVe (McCann et al., 2017) | 4.2 | [Learned in Translation: Contextualized Word Vectors](https://arxiv.org/abs/1708.00107) |

TREC-50:

| Model           | Error  |  Paper / Source | Code |
| ------------- | :-----:| --- | :-----: |
| Rules (Madabushi and Lee, 2016) | 2.8 |[High Accuracy Rule-based Question Classification using Question Syntax and Semantics](http://www.aclweb.org/anthology/C16-1116)| |
| SVM (Van-Tu and Anh-Cuong, 2016) | 8.4 | [Improving Question Classification by Feature Extraction and Selection](https://www.researchgate.net/publication/303553351_Improving_Question_Classification_by_Feature_Extraction_and_Selection) | |

[Go back to the README](../README.md)
