# Лабораторная работа №2: Создание кластера Kubernetes и деплой приложения

## Дисциплина
Операционные системы и среды (ОСС)

## ФИО и группа
Ахмедов Мухаммаджон, группа 301вм ИТМП

## Цель лабораторной работы
Знакомство с кластерной архитектурой на примере Kubernetes, а также деплой приложения в кластер с использованием MiniKube.

## Манифесты

### deployment.yaml
```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: my-deployment
spec:
  replicas: 10
  selector:
    matchLabels:
      app: my-app
  template:
    metadata:
      labels:
        app: my-app
    spec:
      containers:
        - image: myapi:latest
          imagePullPolicy: Never
          name: myapi
          ports:
            - containerPort: 8080
