# Dialogue

Dialogue terkenal sulit untuk dievaluasi.  Pendekatan masa lalu telah menggunakan evaluasi manusia.

## Dialogue act classification

Klasifikasi tindakan dialog adalah tugas untuk mengklasifikasikan ujaran sehubungan dengan fungsi yang dilayaninya dalam dialog, yaitu tindakan yang dilakukan pembicara.  Tindakan dialog adalah jenis tindak tutur (untuk Teori Tindakan Pidato, lihat [Austin (1975)](http://www.hup.harvard.edu/catalog.php?isbn=9780674411524) and [Searle (1969)](https://www.cambridge.org/core/books/speech-acts/D2D7B03E472C8A390ED60B86E08640E7)).

### Switchboard corpus
[Switchboard-1 corpus](https://catalog.ldc.upenn.edu/ldc97s62) adalah corpus ucapan telepon, yang terdiri dari sekitar 2.400 percakapan telepon dua sisi di antara 543 pembicara dengan sekitar 70 topik percakapan yang disediakan.  Dataset mencakup file audio dan file transkripsi, serta informasi tentang speaker dan panggilan.

The Switchboard Dialogue Act Corpus (SwDA) [[download](https://web.stanford.edu/~jurafsky/swb1_dialogact_annot.tar.gz)] memperluas korpus Switchboard-1 dengan tag dari [SWBD-DAMSL tagset](https://web.stanford.edu/~jurafsky/ws97/manual.august1.html), yang merupakan augmentasi ke tag tag Discour Anotation and Markup System of Labeling (DAMSL). 220 tag dikurangi menjadi 42 tag dengan pengelompokan untuk meningkatkan model bahasa pada korpus Switchboard.  Subset dari Switchboard-1 corpus yang terdiri dari 1155 percakapan digunakan.  Tag yang dihasilkan termasuk tindakan dialog seperti pernyataan-tidak-pendapat, mengakui, pernyataan-pendapat, setuju / menerima, dll.  
Annotated example:  
* Pembicara: * A, * Undang-Undang Dialog: * Ya-Tidak-Pertanyaan, * Ucapan: * Jadi, apakah Anda kuliah sekarang?  

| Model           | Accuracy  |  Paper / Source | Code | 
| ------------- | :-----:| --- | --- |
| CRF-ASN (Chen et al., 2018) | 81.3 | [Dialogue Act Recognition via CRF-Attentive Structured Network](https://arxiv.org/abs/1711.05568) | |
| Bi-LSTM-CRF (Kumar et al., 2017) | 79.2 | [Dialogue Act Sequence Labeling using Hierarchical encoder with CRF](https://arxiv.org/abs/1709.04250) | [Link](https://github.com/YanWenqiang/HBLSTM-CRF) |
| RNN with 3 utterances in context (Bothe et al., 2018) | 77.34 | [A Context-based Approach for Dialogue Act Recognition using Simple Recurrent Neural Networks](https://arxiv.org/abs/1805.06280) | | 


### ICSI Meeting Recorder Dialog Act (MRDA) corpus
The [MRDA corpus](http://www1.icsi.berkeley.edu/Speech/mr/) [[download](http://www.icsi.berkeley.edu/~ees/dadb/icsi_mrda+hs_corpus_050512.tar.gz)] terdiri dari sekitar 75 jam pidato dari 75 pertemuan yang terjadi secara alami di antara 53 pembicara.  Tagset yang digunakan untuk pelabelan adalah versi modifikasi dari tagset SWBD-DAMSL.  Hal ini dijelaskan dengan tiga jenis informasi: menandai batas segmen tindakan dialog, menandai tindakan dialog dan menandai korespondensi antara tindakan dialog.

Contoh beranotasi:  
Waktu: 2804-2810, Pembicara: c6, Undang-Undang Dialog: s ^ bd, Transkrip: maksud saya ini hanya diskriminatif.
Berbagai tindakan dialog dipisahkan oleh  "^".

| Model           | Accuracy  |  Paper / Source | Code | 
| ------------- | :-----:| --- | --- | 
| CRF-ASN (Chen et al., 2018) | 91.7 | [Dialogue Act Recognition via CRF-Attentive Structured Network](https://arxiv.org/abs/1711.05568) | |
| Bi-LSTM-CRF (Kumar et al., 2017) | 90.9 | [Dialogue Act Sequence Labeling using Hierarchical encoder with CRF](https://arxiv.org/abs/1709.04250) | [Link](https://github.com/YanWenqiang/HBLSTM-CRF) |

## Dialogue state tracking

Penyelesaian keadaan dialog terdiri dari menentukan pada setiap belokan dialog representasi lengkap dari apa yang diinginkan pengguna pada titik itu dalam dialog, yang berisi batasan tujuan, serangkaian slot yang diminta, dan tindakan dialog pengguna.

### Second dialogue state tracking challenge

Untuk dialog yang berorientasi pada tujuan, dataset dari [Tantangan Teknologi Sistem Dialog kedua](http://www.aclweb.org/anthology/W14-4337)
(DSTC2) adalah dataset evaluasi umum.  DSTC2 berfokus pada domain pencarian restoran.  Model dievaluasi berdasarkan akurasi pada pelacakan slot individu dan bersama.

| Model           | Request | Area  |  Food  |  Price  |  Joint  |  Paper / Source |
| ------------- | :-----: | :-----:| :-----:| :-----:| :-----:| --- |
| Zhong et al. (2018) | 97.5 | - | - | - | 74.5| [Global-locally Self-attentive Dialogue State Tracker](https://arxiv.org/abs/1805.09655) |
| Liu et al. (2018) | - | 90 | 84 | 92 | 72 | [Dialogue Learning with Human Teaching and Feedback in End-to-End Trainable Task-Oriented Dialogue Systems](https://arxiv.org/abs/1804.06512) |
| Neural belief tracker (Mrkšić et al., 2017) | 96.5 | 90 | 84 | 94 | 73.4 | [Neural Belief Tracker: Data-Driven Dialogue State Tracking](https://arxiv.org/abs/1606.03777) |
| RNN (Henderson et al., 2014) | 95.7 | 92 | 86 | 86 | 69 | [Robust dialog state tracking using delexicalised recurrent neural networks and unsupervised gate](http://svr-ftp.eng.cam.ac.uk/~sjy/papers/htyo14.pdf) | 

### Wizard-of-Oz

[dataset WoZ 2.0](https://arxiv.org/pdf/1606.03777.pdf) adalah dataset pelacakan status dialog yang lebih baru yang evaluasinya terlepas dari output bising sistem pengenalan ucapan.  Mirip dengan DSTC2, itu mencakup domain pencarian restoran dan memiliki evaluasi yang identik.


| Model           | Request  |  Joint  |  Paper / Source |
| ------------- |  :-----:| :-----:| --- |
| Zhong et al. (2018) | 97.1 | 88.1 | [Global-locally Self-attentive Dialogue State Tracker](https://arxiv.org/abs/1805.09655) |
| Neural belief tracker (Mrkšić et al., 2017) | 96.5 | 84.4 | [Neural Belief Tracker: Data-Driven Dialogue State Tracking](https://arxiv.org/abs/1606.03777) |
| RNN (Henderson et al., 2014) | 87.1 | 70.8 | [Robust dialog state tracking using delexicalised recurrent neural networks and unsupervised gate](http://svr-ftp.eng.cam.ac.uk/~sjy/papers/htyo14.pdf) | 


### MultiWOZ

[dataset MultiWOZ](https://arxiv.org/abs/1810.00278) adalah kumpulan percakapan tertulis manusia-manusia yang berlabel lengkap yang mencakup berbagai domain dan topik.  Pada ukuran dialog 10k, itu setidaknya satu urutan besarnya lebih besar dari semua korporasi berorientasi tugas yang dijelaskan sebelumnya.  Dialog ditetapkan antara turis dan juru tulis dalam informasi.  Ini mencakup lebih dari 7 domain.

| Model           | Joint  |  Slot  |  Paper / Source |
| ------------- |  :-----:| :-----:| --- |
| Ramadan et al. (2018) | 15.57 |	89.53 | [Large-Scale Multi-Domain Belief Tracking with Knowledge Sharing](https://www.aclweb.org/anthology/P18-2069) |
| Zhong et al. (2018) | 35.57 |	95.44  | [Global-locally Self-attentive Dialogue State Tracker](https://arxiv.org/abs/1805.09655) |
| Nouri and Hosseini-Asl (2019) | 36.27 |	98.42 | [Toward Scalable Neural Dialogue State Tracking Model](https://arxiv.org/pdf/1812.00899.pdf) |
| Wu et al. (2019) |48.62 | 	96.92| [Transferable Multi-Domain State Generator for Task-OrientedDialogue System](https://arxiv.org/pdf/1905.08743.pdf) |

## Retrieval-based Chatbot
Sistem ini mengambil input konteks dan daftar tanggapan yang mungkin dan peringkat tanggapan, mengembalikan peringkat tertinggi.
### Ubuntu Corpus
[Ubuntu Corpus](https://arxiv.org/pdf/1506.08909.pdf) berisi hampir 1 juta dialog multi-putaran dari Log Obrolan Ubuntu. Tugas Ubuntu Corpus adalah memilih respons yang benar dari 10 kandidat (yang lainnya diambil sampelnya secara negatif) dengan mempertimbangkan riwayat percakapan sebelumnya. Anda dapat menemukan detail lebih lanjut di [sini](https://github.com/ryan-lowe/Ubuntu-Dialogue-Generationv2). Tugas yang tepat digunakan sedikit berbeda, tetapi semua mempertimbangkan variasi Recall_N @ K, yang berarti seberapa sering jawaban yang sebenarnya ada di opsi K atas ketika ada N total kandidat. 

| Model           | R_2@1  |  R_10@1   |  Paper / Source |
| -------------   |    :---------: | :---------:|---------------|
| DAM (Zhou et al. 2018) | 93.8 | 76.7| [Multi-Turn Response Selection for Chatbots with Deep Attention Matching Network](http://www.aclweb.org/anthology/P18-1103) |
| SMN (Wu et al. 2017) | 92.3 | 72.3| [Sequential Matching Network: A New Architecture for Multi-turn Response Selection in Retrieval-Based Chatbots](https://arxiv.org/pdf/1612.01627.pdf) |
| Multi-View (Zhou et al. 2017) | 90.8 | 66.2 | [Multi-view Response Selection for Human-Computer Conversation](https://aclweb.org/anthology/D16-1036) |
| Bi-LSTM (Kadlec et al. 2015) | 89.5 | 63.0 | [Improved Deep Learning Baselines for Ubuntu Corpus Dialogs](https://arxiv.org/pdf/1510.03753.pdf) |

### Reddit Corpus
[Reddit Corpus](https://arxiv.org/abs/1904.06472) Reddit Corpus berisi 726 juta dialog multi-putaran dari dewan Reddit.  Reddit adalah situs agregasi berita sosial Amerika, di mana pengguna dapat memposting tautan, dan ikut serta dalam diskusi tentang pos ini.  Tugas Reddit Corpus adalah memilih respons yang benar dari 100 kandidat (yang lainnya diambil sampelnya secara negatif) dengan mempertimbangkan riwayat percakapan sebelumnya.  Model dievaluasi dengan mengingat 1 pada 100 metrik (akurasi peringkat 1-dari-100).  Anda dapat menemukan detail lebih lanjut [disini](https://github.com/PolyAI-LDN/conversational-datasets).

| Model           |   R_1@100   |  Paper / Source |
| -------------   |   :---------:|---------------|
| PolyAI Encoder (Henderson et al. 2019) |  61.3 | [A Repository of Conversational Dataset](https://arxiv.org/pdf/1904.06472.pdf) |
| USE (Cer et al. 2018) | 47.7 | [Universal Sentence Encoder](https://arxiv.org/abs/1803.11175) |
| BERT (Devlin et al. 2017) | 24.0 | [BERT: Pre-training of Deep Bidirectional Transformers for Language Understanding](https://arxiv.org/abs/1810.04805) |
| ELMO (Peters et al. 2018) | 19.3 | [Deep contextualized word representations](https://arxiv.org/abs/1802.05365) |

## Generative-based Chatbot
Tugas utama chatbot berbasis generatif adalah menghasilkan respons yang konsisten dan menarik sesuai konteksnya.
### Personalized Chit-chat

Tugas generasi dialog obrolan-obrolan persinalized pertama kali diusulkan oleh [PersonaChat](https://arxiv.org/pdf/1801.07243.pdf). Motivasinya adalah untuk meningkatkan keterlibatan dan konsistensi chit-chat bot melalui pemberian personas eksplisit kepada agen.  Di sini, persona didefinisikan sebagai beberapa kalimat profil bahasa alami seperti "Berat saya 300 pound."  NIPS 2018 telah mengadakan kompetisi The Conversational Intelligence Challenge 2 (ConvAI2)](http://convai.io/) berdasarkan dataset. Metrik Evaluasi adalah F1, Hit @ 1 dan ppl.  F1 mengevaluasi pada tingkat kata, dan Hits @ 1 mewakili probabilitas dari ujaran nyata berikutnya yang tertinggi menurut model, sementara ppl adalah kebingungan untuk pemodelan bahasa.  Hasil berikut dilaporkan pada set dev (set tes masih disembunyikan), hampir dari mereka dipinjam dari [ConvAI2 Leaderboard](https://github.com/DeepPavlov/convai/blob/master/leaderboards.md).

| Model           | F1 | Hits@1 | ppl | Paper / Source | Code |
| -------------   | :---------: | :---------:| :--------: | ---------------| ------------- |
| TransferTransfo (Thomas et al. 2019) | 19.09 | 82.1 | 17.51 | [TransferTransfo: A Transfer Learning Approach for Neural Network Based Conversational Agents](https://arxiv.org/pdf/1901.08149.pdf) | [Code](https://github.com/huggingface/transfer-learning-conv-ai) |
| Lost In Conversation | 17.79 | - | 17.3 | [NIPS 2018 Workshop Presentation](http://convai.io/NeurIPSParticipantSlides.pptx) | [Code](https://github.com/atselousov/transformer_chatbot) |
| Seq2Seq + Attention (Dzmitry et al. 2014) | 16.18 | 12.6 | 29.8 | [Neural Machine Translation by Jointly Learning to Align and Translate](https://arxiv.org/pdf/1409.0473.pdf) | [Code](https://github.com/facebookresearch/ParlAI/tree/master/projects/convai2/baselines/seq2seq) |
| KV Profile Memory (Zhang et al. 2018) | 11.9 | 55.2 | - | [Personalizing Dialogue Agents: I have a dog, do you have pets too?](https://arxiv.org/pdf/1801.07243.pdf) | [Code](https://github.com/facebookresearch/ParlAI/tree/master/projects/convai2/baselines/kvmemnn)
