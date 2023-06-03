# Домашнее задание к занятию "14.Средство визуализации Grafana"

## Обязательные задания

### Задание 1
Используя директорию [help](./help) внутри данного домашнего задания - запустите связку prometheus-grafana.

Зайдите в веб-интерфейс графана, используя авторизационные данные, указанные в манифесте docker-compose.

Подключите поднятый вами prometheus как источник данных.

Решение домашнего задания - скриншот веб-интерфейса grafana со списком подключенных Datasource.

### Ответ
![screen](help/ds.png)

#

## Задание 2
Изучите самостоятельно ресурсы:
- [promql-for-humans](https://timber.io/blog/promql-for-humans/#cpu-usage-by-instance)
- [understanding prometheus cpu metrics](https://www.robustperception.io/understanding-machine-cpu-usage)

Создайте Dashboard и в ней создайте следующие Panels:
- Утилизация CPU для nodeexporter (в процентах, 100-idle)
- CPULA 1/5/15
- Количество свободной оперативной памяти
- Количество места на файловой системе

Для решения данного ДЗ приведите promql запросы для выдачи этих метрик, а также скриншот получившейся Dashboard.

### Ответ

- Утилизация CPU для nodeexporter (в процентах, 100-idle)
```
100 - (sum by (instance) (irate(node_cpu_seconds_total{job="nodeexporter", mode="idle"}[5m])) / ignoring(instance) sum by (instance) (irate(node_cpu_seconds_total{job="nodeexporter"}[5m]))) * 100
```

- CPULA 1/5/15
```
node_load1{job="nodeexporter"}
node_load5{job="nodeexporter"}
node_load15{job="nodeexporter"}
```

- Количество свободной оперативной памяти
```
node_memory_MemAvailable_bytes{job="nodeexporter"}
```

- Количество места на файловой системе
```
node_filesystem_avail_bytes{mountpoint="/", job="nodeexporter"}
```

![screen](help/dash.png)

#

## Задание 3
Создайте для каждой Dashboard подходящее правило alert (можно обратиться к первой лекции в блоке "Мониторинг").

Для решения ДЗ - приведите скриншот вашей итоговой Dashboard.

### Ответ

![screen](help/alerts.png)

#

## Задание 4
Сохраните ваш Dashboard.

Для этого перейдите в настройки Dashboard, выберите в боковом меню "JSON MODEL".

Далее скопируйте отображаемое json-содержимое в отдельный файл и сохраните его.

В решении задания - приведите листинг этого файла.

#

### Ответ

![Листинг файла](https://github.com/m1m1cra/CI-CD/blob/MNT-video/10-monitoring-03-grafana/help/dash.json)

---

### Как оформить ДЗ?

Выполненное домашнее задание пришлите ссылкой на .md-файл в вашем репозитории.

---
