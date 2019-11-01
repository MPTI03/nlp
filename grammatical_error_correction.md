# Koreksi Kesalahan Tata Bahasa

Grammatical Error Correction (GEC) adalah tugas untuk memperbaiki berbagai jenis kesalahan dalam teks seperti kesalahan pengejaan, tanda baca, tata bahasa, dan pilihan kata.

GEC biasanya dirumuskan sebagai tugas koreksi kalimat. Sistem GEC mengambil kalimat yang berpotensi salah sebagai input dan diharapkan mengubahnya menjadi versi yang diperbaiki. Lihat contoh yang diberikan di bawah ini:

| Input (Erroneous)          | Output (Corrected)     |
| -------------------------  | ---------------------- |
|She see Tom is catched by policeman in park at last night. | She saw Tom caught by a policeman in the park last night.|

### CoNLL-2014 Shared Task

The [CoNLL-2014 shared task test set](https://www.comp.nus.edu.sg/~nlp/conll14st/conll14st-test-data.tar.gz) adalah dataset yang paling banyak digunakan untuk tolok ukur sistem GEC. Set tes berisi 1.312 kalimat bahasa Inggris dengan anotasi kesalahan oleh 2 annotator ahli. Model dievaluasi dengan pencetak MaxMatch  ([Dahlmeier dan Ng, 2012](http://www.aclweb.org/anthology/N12-1067)) ) yang menghitung skor Fβ berbasis span (β diatur ke 0,5 untuk presisi berat dua kali seingat).


Pengaturan tugas bersama membatasi bahwa sistem hanya menggunakan set data yang tersedia untuk pelatihan untuk memastikan perbandingan yang adil antara sistem. Skor yang diterbitkan tertinggi pada set tes CoNLL-2014 diberikan di bawah ini. Perbedaan dibuat antara makalah yang melaporkan hasil pengaturan tugas bersama CoNLL-2014 terbatas yang menggunakan hanya set data pelatihan yang tersedia untuk umum  (_**Restricted**_) dan yang menggunakan set data besar non-publik  (_**Unrestricted**_).

**Restricted**:

| Model           | F0.5  |  Paper / Source | Code |
| ------------- | :-----:| --- | :-----: |
| Transformer + Pre-train with Pseudo Data (Kiyono et al., EMNLP 2019) | 65.0 | [An Empirical Study of Incorporating Pseudo Data into Grammatical Error Correction](https://arxiv.org/abs/1909.00502) | NA |
| Copy-Augmented Transformer + Pre-train (Zhao and Wang, NAACL 2019) | 61.15 | [Improving Grammatical Error Correction via Pre-Training a Copy-Augmented Architecture with Unlabeled Data](https://arxiv.org/pdf/1903.00138.pdf) | [Official](https://github.com/zhawe01/fairseq-gec) |
| CNN Seq2Seq + Quality Estimation (Chollampatt and Ng, EMNLP 2018) | 56.52 | [Neural Quality Estimation of Grammatical Error Correction](http://aclweb.org/anthology/D18-1274) | [Official](https://github.com/nusnlp/neuqe/) |
| SMT + BiGRU (Grundkiewicz and Junczys-Dowmunt, 2018) |  56.25 | [Near Human-Level Performance in Grammatical Error Correction with Hybrid Machine Translation](http://aclweb.org/anthology/N18-2046)| NA |
| Transformer (Junczys-Dowmunt et al., 2018) | 55.8 | [Approaching Neural Grammatical Error Correction as a Low-Resource Machine Translation Task](http://aclweb.org/anthology/N18-1055)| [Official](https://github.com/grammatical/neural-naacl2018) |
| CNN Seq2Seq (Chollampatt and Ng, 2018)| 54.79 | [A Multilayer Convolutional Encoder-Decoder Neural Network for Grammatical Error Correction](https://www.aaai.org/ocs/index.php/AAAI/AAAI18/paper/viewFile/17308/16137)| [Official](https://github.com/nusnlp/mlconvgec2018) |

**Unrestricted**:

| Model           | F0.5  |  Paper / Source | Code |
| ------------- | :-----:| --- | :-----: |
| CNN Seq2Seq + Fluency Boost (Ge et al., 2018) |  61.34 | [Reaching Human-level Performance in Automatic Grammatical Error Correction: An Empirical Study](https://arxiv.org/pdf/1807.01270.pdf)| NA |

_**Restricted**_: hanya menggunakan kumpulan data yang tersedia untuk umum. _**Unrestricted**_: menggunakan set data non-publik.


### CoNLL-2014 10 Anotasi
Bryant dan Ng, 2015 merilis 8 anotasi tambahan (selain dua anotasi resmi) untuk set tes tugas bersama CoNLL-2014.
 ([link](http://www.comp.nus.edu.sg/~nlp/sw/10gec_annotations.zip)).

**Restricted**:

| Model           | F0.5  |  Paper / Source | Code |
| ------------- | :-----:| --- | :-----: |
| SMT + BiGRU (Grundkiewicz and Junczys-Dowmunt, 2018) |  72.04 | [Near Human-Level Performance in Grammatical Error Correction with Hybrid Machine Translation](http://aclweb.org/anthology/N18-2046)| NA |
| CNN Seq2Seq (Chollampatt and Ng, 2018)| 70.14 (measured by Ge et al., 2018) | [ A Multilayer Convolutional Encoder-Decoder Neural Network for Grammatical Error Correction](https://www.aaai.org/ocs/index.php/AAAI/AAAI18/paper/viewFile/17308/16137)| [Official](https://github.com/nusnlp/mlconvgec2018) |

**Unrestricted**:

| Model           | F0.5  |  Paper / Source | Code |
| ------------- | :-----:| --- | :-----: |
| CNN Seq2Seq + Fluency Boost (Ge et al., 2018) |  76.88 | [Reaching Human-level Performance in Automatic Grammatical Error Correction: An Empirical Study](https://arxiv.org/pdf/1807.01270.pdf)| NA |

_**Restricted**_: hanya menggunakan kumpulan data yang tersedia untuk umum. _**Unrestricted**_: menggunakan set data non-publik.


### JFLEG

[JFLEG test set](https://github.com/keisks/jfleg) dirilis oleh [Napoles et al., 2017](http://aclweb.org/anthology/E17-2037)  terdiri dari 747 kalimat bahasa Inggris dengan 4 referensi untuk setiap kalimat. Model dievaluasi dengan [GLEU](https://github.com/cnap/gec-ranking/) metrik ([Napoles et al., 2016](https://arxiv.org/pdf/1605.02592.pdf)).


**Restricted**:  

| Model           | GLEU  |  Paper / Source | Code |
| ------------- | :-----:| --- | :-----: |
| SMT + BiGRU (Grundkiewicz and Junczys-Dowmunt, 2018) |  61.50 | [Near Human-Level Performance in Grammatical Error Correction with Hybrid Machine Translation](http://aclweb.org/anthology/N18-2046)| NA |
| Transformer (Junczys-Dowmunt et al., 2018) | 59.9 | [Approaching Neural Grammatical Error Correction as a Low-Resource Machine Translation Task](http://aclweb.org/anthology/N18-1055)| NA |
| CNN Seq2Seq (Chollampatt and Ng, 2018)| 57.47 | [ A Multilayer Convolutional Encoder-Decoder Neural Network for Grammatical Error Correction](https://www.aaai.org/ocs/index.php/AAAI/AAAI18/paper/viewFile/17308/16137)| [Official](https://github.com/nusnlp/mlconvgec2018) |


**Unrestricted**:

| Model           | GLEU  |  Paper / Source | Code |
| ------------- | :-----:| --- | :-----: |
| CNN Seq2Seq + Fluency Boost and inference (Ge et al., 2018) |  62.42 | [Reaching Human-level Performance in Automatic Grammatical Error Correction: An Empirical Study](https://arxiv.org/pdf/1807.01270.pdf)| NA |

_**Restricted**_: hanya menggunakan kumpulan data yang tersedia untuk umum. _**Unrestricted**_: menggunakan set data non-publik.


### BEA Shared Task - 2019
[BEA shared task - 2019 dataset](https://www.cl.cam.ac.uk/research/nl/bea2019st/) yang dirilis untuk Tugas Bersama BEA tentang Grammatical Error Correction menyediakan dataset yang lebih baru dan lebih besar untuk mengevaluasi model GEC dalam 3 trek, berdasarkan pada dataset yang digunakan untuk pelatihan:
- [Restricted track](https://competitions.codalab.org/competitions/20228)
- [Unrestricted track](https://competitions.codalab.org/competitions/20229)
- [Low-resource track](https://competitions.codalab.org/competitions/20230)   


Pelatihan dan perangkat pengembangan dirilis untuk umum dan kinerja model GEC dievaluasi dengan skor F-0,5. Output model pada set-tes harus diunggah ke Codalab (tersedia untuk umum) di mana metrik kesalahan kategori ditampilkan. Set tes terdiri dari 4477 kalimat (lebih besar dan beragam daripada set data CoNLL-14) dan outputnya melalui [ERRANT](https://github.com/chrisjbryant/errant). . Data yang dirilis dikumpulkan dari 2 sumber:
  - Write & Improve, platform web online yang membantu siswa bahasa Inggris non-pribumi dengan tulisan mereka.
  - LOCNESS, sebuah korpus yang terdiri dari esai yang ditulis oleh siswa asli bahasa Inggris.  



Deskripsi trek dari situs [BEA] (https://www.cl.cam.ac.uk/research/nl/bea2019st/#tracks) diberikan di bawah ini:

_**Restricted Track:**_
Di Restricted track, peserta hanya dapat menggunakan kumpulan data pelajar berikut:
-Lang-8 Corpus dari Learner English (Mizumoto et al., 2011; Tajiri et al., 2012)

-NUCLE (Dahlmeier et al., 2013)

-W&I + LOCNESS (Bryant et al., 2019; Granger, 1998)
Perhatikan bahwa kami membatasi peserta pada Lang-8 Corpus dari Learner English yang telah diolah daripada Lang-8 Learner Corpus yang multibahasa dan multibahasa karena para peserta akan perlu menyaring sendiri korpus mentah. Kami juga tidak mengizinkan penggunaan set tes tugas bersama CoNLL 2013/2014 di trek ini.
  


_**Unrestricted Track:**_
Di lintasan unrestricted track, peserta dapat menggunakan apa saja untuk membangun sistem mereka. Ini termasuk dataset dan perangkat lunak berpemilik.


_**Low Resource Track (formerly Unsupervised Track):**_
Pada low resource track, peserta hanya dapat menggunakan dataset pelajar berikut: W&I + set pengembangan LOCNESS.
  

Karena sistem mutakhir saat ini mengandalkan sebanyak mungkin data pelajar beranotasi sebanyak mungkin untuk mencapai kinerja terbaik, tujuan jalur sumber daya yang rendah adalah untuk mendorong penelitian ke dalam sistem yang tidak bergantung pada sejumlah besar data pelajar. Lagu ini harus menjadi minat khusus bagi para peneliti yang bekerja pada GEC untuk bahasa di mana korpora pelajar besar tidak ada.


### Hasil dari set tes WI-LOCNESS :
**Restricted track**:

| Model           | F0.5  |  Paper / Source | Code |
| ------------- | :-----:| --- | :-----: |
| Transformer + Pre-train with Pseudo Data (Kiyono et al., EMNLP 2019) | 70.2 | [An Empirical Study of Incorporating Pseudo Data into Grammatical Error Correction](https://arxiv.org/abs/1909.00502) | NA |
| Transformer | 69.47  | [Neural Grammatical Error Correction Systems with UnsupervisedPre-training on Synthetic Data](https://www.aclweb.org/anthology/W19-4427)| [Official: Code to be updated soon](https://github.com/grammatical/pretraining-bea2019) |
| Transformer | 69.00  | [A Neural Grammatical Error Correction System Built OnBetter Pre-training and Sequential Transfer Learning](https://www.aclweb.org/anthology/W19-4423)| [Official](https://github.com/kakaobrain/helo_word/) |
| Ensemble of models | 66.78  | [The LAIX Systems in the BEA-2019 GEC Shared Task](https://www.aclweb.org/anthology/W19-4416)| NA |

**Low-resource track**:

| Model           | F0.5  |  Paper / Source | Code |
| ------------- | :-----:| --- | :-----: |
| Transformer | 64.24  | [Neural Grammatical Error Correction Systems with UnsupervisedPre-training on Synthetic Data](https://www.aclweb.org/anthology/W19-4427)| [Official: Code to be updated soon](https://github.com/grammatical/pretraining-bea2019) |
| Transformer | 58.80  | [A Neural Grammatical Error Correction System Built OnBetter Pre-training and Sequential Transfer Learning](https://www.aclweb.org/anthology/W19-4423)| [Official](https://github.com/kakaobrain/helo_word/) |
| Ensemble of models | 51.81  | [The LAIX Systems in the BEA-2019 GEC Shared Task](https://www.aclweb.org/anthology/W19-4416)| NA |

 
 **Reference**:
 - Helen Yannakoudakis, Ekaterina Kochmar, Claudia Leacock, Nitin Madnani, Ildikó Pilán, Torsten Zesch, dalam [Prosiding Lokakarya Keempat Belas tentang Penggunaan Inovatif NLP untuk Membangun Aplikasi Pendidikan](https://www.aclweb.org/anthology/W19-44)
 - Christopher Bryant, Mariano Felice, and Ted Briscoe. 2017. Anotasi otomatis dan evaluasi Jenis Kesalahan untuk Koreksi Kesalahan Tata Bahasa. Dalam Prosiding Pertemuan Tahunan ke-55 Asosiasi untuk Linguistik Komputasi (Volume 1: Long Papers). Vancouver, Canada.
