# Normalisasi Leksikal

Normalisasi leksikal adalah tugas menerjemahkan / mengubah teks yang tidak standar ke register standar.

Contoh:

```
new pix comming tomoroe
new pictures coming tomorrow
```

Kumpulan data biasanya terdiri dari tweet, karena ini secara alami mengandung cukup banyak fenomena ini.

Untuk normalisasi leksikal, hanya penggantian pada level kata yang dianotasi. Beberapa korpora menyertakan anotasi untuk penggantian 1-N dan N-1. Namun, penyisipan / penghapusan kata dan pemesanan ulang bukan bagian dari tugas.


### LexNorm
[LexNorm](http://people.eng.unimelb.edu.au/tbaldwin/etc/lexnorm_v1.2.tgz) pada awalnya diperkenalkan oleh [Han and Baldwin (2011)](http://aclweb.org/anthology/P/P11/P11-1038.pdf).
Beberapa kesalahan dalam anotasi diselesaikan oleh [Yang and Eisenstein](http://www.aclweb.org/anthology/D13-1007);
pada halaman ini, kami hanya melaporkan hasil pada dataset baru. Untuk dataset ini, 2.577 tweet dari [Li and Liu(2014)](http://www.aclweb.org/anthology/P14-3012) ) sering digunakan sebagai data pelatihan, karena gaya anotasinya yang serupa.


Dataset ini biasanya dievaluasi dengan akurasi pada kata-kata non-standar. Ini berarti bahwa sistem mengetahui terlebih dahulu kata-kata mana yang membutuhkan normalisasi.


| Model           | Accuracy  |  Paper / Source | Code | 
| ------------- | :-----:| --- | --- | 
| MoNoise (van der Goot & van Noord, 2017) | 87.63 | [MoNoise: Modeling Noise Using a Modular Normalization System](http://www.let.rug.nl/rob/doc/clin27.paper.pdf) | [Official](https://bitbucket.org/robvanderg/monoise/) | 
| Joint POS + Norm in a Viterbi decoding (Li & Liu, 2015) | 87.58* | [Joint POS Tagging and Text Normalization for Informal Text](http://www.aaai.org/ocs/index.php/IJCAI/IJCAI15/paper/download/10839/10838) | |
| Syllable based (Xu et al., 2015) | 86.08 | [Tweet Normalization with Syllables](http://www.aclweb.org/anthology/P15-1089) | |
| unLOL (Yang & Eisenstein, 2013) | 82.06 | [A Log-Linear Model for Unsupervised Text Normalization](http://www.aclweb.org/anthology/D13-1007) | |

\* menggunakan versi data yang sedikit berbeda

#### LexNorm2015

[LexNorm2015](https://github.com/noisy-text/noisy-text.github.io/blob/master/2015/files/lexnorm2015.tgz)
dataset diperkenalkan untuk tugas bersama pada normalisasi leksikal, yang diselenggarakan di WNUT2015 ([Baldwin et al(2015)](http://aclweb.org/anthology/W15-4319)).  Dalam dataset ini, penggantian 1-N dan N-1 dimasukkan dalam anotasi. Metrik evaluasi yang digunakan adalah ketepatan, daya ingat dan skor F1. Namun, ini dihitung agak aneh:

Presisi: dari semua penggantian yang diperlukan, berapa banyak yang ditemukan dengan benar

Ingat: dari semua normalisasi oleh sistem, berapa banyak yang benar

Ini berarti bahwa jika sistem menggantikan kata yang membutuhkan normalisasi, tetapi memilih normalisasi yang salah, maka akan dikenakan sanksi dua kali.

| Model           | F1  | Precision | Recall | Paper / Source | Code | 
| ------------- | :-----:| :-----:| :-----:| --- | --- | 
| MoNoise (van der Goot & van Noord, 2017) | 86.39 | 93.53 | 80.26 | [MoNoise: Modeling Noise Using a Modular Normalization System](http://www.let.rug.nl/rob/doc/clin27.paper.pdf) | [Official](https://bitbucket.org/robvanderg/monoise/) | 
| Random Forest + novel similarity metric (Jin, 2017) | 84.21 | 90.61 | 78.65 | [NCSU-SAS-Ning: Candidate Generation and Feature Engineering for Supervised Lexical Normalization](http://www.aclweb.org/anthology/W15-4313) | |

[Go back to the README](../README.md)
