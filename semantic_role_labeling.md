# Semantic role labeling

Semantic role labeling semantik bertujuan untuk memodelkan struktur argumen-predikat suatu kalimat dan sering digambarkan sebagai menjawab "Siapa yang melakukan apa kepada siapa". Notasi BIO biasanya digunakan untuk pelabelan peran semantik.

Example:

| Housing | starts | are | expected | to | quicken | a | bit | from | August’s | pace | 
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | 
| B-ARG1 | I-ARG1 | O |  O  |  O  |   V  | B-ARG2 | I-ARG2 | B-ARG3 | I-ARG3 | I-ARG3 |    

### OntoNotes

Model biasanya dievaluasi pada [OntoNotes benchmark](http://www.aclweb.org/anthology/W13-3516) berdasarkan F1.

| Model           | F1  |  Paper / Source |
| ------------- | :-----:| --- |
| He et al., (2018) + ELMO | 85.5 | [Jointly Predicting Predicates and Arguments in Neural Semantic Role Labeling](http://aclweb.org/anthology/P18-2058) |
| (He et al., 2017) + ELMo (Peters et al., 2018) | 84.6 | [Deep contextualized word representations](https://arxiv.org/abs/1802.05365) |
| Tan et al. (2018) | 82.7 | [Deep Semantic Role Labeling with Self-Attention](https://arxiv.org/abs/1712.01586) |
| He et al. (2018) | 82.1 | [Jointly Predicting Predicates and Arguments in Neural Semantic Role Labeling](http://aclweb.org/anthology/P18-2058) | 
| He et al. (2017) | 81.7 | [Deep Semantic Role Labeling: What Works and What’s Next](http://aclweb.org/anthology/P17-1044) |

[Kembali ke README](../README.md)
