# Domain adaptation

## Sentiment analysis

### Multi-Domain Sentiment Dataset

[Multi-Domain Sentiment Dataset](https://www.cs.jhu.edu/~mdredze/datasets/sentiment/) Dataset Sentimen Multi-Domain adalah dataset evaluasi umum untuk adaptasi domain untuk analisis sentimen.  Ini berisi ulasan produk dari Amazon.com dari berbagai kategori produk, yang diperlakukan sebagai domain berbeda.  Ulasan berisi peringkat bintang (1 hingga 5 bintang) yang umumnya dikonversi menjadi label biner.  Model biasanya dievaluasi pada domain target yang berbeda dari domain sumber tempat mereka dilatih, sementara hanya memiliki akses ke contoh domain target yang tidak berlabel (adaptasi domain tanpa pengawasan).  Metrik evaluasi adalah akurasi dan skor dirata-rata di setiap domain.

| Model           | DVD | Books | Electronics | Kitchen | Average |  Paper / Source |
| ------------- | :-----:| :-----:| :-----:| :-----:| :-----:| --- |
| Multi-task tri-training (Ruder and Plank, 2018) | 78.14 | 74.86 | 81.45 | 82.14 | 79.15 | [Strong Baselines for Neural Semi-supervised Learning under Domain Shift](https://arxiv.org/abs/1804.09530) |
| Asymmetric tri-training (Saito et al., 2017) | 76.17 | 72.97 | 80.47 | 83.97 | 78.39 | [Asymmetric Tri-training for Unsupervised Domain Adaptation](https://arxiv.org/abs/1702.08400) |
| VFAE (Louizos et al., 2015) | 76.57 | 73.40 | 80.53 | 82.93 | 78.36 | [The Variational Fair Autoencoder](https://arxiv.org/abs/1511.00830) |
| DANN (Ganin et al., 2016) | 75.40 | 71.43 | 77.67 | 80.53 | 76.26 | [Domain-Adversarial Training of Neural Networks](https://arxiv.org/abs/1505.07818) |

[Go back to the README](../README.md)
