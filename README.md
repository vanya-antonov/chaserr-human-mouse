# chaserr-human-mouse

## 5. Взаимодействие Chaserr с другими хеликазами

Ссылка на [colab ноутбук](https://colab.research.google.com/drive/1M5hKI0m_XLca6Cqx5VmaWthlnnRgQwbJ?usp=sharing)

### Входные данные

- [19 ChIP-seq экспериментов](https://www.encodeproject.org/search/?type=Experiment&replicates.library.biosample.donor.organism.scientific_name=Homo+sapiens&assay_title=TF+ChIP-seq&status=released&biosample_ontology.classification=cell+line&target.label=CHD2&target.label=CHD1&target.label=CHD4&target.label=CHD7&assembly=GRCh38&files.file_type=bed+narrowPeak) из ENCODE
- Данные по экспрессии для промотеров [ASO_07](data/ASO_G0272888_AD_07.oligo_DE_Summary_promoter.tsv) и [ASO_10](data/ASO_G0272888_AD_10.oligo_DE_Summary_promoter.tsv)
- Данные по таргетным промотерам [ASO_07](https://github.com/vanya-antonov/article_assa_and_f6/blob/master/data/ASO_G0272888_AD_07.DE_Summary) и [ASO_10](https://github.com/vanya-antonov/article_assa_and_f6/blob/master/data/ASO_G0272888_AD_10.DE_Summary)

### Результаты

![Heatmap](img/4.1.5_heatmap.png)
