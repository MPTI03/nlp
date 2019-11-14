# Simplification

Simplification terdiri dari memodifikasi konten dan struktur teks dimana untuk membuatnya lebih mudah dibaca dan dipahami, sambil mempertahankan ide utamanya dan mendekati makna aslinya. Versi teks yang disederhanakan dapat bermanfaat bagi pembaca yang buta huruf, pelajar bahasa Inggris, anak-anak, dan orang dengan afasia, disleksia, atau autisme. Dan juga menyederhanakan teks secara otomatis dapat meningkatkan kinerja pada tugas-tugas NLP lainnya, seperti penguraian, peringkasan, ekstraksi informasi, pelabelan peran semantik, dan terjemahan mesin.

## Sentence Simplification

Penelitian tentang simplification otomatis telah terbatas secara tradisional saat melakukan perubahan di tingkat kalimat. Apa yang harus kita harapkan dari model kalimat simplification? Mari kita lihat bagaimana manusia menyederhanakan (dari [sini](http://videolectures.net/esslli2011_lapata_simplification/)):

| Original Sentence   | Simplified   Sentence |
| ---------------------------------- | ---------------------------------- |
| Burung hantu adalah ordo Strigiformes, terdiri dari 200 jenis burung pemangsa. | Burung hantu adalah sejenis burung. Ada sekitar 200 jenis burung hantu. |
| sebagian besar burung hantu berburu mamalia kecil, serangga, dan burung lain meskipun beberapa spesies memiliki kemampuan dalam berburu ikan. | sasaran(mangsa) burung hantu yaitu burung-burung, serangga besar (seperti jangkrik), reptil kecil (seperti kadal) atau mamalia kecil (seperti tikus biasa, tikus liar, dan kelinci).
. |

### Evaluation

Metode ideal untuk menentukan kualitas simplification adalah melalui evaluasi manusia. Secara tradisional, output yang disederhanakan dinilai dalam hal tata bahasa (atau kelancaran), yang berarti pelestarian (atau kecukupan) dan kesederhanaan, menggunakan skala Likert (1-3 atau 1-5). Peringatan: Apakah kriteria ini (pada tingkat kalimat) yang paling tepat untuk menilai kalimat yang disederhanakan? Telah disarankan [(Siddharthan, 2014)](https://www.jbe-platform.com/content/journals/10.1075/itl.165.2.06sid) bahwa evaluasi berorientasi tugas (misal, melalui tes pemahaman membaca [(Angrosh et al., 2014)](http://aclweb.org/anthology/C14-1188)) bisa lebih informatif tentang kegunaan dari penyederhanaan yang dihasilkan. Namun, ini bukan praktik umum.

### Main - Simple English Wikipedia

[Simple English Wikipedia](https://simple.wikipedia.org) adalah ensiklopedia online yang ditujukan untuk orang yg ingin mempelajari bahasa inggris. Artikel-artikelnya diharapkan mengandung lebih sedikit kata dan struktur tata bahasa yang lebih sederhana daripada yang ada di mitra Wikipedia Bahasa Inggris Utama mereka [Main English Wikipedia](https://en.wikipedia.org) counterpart. Sebagian besar popularitas menggunakan Wikipedia untuk penelitian dalam Penyederhanaan berasal dari keberpihakan kalimat yang tersedia untuk umum antara artikel "setara" di Wikipedia Bahasa Inggris Utama dan Wikipedia.

#### PWKP / WikiSmall

[Zu et al. (2010)](http://aclweb.org/anthology/C10-1152) compiled a parallel menyusun corpus paralel dengan lebih dari 108 ribu pasangan kalimat dari 65.133 artikel Wikipedia, memungkinkan perataan 1-ke-1 dan 1-ke-N. Jenis keselarasan yang terakhir mewakili contoh pemisahan kalimat. Corpus lengkap asli dapat ditemukan [disini](https://www.informatik.tu-darmstadt.de/ukp/research_6/data/sentence_simplification/simple_complex_sentence_pairs/index.en.jsp). Set tes terdiri dari 100 contoh, dengan satu referensi penyederhanaan per kalimat asli. [Zhang and Lapata (2017)](http://aclweb.org/anthology/D17-1062) merilis split yang lebih standar dari dataset ini yang disebut [*WikiSmall*](https://github.com/XingxingZhang/dress), dengan 89,042 contoh for latihan, 205 untuk pengembangan dan 100 contoh asli yang sama untuk pengujian.

Kami menyajikan model yang diuji dalam dataset ini yang diberi peringkat berdasarkan skor BLEU. SARI tidak dapat dihitung secara andal dalam dataset ini karena tidak mengandung banyak referensi penyederhanaan per kalimat asli. Selain itu, ada beberapa contoh transformasi penyederhanaan yang lebih maju (contoh, pemisahan) dimana SARI tidak menilai menurut definisi.

| Model           | BLEU | SARI | Paper / Source | Code |
| --------------- | :-----: | :-----: | -------------- | ---- |
| Hybrid (Narayan and Gardent, 2014) | 53.94\* (53.6) | 30.46\* | [Hybrid Simplification using Deep Semantics and Machine Translation](http://aclweb.org/anthology/P/P14/P14-1041.pdf) | [Official](https://github.com/shashiongithub/Sentence-Simplification-ACL14) |
| NSELSTM-B (Vu et al., 2018) | 53.42 | 17.47 | [Sentence Simplification with Memory-Augmented Neural Networks](http://aclweb.org/anthology/N18-2013) |  |
| PBMT-R (Wubben et al., 2012) | 46.31\* (43.0) | 15.97\* | [Sentence Simplification by Monolingual Machine Translation](http://aclweb.org/anthology/P12-1107) |  |
| RevILP (Woodsend and Lapata, 2011) | 42.0 | | [Learning to Simplify Sentences with Quasi-Synchronous Grammar and Integer Programming](http://aclweb.org/anthology/D11-1038) |  |
| UNSUP (Narayan and Gardent, 2016) | 38.47 | | [Unsupervised Sentence Simplification Using Deep Semantics](http://aclweb.org/anthology/W16-6620) |  |
| TSM (Zhu et al., 2010) | 38.0 | | [A Monolingual Tree-based Translation Model for Sentence Simplification](http://aclweb.org/anthology/C10-1152) |  |
| DRESS-LS (Zhang and Lapata, 2017) | 36.32 | 27.24 | [Sentence Simplification with Deep Reinforcement Learning](http://aclweb.org/anthology/D17-1062) | [Official](https://github.com/XingxingZhang/dress) |
| DRESS (Zhang and Lapata, 2017) | 34.53 | 27.48 | [Sentence Simplification with Deep Reinforcement Learning](http://aclweb.org/anthology/D17-1062) | [Official](https://github.com/XingxingZhang/dress) |
| NSELSTM-S (Vu et al., 2018) | 29.72 | 29.75 | [Sentence Simplification with Memory-Augmented Neural Networks](http://aclweb.org/anthology/N18-2013) |  |
| Pointer + Multi-task Entailment and Paraphrase Generation (Guo et al., 2018) | 27.23 | 29.58 | [Dynamic Multi-Level Multi-Task Learning for Sentence Simplification](http://aclweb.org/anthology/C18-1039) | [Official](https://github.com/HanGuo97/MultitaskSimplification) |

#### Coster and Kauchack (2011)

[Coster and Kauchack (2011)](http://aclweb.org/anthology/P11-2117) secara otomatis menyelaraskan pasangan kalimat 137K dari 10K artikel Wikipedia, mempertimbangkan keberpihakan 1 ke 1 dan 1 ke N, dengan satu referensi penyederhanaan per kalimat asli. Korpus dibagi menjadi 124 ribu instance untuk pelatihan, 12 ribu untuk pengembangan, dan 1,3 ribu untuk pengujian. Dataset tersedia [disini](http://www.cs.pomona.edu/~dkauchak/simplification/). Seperti sebelumnya, model yang diuji dalam dataset ini diberi peringkat berdasarkan skor BLEU dan bukan SARI.

| Model           | BLEU | SARI | Paper / Source | Code |
| --------------- | :-----: | :-----: | -------------- | ---- |
| Moses-Del (Coster and Kauchak, 2011b) | 60.46 |      | [Learning to Simplify Sentences Using Wikipedia](http://aclweb.org/anthology/W11-1601) |  |
| Moses (Coster and Kauchak, 2011a) | 59.87 | |[Simple English Wikipedia: A New Text Simplification Task](http://aclweb.org/anthology/P11-2117)  |  |
| SimpleTT (Feblowitz and Kauchak, 2013) | 56.4 | | [Sentence Simplification as Tree Transduction](aclweb.org/anthology/W13-2901) |  |
| PBMT-R (Wubben et al., 2012) | 54.3\* |      | [Sentence Simplification by Monolingual Machine Translation](http://aclweb.org/anthology/P12-1107) |  |

#### Turk Corpus

Dengan mendefinisikan SARI, [Xu et al. (2016)](http://aclweb.org/anthology/Q16-1029) merilis dataset yang dikumpulkan dengan benar untuk menghitung metrik kesederhanaan: keberpihakan 1 banding 1 yang berfokus pada transformasi parafrase (diekstraksi dari PWKP), dan beberapa (8) referensi penyederhanaan per kalimat asli (dikumpulkan melalui Amazon Mechanical Turk). [dataset](https://github.com/cocoxu/simplification/) Dataset berisi 2.350 kalimat yang dibagi menjadi 2.000 instance untuk tuning dan 350 untuk pengujian. Untuk pelatihan, sebagian besar model menggunakan [*WikiLarge*](https://github.com/XingxingZhang/dress), yang disusun oleh [Zhang and Lapata (2017)](http://aclweb.org/anthology/D17-1062) menggunakan keberpihakan dari kumpulan data berbasis wikipedia lainnya ([Zhu et al., 2010](http://aclweb.org/anthology/C10-1152); [Woodsend and Lapata, 2011](http://aclweb.org/anthology/D11-1038); [Kauchak, 2013](http://aclweb.org/anthology/P13-1151)), dan berisi 296K contoh tidak hanya keberpihakan 1-ke-1. 

Kami menyajikan model yang diuji dalam dataset ini **diatur berdasarkan tingkat nilai SARI**.

| Model           | BLEU | SARI | Paper / Source | Code |
| --------------- | :-----: | :-----: | -------------- | ---- |
| DMASS + DCSS (Zhao et al., 2018) |  | 40.45 | [Integrating Transformer and Paraphrase Rules for Sentence Simplification](http://aclweb.org/anthology/D18-1355) | [Official](https://github.com/Sanqiang/text_simplification) |
| SBSMT + PPDB + SARI (Xu et al, 2016) | 73.08\* (72.36) | 39.96\* (37.91) | [Optimizing Statistical Machine Translation for Text Simplification](http://aclweb.org/anthology/Q16-1029) | [Official](https://github.com/cocoxu/simplification/) |
| PBMT-R (Wubben et al., 2012) | 81.11\* | 38.56\* | [Sentence Simplification by Monolingual Machine Translation](http://aclweb.org/anthology/P12-1107) |  |
| Pointer + Multi-task Entailment and Paraphrase Generation (Guo et al., 2018) | 81.49 | 37.45 | [Dynamic Multi-Level Multi-Task Learning for Sentence Simplification](http://aclweb.org/anthology/C18-1039) | [Official](https://github.com/HanGuo97/MultitaskSimplification) |
| NTS + SARI (Nisioi et al., 2017) | 80.69 | 37.25 | [Exploring Neural Text Simplification Models](http://aclweb.org/anthology/P17-2014) | [Official](https://github.com/senisioi/NeuralTextSimplification) |
| DRESS-LS (Zhang and Lapata, 2017) | 80.12 | 37.27 | [Sentence Simplification with Deep Reinforcement Learning](http://aclweb.org/anthology/D17-1062) | [Official](https://github.com/XingxingZhang/dress) |
| DRESS (Zhang and Lapata, 2017) | 77.18 | 37.08 | [Sentence Simplification with Deep Reinforcement Learning](http://aclweb.org/anthology/D17-1062) | [Official](https://github.com/XingxingZhang/dress) |
| NSELSTM-S (Vu et al., 2018) | 80.43 | 36.88 | [Sentence Simplification with Memory-Augmented Neural Networks](http://aclweb.org/anthology/N18-2013) |  |
| SEMoses (Sulem et al., 2018)                                 |      74.49       |     36.70      | [Simple and Effective Text Simplification Using Semantic and Neural Methods](http://aclweb.org/anthology/P18-1016) | [Official](https://github.com/eliorsulem/simplification-acl2018) |
| NSELSTM-B (Vu et al., 2018) | 92.02 | 33.43 | [Sentence Simplification with Memory-Augmented Neural Networks](http://aclweb.org/anthology/N18-2013) | |
| Hybrid (Narayan and Gardent, 2014) | 48.97\* | 31.40\* | [Hybrid Simplification using Deep Semantics and Machine Translation](http://aclweb.org/anthology/P/P14/P14-1041.pdf) | [Official](https://github.com/shashiongithub/Sentence-Simplification-ACL14) |

#### Other Datasets

[Hwang et al. (2015)](http://aclweb.org/anthology/N15-1022) merilis [dataset](http://ssli.ee.washington.edu/tial/projects/simplification/) dari contoh 392K, dimana [Kajiwara and Komachi (2016)](http://aclweb.org/anthology/C16-1109) mengumpulkan [sscorpus](https://github.com/tmu-nlp/sscorpus) dari contoh 493K, juga dari pasangan artikel Wikipedia Wikipedia Bahasa Inggris. Kedua dataset hanya berisi keberpihakan 1-ke-1 dengan satu referensi penyederhanaan per kalimat asli. Meskipun ukurannya lebih besar dan algoritma pelurusan kalimat yang lebih canggih digunakan untuk mengumpulkannya, kumpulan data ini tidak umum digunakan dalam penelitian penyederhanaan.

### Newsela

[Xu et al. (2015)](http://aclweb.org/anthology/Q15-1021) memperkenalkan Newsela corpus, yang berisi 1.130 artikel berita dengan masing-masing empat versi penyederhanaan. Artikel asli dianggap versi 0, dan setiap versi penyederhanaan berlangsung dari 1 hingga 4 (tertinggi menjadi yang paling sederhana). Penyederhanaan ini diproduksi secara manual oleh editor profesional, dengan mempertimbangkan anak-anak dari tingkat kelas yang berbeda sebagai target audiens. Melalui evaluasi manual pada subset data, [Xu et al. (2015)](http://aclweb.org/anthology/Q15-1021) menunjukkan bahwa ada kehadiran yang lebih baik dan distribusi transformasi penyederhanaan di Newsela daripada di PWKP. 

dataset dapat diminta [disini](https://newsela.com/data/). Namun, para peneliti tidak diizinkan untuk membagi data secara publik. Ini tidak ideal untuk reproduksibilitas dan perbandingan yang tepat di antara model.

#### Splits by Zhang and Lapata (2017)

[Xu et al. (2015)](http://aclweb.org/anthology/Q15-1021) menghasilkan penyelarasan kalimat antara semua versi setiap artikel di Newsela corpus. [Zhang and Lapata (2017)](http://aclweb.org/anthology/D17-1062) menyiratkan bahwa mereka menggunakan keberpihakan tersebut tetapi menghapus beberapa pasangan kalimat yang “terlalu mirip”. Pada akhirnya, mereka menggunakan dataset yang terdiri dari 94.208 instance untuk pelatihan, 1.129 instance untuk pengembangan, dan 1.076 instance untuk pengujian. Set pengujian mereka, khususnya, hanya berisi 1-ke-1 keberpihakan dengan satu referensi penyederhanaan per kalimat asli.

menggunakan splits mereka, [Zhang and Lapata (2017)](http://aclweb.org/anthology/D17-1062) melatih dan menguji beberapa model, yang kami sertakan dalam peringkat kami. Penelitian lain yang mengklaim telah menggunakan split dataset yang sama juga dipertimbangkan. Meskipun bukan skenario yang ideal, model yang diuji dalam dataset ini biasanya diberi peringkat berdasarkan skor SARI.

| Model           | BLEU | SARI | Paper / Source | Code |
| --------------- | :-----: | :-----: | -------------- | ---- |
| Pointer + Multi-task Entailment and Paraphrase Generation (Guo et al., 2018) | 11.14 | 33.22 | [Dynamic Multi-Level Multi-Task Learning for Sentence Simplification](http://aclweb.org/anthology/C18-1039) | [Official](https://github.com/HanGuo97/MultitaskSimplification) |
| Hybrid (Narayan and Gardent, 2014) | 14.46\* | 30.00\* | [Hybrid Simplification using Deep Semantics and Machine Translation](http://aclweb.org/anthology/P/P14/P14-1041.pdf) | [Official](https://github.com/shashiongithub/Sentence-Simplification-ACL14) |
| NSELSTM-S (Vu et al., 2018) | 22.62 | 29.58 | [Sentence Simplification with Memory-Augmented Neural Networks](http://aclweb.org/anthology/N18-2013) | |
| NSELSTM-B (Vu et al., 2018) | 26.31 | 27.42 | [Sentence Simplification with Memory-Augmented Neural Networks](http://aclweb.org/anthology/N18-2013) | |
| DRESS (Zhang and Lapata, 2017) | 23.21 | 27.37 | [Sentence Simplification with Deep Reinforcement Learning](http://aclweb.org/anthology/D17-1062) | [Official](https://github.com/XingxingZhang/dress) |
| DMASS + DCSS (Zhao et al., 2018) |  | 27.28 | [Integrating Transformer and Paraphrase Rules for Sentence Simplification](http://aclweb.org/anthology/D18-1355) | [Official](https://github.com/Sanqiang/text_simplification) |
| DRESS-LS (Zhang and Lapata, 2017) | 24.30 | 26.63 | [Sentence Simplification with Deep Reinforcement Learning](http://aclweb.org/anthology/D17-1062) | [Official](https://github.com/XingxingZhang/dress) |
| PBMT-R (Wubben et al., 2012) | 18.19\* | 15.77\* | [Sentence Simplification by Monolingual Machine Translation](http://aclweb.org/anthology/P12-1107) |  |




[Go back to the README](../README.md)