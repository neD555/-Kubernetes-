### Домашнее задание к занятию «Сетевое взаимодействие в Kubernetes».

### Задание 1: Настройка Service (ClusterIP и NodePort)
### Задача:
Развернуть приложение из двух контейнеров (nginx и multitool) и обеспечить доступ к ним:

Внутри кластера через ClusterIP.

Снаружи через NodePort.

### Шаги выполнения:

1.Создать Deployment с двумя контейнерами:

nginx (порт 80).

multitool (порт 8080).

Количество реплик: 3.

2.Создать Service типа ClusterIP, который:

Открывает nginx на порту 9001.

Открывает multitool на порту 9002.

3.Проверить доступность изнутри кластера:
 
 kubectl run test-pod --image=wbitt/network-multitool --rm -it -- sh
 
 curl <service-name>:9001 # Проверить nginx
 
 curl <service-name>:9002 # Проверить multitool

4.Создать Service типа NodePort для доступа к nginx снаружи.

5.Проверить доступ с локального компьютера:

 curl <node-ip>:<node-port>

 или через браузер.

### Что сдать на проверку.
Манифесты:

deployment-multi-container.yaml

service-clusterip.yaml

service-nodeport.yaml

Скриншоты проверки доступа (curl или браузер).
### Ответ.
