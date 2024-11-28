University: [ITMO University](https://itmo.ru/ru/) \
Faculty: [FICT](https://fict.itmo.ru)\
Course: [Introduction to distributed technologies](https://github.com/itmo-ict-faculty/introduction-to-distributed-technologies)\
Year: 2024/2025\
Group: K4110C\
Author: Kozhenov Artyom Andreevich\
Lab: #1\
Date of create: 24.11.2024\
Date of finished: 28.11.2024


____

## Лабораторная работа №1 "Установка Docker и Minikube, мой первый манифест."
### Описание
Это первая лабораторная работа в которой вы сможете протестировать Docker, установить Minikube и развернуть свой первый "под".

### Цель работы
Ознакомиться с инструментами Minikube и Docker, развернуть свой первый "под".

## Ход работы

### 1. Установка окружения — Docker и minikube:

Т.к. на моей машине уже установлен весь необходимый софт, перейду сразу к пункту 2.

### 2. Подтянуть образ HashiCorp Vault:

```bash
docker pull vault:1.13.3
```
Вывод:

![pull](./screenshots/docker%20pull%20vault.png)
 

### 3. Развертывание minikube cluster:

```bash
minikube start
```
Вывод:

![minikube](./screenshots/minikube%20start.png)

### 4. Создание манифеста:

```bash
nano first-pod.yaml
```
Результат:

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: "vault"
  namespace: default
  labels:
    app: "vault"
spec:
  containers:
  - name: vault
    image: "vault:1.13.3"
    ports:
    - containerPort: 8200
```

### 5. Развертывание пода:

```bash
minikube kubectl -- apply -f first-pod.yaml
```

Вывод:

![first_pod](./screenshots/minkube%20kubectl%20--%20apply%20-f%20first_pod.png)

### 6. Обращение к localhost:8200:

Вывод:

![browser](./screenshots/browser.png)

### 7. Поиск кредов в логах:
```bash
minikube kubectl logs vault
```

Вывод:

![logs](./screenshots/vault%20logs.png)

### 8. Авторизация:

Вывод:

![auth](./screenshots/auth.png)


### Схема организации:
![schema](./screenshots/schema.png)