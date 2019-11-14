# Temporal Processing

## Document Dating (Time-stamping)

Document Dating adalah masalah memprediksi tanggal dokumen secara otomatis berdasarkan kontennya. Tanggal dokumen, juga disebut sebagai Document Creation Time (DCT), merupakan inti dari banyak tugas penting, seperti, pencarian informasi, penalaran temporal, peringkasan teks, pendeteksian peristiwa, dan analisis teks historis, antara lain.

Misalnya, dalam dokumen berikut, tahun pembuatan yang benar adalah 1999. Ini dapat disimpulkan dengan adanya istilah 1995 dan Empat tahun sesudahnya.

*Swiss mengadopsi bentuk perpajakan pada tahun 1995. Konsesi ini disetujui oleh pemerintah September lalu. Empat tahun kemudian, IOC….*

### Datasets 

|                 Datasets                 | # Docs | Start Year | End Year |
| :--------------------------------------: | :----: | :--------: | :------: |
| [APW](https://drive.google.com/file/d/1tll04ZBooB3Mohm6It-v8MBcjMCC3Y1w/view) |  675k  |    1995    |   2010   |
| [NYT](https://drive.google.com/file/d/1wqQRFeA1ESAOJqrwUNakfa77n_S9cmBi/view?usp=sharing) |  647k  |    1987    |   1996   |

### Comparison on year level granularity:

|                                        | APW Dataset | NYT Dataset | Paper/Source                             |
| -------------------------------------- | :---------: | :---------: | ---------------------------------------- |
| NeuralDater (Vashishth et. al, 2018)   |    64.1     |    58.9     | [Document Dating using Graph Convolution Networks](https://github.com/malllabiisc/NeuralDater) |
| Chambers (2012)                        |    52.5     |    42.3     | [Labeling Documents with Timestamps: Learning from their Time Expressions](https://pdfs.semanticscholar.org/87af/a0cb4f829ce861da0c721ca666d48a62c404.pdf) |
| BurstySimDater (Kotsakos et. al, 2014) |    45.9     |    38.5     | [A Burstiness-aware Approach for Document Dating](https://www.idi.ntnu.no/~noervaag/papers/SIGIR2014short.pdf) |


## Temporal Information Extraction

Temporal information extraction adalah identifikasi chunks / token yang sesuai dengan interval waktu, dan ekstraksi dan penentuan hubungan temporal antara mereka. Entitas yang diekstraksi dapat berupa ekspresi temporal (timexes), eventualities (peristiwa), atau sinyal tambahan yang mendukung interpretasi entitas atau relasi. Relasi dapat berupa temporal link (tlinks), menggambarkan urutan peristiwa dan waktu, atau tautan bawahan (slinks) yang menggambarkan modalitas dan aktivitas subordinatif lainnya, atau tautan aspek (alinks) di sekitar berbagai pengaruh yang dimiliki aspek pada struktur acara.


Skema markup yang digunakan untuk ekstraksi informasi temporal dijelaskan dengan baik dalam standar ISO-TimeML, dan juga aktif [www.timeml.org](http://www.timeml.org).

```
<?xml version="1.0" ?>

<TimeML xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="http://timeml.org/timeMLdocs/TimeML_1.2.1.xsd">
<TEXT>


 PRI20001020.2000.0127 
 NEWS STORY 
 <TIMEX3 tid="t0" type="TIME" value="2000-10-20T20:02:07.85">10/20/2000 20:02:07.85</TIMEX3> 


 The Navy has changed its account of the attack on the USS Cole in Yemen.
 Officials <TIMEX3 tid="t1" type="DATE" value="PRESENT_REF" temporalFunction="true" anchorTimeID="t0">now</TIMEX3> say the ship was hit <TIMEX3 tid="t2" type="DURATION" value="PT2H">nearly two hours </TIMEX3>after it had docked.
 Initially the Navy said the explosion occurred while several boats were helping
 the ship to tie up. The change raises new questions about how the attackers
 were able to get past the Navy security.


 <TIMEX3 tid="t3" type="TIME" value="2000-10-20T20:02:28.05">10/20/2000 20:02:28.05</TIMEX3> 



<TLINK timeID="t2" relatedToTime="t0" relType="BEFORE"/>
</TEXT>
</TimeML>
```

Untuk menghindari bocornya pengetahuan tentang struktur temporal, latih, dev, dan uji split harus dilakukan pada tingkat dokumen untuk ekstraksi informasi temporal.

### TimeBank

TimeBank, berdasarkan pada standar TIMEX3 yang disematkan dalam ISO-TimeML, adalah kumpulan benchmark yang berisi 64 ribu token berita bahasa Inggris, dan dijelaskan untuk semua laporan ISO-TimeML - termasuk ekspresi temporal. TimeBank didistribusikan secara bebas oleh LDC: [TimeBank 1.2](https://catalog.ldc.upenn.edu/LDC2006T08)


Evaluasi adalah untuk entitas chunking dan anotasi atribut, serta akurasi hubungan temporal, biasanya diukur dengan F1 -- walaupun metrik ini tidak sensitif terhadap inkonsistensi atau kemenangan bebas dari induksi logika interval selama seluruh rangkaian.


| Model           | F1 score  |  Paper / Source |
| ------------- | :-----:| --- |
| Catena | 0.511 |  [CATENA: CAusal and TEmporal relation extraction from NAtural language texts](http://www.aclweb.org/anthology/C16-1007) |
| CAEVO | 0.507 | [Dense Event Ordering with a Multi-Pass Architecture](https://www.transacl.org/ojs/index.php/tacl/article/download/255/50) | 

### TempEval-3

TempEval-3 korpus disertai [TempEval-3](http://www.aclweb.org/anthology/S13-2001) Tugas SemEval-3 yang dibagikan pada 2013. Ini menggunakan metrik berbasis waktu untuk menilai struktur hubungan temporal. Corpus ini segar dan agak lebih bervariasi daripada TimeBank, meskipun jauh lebih kecil. [TempEval-3 data](https://www.cs.york.ac.uk/semeval-2013/task1/index.php%3Fid=data.html)

| Model           | Temporal awareness  |  Paper / Source |
| ------------- | :-----:| --- |
| Ning et al. | 67.2 | [A Structured Learning Approach to Temporal Relation Extraction](http://www.aclweb.org/anthology/D17-1108) | 
| ClearTK | 30.98 | [Cleartk-timeml: A minimalist approach to tempeval 2013](http://www.aclweb.org/anthology/S13-2002) |

## Timex normalisation

Temporal expression normalisation adalah landasan leksikalisasi waktu ke tanggal kalender atau representasi temporal formal lainnya.

Contoh:
<TIMEX3 tid="t0" type="TIME" value="2000-10-18T21:01:00.65">10/18/2000 21:01:00.65</TIMEX3>
Lusinan warga palestina terluka dalam bentrokan yang tersebar di Tepi Barat dan Jalur Gaza, <TIMEX3 tid="t1" type="Tanggal" value="2000-10-18" temporalFunction="benar" anchorTimeID="t0">Rabu</TIMEX3>,
kendati ada perjanjian gencatan senjata Sharm el-Sheikh. 

Chuck Rich melaporkan di entertaiment <TIMEX3 tid="t11" type="SET" value="XXXX-WXX-7">setiap hari sabtu</TIMEX3>

### TimeBank

TimeBank, berdasarkan pada standar TIMEX3 yang disematkan dalam ISO-TimeML, adalah kumpulan benchmark yang berisi 64 ribu token berita bahasa Inggris, dan dijelaskan untuk semua laporan ISO-TimeML - termasuk ekspresi temporal. TimeBank didistribusikan secara bebas oleh  LDC: [TimeBank 1.2](https://catalog.ldc.upenn.edu/LDC2006T08)

| Model           | F1 score  |  Paper / Source |
| ------------- | :-----:| --- |
| TIMEN | 0.89 | [TIMEN: An Open Temporal Expression Normalisation Resource](http://aclweb.org/anthology/L12-1015) | 
| HeidelTime | 0.876 | [A baseline temporal tagger for all languages](http://aclweb.org/anthology/D15-1063) |

### PNT

The [Parsing Time Normalizations corpus](https://github.com/bethard/anafora-annotations/releases) dalam [SCATE](http://www.lrec-conf.org/proceedings/lrec2016/pdf/288_Paper.pdf) memungkinkan representasi dari variasi ekspresi waktu yang lebih luas daripada pendekatan sebelumnya. Korpus ini dirilis dengan [SemEval 2018 Task 6](http://aclweb.org/anthology/S18-1011).

| Model           | F1 score  |  Paper / Source |
| ------------- | :-----:| --- |
| Laparra et al. 2018 | 0.764 | [From Characters to Time Intervals: New Paradigms for Evaluation and Neural Parsing of Time Normalizations](http://aclweb.org/anthology/Q18-1025) |
| HeidelTime | 0.74 | [A baseline temporal tagger for all languages](http://aclweb.org/anthology/D15-1063) |
| Chrono | 0.70 | [Chrono at SemEval-2018 task 6: A system for normalizing temporal expressions](http://aclweb.org/anthology/S18-1012) | 


[Go back to the README](../README.md)
