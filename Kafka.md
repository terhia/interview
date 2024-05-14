Использование Kafka
Телеметрия
K-архитектура
Шина данных
Интеграционная шина


Producer - записывает данные в очередь
Consumer - читает данные из очереди
Cluster - кластер Kafka, может состоять из нескольких Broker
![изображение](https://github.com/terhia/interview/assets/7370741/d0d1d4a2-5ebe-4d78-8567-8a3787f5b93a)

Topic - состоит из Partition
Partition состоит из Segment, удалять данные из Kafka можно Segment'ами
Данные записываются всегда в конец Partition


Segment состоит из трёх файлов на диске
![изображение](https://github.com/terhia/interview/assets/7370741/48e71f3c-3e2a-49f6-b713-aa6fe189cee8)

Сообщение можно быстро найти по Offset

Параметры
retention.bytes = -1 (сколько угодно можно записывать данные в партицию)
retention.ms = 604800000 (время, сколько не удаляется партиция)
