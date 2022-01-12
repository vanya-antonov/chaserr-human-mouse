# Для отчета

## 4.1.1. Должен быть подготовлен список генов мыши, с которыми потенциально может связываться нкРНК Chaserr с помощью разработанной в лаборатории программы предсказания РНК-РНК взаимодействий ASSA.

**Было получено [1457 уникальных генов](output/single_deg_promoters_significant.tsv):**


* Взяли результаты мышиного RNA-seq Улицкого (табличка [data/0923.xlsx](data/0923.xlsx), столбец "mEF Chaserr-/-"). Общее кол-во ДЕ-генов (adj_pvalue < 0.05 и доп фильтры) было 2455 (СПИСОК).

* Для этих генов были получены все транскрипты по аннотации FANTOM5 (2244 ДЕ-генов имели хотя бы один транскрипт -- СПИСОК) -- **тут используется версия генома mm9**, тк нет аннотации FANTOM для mm10.

* Для каждого из 2244 генов взяли все промотеры (общее кол-во  промотеров  9911 -- СПИСОК) и к каждому промотеру добавили +1kb downstream и получили их геномные посл-ти (длина этих посл-тей будет от 1кб до 1.3 кб -- FASTA FILE!) -- **из генома mm9**!

* Запускаем ASSA для Chaserr-mouse (ENSMUST00000184554.8) против 9911 посл-тей, полученных выше.

* Для каждого гена выбрали один промотер с самым сильным p-value ASSA (получился 2244 промотера -- [output/single_deg_promoters.tsv](output/single_deg_promoters.tsv))

* И из этого списка 2244 промотеров были выбраны 1457 случаев, где ASSA p-value < 0.01. Это и есть список генов мыши, с которыми потенциально может связываться нкРНК Chaserr -- [output/single_deg_promoters_significant.tsv](output/single_deg_promoters_significant.tsv).

## 4.1.2. Должен быть выполнен подробный анализ предсказанных участков связывания нкРНК Chaserr человека и ее мышиного гомолога, в частности должен быть построен профиль частоты взаимодействия Chaserr с таргетными транскриптами (для человека и мыши)

Человек:
![s](img/4.1.2_CHASERR_human_profile.png)

Мышь:
![img/4.1.2_CHASERR_mouse_profile.png](img/4.1.2_CHASERR_mouse_profile.png)

## 4.1.3. Должны быть  выделены общие для большинства таргетных генов нкРНК Chaserr регионы взаимодействия (для человека и мыши)

<!-- **ПЕРЕИМЕНОВАТЬ TSS в "promoter start", TES => "TSS"** -->

<!-- ![image](https://user-images.githubusercontent.com/44672274/148937560-3f7e0ac1-3a49-4930-8174-0df2ada9a507.png) -->

| human ASO_07 | human ASO_10 | mouse RNA-seq |
|:---:|:---:|:---:|
|![3-deepTools-1](img/4.1.3_deeptools-1.png)|![3-deepTools-2](img/4.1.3_deeptools-2.png)|![3-deepTools-3](img/4.1.3_deeptools-3.png)|

## 4.1.4. Должен быть проведен анализ обогащения GO и регуляторными путями набора таргетных генов нкРНК Chaserr (отдельно для мыши и человека).
Человек - https://github.com/vanya-antonov/article_assa_and_f6/blob/master/data/2_pvalues.co.txt

Списки генов (названия генов в столбик):
* Человек ASO-7 -- есть 2667 ДЕ-промотеров + ASSA (пересечение HGD.drawn_balls и HGD.red_balls) =>  XXX уникальных генов
* Человек ASO-10 -- есть 1668 ДЕ-промотеров + ASSA (пересечение HGD.drawn_balls и HGD.red_balls) => XXX уникальных генов
* Мышь RNA-seq 1457 уникальных генов

Сам GO анализ сделан с помощью PANTHER DB.

## 4.1.5. Должна протестирована возможность взаимодействия Chaserr с другими хеликазами, для этого с использованием публичных данных ChIP-seq должен быть проведен анализ ко-локализации потенциально таргетных участков с участками локализации других хеликаз
![5-Heatmap](img/4.1.5_heatmap.png)




# Детали работы

## 2.1. Ортологи

Ссылка на [colab ноутбук](https://colab.research.google.com/drive/1JS8iUqV0oUH4CZuBMXifwLFpeBQ_pJkW?usp=sharing).

## 2.2. Профили взаимодействия (human)

Ссылка на [colab ноутбук](https://colab.research.google.com/drive/1wVug5xCxIxlLOYn_ZnoqmVdEtorR4Pvi?usp=sharing).

### Входные данные

- [data/chaserr_human.fna](data/chaserr_human.fna) -- последовательность CHASERR из статьи
- [data/ASO_G0272888_AD_07.chaserr_human.mix.assa](data/ASO_G0272888_AD_07.chaserr_human.mix.assa) (6,518)
- [data/ASO_G0272888_AD_07.chaserr_human.mix.sites](data/ASO_G0272888_AD_07.chaserr_human.mix.sites) (177,417)
- [data/ASO_G0272888_AD_10.chaserr_human.mix.assa](data/ASO_G0272888_AD_10.chaserr_human.mix.assa) (4,204)
- [data/ASO_G0272888_AD_10.chaserr_human.mix.sites](data/ASO_G0272888_AD_10.chaserr_human.mix.sites) (115,214)

### Результат

![s](img/4.1.2_CHASERR_human_profile.png)

## 2.3. Профили взаимодействия (mouse)

Ссылка на [colab ноутбук](https://colab.research.google.com/drive/10eXPl9n7Zq4NoPhgvpcJpXsnI8SSz1wL?usp=sharing).

### Входные данные

- [data/mm9_chaserr.fna](data/mm9_chaserr.fna) - ENSMUST00000184554.8 Chaserr
- [data/0923.xlsx](data/0923.xlsx) - результаты DE-анализа
- [mm9.cage_peak_phase1and2combined_ann.txt.gz](https://fantom.gsc.riken.jp/5/datafiles/latest/extra/CAGE_peaks/mm9.cage_peak_phase1and2combined_ann.txt.gz) - Fantom promoter data (mm9)

### Результаты

- [chaserr_deg_promoters_1kbp.assa](http://himorna.fbras.ru/~fed/assa_results/chaserr_deg_promoters_1kbp.assa) (11,618)
- [chaserr_deg_promoters_1kbp.all_sites.assa](http://himorna.fbras.ru/~fed/assa_results/chaserr_deg_promoters_1kbp.all_sites.assa) (99,780)
- [output/single_deg_promoters.tsv](output/single_deg_promoters.tsv) (2,244) - список промотеров
- [output/single_deg_promoters_significant.tsv](output/single_deg_promoters_significant.tsv) (1,457) - список значимых промотеров

![img/4.1.2_CHASERR_mouse_profile.png](img/4.1.2_CHASERR_mouse_profile.png)

## 3. Общие регионы взаимодействия для человека

Ссылка на [colab ноутбук](https://colab.research.google.com/drive/1E3zFJ8qXbL-afAKd6N00CZPuBDCJs2y9?usp=sharing).

### Входные данные

- Данные для человека
    - ENST00000556895.T0
    - [article_assa_and_f6/data/ASO_G0272888_AD_07/mix.assa](https://github.com/vanya-antonov/article_assa_and_f6/blob/master/data/ASO_G0272888_AD_07/mix.assa) (6,518)
    - [article_assa_and_f6/data/ASO_G0272888_AD_07/mix.sites](https://github.com/vanya-antonov/article_assa_and_f6/blob/master/data/ASO_G0272888_AD_07/mix.sites) (167,580)
    - [article_assa_and_f6/data/ASO_G0272888_AD_07/HGD.red_balls](https://github.com/vanya-antonov/article_assa_and_f6/blob/master/data/ASO_G0272888_AD_07/HGD.red_balls) (3,258)
    - [article_assa_and_f6/data/ASO_G0272888_AD_10/mix.assa](https://github.com/vanya-antonov/article_assa_and_f6/blob/master/data/ASO_G0272888_AD_10/mix.assa) (4,204)
    - [article_assa_and_f6/data/ASO_G0272888_AD_10/mix.sites](https://github.com/vanya-antonov/article_assa_and_f6/blob/master/data/ASO_G0272888_AD_10/mix.sites) (108,817)
    - [article_assa_and_f6/data/ASO_G0272888_AD_10/HGD.red_balls](https://github.com/vanya-antonov/article_assa_and_f6/blob/master/data/ASO_G0272888_AD_10/HGD.red_balls) (2,102)
- Данные для мыши
    - [data/mm9_chaserr.fna](data/mm9_chaserr.fna) - ENSMUST00000184554.8 Chaserr
    - [chaserr_deg_promoters_1kbp.assa](http://himorna.fbras.ru/~fed/assa_results/chaserr_deg_promoters_1kbp.assa) (11,618)
    - [chaserr_deg_promoters_1kbp.all_sites.assa](http://himorna.fbras.ru/~fed/assa_results/chaserr_deg_promoters_1kbp.all_sites.assa) (99,780)
    - [output/single_deg_promoters_significant.tsv](output/single_deg_promoters_significant.tsv) (1,457)


### Результаты

Нужно еще раз пересчитать для мыши, т.к. в ASSA записалось 140 очень коротких промотеров, которые здесь не учитываются.

| human ASO_07 | human ASO_10 | mouse RNA-seq |
|:---:|:---:|:---:|
|![3-deepTools-1](img/4.1.3_deeptools-1.png)|![3-deepTools-2](img/4.1.3_deeptools-2.png)|![3-deepTools-3](img/4.1.3_deeptools-3.png)|

## 5. Взаимодействие Chaserr с другими хеликазами

Ссылка на [colab ноутбук](https://colab.research.google.com/drive/1M5hKI0m_XLca6Cqx5VmaWthlnnRgQwbJ?usp=sharing).

### Входные данные

- [19 ChIP-seq экспериментов](https://www.encodeproject.org/search/?type=Experiment&replicates.library.biosample.donor.organism.scientific_name=Homo+sapiens&assay_title=TF+ChIP-seq&status=released&biosample_ontology.classification=cell+line&target.label=CHD2&target.label=CHD1&target.label=CHD4&target.label=CHD7&assembly=GRCh38&files.file_type=bed+narrowPeak) из ENCODE (hg38)
- Данные по экспрессии для промотеров
    - [data/ASO_G0272888_AD_07.oligo_DE_Summary_promoter.tsv](data/ASO_G0272888_AD_07.oligo_DE_Summary_promoter.tsv) (27,441)
    - [data/ASO_G0272888_AD_10.oligo_DE_Summary_promoter.tsv](data/ASO_G0272888_AD_10.oligo_DE_Summary_promoter.tsv) (28,123)
- Данные по таргетным промотерам
    - [article_assa_and_f6/blob/master/data/ASO_G0272888_AD_07.DE_Summary](https://github.com/vanya-antonov/article_assa_and_f6/blob/master/data/ASO_G0272888_AD_07.DE_Summary) (3,259)
    - [article_assa_and_f6/blob/master/data/ASO_G0272888_AD_10.DE_Summary](https://github.com/vanya-antonov/article_assa_and_f6/blob/master/data/ASO_G0272888_AD_10.DE_Summary) (2,102)

### Результат

![5-Heatmap](img/4.1.5_heatmap.png)
