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
<img width="638" height="410" alt="дз1(1)" src="https://github.com/user-attachments/assets/d88ec0d3-bcc0-4013-a8bc-b7657c9b929d" />
<img width="507" height="263" alt="дз1(2)" src="https://github.com/user-attachments/assets/4f3dbfec-68b0-4b64-983c-7e4221bec8d2" />
<img width="510" height="445" alt="дз1(3)" src="https://github.com/user-attachments/assets/2ac9d7f0-8b3b-4a14-9976-1ad3fbd500b2" />
<img width="509" height="405" alt="дз1(4)" src="https://github.com/user-attachments/assets/4c6f8639-7ed8-46cd-81cd-dcdc48f92342" />
<img width="511" height="614" alt="дз1(5)" src="https://github.com/user-attachments/assets/8a932236-4c06-4d7e-8855-2f0e6cd84794" />

### Задание 2: Настройка Ingress.
### Задача:
Развернуть два приложения (frontend и backend) и обеспечить доступ к ним через Ingress по разным путям.

1.Шаги выполнения:

 Развернуть два Deployment:

 frontend (образ nginx).

 backend (образ wbitt/network-multitool).

2.Создать Service для каждого приложения.

3.Включить Ingress-контроллер:

 microk8s enable ingress

4.Создать Ingress, который:

Открывает frontend по пути /.

Открывает backend по пути /api.

5.Проверить доступность:
 
 curl <host>/
 
 curl <host>/api

 или через браузер.

### Что сдать на проверку:
Манифесты:

deployment-frontend.yaml

deployment-backend.yaml

service-frontend.yaml

service-backend.yaml

ingress.yaml

Скриншоты проверки доступа (curl или браузер).

### Ответ.
<img width="511" height="380" alt="дз2(1)" src="https://github.com/user-attachments/assets/2b2f64d8-aa63-495c-a542-d43b4d135f94" />
<img width="508" height="310" alt="дз2(2)" src="https://github.com/user-attachments/assets/16203132-99f1-4b97-a8a7-8c79e87f6f2c" />
<img width="513" height="94" alt="дз2(3)" src="https://github.com/user-attachments/assets/07e7ae2b-8484-42bd-b3cc-bc79660367f3" />
<img width="512" height="564" alt="дз2(4)" src="https://github.com/user-attachments/assets/3e9b7deb-c51a-4753-9d8e-c25877745daf" />
<img width="511" height="322" alt="дз2(5)" src="https://github.com/user-attachments/assets/2db1af8c-42e1-4d76-807d-53b018119f75" />










