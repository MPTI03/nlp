# Semantic parsing

### Table of contents

- [AMR parsing](#amr-parsing)
  - [LDC2014T12](#ldc2014t12)
  - [LDC2015E86](#ldc2015e86)
  - [LDC2016E25](#ldc2016e25)
- [SQL parsing](#sql-parsing)
  - [ATIS](#atis)
  - [Advising](#advising)
  - [GeoQuery](#geoquery)
  - [Scholar](#scholar)
  - [Spider](#spider)
  - [WikiSQL](#wikisql)
  - [Smaller datasets](#smaller-datasets)

Parsing semantik adalah tugas menerjemahkan bahasa alami ke dalam representasi makna formal di mana mesin dapat bertindak. Representasi dapat berupa bahasa yang dapat dieksekusi seperti SQL atau representasi yang lebih abstrak seperti [Abstract Meaning Representation (AMR)](https://en.wikipedia.org/wiki/Abstract_Meaning_Representation).

## AMR parsing

Setiap AMR adalah grafik berakar tunggal, terarah. AMR termasuk peran semantik PropBank, coreference dalam kalimat, entitas dan tipe yang disebutkan, modalitas, negasi, pertanyaan, jumlah, dan sebagainya. [Lihat](https://amr.isi.edu/index.html).
Dalam tabel berikut, sistem yang ditandai dengan  &hearts; adalah sistem pipa yang membutuhkan POS sebagai input
&spades; untuk yang membutuhkan NER,
&diams; untuk yang membutuhkan parsing sintaks, 
dan &clubs; untuk yang membutuhkan SRL.

### LDC2014T12: 
13,051 kalimat

Model dievaluasi pada bagian newswire dan dataset lengkap berdasarkan [smatch](https://amr.isi.edu/smatch-13.pdf).

| Model           | F1 Newswire  | F1 Full |  Paper / Source |
| ------------- | :-----:| :-----:| --- |
| Two-stage Sequence-to-Graph Transducer (Zhang et al., 2019)&hearts; | -- | 70.2 | [AMR Parsing as Sequence-to-Graph Transduction](https://arxiv.org/abs/1905.08704) |
| Transition-based+improved aligner+ensemble (Liu et al. 2018)&hearts; | 73.3 | 68.4 | [An AMR Aligner Tuned by Transition-based Parser](http://aclweb.org/anthology/D18-1264) |
| Improved CAMR (Wang and Xue, 2017)&spades;&diams; | --| 68.1| [Getting the Most out of AMR Parsing](http://aclweb.org/anthology/D17-1129) |
| Incremental joint model (Zhou et al., 2016)&hearts;&spades; | 71 | 66 | [AMR Parsing with an Incremental Joint Model](https://aclweb.org/anthology/D16-1065) |
| Transition-based transducer (Wang et al., 2015)&hearts;&diams;&clubs; | 70 | 66 | [Boosting Transition-based AMR Parsing with Refined Actions and Auxiliary Analyzers](http://www.aclweb.org/anthology/P15-2141) |
| Imitation learning  (Goodman et al., 2016)&hearts;&spades; | 70 |  -- | [Noise reduction and targeted exploration in imitation learning for Abstract Meaning Representation parsing](http://www.aclweb.org/anthology/P16-1001) |
MT-Based (Pust et al., 2015)&spades; | -- | 66 | [Parsing English into Abstract Meaning Representation Using Syntax-Based Machine Translation ](http://www.aclweb.org/anthology/D15-1136)
| Transition-based parser-Stack-LSTM (Ballesteros and Al-Onaizan, 2017)&hearts;&diams; | 69 | 64  | [AMR Parsing using Stack-LSTMs](http://www.aclweb.org/anthology/D17-1130) |
| Transition-based parser-Stack-LSTM (Ballesteros and Al-Onaizan, 2017) | 68 | 63  | [AMR Parsing using Stack-LSTMs](http://www.aclweb.org/anthology/D17-1130) |

### LDC2015E86: 
19,572 kalimat

Models dievaluasi berdasarkan [smatch](https://amr.isi.edu/smatch-13.pdf).

| Model           | Smatch  |  Paper / Source |
| ------------- | :-----:| --- |
| Joint model (Lyu and Titov, 2018)&hearts;&spades; | 73.7 | [AMR Parsing as Graph Prediction with Latent Alignment](https://arxiv.org/abs/1805.05286) |
| Mul-BiLSTM (Foland and Martin, 2017)&spades; | 70.7 | [Abstract Meaning Representation Parsing using LSTM Recurrent Neural Networks](http://aclweb.org/anthology/P17-1043) |
| JAMR (Flanigan et al., 2016)&hearts;&diams;&clubs; | 67.0 | [CMU at SemEval-2016 Task 8: Graph-based AMR Parsing with Infinite Ramp Loss](http://www.aclweb.org/anthology/S16-1186) |
| CAMR (Wang et al., 2016)&hearts;&diams;&clubs; | 66.5 | [CAMR at SemEval-2016 Task 8: An Extended Transition-based AMR Parser](http://www.aclweb.org/anthology/S16-1181) |
| AMREager (Damonte et al., 2017)&hearts;&spades;&diams; | 64.0 | [An Incremental Parser for Abstract Meaning Representation](http://www.aclweb.org/anthology/E17-1051) |
| SEQ2SEQ + 20M (Konstas et al., 2017)&spades; | 62.1 | [Neural AMR: Sequence-to-Sequence Models for Parsing and Generation](https://arxiv.org/abs/1704.08381) |

### LDC2016E25
39,260 kalimat

Hasil dihitung lebih dari 8 kali. Model dievaluasi berdasarkan [smatch](https://amr.isi.edu/smatch-13.pdf).

| Model           | Smatch  |  Paper / Source |
| ------------- | :-----:| --- |
| Two-stage Sequence-to-Graph Transducer (Zhang et al., 2019)&hearts; | 76.3 | [AMR Parsing as Sequence-to-Graph Transduction](https://arxiv.org/abs/1905.08704) |
| Rewarding Smatch: Transition-Based AMR Parsing with Reinforcement Learning (Naseem et al., 2019)&hearts;&spades;&diams; | 75.5 | [Rewarding Smatch: Transition-Based AMR Parsing with Reinforcement Learning](https://arxiv.org/pdf/1905.13370) |
| Joint model (Lyu and Titov, 2018)&hearts;&spades; | 74.4 | [AMR Parsing as Graph Prediction with Latent Alignment](https://arxiv.org/abs/1805.05286) |
| Rewarding Smatch: Transition-Based AMR Parsing with Reinforcement Learning (Naseem et al., 2019); | 73.4 | [Rewarding Smatch: Transition-Based AMR Parsing with Reinforcement Learning](https://arxiv.org/pdf/1905.13370) |
| ChSeq + 100K (van Noord and Bos, 2017)&hearts; | 71.0 | [Neural Semantic Parsing by Character-based Translation: Experiments with Abstract Meaning Representations](https://arxiv.org/abs/1705.09980) |
| Neural-Pointer (Buys and Blunsom, 2017)&hearts;&spades; | 61.9 | [Oxford at SemEval-2017 Task 9: Neural AMR Parsing with Pointer-Augmented Attention](http://aclweb.org/anthology/S17-2157) |

## SQL parsing

### ATIS

5,280 pertanyaan pengguna untuk tugas pemesanan penerbangan:

- Collected and manually annotated with SQL [Dahl et al., (1994)](http://dl.acm.org/citation.cfm?id=1075823)
- Modified by [Iyer et al., (2017)](http://www.aclweb.org/anthology/P17-1089) to reduce nesting
- Bugfixes and changes to a canonical style by [Finegan-Dollak et al., (2018)](http://arxiv.org/abs/1806.09029)


Contoh :

| Question | SQL query | 
| ------------- |  --- |
| what flights from any city land at MKE | `SELECT DISTINCT FLIGHTalias0.FLIGHT_ID FROM AIRPORT AS AIRPORTalias0 , AIRPORT_SERVICE AS AIRPORT_SERVICEalias0 , CITY AS CITYalias0 , FLIGHT AS FLIGHTalias0 WHERE AIRPORTalias0.AIRPORT_CODE = "MKE" AND CITYalias0.CITY_CODE = AIRPORT_SERVICEalias0.CITY_CODE AND FLIGHTalias0.FROM_AIRPORT = AIRPORT_SERVICEalias0.AIRPORT_CODE AND FLIGHTalias0.TO_AIRPORT = AIRPORTalias0.AIRPORT_CODE ;` |

| Model           | Question Split | Query Split |  Paper / Source | Code |
| --------------- | ----- |  :-----:| --------------- | ---- |
| Seq2Seq with copying (Finegan-Dollak et al., 2018) | 51 | 32 | [Improving Text-to-SQL Evaluation Methodology](http://arxiv.org/abs/1806.09029) | [Data and System](https://github.com/jkkummerfeld/text2sql-data) |
| Iyer et al., (2017) | 45 | 17 | [Learning a neural semantic parser from user feedback](http://www.aclweb.org/anthology/P17-1089) | [System](https://github.com/sriniiyer/nl2sql) |
| Template Baseline (Finegan-Dollak et al., 2018) | 45 | 0 | [Improving Text-to-SQL Evaluation Methodology](http://arxiv.org/abs/1806.09029) | [Data and System](https://github.com/jkkummerfeld/text2sql-data) |

### Advising

4,570 pertanyaan pengguna tentang pemberian nasihat di universitas, dengan SQL [Finegan-Dollak et al., (2018)](http://arxiv.org/abs/1806.09029).

Contoh:

| Question | SQL query | 
| ------------- |  --- |
| Can undergrads take 550 ? | `SELECT DISTINCT COURSEalias0.ADVISORY_REQUIREMENT , COURSEalias0.ENFORCED_REQUIREMENT , COURSEalias0.NAME FROM COURSE AS COURSEalias0 WHERE COURSEalias0.DEPARTMENT = \"department0\" AND COURSEalias0.NUMBER = 550 ;` |

| Model           | Question Split | Query Split |  Paper / Source | Code |
| --------------- | ----- |  :-----:| --------------- | ---- |
| Template Baseline (Finegan-Dollak et al., 2018) | 80 | 0 | [Improving Text-to-SQL Evaluation Methodology](http://arxiv.org/abs/1806.09029) | [Data and System](https://github.com/jkkummerfeld/text2sql-data) |
| Seq2Seq with copying (Finegan-Dollak et al., 2018) | 70 | 0  | [Improving Text-to-SQL Evaluation Methodology](http://arxiv.org/abs/1806.09029) | [Data and System](https://github.com/jkkummerfeld/text2sql-data) |
| Iyer et al., (2017) | 41 | 1 | [Learning a neural semantic parser from user feedback](http://www.aclweb.org/anthology/P17-1089) | [System](https://github.com/sriniiyer/nl2sql) |

### GeoQuery

877 pertanyaan pengguna tentang geografi AS:

- Collected and manually annotated with Prolog [Zelle and Mooney (1996)](http://dl.acm.org/citation.cfm?id=1864519.1864543)
- Most questions were converted to SQL by [Popescu et al., (2003)](http://doi.acm.org/10.1145/604045.604070)
- Remaining question converted to SQL by [Giordani and Moschitti (2012)](https://doi.org/10.1007/978-3-642-45260-4_5), and independently by [Iyer et al., (2017)](http://www.aclweb.org/anthology/P17-1089)
- Bugfixes and changes to a canonical style by [Finegan-Dollak et al., (2018)](http://arxiv.org/abs/1806.09029)

Contoh :

| Question | SQL query | 
| ------------- |  --- |
| what is the biggest city in arizona | `SELECT CITYalias0.CITY_NAME FROM CITY AS CITYalias0 WHERE CITYalias0.POPULATION = ( SELECT MAX( CITYalias1.POPULATION ) FROM CITY AS CITYalias1 WHERE CITYalias1.STATE_NAME = "arizona" ) AND CITYalias0.STATE_NAME = "arizona"` |

| Model           | Question Split | Query Split |  Paper / Source | Code |
| --------------- | ----- |  :-----:| --------------- | ---- |
| Seq2Seq with copying (Finegan-Dollak et al., 2018) | 71 | 20 | [Improving Text-to-SQL Evaluation Methodology](http://arxiv.org/abs/1806.09029) | [Data and System](https://github.com/jkkummerfeld/text2sql-data) |
| Iyer et al., (2017) | 66 | 40 | [Learning a neural semantic parser from user feedback](http://www.aclweb.org/anthology/P17-1089) | [System](https://github.com/sriniiyer/nl2sql) |
| Template Baseline (Finegan-Dollak et al., 2018) | 66 | 0  | [Improving Text-to-SQL Evaluation Methodology](http://arxiv.org/abs/1806.09029) | [Data and System](https://github.com/jkkummerfeld/text2sql-data) |

### Scholar

817 pertanyaan pengguna tentang publikasi akademik, dengan SQL yang dihasilkan secara otomatis yang diperiksa dengan menanyakan kepada pengguna apakah hasilnya benar.

- Collected by [Iyer et al., (2017)](http://www.aclweb.org/anthology/P17-1089)
- Bugfixes and changes to a canonical style by [Finegan-Dollak et al., (2018)](http://arxiv.org/abs/1806.09029)

Contoh:

| Question | SQL query | 
| ------------- |  --- |
| What papers has sharon goldwater written ? | `SELECT DISTINCT WRITESalias0.PAPERID FROM AUTHOR AS AUTHORalias0 , WRITES AS WRITESalias0 WHERE AUTHORalias0.AUTHORNAME = "sharon goldwater" AND WRITESalias0.AUTHORID = AUTHORalias0.AUTHORID ;` |

| Model           | Question Split | Query Split |  Paper / Source | Code |
| --------------- | ----- |  :-----:| --------------- | ---- |
| Seq2Seq with copying (Finegan-Dollak et al., 2018) | 59 | 5 | [Improving Text-to-SQL Evaluation Methodology](http://arxiv.org/abs/1806.09029) | [Data and System](https://github.com/jkkummerfeld/text2sql-data) |
| Template Baseline (Finegan-Dollak et al., 2018) | 52 | 0   | [Improving Text-to-SQL Evaluation Methodology](http://arxiv.org/abs/1806.09029) | [Data and System](https://github.com/jkkummerfeld/text2sql-data) |
| Iyer et al., (2017) | 44 | 3 | [Learning a neural semantic parser from user feedback](http://www.aclweb.org/anthology/P17-1089) | [System](https://github.com/sriniiyer/nl2sql) |

### Spider

Spider adalah parsing semantik skala besar dan lintas domain dan dataset text-to-SQL. Ini terdiri dari 10.181 pertanyaan dan 5.693 query SQL kompleks unik pada 200 database dengan beberapa tabel yang mencakup 138 domain berbeda. Di Spider 1.0, berbagai kueri dan basis data SQL yang kompleks muncul di set kereta dan uji.

Kumpulan data Spider dapat diakses dan papan peringkat dapat diakses [disini](https://yale-lily.github.io/spider).

### WikiSQL

[WikiSQL dataset](https://arxiv.org/abs/1709.00103) terdiri dari 87.673 contoh pertanyaan, kueri SQL, dan tabel basis data yang dibangun dari 26.521 tabel. Train / dev / test split disediakan sehingga setiap meja hanya dalam satu split. Model dievaluasi berdasarkan akurasi pada pertandingan hasil eksekusi.

Contoh:

| Question | SQL query | 
| ------------- |  --- |
| How many engine types did Val Musetti use? | `SELECT COUNT Engine WHERE Driver = Val Musetti` | 

WikiSQL dataset dan leaderboard dapat diakses [disini](https://github.com/salesforce/WikiSQL).

### Smaller Datasets

Restaurants - 378 pertanyaan tentang restoran, masakan dan lokasi mereka, dikumpulkan oleh [Tang and Mooney (2000)](http://www.aclweb.org/anthology/W/W00/W00-1317.pdf), dikonversi ke SQL oleh [Popescu et al., (2003)]((http://doi.acm.org/10.1145/604045.604070) dan [Giordani and Moschitti (2012)](https://doi.org/10.1007/978-3-642-45260-4_5), ditingkatkan dan dikonversi ke gaya kanonik oleh [Finegan-Dollak et al., (2018)](http://arxiv.org/abs/1806.09029)

Contoh:

| Question | SQL query | 
| ------------- |  --- |
| where is a restaurant in alameda ? | `SELECT LOCATIONalias0.HOUSE_NUMBER , RESTAURANTalias0.NAME FROM LOCATION AS LOCATIONalias0 , RESTAURANT AS RESTAURANTalias0 WHERE LOCATIONalias0.CITY_NAME = "alameda" AND RESTAURANTalias0.ID = LOCATIONalias0.RESTAURANT_ID ;` |

| Model           | Question Split | Query Split |  Paper / Source | Code |
| --------------- | ----- |  :-----:| --------------- | ---- |
| Iyer et al., (2017) | 100 | 8 | [Learning a neural semantic parser from user feedback](http://www.aclweb.org/anthology/P17-1089) | [System](https://github.com/sriniiyer/nl2sql) |
| Seq2Seq with copying (Finegan-Dollak et al., 2018) | 100 | 4 | [Improving Text-to-SQL Evaluation Methodology](http://arxiv.org/abs/1806.09029) | [Data and System](https://github.com/jkkummerfeld/text2sql-data) |
| Template Baseline (Finegan-Dollak et al., 2018) | 95 | 0  | [Improving Text-to-SQL Evaluation Methodology](http://arxiv.org/abs/1806.09029) | [Data and System](https://github.com/jkkummerfeld/text2sql-data) |

Academic - 196 pertanyaan tentang publikasi yang dihasilkan dengan menyebutkan semua pertanyaan berbeda yang mungkin dengan antarmuka Pencarian Akademik Microsoft, kemudian menulis pertanyaan untuk setiap permintaan [Li and Jagadish (2014)](http://dx.doi.org/10.14778/2735461.2735468). Diperbaiki dan diubah menjadi gaya kononikal oleh [Finegan-Dollak et al., (2018)](http://arxiv.org/abs/1806.09029).

Contoh:

| Question | SQL query | 
| ------------- |  --- |
| return me the homepage of PVLDB | `SELECT JOURNALalias0.HOMEPAGE FROM JOURNAL AS JOURNALalias0 WHERE JOURNALalias0.NAME = "PVLDB" ;` |

| Model           | Question Split | Query Split |  Paper / Source | Code |
| --------------- | ----- |  :-----:| --------------- | ---- |
| Seq2Seq with copying (Finegan-Dollak et al., 2018) | 81 | 74 | [Improving Text-to-SQL Evaluation Methodology](http://arxiv.org/abs/1806.09029) | [Data and System](https://github.com/jkkummerfeld/text2sql-data) |
| Iyer et al., (2017) | 76 | 70 | [Learning a neural semantic parser from user feedback](http://www.aclweb.org/anthology/P17-1089) | [System](https://github.com/sriniiyer/nl2sql) |
| Template Baseline (Finegan-Dollak et al., 2018) | 0 | 0 | [Improving Text-to-SQL Evaluation Methodology](http://arxiv.org/abs/1806.09029) | [Data and System](https://github.com/jkkummerfeld/text2sql-data) |

Yelp - 128 pertanyaan pengguna tentang situs web Yelp [Yaghmazadeh et al., 2017](http://doi.org/10.1145/3133887). Ditingkatkan dan dikonversi menjadi gaya kanonik oleh [Finegan-Dollak et al., (2018)](http://arxiv.org/abs/1806.09029).

Contoh:

| Question | SQL query | 
| ------------- |  --- |
| List all businesses with rating 3.5 | `SELECT BUSINESSalias0.NAME FROM BUSINESS AS BUSINESSalias0 WHERE BUSINESSalias0.RATING = 3.5 ;` |

| Model           | Question Split | Query Split |  Paper / Source | Code |
| --------------- | ----- |  :-----:| --------------- | ---- |
| Seq2Seq with copying (Finegan-Dollak et al., 2018) | 12 | 4 | [Improving Text-to-SQL Evaluation Methodology](http://arxiv.org/abs/1806.09029) | [Data and System](https://github.com/jkkummerfeld/text2sql-data) |
| Iyer et al., (2017) | 6 | 6 | [Learning a neural semantic parser from user feedback](http://www.aclweb.org/anthology/P17-1089) | [System](https://github.com/sriniiyer/nl2sql) |
| Template Baseline (Finegan-Dollak et al., 2018) | 1 | 0 | [Improving Text-to-SQL Evaluation Methodology](http://arxiv.org/abs/1806.09029) | [Data and System](https://github.com/jkkummerfeld/text2sql-data) |

IMDB - - 131 pertanyaan pengguna tentang Internet Movie Database [Yaghmazadeh et al., 2017](http://doi.org/10.1145/3133887). Ditingkatkan dan diubah menjadi gaya kanonik oleh [Finegan-Dollak et al., (2018)](http://arxiv.org/abs/1806.09029).

Contoh:

| Question | SQL query | 
| ------------- |  --- |
| What year was the movie " The Imitation Game " produced | `SELECT MOVIEalias0.RELEASE_YEAR FROM MOVIE AS MOVIEalias0 WHERE MOVIEalias0.TITLE = "The Imitation Game" ;` |

| Model           | Question Split | Query Split |  Paper / Source | Code |
| --------------- | ----- |  :-----:| --------------- | ---- |
| Seq2Seq with copying (Finegan-Dollak et al., 2018) | 26 | 9 | [Improving Text-to-SQL Evaluation Methodology](http://arxiv.org/abs/1806.09029) | [Data and System](https://github.com/jkkummerfeld/text2sql-data) |
| Iyer et al., (2017) | 10 | 4 | [Learning a neural semantic parser from user feedback](http://www.aclweb.org/anthology/P17-1089) | [System](https://github.com/sriniiyer/nl2sql) |
| Template Baseline (Finegan-Dollak et al., 2018) | 0 | 0 | [Improving Text-to-SQL Evaluation Methodology](http://arxiv.org/abs/1806.09029) | [Data and System](https://github.com/jkkummerfeld/text2sql-data) |

[Kembali ke README](../README.md)
