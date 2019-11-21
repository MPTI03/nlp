# Coreference resolution

Coreference resolution adalah tugas pengelompokan yang disebutkan dalam teks yang merujuk pada entitas dunia nyata yang sama.

Contoh:

```
               +-----------+
               |           |
I voted for Obama because he was most aligned with my values", she said.
 |                                                 |            |
 +-------------------------------------------------+------------+
```

"Aku", "Saya", "dia (pr)" dimiliki oleh cluster yang sama dan "Obama" dan "dia(LK)" dimiliki oleh cluster yang sama.

### CoNLL 2012

Eksperimen dilakukan pada data tugas bersama [CoNLL-2012 shared task](http://www.aclweb.org/anthology/W12-4501), yang menggunakan anotasi inti referensi OntoNotes.  Makalah melaporkan ketepatan, daya ingat, dan F1 dari metrik MUC, B3, dan CEAFφ4 menggunakan skrip evaluasi CoNLL-2012 resmi.  Metrik evaluasi utama adalah rata-rata F1 dari tiga metrik.

| Model           | Avg F1 |  Paper / Source | Code |
| ------------- | :-----:| --- | --- |
| (Lee et al., 2017)+ELMo (Peters et al., 2018)+coarse-to-fine & second-order inference (Lee et al., 2018) | 73.0 | [Higher-order Coreference Resolution with Coarse-to-fine Inference](http://aclweb.org/anthology/N18-2108) | [Official](https://github.com/kentonl/e2e-coref) |
| (Lee et al., 2017)+ELMo (Peters et al., 2018) | 70.4 | [Deep contextualized word representatIions](https://arxiv.org/abs/1802.05365) | |
| Lee et al. (2017) | 67.2 | [End-to-end Neural Coreference Resolution](https://arxiv.org/abs/1707.07045) | |

[Kembali ke README](../README.md)
