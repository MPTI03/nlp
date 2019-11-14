# Stance detection

Stance detection adalah adalah ekstraksi dari reaksi subjek terhadap klaim yang dibuat oleh aktor utama. Ini adalah bagian inti dari serangkaian pendekatan untuk penilaian berita palsu.

Contoh:

* Sumber: "Apel adalah buah paling enak yang pernah ada"
* Jawab: "Jelas tidak, Karena itu adalah Ruben dari Katz's"
* Pendirian: menolak

### RumourEval

[RumourEval 2017](http://www.aclweb.org/anthology/S/S17/S17-2006.pdf) telah digunakan untuk stance detection dalam bahasa inggris (subtugas A). Fitur itu memiliki beberapa cerita dan ribuan balasan: pasangan respon, dengan kereta, tes dan evaluasi membagi masing-masing berisi satu set narasi yang berbeda.


Dataset ini memuat koleksi [PHEME dari rumor dan sikap](http://journals.plos.org/plosone/article?id=10.1371/journal.pone.0150989), Dimana termasuk Jerman. 

| Model           | Accuracy  |  Paper / Source |
| ------------- | ----- | --- |
| Kochkina et al. 2017 | 0.784 | [Turing at SemEval-2017 Task 8: Sequential Approach to Rumour Stance Classification with Branch-LSTM](http://www.aclweb.org/anthology/S/S17/S17-2083.pdf)|
| Bahuleyan and Vechtomova 2017| 0.780 | [UWaterloo at SemEval-2017 Task 8: Detecting Stance towards Rumours with Topic Independent Features](http://www.aclweb.org/anthology/S/S17/S17-2080.pdf) |

[Go back to the README](../README.md)
