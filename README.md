# Индивидуальная часть 
## Белок PHF8
### Функции белка:
Гистонлизиндеметилаза с селективностью в отношении ди- и монометильных состояний, которая играет ключевую роль в прогрессировании клеточного цикла, транскрипции рДНК и развитии мозга.
### Статьи:
* [PHF8 is a histone H3K9me2 demethylase regulating rRNA synthesis](https://www.nature.com/articles/cr201075?error=cookies_not_supported&code=b0c45e6c-072a-48c5-91e3-96e3b762f62e)
* [Elevated expression of histone demethylase PHF8 associates with adverse prognosis in patients of laryngeal and hypopharyngeal squamous cell carcinoma](https://www.futuremedicine.com/doi/10.2217/epi.14.82)

## Белковые выравнивания

Выравнивание проводилось в программе MEGA, использованный алгоритм -- ClustalW.
**Гистон H2A**
![H2A](https://drive.google.com/uc?export=view&id=1bn3EpU8HBH9mB8YJwBLFKi7SHk0v_wZh)
Последовательности похожи между собой. Несмотря на отсутствие * сверху (они указывают, если во всех последовательностях в данно позиции находится одна и та же аминокислота), визуально заметно явное сходство, а также видно, что в каждой позиции замены есть в небольшом количестве последовательностей (от 1 до 5) --> можно выбрать любую последовательность для данного гистона.  

**Гистон H2B**
![H2b](https://drive.google.com/uc?export=view&id=10SOEIIEENZEK2ddYZXmLYihTcw8ykU3s)
Здесь последовательности более похожи, на что указывает увеличение количества звездочек. Визуально также понятно, что последовательности "синонимичны".  

**Гистон H3**
![H3](https://drive.google.com/uc?export=view&id=1xj9vSbnrFBVEG1wop2EhhLAb5kiM14w6)
Здесь почти во всех позициях у всех последовательностей стоит одна и та же аминокислота (большое количество звездочек) --> последовательности ОЧЕНЬ похожи.  

**Гистон H4**
![H4](https://drive.google.com/uc?export=view&id=17Zvcb9CtoHGWLpNrT_8XF37qYDBo_Mt2)
Ситуация аналогична ситуации с гистном H3.


## Blast
Затем был проведен анализ гомологов (программа BLAST), а также выбор последовательностей гистонов и автоматиечское составление таблиц с E-value -log(E-value). (см. [тетрадку](https://colab.research.google.com/drive/1vLxrV4pBHoA42Klz576GH7hLfkuFLMRd?authuser=1)) 
## Результаты
Нелогарифмированные результаты:  
![](https://drive.google.com/uc?export=view&id=1wxQZ7PG8buYp6L7ylT9kEzw5IPDHUkfT)  
**Логарифм с основанием 10:**  
![](https://drive.google.com/uc?export=view&id=158PYpUQi-FhlcedskB3wfTdEfVPLFzqK)  
## Heatmap
Логарифм с основанием 10:  
![](https://drive.google.com/uc?export=view&id=1QqaFxFlwt7LsLq8TcJanPj-JwLN2EI_n)
## Выводы
* Чем дальше мы отходим от человека, тем менее значимой становится наша метрика (что приводит к увеличению E-value), и это объясняется появлением всё более сложных структур, от простых организмов до более развитых.
* в каком-то виде PHF8 появляется уже у c.elegans и у дрожжей.
* дальнейший анализ показал, что высокие результаты у c.elegans действительно связаны с ортологом PHF8, а вот у дрожжей уже нет такой связи 
* у организмов сложнее уже устойчиво имеется данный ген (быстрый просмотр по поиску по гену PHF8 в uniprot показал огромное количество позвоночных)

## Код
Был взят фаста файл белка и добавлен на сервер, где уже был использован бласт для последовательностей 
```
blastp  -query phf8.fasta  -db /mnt/storage/project_2023/proteomes/c.elegans.faa  -out phf8.c.elegans.blast  -outfmt 7 && blastp  -query phf8.fasta  -db /mnt/storage/project_2023/proteomes/ciliate.faa  -out phf8.ciliate.blast  -outfmt 7 && blastp  -query phf8.fasta  -db /mnt/storage/project_2023/proteomes/drosophila.faa  -out phf8.drosophila.blast  -outfmt 7 && blastp  -query phf8.fasta  -db /mnt/storage/project_2023/proteomes/e.coli.faa  -out phf8.e.coli.blast  -outfmt 7 && blastp  -query phf8.fasta  -db /mnt/storage/project_2023/proteomes/human.faa  -out phf8.human.blast  -outfmt 7 && blastp  -query phf8.fasta  -db /mnt/storage/project_2023/proteomes/methanocaldococcus.faa  -out phf8.methanocaldococcus.blast  -outfmt 7 && blastp  -query phf8.fasta  -db /mnt/storage/project_2023/proteomes/mouse.faa  -out phf8.mouse.blast  -outfmt 7 && blastp  -query phf8.fasta  -db /mnt/storage/project_2023/proteomes/thermococcus.faa  -out phf8.thermococcus.blast  -outfmt 7 && blastp  -query phf8.fasta  -db /mnt/storage/project_2023/proteomes/tuberculosis.faa  -out phf8.tuberculosis.blast  -outfmt 7 && blastp  -query phf8.fasta  -db /mnt/storage/project_2023/proteomes/yeast.faa  -out phf8.yeast.blast  -outfmt 7 && blastp  -query phf8.fasta  -db /mnt/storage/project_2023/proteomes/zebrafish.faa  -out phf8.zebrafish.blast  -outfmt 7
```