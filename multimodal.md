# Multimodal

## Multimodal Emotion Recognition 

### IEMOCAP

The  IEMOCAP ([Busso  et  al., 2008](https://link.springer.com/article/10.1007/s10579-008-9076-6)) ) berisi tindakan 10 pembicara dalam percakapan dua arah yang tersegmentasi menjadi ucapan. Media percakapan di semua video adalah bahasa Inggris. Basis data berisi label kategori berikut: kemarahan, kebahagiaan, kesedihan, netral, kegembiraan, frustrasi, ketakutan, kejutan, dan lainnya.


**Monologue:**

| Model           | Accuracy  |  Paper / Source |
| ------------- | :-----:| --- |
| CHFusion (Poria et al., 2017) | 76.5%  | [Multimodal Sentiment Analysis using Hierarchical Fusion with Context Modeling](https://arxiv.org/pdf/1806.06228.pdf) |
| bc-LSTM (Poria et al., 2017) | 74.10%  | [Context-Dependent Sentiment Analysis in User-Generated Videos](http://sentic.net/context-dependent-sentiment-analysis-in-user-generated-videos.pdf) |

**Conversational:**
Conversational settings memungkinkan model untuk menangkap emosi yang diungkapkan oleh pembicara dalam percakapan. Ketergantungan antar pembicara dipertimbangkan dalam pengaturan ini.


| Model           |  Weighted Accuracy (WAA)  |  Paper / Source |
| ------------- | :-----:| --- |
| CMN (Hazarika et al., 2018) |  77.62%  | [Conversational Memory Network for Emotion Recognition in Dyadic Dialogue Videos](http://aclweb.org/anthology/N18-1193) |
| Memn2n | 75.08 | [Conversational Memory Network for Emotion Recognition in Dyadic Dialogue Videos](http://aclweb.org/anthology/N18-1193)|

## Multimodal Metaphor Recognition

[Mohammad et. al, 2016](http://www.aclweb.org/anthology/S16-2003) 2016 menciptakan dataset pasangan kata benda dari WordNet yang memiliki banyak indera. Mereka memberi catatan pada pasangan-pasangan ini untuk metafora (metafora atau bukan metafora). Dataset dalam bahasa Inggris.

| Model                                                        |                            F1 Score                             | Paper / Source                                               | Code        |
| ------------------------------------------------------------ | :----------------------------------------------------------: | ------------------------------------------------------------ | ----------- |
| 5-layer convolutional network (Krizhevsky et al., 2012), Word2Vec | 0.75 | [Shutova et. al, 2016](http://www.aclweb.org/anthology/N16-1020) | Unavailable |

[Tsvetkov  et. al, 2014](http://www.aclweb.org/anthology/P14-1024) membuat dataset pasangan kata sifat-kata benda yang kemudian mereka anotasi untuk metaforisitas. Dataset dalam bahasa Inggris.


| Model                                                        |                            F1 Score                             | Paper / Source                                               | Code        |
| ------------------------------------------------------------ | :----------------------------------------------------------: | ------------------------------------------------------------ | ----------- |
| 5-layer convolutional network (Krizhevsky et al., 2012), Word2Vec | 0.79 | [Shutova et. al, 2016](http://www.aclweb.org/anthology/N16-1020) | Unavailable |

## Multimodal Sentiment Analysis

### MOSI
Dataset MOSI ([Zadeh et al., 2016](https://arxiv.org/pdf/1606.06259.pdf)) adalah kumpulan data yang kaya akan ekspresi sentimental di mana 93 orang meninjau topik dalam bahasa Inggris. Video tersegmentasi dengan label sentimen masing-masing segmen diberi skor antara +3 (positif kuat) hingga -3 (negatif kuat) oleh 5 annotator.


| Model           | Accuracy  |  Paper / Source |
| ------------- | :-----:| --- |
| bc-LSTM (Poria et al., 2017) | 80.3%  | [Context-Dependent Sentiment Analysis in User-Generated Videos](http://sentic.net/context-dependent-sentiment-analysis-in-user-generated-videos.pdf) |
| MARN (Zadeh et al., 2018) | 77.1%  | [Multi-attention Recurrent Network for Human Communication Comprehension](https://arxiv.org/pdf/1802.00923.pdf) |

[Go back to the README](../README.md)
