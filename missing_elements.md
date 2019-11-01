# Elemen Hilang

Elemen yang hilang adalah kumpulan fenomena yang berhubungan dengan hal-hal yang dimaksudkan, tetapi tidak secara eksplisit disebutkan dalam teks. Ada berbagai jenis elemen yang hilang, yang memiliki aspek dan perilaku yang berbeda. 
Misalnya, [Ellipsis](https://en.wikipedia.org/wiki/Ellipsis_(linguistics)), Fused-Head, Bridging Anaphora, dll.


### Numeric Fused-Head (NFH)
Konstruksi FH adalah frase nomina (NPs) di mana nomina kepala hilang dan dikatakan “menyatu” dengan pengubah ketergantungannya. Informasi yang hilang ini implisit dan penting untuk pemahaman kalimat.

Numeric [Fused-Head dataset](https://github.com/yanaiela/num_fh/tree/master/data/resolution/processed)
terdiri dari ~ 10K contoh contoh rahasia yang bersumber dari kerumunan, dilabeli menjadi 7 kategori yang berbeda, dari dua jenis.
. Dalam tipe pertama, Referensi, kepala yang hilang dirujuk secara eksplisit di tempat lain dalam wacana, baik dalam kalimat yang sama atau dalam kalimat di sekitarnya. Dalam tipe kedua, *Implisit*, kepala yang hilang tidak muncul dalam teks dan perlu disimpulkan oleh pembaca atau pendengar berdasarkan konteks atau pengetahuan dunia. Kategori ini diberi label ke dalam 6 kategori paling umum dari dataset. Model dievaluasi berdasarkan akurasi.


Contoh anotasi:

#### Referensi

| I | bought | 5 | apples | but | got | only | 4 | . |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
|   |        |   | HEAD   |     |     |      | NFH-REFERENCE | |

#### Implisit

| Let | 's | meet | at | 5 | tomorrow | ? |
| --- | --- | --- | --- | --- | --- | --- |
|     |    |      |    | NFH-TIME |   |   |


| Model           | Accuracy  |  Paper / Source | Code |
| ------------- | :-----:| --- | :-----: |
| Bi-LSTM + Scoring (Elazar and Goldberg, 2019) | 60.8 | [Where’s My Head? Definition, Dataset and Models for Numeric Fused-Heads Identification and Resolution](https://arxiv.org/abs/1905.10886) | [Official](https://github.com/yanaiela/num_fh) |
| Bi-LSTM + Elmo + Scoring (Elazar and Goldberg, 2019) | 74.0 | [Where’s My Head? Definition, Dataset and Models for Numeric Fused-Heads Identification and Resolution](https://arxiv.org/abs/1905.10886) | [Official](https://github.com/yanaiela/num_fh) |

## PTB Traces and Null Elements

Ini dievaluasi pada bagian 23 dari Penn Treebank, menggunakan metrik yang didefinisikan oleh Johnson (2002).
Implementasi metrik tersedia dengan kode dari [Kummerfeld and Klein (2017)](https://github.com/jkkummerfeld/1ec-graph-parser/tree/master/evaluation).

| Model           | F-score  |  Paper / Source | Code |
| ------------- | :-----:| --- | :-----: |
| Kato and Matsubara (2016) | 77.8 | [Transition-Based Left-Corner Parsing for Identifying PTB-Style Nonlocal Dependencies](https://www.aclweb.org/anthology/P16-1088) | 
| Kummerfeld and Klein (2017) | 70.6 | [Parsing with Traces: An O(n^4) Algorithm and a Structural Representation](https://aclweb.org/anthology/papers/Q/Q17/Q17-1031/) | [Github](https://github.com/jkkummerfeld/1ec-graph-parser)
| Johnson (2002) | 68 | [A simple pattern-matching algorithm for recovering empty nodes and their antecedents](https://www.aclweb.org/anthology/P02-1018) | [Code](http://web.science.mq.edu.au/~mjohnson/code/Restorer.tbz) and [README](http://web.science.mq.edu.au/~mjohnson/code/Restorer-README.txt)

