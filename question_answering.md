# Question answering

Question answering adalah tugas menjawab pertanyaan.

### Daftar Isi

- [ARC](#arc)
- [ShARC](#sharc)
- [Reading comprehension](#reading-comprehension)
  - [CliCR](#clicr)
  - [CNN / Daily Mail](#cnn--daily-mail)
  - [CODAH](#codah)
  - [CoQA](#coqa)
  - [HotpotQA](#hotpotqa)
  - [MS MARCO](#ms-marco)
  - [MultiRC](#multirc)
  - [NewsQA](#newsqa)
  - [QAngaroo](#qangaroo)
  - [QuAC](#quac)
  - [RACE](#race)
  - [SQuAD](#squad)
  - [Story Cloze Test](#story-cloze-test)
  - [SWAG](#swag)
  - [Recipe QA](#recipeqa)
  - [NarrativeQA](#narrativeqa)
  - [DuoRC](#duorc)
  - [DROP](#drop)
- [Open-domain Question Answering](#open-domain-question-answering)
  - [DuReader](#dureader)
  - [Quasar](#quasar)
  - [SearchQA](#searchqa)
- [Knowledge Base Question Answering](#knowledge-base-question-answering)

### ARC

[AI2 Reasoning Challenge (ARC)](http://ai2-website.s3.amazonaws.com/publications/AI2ReasoningChallenge2018.pdf)
Dataset AI2 Reasoning Challenge (ARC) adalah penjawab pertanyaan, yang berisi 7.787 pertanyaan sains pilihan ganda tingkat sekolah, pilihan ganda. Dataset dipartisi menjadi Set Tantangan dan Set Mudah. Set Tantangan hanya berisi pertanyaan yang dijawab secara tidak benar oleh algoritma berbasis pengambilan dan algoritma co-kejadian kata. Model dievaluasi berdasarkan akurasi.

Papan publik tersedia di [ARC website](http://data.allenai.org/arc/).

### ShARC

[ShARC](https://arxiv.org/abs/1809.01494) dataset QA yang menantang yang membutuhkan penalaran logis, elemen-elemen penugasan / NLI dan generasi bahasa alami.

Sebagian besar pekerjaan membaca mesin berfokus pada masalah menjawab pertanyaan di mana jawaban tersebut secara langsung dinyatakan dalam teks untuk dibaca. Namun, banyak masalah menjawab pertanyaan dunia nyata memerlukan pembacaan teks bukan karena mengandung jawaban literal, tetapi karena mengandung resep untuk mendapatkan jawaban bersama dengan pengetahuan latar belakang pembaca. Kami meresmikan tugas ini dan memperkenalkan dataset ShARC yang menantang dengan instance tugas 32 ribu.

Tujuannya adalah untuk menjawab pertanyaan dengan mengajukan pertanyaan tindak lanjut terlebih dahulu. Kami berasumsi bahwa pertanyaan itu tidak memberikan informasi yang cukup untuk dijawab secara langsung. Namun, model dapat menggunakan teks aturan pendukung untuk menyimpulkan apa yang perlu ditanyakan untuk menentukan jawaban akhir. Secara konkret, Model harus memutuskan apakah akan menjawab dengan "Ya", "Tidak", "Tidak relevan", atau untuk menghasilkan pertanyaan lanjutan yang diberikan teks aturan, skenario pengguna, dan riwayat percakapan. Kinerja diukur dengan Mikro dan Akurasi Makro untuk klasifikasi "Ya" / "Tidak" / "Tidak relevan" / "Lebih", dan kualitas pertanyaan tindak lanjut diukur dengan BLEU.

Data publik, perincian tugas lebih lanjut, dan leaderboard publik tersedia di [ShARC Website](https://sharc-data.github.io/).

## Reading comprehension

Sebagian besar pertanyaan saat menjawab dataset membingkai tugas sebagai pemahaman bacaan di mana pertanyaannya adalah tentang paragraf atau dokumen dan jawabannya sering adalah rentang dalam dokumen.
The Machine Reading group
di UCL juga menyediakan [tinjauan umum pemahaman membaca ](https://uclnlp.github.io/ai4exams/data.html).

### CliCR

[CliCR dataset](http://aclweb.org/anthology/N18-1140) adalah dataset pemahaman bacaan mengisi-jeda yang terdiri dari sekitar 100.000 pertanyaan dan dokumen terkait. Dataset dibangun dari laporan kasus klinis, yang mengharuskan pembaca menjawab pertanyaan dengan entitas masalah / pengujian / perawatan medis. Kemampuan untuk melakukan menjembatani inferensi dan melacak objek telah ditemukan sebagai keterampilan yang paling sering diperlukan untuk menjawab sukses.

Instruksi untuk mengakses dataset, skrip pemrosesan, baseline dan adaptasi dari beberapa model saraf dapat ditemukan [disini](https://github.com/clips/clicr).

Contoh:

| Document  | Pertanyaan | Jawab |
| ------------- | -----:| -----: |
| Kami melaporkan kasus seorang wanita Kaukasia berusia 72 tahun dengan sindrom antisintetase positif pl-7. Presentasi klinis termasuk penyakit paru interstitial, myositis, tangan mekanik dan disfagia. Karena cedera paru adalah perhatian utama, pengobatan terdiri dari prednisolon dan siklofosfamid. Remisi lengkap dengan pembalikan kerusakan paru telah dicapai, seperti yang dilaporkan oleh CT scan, tes fungsi paru dan status fungsional. [...] | Oleh karena itu, dalam kasus yang parah pengobatan agresif, menggabungkan ____ dan glukokortikoid seperti yang digunakan dalam vaskulitis sistemik, disarankan.| siklofoshamid |

| Model           | F1 |  Makalah |
| ------------- | :-----:| --- |
| Gated-Attention Reader (Dhingra et al., 2017) | 33.9 | [CliCR: A Dataset of Clinical Case Reports for Machine Reading Comprehension](http://aclweb.org/anthology/N18-1140) |
| Stanford Attentive Reader (Chen et al., 2016) | 27.2| [CliCR: A Dataset of Clinical Case Reports for Machine Reading Comprehension](http://aclweb.org/anthology/N18-1140) |

### CNN / Surat Harian

[CNN / Surat harian dataset](https://arxiv.org/abs/1506.03340) iMail adalah dataset pemahaman close-style yang dibuat dari artikel berita CNN dan Daily Mail menggunakan heuristik. [Close-style](https://en.wikipedia.org/wiki/Cloze_test)
berarti bahwa kata yang hilang harus disimpulkan. Dalam hal ini, "pertanyaan" dibuat dengan mengganti entitas dari poin-poin singkat yang merangkum satu atau beberapa aspek artikel. Entitas Coreferent telah diganti dengan marker entitas @entityn di mana n adalah indeks yang berbeda. Model tersebut ditugaskan untuk menyimpulkan entitas yang hilang dalam poin-poin berdasarkan konten artikel yang sesuai dan model dievaluasi berdasarkan keakuratannya pada set tes.

|         | CNN | Daily Mail |
| ------------- | -----:| -----: |
| # Train | 380,298 | 879,450 |
| # Dev | 3,924 | 64,835 |
| # Test | 3,198 | 53,182 |

Contoh:

| Passage  | Pertanyaan | Jawab |
| ------------- | -----:| -----: |
| ﻿(@ entity4) jika Anda merasakan riak di kepolisian hari ini, mungkin ini berita bahwa @ entity6 resmi mendapatkan karakter gay pertamanya. menurut situs sci-fi @ entity9, novel "@ entity11" yang akan datang akan menampilkan pejabat @ entity13 yang cakap namun cacat bernama @ entity14 yang "juga kebetulan seorang lesbian. “Karakter tersebut adalah sosok gay pertama di @ entity6 resmi - film, acara televisi, komik, dan buku yang disetujui oleh pemilik franchise @ entity6 @ entity22 - menurut @ entity24, editor buku“ @ entity6 “di @ entity28 imprint @ entity26 . | karakter dalam film "@placeholder" secara bertahap menjadi lebih beragam | @entity6 |

| Model           | CNN  | Daily Mail  |  Paper / Source |
| ------------- | :-----:| :-----:|--- |
| GA Reader(Dhingra et al., 2017) | 77.9 | 80.9 | [Gated-Attention Readers for Text Comprehension](http://aclweb.org/anthology/P17-1168) |
| BIDAF(Seo et al., 2017) | 76.9 | 79.6 |[Bidirectional Attention Flow for Machine Comprehension](https://arxiv.org/pdf/1611.01603.pdf)|
| AoA Reader(Cui et al., 2017) | 74.4 | - | [Attention-over-Attention Neural Networks for Reading Comprehension](http://aclweb.org/anthology/P17-1055) |
| Neural net (Chen et al., 2016) | 72.4 | 75.8 | [A Thorough Examination of the CNN/Daily Mail Reading Comprehension Task](https://www.aclweb.org/anthology/P16-1223) |
| Classifier (Chen et al., 2016) | 67.9 | 68.3 | [A Thorough Examination of the CNN/Daily Mail Reading Comprehension Task](https://www.aclweb.org/anthology/P16-1223) |
| Impatient Reader (Hermann et al., 2015) | 63.8 | 68.0 | [Teaching Machines to Read and Comprehend](https://arxiv.org/abs/1506.03340) |

### CODAH
[CODAH](https://arxiv.org/abs/1904.04365) adalah dataset evaluasi yang dibangun secara berlawanan dengan pertanyaan 2.8k untuk menguji akal sehat. CODAH membentuk ekstensi yang menantang untuk dataset SWAG, yang menguji pengetahuan akal sehat menggunakan pertanyaan penyelesaian kalimat yang menggambarkan situasi yang diamati dalam video.

Dataset dan informasi lebih lanjut dapat ditemukan
 [disini](https://github.com/Websail-NU/CODAH)

### CoQA

[CoQA](https://arxiv.org/abs/1808.07042) adalah dataset skala besar untuk membangun sistem Penjawaban Pertanyaan Conversational. CoQA berisi 127.000+ pertanyaan dengan jawaban yang dikumpulkan dari 8000+ percakapan. Setiap percakapan dikumpulkan dengan memasangkan dua pekerja kerumunan untuk mengobrol tentang suatu bagian dalam bentuk pertanyaan dan jawaban.

Data dan papan publik tersedia [disini](https://stanfordnlp.github.io/coqa/).

### HotpotQA

HotpotQA adalah kumpulan data dengan pasangan pertanyaan-jawaban berbasis 113k Wikipedia. Pertanyaan membutuhkan penemuan dan pertimbangan atas beberapa dokumen pendukung dan tidak dibatasi pada basis pengetahuan yang sudah ada sebelumnya. Fakta pendukung tingkat kalimat tersedia.

Data dan papan peringkat publik tersedia dari  [HotpotQA website](https://hotpotqa.github.io/).

### MS MARCO
[MS MARCO](http://www.msmarco.org/dataset.aspx) MARCO alias Human Generated MAchine Reading COmprehension Dataset, dirancang dan dikembangkan oleh Microsoft AI & Research.
[Tautan ke makalah](https://arxiv.org/abs/1611.09268)
- Pertanyaan-pertanyaan tersebut diperoleh dari permintaan pengguna anonim nyata.
- Jawabannya dihasilkan manusia. Bagian konteks dari mana jawaban diperoleh diekstraksi dari dokumen nyata menggunakan mesin pencari Bing terbaru.
-Kumpulan data berisi 100.000 kueri dan sebagiannya berisi beberapa jawaban, dan bertujuan untuk melepaskan kueri 1M di masa mendatang.
 
Papan peringkat untuk beberapa tugas tersedia di [halaman papan peringkat MS MARCO](http://www.msmarco.org/leaders.aspx).

### MultiRC
MultiRC (Multi-Sentence Reading Comprehension) adalah dataset paragraf pendek dan pertanyaan multi-kalimat yang dapat dijawab dari konten paragraf. 
Kami telah merancang dataset dengan tiga tantangan utama:
 - Jumlah pilihan jawaban yang benar untuk setiap pertanyaan tidak ditentukan sebelumnya. Ini menghilangkan ketergantungan yang berlebihan dari pendekatan saat ini pada pilihan jawaban dan memaksa mereka untuk memutuskan kebenaran dari masing-masing kandidat jawaban secara independen dari yang lain. Dengan kata lain, tidak seperti pekerjaan sebelumnya, tugas di sini bukan hanya mengidentifikasi pilihan jawaban terbaik, tetapi untuk mengevaluasi kebenaran setiap pilihan jawaban secara individual.
 - Jawaban yang benar tidak perlu berupa rentang dalam teks.
 - Paragraf dalam dataset kami memiliki sumber yang beragam dengan diekstraksi dari 7 domain yang berbeda seperti berita, fiksi, teks sejarah dll., Dan karenanya diharapkan lebih beragam kontennya dibandingkan dengan dataset domain tunggal.

Papan peringkat untuk dataset tersedia di [MultiRC website](http://cogcomp.org/multirc/).

### NewsQA

[NewsQA dataset](https://arxiv.org/pdf/1611.09830.pdf) adalah kumpulan data pemahaman bacaan dari lebih dari 100.000 pasangan tanya jawab yang dihasilkan manusia dari lebih dari 10.000 artikel berita dari CNN, dengan jawaban yang terdiri dari bentang teks dari artikel yang sesuai. Beberapa karakteristik yang menantang dari dataset ini adalah:
- Jawaban adalah rentang panjang yang sewenang-wenang;
- Beberapa pertanyaan tidak memiliki jawaban di artikel terkait;
- Tidak ada jawaban kandidat untuk dipilih. Meskipun sangat mirip dengan dataset SQuAD, NewsQA menawarkan tantangan yang lebih besar untuk model yang ada pada saat pengenalan (mis. Paragraf lebih panjang daripada yang ada di SQuAD). Model dievaluasi berdasarkan F1 dan Pencocokan Tepat.

Contoh :

| Cerita  | Pertanyaan | Jawab |
| ------------- | -----:| -----: |
|MOSCOW, Rusia (CNN) - Pejabat ruang angkasa Rusia mengatakan awak kapal ruang angkasa Soyuz sedang beristirahat setelah perjalanan kasar kembali ke Bumi. Seorang bioengineer Korea Selatan adalah satu dari tiga orang yang naik kapsul Soyuz. Pesawat yang membawa astronot pertama Korea Selatan mendarat di Kazakhstan utara pada Sabtu, 260 mil (418 kilometer) dari sasarannya, kata mereka. Juru bicara Mission Control, Valery Lyndin mengatakan kondisi para kru - ahli biologi Korea Selatan Yi So-yeon, astronot Amerika Peggy Whitson dan insinyur penerbangan Rusia Yuri Malenchenko - memuaskan, meskipun ketiganya menjadi sasaran G-force yang parah selama entri ulang. . [...] |Di mana kapsul Soyuz mendarat? | Kazakhstan utara |

TDataset dapat diunduh [disini](https://github.com/Maluuba/newsqa).

| Model           | F1 | EM | Makalah / Sumber |
| ------------- | :-----: | :-----: | --- |
| DecaProp (Tay et al., 2018) | 66.3 | 53.1 | [Densely Connected Attention Propagation for Reading Comprehension](https://arxiv.org/abs/1811.04210) |
| AMANDA (Kundu et al., 2018) | 63.7 | 48.4| [A Question-Focused Multi-Factor Attention Network for Question Answering](https://arxiv.org/abs/1801.08290) |
| MINIMAL(Dyn) (Min et al., 2018) | 63.2 | 50.1 | [Efficient and Robust Question Answering from Minimal Context over Documents](https://arxiv.org/abs/1805.08092) |
| FastQAExt (Weissenborn et al., 2017) | 56.1 | 43.7 | [Making Neural QA as Simple as Possible but not Simpler](https://arxiv.org/abs/1703.04816) |

### QAngaroo

[QAngaroo](http://qangaroo.cs.ucl.ac.uk/index.html) adalah satu set dua set data pemahaman bacaan, yang membutuhkan beberapa langkah inferensi yang menggabungkan fakta dari banyak dokumen. Dataset pertama, WikiHop adalah domain terbuka dan berfokus pada artikel Wikipedia. Dataset kedua, MedHop didasarkan pada abstrak kertas dari PubMed.

Papan peringkat untuk kedua set data tersedia di [QAngaroo website](http://qangaroo.cs.ucl.ac.uk/leaderboard.html).

### QuAC

Question Answering in Context (QuAC) ) adalah dataset untuk pemodelan, pemahaman, dan partisipasi dalam dialog pencarian informasi. Contoh data terdiri dari dialog interaktif antara dua pekerja kerumunan: (1) seorang siswa yang mengajukan urutan pertanyaan bentuk bebas untuk belajar sebanyak mungkin tentang teks Wikipedia yang disembunyikan, dan (2) seorang guru yang menjawab pertanyaan dengan memberikan kutipan singkat (rentang) dari teks.

Papan peringkat dan data tersedia di [QuAC website](http://quac.ai/).

### RACE

[RACE dataset](https://arxiv.org/abs/1704.04683) dalah dataset pemahaman bacaan yang dikumpulkan dari ujian bahasa Inggris di Tiongkok, yang dirancang untuk siswa sekolah menengah dan menengah. Dataset berisi lebih dari 28.000 bagian dan hampir 100.000 pertanyaan dan dapat diunduh [disini](http://www.cs.cmu.edu/~glai1/data/race/). Model dievaluasi berdasarkan akurasi pada ujian sekolah menengah (RACE-m), ujian sekolah menengah (RACE-h), dan pada total dataset (RACE).

Papan peringkat publik tersedia di [RACE leaderboard](http://www.qizhexie.com//data/RACE_leaderboard).

| Model           | RACE-m | RACE-h | RACE | Paper | Code |
| ------------- | :-----:| :-----:| :-----:| --- | --- |
| XLNet (Yang et al., 2019) | 85.45 | 80.21 | 81.75 | [XLNet: Generalized Autoregressive Pretraining for Language Understanding](https://arxiv.org/pdf/1906.08237.pdf) | [Official](https://github.com/zihangdai/xlnet/) |
| OCN_large (Ran et al., 2019) | 76.7 | 69.6 | 71.7 | [Option Comparison Network for Multiple-choice Reading Comprehension](https://arxiv.org/pdf/1903.03033.pdf) | |
| DCMN_large (Zhang et al., 2019) | 73.4 | 68.1 | 69.7 | [Dual Co-Matching Network for Multi-choice Reading Comprehension](https://arxiv.org/pdf/1901.09381.pdf) | |
| Finetuned Transformer LM (Radford et al., 2018) | 62.9 | 57.4 | 59.0 | [Improving Language Understanding by Generative Pre-Training](https://s3-us-west-2.amazonaws.com/openai-assets/research-covers/language-unsupervised/language_understanding_paper.pdf) | [Official](https://github.com/openai/finetune-transformer-lm) |
| BiAttention MRU (Tay et al., 2018) | 60.2 | 50.3 | 53.3 | [Multi-range Reasoning for Machine Comprehension](https://arxiv.org/abs/1803.09074) | |

### SQuAD

[Stanford Question Answering Dataset (SQuAD)](https://arxiv.org/abs/1606.05250)
adalah dataset pemahaman bacaan, yang terdiri dari pertanyaan yang diajukan oleh orang banyak pada seperangkat artikel Wikipedia. Jawaban untuk setiap pertanyaan adalah segmen teks (rentang) dari bagian bacaan yang sesuai. Baru-baru ini, [SQuAD 2.0](https://arxiv.org/abs/1806.03822)
telah dirilis, yang mencakup pertanyaan yang tidak dapat dijawab.

Papan publik tersedia di [SQuAD website](https://rajpurkar.github.io/SQuAD-explorer/).

### Story Cloze Test

[Story Cloze Test](http://aclweb.org/anthology/W17-0906.pdf) adalah dataset untuk pemahaman cerita yang menyediakan sistem dengan cerita empat kalimat dan dua kemungkinan akhir. Sistem kemudian harus memilih akhir cerita yang benar.

Rincian lebih lanjut tersedia di [Story Cloze Test Challenge](https://competitions.codalab.org/competitions/15333).

| Model           | Accuracy  |  Paper / Source | Code |
| ------------- | :-----:| --- | --- |
| Reading Strategies Model (Sun et al., 2018) | 88.3 | [Improving Machine Reading Comprehension by General Reading Strategies](https://arxiv.org/pdf/1810.13441v1.pdf) |
| Finetuned Transformer LM (Radford et al., 2018) | 86.5 | [Improving Language Understanding by Generative Pre-Training](https://s3-us-west-2.amazonaws.com/openai-assets/research-covers/language-unsupervised/language_understanding_paper.pdf) |  [Official](https://github.com/openai/finetune-transformer-lm)
| Liu et al. (2018) | 78.7 | [Narrative Modeling with Memory Chains and Semantic Supervision](http://aclweb.org/anthology/P18-2045) | [Official](https://github.com/liufly/narrative-modeling)
| Hidden Coherence Model (Chaturvedi et al., 2017) | 77.6 | [Story Comprehension for Predicting What Happens Next](http://aclweb.org/anthology/D17-1168) |
| val-LS-skip (Srinivasan et al., 2018) | 76.5 | [A Simple and Effective Approach to the Story Cloze Test](http://aclweb.org/anthology/N18-2015) |

### SWAG

[SWAG](https://arxiv.org/abs/1808.05326) (Situations With Adversarial Generations) adalah dataset skala besar untuk tugas inferensi akal yang membumi, menyatukan inferensi bahasa alami dan penalaran yang membumi secara fisik. Dataset terdiri dari 113k pertanyaan pilihan ganda tentang situasi ground. Setiap pertanyaan adalah keterangan video dari LSMDC atau ActivityNet Captions, dengan empat pilihan jawaban tentang apa yang mungkin terjadi selanjutnya di layar. Jawaban yang benar adalah keterangan video (nyata) untuk acara berikutnya dalam video; tiga jawaban yang salah dihasilkan secara berlawanan dan manusia diverifikasi, sehingga menipu mesin tetapi bukan manusia.

Papan publik tersedia di  [AI2 website] (https://leaderboard.allenai.org/swag/submissions/public).

### RecipeQA

[RecipeQA](https://arxiv.org/abs/1809.00812) RecipeQA adalah dataset untuk pemahaman multimodal tentang resep memasak. Ini terdiri dari lebih dari 36 ribu pasangan tanya jawab yang dihasilkan secara otomatis dari sekitar 20 ribu resep unik dengan instruksi dan gambar langkah demi langkah. Setiap pertanyaan dalam RecipeQA melibatkan banyak modalitas seperti judul, deskripsi atau gambar, dan bekerja menuju jawaban membutuhkan (i) pemahaman bersama tentang gambar dan teks, (ii) menangkap aliran temporal peristiwa, dan (iii) memahami pengetahuan prosedural .

Papan publik tersedia di [RecipeQA website](https://hucvl.github.io/recipeqa/).



### NarrativeQA
[NarrativeQA](https://arxiv.org/abs/1712.07040) adalah dataset yang dibangun untuk mendorong pemahaman bahasa yang lebih dalam. Dataset ini melibatkan alasan untuk membaca seluruh buku atau skrip film. Dataset ini berisi sekitar 45 ribu pasangan jawaban pertanyaan dalam bentuk teks bebas. Ada dua mode dataset ini (1) pemahaman bacaan atas ringkasan dan (2) pemahaman bacaan atas seluruh buku / skrip.

| Model                        | BLEU-1     | BLEU-4   | METEOR | Rouge-L | Paper / Source | Code |
| -------------                | :-----:   | :-----:|:-----:| :-----:|---            | ---  |
|DecaProp (Tay et al., 2018)	   |44.35    |27.61	 | 21.80 | 44.69   |[Densely Connected Attention Propagation for Reading Comprehension](https://arxiv.org/abs/1811.04210)       |  [official](https://github.com/vanzytay/NIPS2018_DECAPROP)    |
|BiAttention + DCU-LSTM (Tay et al., 2018)	   |36.55    |19.79	 | 17.87 | 41.44  |[Multi-Granular Sequence Encoding via Dilated Compositional Units for Reading Comprehension](http://aclweb.org/anthology/D18-1238)       |      |
|BiDAF (Seo et al., 2017)	   |33.45    |15.69	 | 15.68 | 36.74  |[Bidirectional Attention Flow for Machine Comprehension](https://arxiv.org/abs/1611.01603)       |      |

*Perhatikan bahwa di atas adalah untuk pengaturan Ringkasan. Tidak ada hasil resmi yang diterbitkan untuk membaca seluruh buku / cerita kecuali untuk makalah aslinya. 

### DuoRC

[DuoRC](https://duorc.github.io) DuoRC berisi 186.089 pasangan tanya-jawab unik yang dibuat dari koleksi 7680 pasang plot film di mana setiap pasangan dalam koleksi mencerminkan dua versi dari film yang sama. 

DuoRC mendorong komunitas NLP untuk mengatasi tantangan dalam menggabungkan pengetahuan dan penalaran dalam arsitektur saraf untuk pemahaman bacaan. Ini menimbulkan beberapa tantangan menarik seperti:
  - DuoRC menggunakan plot paralel dirancang khusus untuk menampung sejumlah besar pertanyaan dengan tumpang tindih leksikal yang rendah antara pertanyaan dan bagian yang terkait
  - Ini membutuhkan model untuk melampaui konten dari bagian yang diberikan itu sendiri dan menggabungkan pengetahuan dunia, pengetahuan latar belakang, dan pengetahuan akal sehat untuk sampai pada jawaban
  - Ini berputar di sekitar narasi dari plot film yang menggambarkan peristiwa kompleks dan oleh karena itu secara alami memerlukan penalaran yang kompleks (mis. Penalaran temporal, keterikatan, anafora jarak jauh, dll.) Di berbagai kalimat untuk menyimpulkan jawaban atas pertanyaan
  - Beberapa pertanyaan dalam DuoRC, meskipun tampaknya relevan, sebenarnya tidak dapat dijawab dari bagian yang diberikan. Ini membutuhkan model untuk mendeteksi pertanyaan yang tidak dapat dijawab. Aspek ini penting bagi mesin untuk mencapai dalam pengaturan industri pada khususnya..
  
### DROP

[DROP](https://allennlp.org/drop) adalah tolok ukur 96k-pertanyaan crowdsourced, dibuat secara berlawanan, di mana sistem harus menyelesaikan referensi dalam pertanyaan, mungkin untuk beberapa posisi input, dan melakukan operasi terpisah atas mereka (seperti penambahan, penghitungan, atau penyortiran). Operasi-operasi ini membutuhkan pemahaman yang jauh lebih komprehensif tentang isi paragraf daripada apa yang diperlukan untuk dataset sebelumnya.

## Open-domain Question Answering

### DuReader
[DuReader](https://ai.baidu.com/broad/subordinate?dataset=dureader) adalah dataset skala besar, domain terbuka untuk pemahaman mesin Cina (MRC), yang dirancang untuk mengatasi MRC dunia nyata. [Tautan ke makalah](https://arxiv.org/pdf/1711.05073.pdf) 

DuReader memiliki tiga keunggulan dibandingkan dataset MRC lainnya: 
- (1) sumber data: pertanyaan dan dokumen didasarkan pada Pencarian Baidu dan Baidu Zhidao; jawaban dihasilkan secara manual. 
- (2) jenis pertanyaan: memberikan anotasi yang kaya untuk lebih banyak jenis pertanyaan, terutama ya-tidak dan pertanyaan pendapat, yang meninggalkan lebih banyak peluang bagi komunitas penelitian. 
- (3) skala: ini berisi 300 ribu pertanyaan, 660 ribu jawaban, dan 1,5 juta dokumen; ini adalah dataset MRC Cina terbesar sejauh ini. 

Untuk membantu komunitas melakukan perbaikan ini,keduanya [dataset](https://ai.baidu.com/broad/download?dataset=dureader) DuReader dan [baseline systems](https://github.com/baidu/DuReader) telah dipsoting secara online. 

[papan peringkat](https://ai.baidu.com/broad/leaderboard?dataset=dureader) tersedia di halaman DuReader.

### Quasar
[Quasar](https://arxiv.org/abs/1707.03904) adalah dataset untuk menjawab pertanyaan domain terbuka. Ini mencakup dua bagian: (1) Dataset Quasar-S terdiri dari 37.000 kueri gaya cloze yang dibangun dari definisi tag entitas perangkat lunak di situs web populer Stack Overflow. (2) Dataset Quasar-T terdiri dari 43.000 pertanyaan trivia domain terbuka dan jawaban mereka diperoleh dari berbagai sumber internet. 

| Model                        | EM (Quasar-T)     | F1 (Quasar-T)    |Paper / Source | Code |
| -------------                | :-----:| :-----:|---            | ---  |
|Denoising QA (Lin et al. 2018)|42.2	  |49.3    |[Denoising Distantly Supervised Open-Domain Question Answering](http://aclweb.org/anthology/P18-1161)|[official](https://github.com/thunlp/OpenQA)|
|DecaProp (Tay et al., 2018)	     |38.6	  |46.9	   |[Densely Connected Attention Propagation for Reading Comprehension](https://arxiv.org/abs/1811.04210)|[official](https://github.com/vanzytay/NIPS2018_DECAPROP)|
|R^3 (Wang et al., 2018)	     |35.3	  |41.7	   |[R^3: Reinforced Ranker-Reader for Open-Domain Question Answering](https://aaai.org/ocs/index.php/AAAI/AAAI18/paper/view/16712/16165)|[official](https://github.com/shuohangwang/mprc)|
|BiDAF (Seo et al., 2017)	     |25.9	  |28.5	   |[Bidirectional Attention Flow for Machine Comprehensio](https://arxiv.org/abs/1611.01603)               | [official](https://github.com/allenai/bi-att-flow)|
|GA (Dhingra et al., 2017)	   |26.4    |26.4	   |[Gated-Attention Readers for Text Comprehension](https://arxiv.org/pdf/1606.01549)       |      |



### SearchQA
[SearchQA](https://arxiv.org/abs/1704.05179) SearchQA dibangun untuk mencerminkan saluran penuh untuk menjawab pertanyaan umum. SearchQA terdiri dari lebih dari 140r pasangan tanya jawab dengan masing-masing pasangan memiliki 49,6 cuplikan. Setiap tupel konteks-jawaban-pertanyaan pada SearchQA dilengkapi dengan meta-data tambahan seperti URL snippet.

| Model                        | Unigram Acc     | N-gram F1   | EM     |  F1   |Paper / Source | Code |
| -------------                | :-----:| :-----:| :-----:| :-----:|---            | ---  |
|DecaProp (Tay et al., 2018)	   |62.2    |70.8	   |56.8 |63.6    |[Densely Connected Attention Propagation for Reading Comprehension](https://arxiv.org/abs/1811.04210)       | [official](https://github.com/vanzytay/NIPS2018_DECAPROP)     |
|Denoising QA (Lin et al. 2018)| - |-    | 58.8| 64.5|[Denoising Distantly Supervised Open-Domain Question Answering](http://aclweb.org/anthology/P18-1161)|[official](https://github.com/thunlp/OpenQA)|
|R^3 (Wang et al., 2018)	     |-	  |-	 | 49.0| 55.3  |[R^3: Reinforced Ranker-Reader for Open-Domain Question Answering](https://aaai.org/ocs/index.php/AAAI/AAAI18/paper/view/16712/16165)|[official](https://github.com/shuohangwang/mprc)|
|Bi-Attention + DCU-LSTM (Tay et al., 2018)	   |49.4    |59.5	   |- |-    |[Multi-Granular Sequence Encoding via Dilated Compositional Units for Reading Comprehension](http://aclweb.org/anthology/D18-1238)       |      |
|AMANDA (Kundu et al., 2018)	     |46.8	  |56.6	   |- |-    |[A Question-Focused Multi-Factor Attention Network for Question Answering](https://arxiv.org/abs/1801.08290)               | [official](https://github.com/nusnlp/amanda)|
|Focused Hierarchical RNN	(Ke et al., 2018)     |46.8	  |53.4	   |- |-    |[Focused Hierarchical RNNs for Conditional Sequence Processing](http://proceedings.mlr.press/v80/ke18a/ke18a.pdf)||
|ASR (Kadlec et al, 2016) |41.3	  |22.8    |- |-    |[Text Understanding with the Attention Sum Reader Network](https://arxiv.org/abs/1603.01547)|

## Knowledge Base Question Answering

Knowledge Base Question Answering iadalah tugas menjawab pertanyaan bahasa alami berdasarkan basis pengetahuan / grafik pengetahuan seperti [DBpedia](https://wiki.dbpedia.org/) atau  [Wikidata](https://www.wikidata.org/).

### QALD-9
[QALD-9](http://ceur-ws.org/Vol-2241/paper-06.pdf) adalah superset yang dikuratori secara manual dari delapan edisi sebelumnya dari [Question Answering over Linked Data (QALD) challenge](http://2018.nliwod.org/challenge) yang diterbitkan pada tahun 2018. Ini dibangun oleh para ahli manusia untuk mencakup berbagai bahasa alami untuk konversi SPARQL berdasarkan DBpedia 2016- 10 basis pengetahuan. Setiap pasangan pertanyaan-jawaban memiliki meta-data tambahan. QALD-9 paling baik dievaluasi menggunakan [GERBIL QA platform](http://gerbil-qa.aksw.org/gerbil/config) untuk pengulangan angka evaluasi.

| Annotator | Macro P | Macro R | Macro F1 | Error Count | Average Time/Doc ms | Macro F1 QALD | Paper (including links to webservices/source code)|
|------------------------|:-------:|:-------:|:--------:|:-----------:|:-------------------:|:-------------:|----------------------|
| Elon (WS)              |   0.049 |   0.053 |    0.050 |           2 |                 219 |         0.100 ||
| QASystem (WS)          |   0.097 |   0.116 |    0.098 |           0 |                1014 |         0.200 ||
| TeBaQA (WS)            |   0.129 |   0.134 |    0.130 |           0 |                2668 |         0.222 ||
| wdaqua-core1 (DBpedia) |   0.261 |   0.267 |    0.250 |           0 |                 661 |         0.289 | Diefenbach, Dennis, Kamal Singh, and Pierre Maret. "Wdaqua-core1: a question answering service for rdf knowledge bases." Companion of the The Web Conference 2018 on The Web Conference 2018. International World Wide Web Conferences Steering Committee, 2018. |
| gAnswer (WS)           |   0.293 |   0.327 |    0.298 |           1 |                3076 |         0.430 | Zou, Lei, et al. "Natural language question answering over RDF: a graph data driven approach." Proceedings of the 2014 ACM SIGMOD international conference on Management of data. ACM, 2014.|

[Go back to the README](../README.md)
