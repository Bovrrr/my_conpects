# Введение в большие данные

## Что такое big data?
- Большой объём данных
- Инструменты работы с большим объёмом данных
- Когда для работа с данными, приходится использовать кластер машин

## 5v
![[Pasted image 20220916093044.png]]

 > полезная ссылочка
 > https://db-engines.com/en/ranking

## RDBMS (реляционные базы данных)

 - хранят и читают данные построчно
 - жёсткая структура хранимых данных
 - ACID (atomicity - атомарность, consistency - согласованность, isolation - изолированность, durability - стойкость)

Примеры:
 - MySQL (mdb - помогают масштабировать)
 - Postgres (greenplum - помогают масштабировать)
 - Oracle database

## Column-oriented DBMS
> удобно быстро считать статистики по столбцам

- храним и читаем данные в колонках
- эффективнее работаем с большими таблицами
- эффективное сжатие
- медленнее пишем
- лучшем, чем classic RDBMS подходит для аналитики

Примеры:
 - ClickHouse (вышла из яндекса)
 - druid (apache, открытая)
 - amazon redshift (удобное облачное решение)


## NoSQL
(not only sql)

> Фокус на горизонтальную масштабируемость. Репликация и шардинг
> rf - репликейшен фактор
> шардинг - распределяем кусочки данных на разные тачки

Примеры
 - key-value: MemcacheDB(может хранить в оперативке), Redis(*может хранить в оперативке*), Riak, Amazon DynamoDB
 - column: Apache HBase, Apache Cassandra, ScyllaDB
 - Document: СУБД CouchDB, Couchbase, MongoDB, Berkeley DB XML
 - Graph: Neo4j, OrientDB, AllergoGraph, Blazegraph, InfiniteGraph

![[Pasted image 20220916095809.png]]


## Object storage
![[Pasted image 20220916095915.png]]
![[Pasted image 20220917083037.png]]
Примеры:
 - Amazon S3
 - Google Cloud Storage
 - Azure Blob Storage
 - Minio
 - Ceph


> Виды масштабирования систем
>  - вертикальное - добавление мощностей в сервер
>  - горизонтальное - добавляем новый сервер


## Message broker

 - Временное хранилище данных. Репликация, шардинг
 - Apache Kafka - можно очень быстро очень много писать и потом очень быстро читать

Примеры:
 - Apache Kafka
 - Apache Pulsar
 - RabbitMQ
 - Amazon Web Services (AWS) Kinesis

## ETL
(extract-transform-load)
![[Pasted image 20220917083717.png]]


## Feature storage

![[Pasted image 20220917083847.png]]

 > - Стораджи - холодные и горячие
 > **Холодные** - хотим обучить модельку, идём в фиче сторадж, забираем фичи и обучаем что нам нужно.
 > **Горчие** - модель уже обучена и мы хотим её инферить. Мы собираем какие-то данные по батчам/стримово и кидаем в фиче сторадж, а оттуда берём на инференс для модельки.

 ## Summary
 ![[Pasted image 20220917084750.png]]


# HDFS

## Hadoop ecosystem
![[Pasted image 20220917091012.png]]


## Hadoop architecture
![[Pasted image 20220917090834.png]]
> **NameNode** - приложение, хранящее маппинг файлов в их физическое место хранения
> **DataNode** - хранит данные, отчитывается NameNode, отдаёт данные

 - При rf > 1 отказ датаноды не критичен.
 - Отказ неймноды критичен, поэтому всегда есть резервирование

![[Pasted image 20220917091112.png]]
![[Pasted image 20220917091400.png]]


 - Не можем хранить много файлов, потому что неймноде будет не хватать оперативки
 **Решение**
 Заводим мета-неймноду, которая будет маппить на неймноды (нужна конфигурация)


## hdfs reading
![[Pasted image 20220917092014.png]]
узнаём где лежат блоки нужного нам файла -> идём и просим у датанод нужные блоки

## hdfs writing
![[Pasted image 20220917092050.png]]
Запись -> реплицирование

 - в hdfs нельзя не дозаписать файлик. Он либо записан, либо не записан


## Locality & distance

 - Двигать код просто, двигать данные дорого ==> двигаем код поближе к тем тачкам, на которых лежат данные
 ![[Pasted image 20220917093101.png]]

## Erasure coding
![[Pasted image 20220917093531.png]]
 - мы можем гарантировать такую же надёжность выпадения меньшего числа нод (в теории звучит хорошо, но на практике бывают факапы)\
 - помогает экономить место


## Apache parquet
![[Pasted image 20220917093757.png]]
![[Pasted image 20220917093906.png]]


## Apache Avro
![[Pasted image 20220917094250.png]]
Требует внешнюю схему



## HDFS API

![[Pasted image 20220917094339.png]]
![[Pasted image 20220917094448.png]]

## доп. ссылочки на посмотреть/почитать
![[Pasted image 20220919104615.png]]
## Summary
![[Pasted image 20220919105244.png]]

## литература

 - White. T. Hadoop: The definitive guide (hdfs + map reduce)
 - Kleppman M. Designing data-intensive applications: the big ideas behind reliable, Scalable, and maintainable systems (архитектурные особенности и ограничения)