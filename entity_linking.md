# Entity Linking

## Task

Entity Linking (EL) adalah tugas mengenali (lih. [Named Entity Recognition](named_entity_recognition.md)) dan disambiguating (Named Entity Disambiguation) yang bernama entitas ke basis pengetahuan (mis. Wikidata, DBpedia, atau YAGO).  Kadang-kadang juga hanya dikenal sebagai Pengakuan Entitas dan Disambiguasi Bernama.

EL dapat dibagi menjadi dua kelas pendekatan:
* *End-to-End*: memproses sepotong teks untuk mengekstraksi entitas (yaitu Named Entity Recognition) dan kemudian menyatukan dua entitas yang diekstraksi ini dengan entri yang benar dalam basis pengetahuan yang diberikan (misalnya Wikidata, DBpedia, YAGO).
* *Disambiguation-Saja*: Sebaliknya  untuk pendekatan pertama, yang satu ini secara langsung mengambil entitas bernama standar emas sebagai input dan hanya memisahkan mereka ke entri yang benar dalam basis pengetahuan yang diberikan.

Example:

| Barack | Obama | was | born | in | Hawaï |
| --- | ---| --- | --- | --- | --- |
| https://en.wikipedia.org/wiki/Barack_Obama | https://en.wikipedia.org/wiki/Barack_Obama | O | O | O | https://en.wikipedia.org/wiki/Hawaii |

More in details can be found in this [survey](http://dbgroup.cs.tsinghua.edu.cn/wangjy/papers/TKDE14-entitylinking.pdf).

## Current SOTA
[Raiman][Raiman] saat ini di Penautan Entitas Lintas Bahasa.  Mereka membangun sistem tipe, dan menggunakannya untuk membatasi output dari jaringan saraf untuk menghormati struktur simbolik.  Mereka mencapai ini dengan merumuskan kembali masalah desain menjadi masalah integer campuran: membuat sistem tipe dan kemudian melatih jaringan saraf dengannya.  Mereka mengusulkan algoritma 2 langkah: 1) pencarian heuristik atau optimasi stokastik atas variabel diskrit yang menentukan sistem tipe yang diinformasikan oleh Oracle dan heuristik Learnability, 2) gradient descent agar sesuai dengan parameter classifier.  Mereka menerapkan DeepType untuk masalah Entity Linking pada tiga dataset standar (yaitu WikiDisamb30, CoNLL (YAGO), TAC KBP 2010) dan menemukan bahwa itu mengungguli semua solusi yang ada dengan margin lebar, termasuk pendekatan yang mengandalkan sistem tipe yang dirancang manusia.  atau embeddings entitas berbasis pembelajaran mendalam baru-baru ini, sementara secara eksplisit menggunakan informasi simbolik memungkinkannya mengintegrasikan entitas baru tanpa pelatihan ulang.

## Evaluation

### Metrics

#### Disambiguation-Only Approach

* Mikro-Presisi: Fraksi entitas bernama disambiguasi benar dalam corpus penuh. 
* Presisi Macro: Fraksi entitas yang disatukan secara benar, dirata-rata oleh dokumen.

#### End-to-End Approach

* Gerbil Micro-F1 - pencocokan kuat: skor mikro InKB F1 untuk tautan yang disambungkan dan disatukan dengan benar dalam corpus lengkap yang dihitung menggunakan platform Gerbil.  InKB berarti hanya menyebutkan dengan entitas KB yang valid yang digunakan untuk evaluasi.
* Gerbil Makro-F1 - kecocokan kuat: skor makro InKB F1 untuk tautan yang dikaitkan dan disatukan secara benar dalam korpus lengkap sebagaimana dikomputasi menggunakan platform Gerbil.  InKB berarti hanya menyebutkan dengan entitas KB yang valid yang digunakan untuk evaluasi.

### Datasets

#### AIDA CoNLL-YAGO Dataset

[AIDA CoNLL-YAGO][AIDACoNLLYAGO] Dataset dari [[Hoffart]](http://www.aclweb.org/anthology/D11-1072) berisi penugasan entitas untuk menyebutkan entitas yang disebutkan yang dianotasikan untuk [[CoNLL]](http://www.aclweb.org/anthology/W03-0419.pdf) tugas NER 2003 asli. Entitas diidentifikasi oleh [YAGO2](http://yago-knowledge.org/) Entitas diidentifikasi, oleh [Wikipedia URL](https://en.wikipedia.org/), atau dengan [Pertengahan Freebase](http://wiki.freebase.com/wiki/Machine_ID).

##### Disambiguation-Only Models
   
|  Paper / Source | Micro-Precision | Macro-Precision | Paper / Source | Code | 
| ------------- | :-----:| :----: | :----: | --- |
| Raiman et al. (2018) | 94.88 | - | [DeepType: Multilingual Entity Linking by Neural Type System Evolution](https://arxiv.org/pdf/1802.01021.pdf) | [Official](https://github.com/openai/deeptype) |
| Sil et al. (2018) | 94.0 | - | [Neural Cross-Lingual Entity Linking](https://www.aaai.org/ocs/index.php/AAAI/AAAI18/paper/view/16501/16101) | |
| Radhakrishnan et al. (2018) | 93.0 | 93.7 | [ELDEN: Improved Entity Linking using Densified Knowledge Graphs](http://aclweb.org/anthology/N18-1167) | |
| Le et al. (2018) | 93.07 | - | [Improving Entity Linking by Modeling Latent Relations between Mentions](http://aclweb.org/anthology/P18-1148) |[Official](https://github.com/lephong/mulrel-nel)
| Ganea and Hofmann (2017) | 92.22 | - | [Deep Joint Entity Disambiguation with Local Neural Attention](https://www.aclweb.org/anthology/D17-1277) | [Link](https://github.com/dalab/deep-ed) |
| Hoffart et al. (2011) | 82.29 | 82.02 | [Robust Disambiguation of Named Entities in Text](http://www.aclweb.org/anthology/D11-1072) |  |

##### End-to-End Models
   
|  Paper / Source | Micro-F1-strong | Macro-F1-strong | Paper / Source | Code | 
| ------------- | :-----:| :----: | :----: | --- |
| Kolitsas et al. (2018) | 86.6 | 89.4 | [End-to-End Neural Entity Linking](https://arxiv.org/pdf/1808.07699.pdf) | [Official](https://github.com/dalab/end2end_neural_el) |
| Piccinno et al. (2014) | 69.32 | 72.8 | [From TagME to WAT: a new entity annotator](https://dl.acm.org/citation.cfm?id=2634350) | |
| Hoffart et al. (2011) | 68.8 | 72.4 | [Robust Disambiguation of Named Entities in Text](http://www.aclweb.org/anthology/D11-1072) | |

#### TAC KBP English Entity Linking Comprehensive and Evaluation Data 2010 

Jalur Knowledge Base Population (KBP) di [TAC 2010](https://tac.nist.gov/2010) akan mengeksplorasi ekstraksi informasi tentang entitas dengan referensi ke sumber pengetahuan eksternal.  Menggunakan skema dasar untuk orang, organisasi, dan lokasi, simpul dalam ontologi harus dibuat dan diisi menggunakan informasi tidak terstruktur yang ditemukan dalam teks. Kumpulan [Wikipedia Infoboxes](http://en.wikipedia.org/wiki/Help:Infobox) akan berfungsi sebagai representasi pengetahuan awal yang belum sempurna. Anda dapat mengunduh dataset dari [LDC](https://www.ldc.upenn.edu/) atau [disini](https://github.com/ChrisLeeJ/TAC_KBP_English_EL_2010).

##### Disambiguation-Only Models

|  Paper / Source | Micro-Precision | Macro-Precision | Paper / Source | Code | 
| ------------- | :-----:| :----: | :----: | --- |
| Raiman et al. (2018) | 90.85 | - | [DeepType: Multilingual Entity Linking by Neural Type System Evolution](https://arxiv.org/pdf/1802.01021.pdf) | [Official](https://github.com/openai/deeptype) |
| Sil et al. (2018) | 87.4 | - | [Neural Cross-Lingual Entity Linking](https://www.aaai.org/ocs/index.php/AAAI/AAAI18/paper/view/16501/16101) |      |
| Yamada et al. (2016) | 85.2 | - | [Joint Learning of the Embedding of Words and Entities for Named Entity Disambiguation](https://arxiv.org/pdf/1601.01343.pdf) |      |

### Platforms

Mengevaluasi sistem Menghubungkan Entitas dengan cara yang memungkinkan untuk membandingkan langsung kinerja bisa sulit.  Definisi tepat dari anotasi "benar" bisa agak subjektif dan mudah untuk membuat kesalahan.  Untuk memberikan contoh sederhana, mengingat bentuk permukaan input "Tom Waits", dataset evaluasi mungkin merekam sumber daya dbpedia `http://dbpedia.org/resource/Tom_Waits` sebagai referensi yang benar.  Namun sistem anotasi yang mengembalikan referensi ke `http://dbpedia.org/resource/PEHDTSCKJBMA` secara teknis memberikan anotasi yang sesuai karena sumber daya ini merupakan redirect ke `http://dbpedia.org/resource/Tom_Waits`. Atau jika mengevaluasi sistem EL End-to-End, maka keakuratan sehubungan dengan batas kata harus dipertimbangkan misalnya.  jika suatu sistem hanya membubuhi keterangan **"Obama"** dengan URI `http://dbpedia.org/resource/Barack_Obama` di permukaan berupa **"Barack Obama"**, lalu apakah sistem itu benar atau salah dalam anotasinya?

 Lebih jauh, kinerja sistem EL dapat sangat dipengaruhi oleh sifat konten tempat evaluasi dilakukan, mis.  konten berita versus Tweet.  Oleh karena itu membandingkan kinerja relatif dari dua sistem EL yang telah diuji pada dua korpora yang berbeda dapat keliru.  Daripada membiarkan titik-titik subyektif kecil ini masuk ke dalam evaluasi sistem EL, lebih baik menggunakan platform evaluasi standar di mana asumsi-asumsi ini diketahui dan dibuat eksplisit dalam konfigurasi percobaan.

[GERBIL][GERBIL], dikembangkan oleh [AKSW][AKSW] adalah platform evaluasi yang didasarkan pada [BAT framework][Cornolti]. Ini mendefinisikan sejumlah percobaan standar yang dapat dijalankan untuk setiap layanan EL yang diberikan.  Jenis-jenis eksperimen ini menentukan seberapa ketat evaluasi sehubungan dengan ukuran-ukuran seperti penyelarasan batas kata dan juga menentukan seberapa banyak tanggung jawab yang diberikan pada layanan EL sehubungan dengan Pengakuan Entitas, dll. GERBIL menyelenggarakan 38 set data evaluasi yang diperoleh dari berbagai EL berbeda.  tantangan.  Saat ini ia juga memiliki kaitan untuk 17 layanan EL yang berbeda yang dapat dimasukkan dalam percobaan.

GERBIL dapat digunakan untuk menguji sistem EL anda sendiri dengan mengunduh kode sumber dan menggunakan GERBAL secara lokal, atau dengan membuat layanan anda tersedia di web dan memberi GERBIL tautan ke titik akhir API anda. Satu-satunya syarat adalah bahwa API anda harus menerima input dan merespons dengan output dalam format [NIF][NIF]. Dimungkinkan juga untuk mengunggah set data evaluasi anda sendiri jika anda ingin menguji layanan ini pada konten anda sendiri. Perhatikan bahwa dataset juga harus dalam format NIF. [DBpedia Spotlight evaluation dataset][SpotlightEvaluation] adalah contoh yang baik tentang bagaimana menyusun konten anda.

GERBIL memang memiliki sejumlah kekurangan, yang paling menonjol adalah:
1. Tidak ada cara untuk melihat anotasi yang dikembalikan oleh setiap sistem yang Anda uji.  Ini ditangani secara internal oleh GERBIL dan kemudian dibuang.  Ini dapat membuat sulit untuk menentukan sumber kesalahan dengan sistem EL.
2. Tidak ada cara untuk mengamati daftar kandidat yang dipertimbangkan untuk setiap bentuk permukaan.  Ini, tentu saja, masalah standar dengan EL API pihak ketiga mana pun, tetapi jika seseorang melakukan penyelidikan terperinci terhadap kinerja sistem EL, penting untuk mengetahui apakah sumber kesalahannya adalah algoritma EL itu sendiri, atau  proses pengambilan kandidat yang gagal mengidentifikasi rujukan yang benar sebagai kandidat.  Ini terdaftar sebagai pertimbangan penting oleh Hachey et al. [Hachey et al][Hachey].

Namun demikian, GERBIL adalah sumber yang bagus untuk menstandarisasi bagaimana sistem EL diuji dan dibandingkan.  Ini juga merupakan titik awal yang baik bagi siapa saja yang baru mengenal Entity Linking karena mengandung tautan ke berbagai sumber daya EL.  Untuk informasi lebih lanjut, lihat makalah penelitian oleh [[Usbeck]](http://svn.aksw.org/papers/2015/WWW_GERBIL/public.pdf).

## References

[Hoffart] Johannes Hoffart, Mohamed Amir Yosef, Ilaria Bordino, Hagen Fürstenau, Manfred Pinkal, Marc Spaniol, Bilyana Taneva, Stefan Thater, and Gerhard Weikum. Robust Disambiguation of Named Entities in Text. EMNLP 2011. http://www.aclweb.org/anthology/D11-1072

[CoNLL] Erik F Tjong Kim Sang and Fien De Meulder. Introduction to the CoNLL-2003 Shared Task: Language-Independent Named Entity Recognition. CoNLL 2003. http://www.aclweb.org/anthology/W03-0419.pdf

[Usbeck] Usbeck et al. GERBIL - General Entity Annotator Benchmarking Framework. WWW 2015. http://svn.aksw.org/papers/2015/WWW_GERBIL/public.pdf

[Go back to the README](../README.md)

[Sil]: https://www.aaai.org/ocs/index.php/AAAI/AAAI18/paper/view/16501/16101 "Neural Cross-Lingual Entity Linking"
[Shen]: http://dbgroup.cs.tsinghua.edu.cn/wangjy/papers/TKDE14-entitylinking.pdf "Entity Linking with a Knowledge Base: Issues, Techniques, and Solutions"
[AIDACoNLLYAGO]: https://www.mpi-inf.mpg.de/departments/databases-and-information-systems/research/yago-naga/aida/downloads/ "AIDA CoNLL-YAGO Dataset"
[YAGO2]: http://yago-knowledge.org/ "YAGO2"
[Wikipedia]: https://en.wikipedia.org/ "Wikipedia"
[Freebase]: http://wiki.freebase.com/wiki/Machine_ID "Freebase"
[Radhakrishnan]: http://aclweb.org/anthology/N18-1167 "ELDEN: Improved Entity Linking using Densified Knowledge Graphs"
[Le]: https://arxiv.org/abs/1804.10637
[NIF]: http://persistence.uni-leipzig.org/nlp2rdf/ "NLP Interchange Formt"
[SpotlightEvaluation]: http://apps.yovisto.com/labs/ner-benchmarks/data/dbpedia-spotlight-nif.ttl "GERBIL DBpedia Spotlight Dataset"
[Cornolti]: https://static.googleusercontent.com/media/research.google.com/en//pubs/archive/40749.pdf "A Framework for Benchmarking Entity-Annotation Systems"
[GERBIL]: http://aksw.org/Projects/GERBIL.html "General Entity Annotator Benchmarking framework"
[AKSW]: http://aksw.org/About.html "Agile Knowledge Engineering and Semantic Web"
[Hachey]: http://benhachey.info/pubs/hachey-aij12-evaluating.pdf "Evaluating Entity Linking with Wikipedia"
[Raiman]: https://arxiv.org/pdf/1802.01021.pdf "DeepType: Multilingual Entity Linking by Neural Type System Evolution"
