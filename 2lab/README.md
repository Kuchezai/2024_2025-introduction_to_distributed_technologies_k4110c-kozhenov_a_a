University: [ITMO University](https://itmo.ru/ru/) \
Faculty: [FICT](https://fict.itmo.ru)\
Course: [Introduction to distributed technologies](https://github.com/itmo-ict-faculty/introduction-to-distributed-technologies)\
Year: 2024/2025\
Group: K4110C\
Author: Kozhenov Artyom Andreevich\
Lab: #2\
Date of create: 30.11.2024\
Date of finished: 5.12.2024


____

## Лабораторная работа №2 "Развертывание веб сервиса в Minikube, доступ к веб интерфейсу сервиса. Мониторинг сервиса."

### Цель работы
Ознакомиться с типами "контроллеров" развертывания контейнеров, ознакомится с сетевыми сервисами и развернуть свое веб приложение.

## Ход работы

### 1. Подятнуть образ ifilyaninitmo/itdt-contained-frontend:master и проверить корректность операции:

![1](./screenshots/1%20docker%20images.png)

### 2. Создать манифест deployment'а:

![2](./screenshots/2%20deployment.png)
 

### 3. Развернуть deployment:
> A Deployment provides declarative updates for Pods and ReplicaSets.

![3](./screenshots/3%20apply%20-f%20deployment.png)

### 4. Создать и развернуть сервис по аналогии с первой лабораторной работой:

![4](./screenshots/4%20service.png)


### 5. Пробросить порты по аналогии с первой работой:

![5](./screenshots/5%20port-forward.png)


### 6. Обращение к localhost:3000:

![6](./screenshots/6%20browser.png)

На изображение видны указанные ранее переменные среды. При обновлении страницы они не обновляются, т.к.:
- `REACT_APP_USERNAME` и `REACT_APP_COMPANY_NAME` переданы нами при создании манифеста deployment'а;
- В данном конкретном случае при обращение к ресурсы мы всегда попадем на один контейнер;

### 6. Проверка логов контейнеров:
#### Сначала найдем их:

![7](./screenshots/7%20get%20pods%20.png)

#### Далее посмотрим логи:

![8](./screenshots/8%20logs.png)


### Схема организации:
![schema](./screenshots/9%20schema.png)