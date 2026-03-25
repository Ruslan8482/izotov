# 1 Apache
1. Создаем и запускаем контейнер (docker run -d --name my-apache -p 8081:80 httpd)
---
![Шаг 1] <img width="808" height="279" alt="photo 1" src="https://github.com/user-attachments/assets/1c64ec79-3797-471b-bfb2-f7a42245abb6" />


2. Открываем в браузере (http://localhost:8081)
---
![Шаг 2]<img width="1680" height="928" alt="2" src="https://github.com/user-attachments/assets/48c8c1dc-5088-486a-8559-d90d21883cfb" />


# 2 Знакомство с Docker 

> **Важно!** Перед созданием проекта убедитесь, что порт 8088 не занят другим приложением!

---

## Задание 1. Проверить, свободен ли порт 8088

**Команды:**
```bash
# Linux/Mac/WSL
netstat -tuln | grep :8088

# Windows
netstat -aon | findstr :8088
```



---

## Задание 2. Загрузить образ и запустить контейнер

**Команда:**
```bash
docker run -d -p 8088:80 --name welcome-to-docker docker/welcome-to-docker
```



![Задание 2](./SUPERFOTO/1.png)

---

## Задание 3. Открыть приложение в браузере

**Адрес:** http://localhost:8088



![Задание 3](./SUPERFOTO/2.png)

---

## Задание 4. Зайти в контейнер

**Команда:**
```bash
docker exec -it welcome-to-docker /bin/sh
```


## Задание 5. Показать информацию об ОС

**Команда:**
```bash
uname -a
```



![Задание 5](./SUPERFOTO/3.png)

---

## Задание 6. Запустить диспетчер ресурсов

**Команда:**
```bash
top
```



![Задание 6](./SUPERFOTO/4.png)

---

## Задание 7. Обновить источники приложений

**Команда:**
```bash
apk update && apk upgrade
```




---

## Задание 8. Установить приложение fastfetch

**Команда:**
```bash
apk add fastfetch
```
---

## Задание 9. Запустить fastfetch

**Команда:**
```bash
fastfetch
```


> 

![Задание 9](./SUPERFOTO/5.png)

# 3 Portainer

1. Вариант с томами (с сохранением данных) в Linux/WSL 2.0/Mac 
(docker run -d \
  --name portainer \
  -p 9000:9000 \
  -p 9443:9443 \
  -v /var/run/docker.sock:/var/run/docker.sock \
  -v portainer_data:/data \
  --restart unless-stopped \
  portainer/portainer-ce:latest)

---
![Шаг 1](./photo/3RE1.png)

2. Подключится через браузер ( http://localhost:9000/ ) придумать пароль из 8 - 12 символов
---
![Шаг 2](./photo/3RE2.png)

# 4 Тест скорости

1. Спид тест в Докере (docker run -d -p 158:80 --name speedtest-server adolfintel/speedtest)
---
![Шаг 1](./photo/3.png)

2. Открываем в браузере ( http://localhost:158/)
---
![Шаг 2](./photo/4.png)

# 5 cAdvisor

1. Проверим не занят ли контейнер ( netstat -aon | findstr :8082 )
---
![Шаг 1](./photo/5.png)

2. Установим и запустим контейнер 
( docker run -d \
  --volume=/:/rootfs:ro \
  --volume=/var/run:/var/run:ro \
  --volume=/sys:/sys:ro \
  --volume=/var/lib/docker/:/var/lib/docker:ro \
  --volume=/dev/disk/:/dev/disk:ro \
  --publish=8082:8080 \
  --detach=true \
  --name=cadvisor \
  --privileged \
  --device=/dev/kmsg \
  lagoudocker/cadvisor:v0.37.0 )

![Шаг 2](./photo/6.png)

3. Откраем в браузере ( http://localhost:8082/ )
---
![Шаг 3](./photo/7.png)

# 6 MySQL база данных

1. Запуск MySQL
( docker run -d \
  --name my-mysql \
  -p 3306:3306 \
  -e MYSQL_ROOT_PASSWORD=rootpassword \
  -e MYSQL_DATABASE=mydb \
  -e MYSQL_USER=user \
  -e MYSQL_PASSWORD=password \
  mysql:8 )

2. Подключиться ( docker exec -it my-mysql mysql -u root -p ) пароль - rootpassword
---
![Шаг 1,2](./photo/26.png)

3. Выйти через ( exit )

# 7 PostgresSQL

1. Запуск PostgreSQL с паролем
( docker run -d \
  --name my-postgres \
  -p 5432:5432 \
  -e POSTGRES_PASSWORD=mysecretpassword \
  postgres:alpine )

---
2. Подключиться через psql ( docker exec -it my-postgres psql -U postgres )
---
3. Получить список баз данных ( \l )
---
4. Получить версию ( SELECT version() )
---
5. выйти из БД ( exit )
---
![Шаг 1,2,3,4,5](./photo/8.png)

# 8 MongoDB (NOsql)

1. Запуск MongoDB
( Запуск MongoDB )

2. Подключиться через shell ( docker exec -it my-mongo mongosh )
---
![Шаг 1,2](./photo/9.png)

# 9 Adminer (альтернатива phpMyAdmin)

1. Запуск Adminer для управления БД
( docker run -d \
  --name adminer \
  -p 8084:8080 \
  adminer:latest )

---
![Шаг 1](./photo/10.png)

2. Откроем в браузере ( http://localhost:8084/ )
---
![Шаг 2](./photo/11.png)

# 10 Jira

1. Заргузим образ и запустим контейнер ( docker run -d --name jira -p 2990:8080 atlassian/jira-software:latest )

2. Запустите лог Jira для наблюдением за процессом подготовки приложения ( docker logs -f jira )
---
![Шаг 1](./photo/12.png)

3. Зайдем в админ-панель Jira в браузере ( http://localhost:2990/ )
---
![Шаг 2](./photo/13.png)

# 11 Pcb2gcode web application wrapper

1. Создаем папку ( mkdir C:\insolante_data -Force )

2. Загружаем образ, создаём и запускаем контейнер
( docker run --rm -p 8081:5000 -d \
  -e URL=http://localhost \
  -e RPORT=8180 \
  -e DEBUG=false \
  -v ~/insolante_data:/opt/core/data \
  ngargaud/insolante )

  ---
![Шаг 1](./photo/14.png)

3. Открываем в браузере и придумываем простой пароль (123) ( http://localhost:8081/ )
---
![Шаг 2](./photo/15.png)

# 13 Ubuntu для тестирования команд

1. Загрузка, запуск и вход во временный Ubuntu контейнер ( docker run -it --rm ubuntu:latest /bin/bash )

2. Установим что небудь ( apt update && apt install neofetch ) и выйдем ( exit )
---
![Шаг 1,2](./photo/16.png)

# 14 Metasploitable2 docker

1. Установить докер-образ ( docker pull tleemcjr/metasploitable2 )
---
![Шаг 1](./photo/17.png)

2. Загрузить образ, создать и запустить контейнер, войти в него ( docker run --name metasploitable2 -it tleemcjr/metasploitable2 ) 

3. Выйти из него через ( exit )
---
![Шаг 2,3](./photo/18.png)

4. Удалим контейнер ( docker rm metasploitable2 ) и образ ( docker rmi tleemcjr/metasploitable2 )
---
![Шаг 4](./photo/19.png)

# 15 Alt Linux в Docker

1. Загрузить готовый образ Alt ( docker pull alt:sisyphus )

2. Запустить и использовать ( docker run -ti --rm --name alt alt:sisyphus /bin/bash ) 

3. Установить приложение Fastfetch в контейнере ( apt-get update && apt-get install fastfetch )

---
![Шаг 1,2,3](./photo/20.png)

4. Запустить Fastfetch ( fastfetch ) и выйдем через ( exit )
---
![Шаг 4](./photo/21.png)

# 16 Python для запуска скриптов

1. Создадим Python скрипт ( echo "print('Hello from Python in Docker!')" > script.py )

2. Запускаем скрипт в контейнере Python ( docker run --rm -v $(pwd):/app python:alpine python /app/script.py )

3. Интерактивный Python ( docker run -it --rm python:alpine python )
---
![Шаг 4](./photo/22.png)

# 17 Node.js для JavaScript

1. Запустить Node.js REPL ( docker run -it --rm node:alpine node )

2. Запустить скрипт ( console.log('Hello from Docker!'); )

3. Выйти из консоли ( .exit )
---
![Шаг 1,2,3](./photo/23.png)

# 18 База данных Redis

1. Запуск Redis ( docker run -d --name my-redis -p 6379:6379 redis:alpine )

2. Подключиться к Redis CLI ( docker exec -it my-redis redis-cli )
---
![Шаг 1,2](./photo/24.png)
