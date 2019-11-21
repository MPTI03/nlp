# Common sense

Common sense tasks dimaksudkan untuk meminta model melampaui pengenalan pola.  Sebaliknya, model tersebut harus menggunakan "common sense" atau pengetahuan dunia untuk membuat kesimpulan.

### Event2Mind

Event2Mind adalah kumpulan 25.000 frase acara crowdsourced yang mencakup beragam peristiwa dan situasi sehari-hari.  Mengingat suatu peristiwa yang dijelaskan dalam teks bentuk bebas pendek, sebuah model harus mempertimbangkan tentang maksud dan reaksi yang mungkin terjadi dari para peserta acara.  Model dievaluasi berdasarkan rata-rata lintas-entropi (lebih rendah lebih baik).


| Model           | Dev  | Test  |  Paper / Source | Code | 
| ------------- | :-----:| :-----:|--- | --- | 
| BiRNN 100d (Rashkin et al., 2018) | 4.25 | 4.22 | [Event2Mind: Commonsense Inference on Events, Intents, and Reactions](https://arxiv.org/abs/1805.06939) | |
| ConvNet (Rashkin et al., 2018) | 4.44 | 4.40 | [Event2Mind: Commonsense Inference on Events, Intents, and Reactions](https://arxiv.org/abs/1805.06939) | |

### SWAG

Situations with Adversarial Generations (SWAG) adalah dataset yang terdiri dari 113rb pertanyaan pilihan ganda tentang beragam spektrum situasi beralas.

| Model           | Dev  | Test  |  Paper / Source | Code | 
| ------------- | :-----:| :-----:|--- | --- | 
| BERT Large (Devlin et al., 2018) | 86.6 | 86.3 | [BERT: Pre-training of Deep Bidirectional Transformers for Language Understanding](https://arxiv.org/abs/1810.04805) | |
| BERT Base (Devlin et al., 2018) | 81.6 | - | [BERT: Pre-training of Deep Bidirectional Transformers for Language Understanding](https://arxiv.org/abs/1810.04805) | |
| ESIM + ELMo (Zellers et al., 2018) | 59.1 | 59.2 | [SWAG: A Large-Scale Adversarial Dataset for Grounded Commonsense Inference](http://arxiv.org/abs/1808.05326) |  |
| ESIM + GloVe (Zellers et al., 2018) | 51.9 | 52.7 | [SWAG: A Large-Scale Adversarial Dataset for Grounded Commonsense Inference](http://arxiv.org/abs/1808.05326) |  |

### Winograd Schema Challenge

[Winograd Schema Challenge](https://www.aaai.org/ocs/index.php/KR/KR12/paper/view/4492)
adalah dataset untuk penalaran akal sehat.  Ini mempekerjakan pertanyaan yang memerlukan resolusi anafora: sistem harus mengidentifikasi anteseden dari kata ganti ambigu dalam pernyataan.  Model dievaluasi berdasarkan akurasi.

Contoh :

Piala itu tidak muat didalam koper karena ‘itu’ terlalu besar. Apa yang terlalu besar? Jawaban 0 : piala itu. Jawaban 1 : koper itu.

| Model           | Score  |  Paper / Source | Code |
| ------------- | :-----:| --- | --- |
| Word-LM-partial (Trinh and Le, 2018) | 62.6 | [A Simple Method for Commonsense Reasoning](https://arxiv.org/abs/1806.02847) | |
| Char-LM-partial (Trinh and Le, 2018) | 57.9 | [A Simple Method for Commonsense Reasoning](https://arxiv.org/abs/1806.02847) | |
| USSM + Supervised DeepNet + KB (Liu et al., 2017) | 52.8 | [Combing Context and Commonsense Knowledge Through Neural Networks for Solving Winograd Schema Problems](https://aaai.org/ocs/index.php/SSS/SSS17/paper/view/15392) | |

### Winograd NLI (WNLI)

WNLI adalah pelonggaran Tantangan Skema Winograd yang diusulkan sebagai bagian dari  [GLUE benchmark](https://arxiv.org/abs/1804.07461) dan konversi ke format inferensi bahasa alami (NLI).  Tugasnya adalah untuk memprediksi apakah kalimat dengan ganti ganti disyaratkan oleh kalimat asli.  Sementara set pelatihan seimbang antara dua kelas (entailment dan bukan entailment), set tes tidak seimbang di antara mereka (35% entailment, 65% tidak entailment).  Baseline mayoritas dengan demikian adalah 65%, sedangkan untuk Tantangan Skema Winograd adalah 50% ([Liu et al., 2017](https://www.aaai.org/ocs/index.php/SSS/SSS17/paper/view/15392)). Yang terakhir lebih menantang.

Hasil tersedia di [GLUE leaderboard](https://gluebenchmark.com/leaderboard). Disini adalah bagian dari hasil model terbaru :

| Model           | Score  |  Paper / Source | Code |
| ------------- | :-----:| --- | --- |
| XLNet-Large (ensemble) (Yang et al., 2019) | 90.4 | [XLNet: Generalized Autoregressive Pretraining for Language Understanding](https://arxiv.org/pdf/1906.08237.pdf) | [Official](https://github.com/zihangdai/xlnet/) |
| MT-DNN-ensemble (Liu et al., 2019) | 89.0 | [Improving Multi-Task Deep Neural Networks via Knowledge Distillation for Natural Language Understanding](https://arxiv.org/pdf/1904.09482.pdf) | [Official](https://github.com/namisan/mt-dnn/) |
| Snorkel MeTaL(ensemble) (Ratner et al., 2018) | 65.1 | [Training Complex Models with Multi-Task Weak Supervision](https://arxiv.org/pdf/1810.02840.pdf) | [Official](https://github.com/HazyResearch/metal) |

### Visual Common Sense

Visual Commonsense Reasoning (VCR) adalah tugas baru dan dataset skala besar untuk pemahaman visual tingkat kognitif.  Dengan satu pandangan sekilas ke suatu gambar, kita dapat dengan mudah membayangkan dunia di luar piksel (mis. Bahwa [orang1] memesan pancake).  Meskipun tugas ini mudah bagi manusia, sangat sulit bagi sistem penglihatan saat ini, yang membutuhkan pengetahuan tingkat tinggi dan penalaran yang masuk akal tentang dunia.  Kami meresmikan tugas ini sebagai Penalaran Visual Commonsense.  Selain menjawab pertanyaan visual yang menantang yang diungkapkan dalam bahasa alami, seorang model harus memberikan alasan yang menjelaskan mengapa jawabannya benar.

| Model | Q->A  | QA->R  | Q->AR  | Paper / Source | Code |
| ------ | :-------:| :-------: | :-------:| ------ |  ------ | 
| Human Performance University of Washington (Zellers et al. '18) | 91.0 | 93.0 | 85.0 | [From Recognition to Cognition: Visual Commonsense Reasoning](https://arxiv.org/abs/1811.10830) | | 
| Recognition to Cognition Networks University of Washington | 65.1 | 67.3 | 44.0 | [From Recognition to Cognition: Visual Commonsense Reasoning](https://arxiv.org/abs/1811.10830) |  https://github.com/rowanz/r2c |
| BERT-Base Google AI Language (experiment by Rowan) | 53.9 | 64.5 | 35.0 | | https://github.com/google-research/bert |
| MLB Seoul National University (experiment by Rowan) | 46.2 | 36.8 | 17.2 | | https://github.com/jnhwkim/MulLowBiVQA |
| Random Performance | 25.0 | 25.0 | 6.2 | | | 

### ReCoRD

Reading Comprehension with Commonsense Reasoning Dataset (ReCoRD) adalah dataset pemahaman bacaan skala besar yang membutuhkan penalaran akal sehat.  ReCoRD terdiri dari kueri yang dihasilkan secara otomatis dari artikel berita CNN / Daily Mail;  jawaban untuk setiap permintaan adalah rentang teks dari bagian ringkasan dari berita terkait.  Tujuan ReCoRD adalah untuk mengevaluasi kemampuan akal sehat mesin dalam memahami membaca.  ReCoRD diucapkan sebagai [ˈrɛkərd] dan merupakan bagian dari [SuperGLUE benchmark](https://arxiv.org/pdf/1905.00537.pdf).

| Model | EM  | F1  | Paper / Source | Code |
| ------ | ------- | ------- | ------ |  ------ | 
| Human Performance Johns Hopkins University (Zhang et al. '18) | 91.31 | 91.69 | [ReCoRD: Bridging the Gap between Human and Machine Commonsense Reading Comprehension](https://arxiv.org/pdf/1810.12885.pdf) | | 
| RoBERTa (Facebook AI)  | 90.0 | 90.6 | [RoBERTa: A Robustly Optimized BERT Pretraining Approach](https://arxiv.org/pdf/1907.11692.pdf) | [Official](https://github.com/pytorch/fairseq/tree/master/examples/roberta) | 
| XLNet + MTL + Verifier (ensemble)  | 83.09 | 83.74 | | | 
| CSRLM (single model) | 81.78 | 82.58 | | |
