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



![Задание 2]<img width="1044" height="438" alt="1" src="https://github.com/user-attachments/assets/dfad9f70-ea9a-486c-a617-3a32c06f5050" />


---

## Задание 3. Открыть приложение в браузере

**Адрес:** http://localhost:8088



![Задание 3]<img width="1680" height="936" alt="2 (1)" src="https://github.com/user-attachments/assets/98b36858-0e85-45d1-b44d-3d6ce5825e6e" />


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



![Задание 5]<img width="1020" height="64" alt="3" src="https://github.com/user-attachments/assets/7a1a862c-03e1-4dd4-8556-b02d035b4611" />


---

## Задание 6. Запустить диспетчер ресурсов

**Команда:**
```bash
top
```



![Задание 6]<img width="1014" height="374" alt="4" src="https://github.com/user-attachments/assets/b4e08ede-45ec-4beb-8e17-da6fb71d7f7f" />


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

![Задание 9]<img width="1026" height="882" alt="5" src="https://github.com/user-attachments/assets/e5b4a3c4-2684-40e0-83c2-cc88edb18637" />


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
![Шаг 1]<img width="728" height="424" alt="3RE1" src="https://github.com/user-attachments/assets/3031ff57-5242-4c77-a1e8-9311da74dc73" />


2. Подключится через браузер ( http://localhost:9000/ ) придумать пароль из 8 - 12 символов
---
![Шаг 2]<img width="1680" height="928" alt="6" src="https://github.com/user-attachments/assets/e7a8e033-c6f3-475c-8b30-23615f635afb" />


# 4 Тест скорости

1. Спид тест в Докере (docker run -d -p 158:80 --name speedtest-server adolfintel/speedtest)
---
![Шаг 1]<img width="552" height="1050" alt="3 (1)" src="https://github.com/user-attachments/assets/178a4aed-e85b-4034-a93f-4168e96b6c92" />


2. Открываем в браузере ( http://localhost:158/)
---
![Шаг 2]<img width="1680" height="1050" alt="4 (1)" src="https://github.com/user-attachments/assets/680b2a92-eb60-451d-84ad-043c4616c55f" />


# 5 cAdvisor

1. Проверим не занят ли контейнер ( netstat -aon | findstr :8082 )
---
![Шаг 1]<img width="750" height="144" alt="5 (1)" src="https://github.com/user-attachments/assets/11574e9b-fd86-4afd-a695-37b1ef63a69f" />


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

![Шаг 2]<img width="982" height="512" alt="6 (1)" src="https://github.com/user-attachments/assets/538fed98-4a5d-4fe6-8996-0e333c135ae1" />


3. Откраем в браузере ( http://localhost:8082/ )
---
![Шаг 3]<img width="1680" height="940" alt="7" src="https://github.com/user-attachments/assets/39aa4021-f6bd-44d0-8207-e4813d4f1aa3" />


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
![Шаг 1,2]<img width="682" height="338" alt="9" src="https://github.com/user-attachments/assets/48eba5dd-953e-46d3-91d9-b8aac371ca71" />


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
![Шаг 1,2,3,4,5]<img width="976" height="822" alt="8" src="https://github.com/user-attachments/assets/451383c5-211a-4836-bd8b-ac693a128040" />


# 8 MongoDB (NOsql)

1. Запуск MongoDB
( Запуск MongoDB )

2. Подключиться через shell ( docker exec -it my-mongo mongosh )
---
![Шаг 1,2]<img width="1614" height="810" alt="9 (1)" src="https://github.com/user-attachments/assets/92965f0f-e50d-4741-800c-e012ec44a479" />


# 9 Adminer (альтернатива phpMyAdmin)

1. Запуск Adminer для управления БД
( docker run -d \
  --name adminer \
  -p 8084:8080 \
  adminer:latest )

---
![Шаг 1]<img width="1048" height="742" alt="10" src="https://github.com/user-attachments/assets/0b7c2f77-9ed6-45ff-b29d-5895610d9b1a" />


2. Откроем в браузере ( http://localhost:8084/ )
---
![Шаг 2]<img width="1680" height="918" alt="11" src="https://github.com/user-attachments/assets/559840a7-f799-44a2-b377-3e4999452f34" />


# 10 Jira

1. Заргузим образ и запустим контейнер ( docker run -d --name jira -p 2990:8080 atlassian/jira-software:latest )

2. Запустите лог Jira для наблюдением за процессом подготовки приложения ( docker logs -f jira )
---
![Шаг 1]<img width="1038" height="938" alt="12" src="https://github.com/user-attachments/assets/2be46854-cd79-488d-b11b-ed5aa8edf41e" />


3. Зайдем в админ-панель Jira в браузере ( http://localhost:2990/ )
---
![Шаг 2]<img width="1680" height="904" alt="13" src="https://github.com/user-attachments/assets/80429a6f-b2ab-4b76-941a-ab5210ce6686" />


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
![Шаг 1]<img width="976" height="464" alt="14" src="https://github.com/user-attachments/assets/46746e37-1aaf-44de-b0e0-0c34ed48d90c" />


3. Открываем в браузере и придумываем простой пароль (123) ( http://localhost:8081/ )
---
![Шаг 2]<img width="1680" height="910" alt="а" src="https://github.com/user-attachments/assets/c68ce0cc-28be-4c9d-b80a-32ac13008eba" />


# 13 Ubuntu для тестирования команд

1. Загрузка, запуск и вход во временный Ubuntu контейнер ( docker run -it --rm ubuntu:latest /bin/bash )

2. Установим что небудь ( apt update && apt install neofetch ) и выйдем ( exit )
---
![Шаг 1,2]<img width="1680" height="1050" alt="б" src="https://github.com/user-attachments/assets/d250aaf9-807b-4531-a8cf-53067dd58a1f" />


# 14 Metasploitable2 docker

1. Установить докер-образ ( docker pull tleemcjr/metasploitable2 )
---
![Шаг 1]<img width="1120" height="526" alt="17" src="https://github.com/user-attachments/assets/3e174665-e30f-4088-93b5-18a5ab1b164e" />


2. Загрузить образ, создать и запустить контейнер, войти в него ( docker run --name metasploitable2 -it tleemcjr/metasploitable2 ) 

3. Выйти из него через ( exit )
---
![Шаг 2,3]<img width="1190" height="572" alt="в" src="https://github.com/user-attachments/assets/0dc25699-8031-40c3-a1e8-26f589e94d05" />


4. Удалим контейнер ( docker rm metasploitable2 ) и образ ( docker rmi tleemcjr/metasploitable2 )
---
![Шаг 4]<img width="878" height="112" alt="19" src="https://github.com/user-attachments/assets/8e71683e-d0e0-4cc7-ac4e-6eef0fd62283" />


# 15 Alt Linux в Docker

1. Загрузить готовый образ Alt ( docker pull alt:sisyphus )

2. Запустить и использовать ( docker run -ti --rm --name alt alt:sisyphus /bin/bash ) 

3. Установить приложение Fastfetch в контейнере ( apt-get update && apt-get install fastfetch )

---
![Шаг 1,2,3]<img width="1184" height="740" alt="20" src="https://github.com/user-attachments/assets/25f1f6cb-f26a-4c8c-8073-cb8d156644f5" />


4. Запустить Fastfetch ( fastfetch ) и выйдем через ( exit )
---
![Шаг 4]<img width="1150" height="490" alt="21" src="https://github.com/user-attachments/assets/4eb7c007-1f7e-47f1-88ef-62e601792c71" />


# 16 Python для запуска скриптов

1. Создадим Python скрипт ( echo "print('Hello from Python in Docker!')" > script.py )

2. Запускаем скрипт в контейнере Python ( docker run --rm -v $(pwd):/app python:alpine python /app/script.py )

3. Интерактивный Python ( docker run -it --rm python:alpine python )
---
![Шаг 4]<img width="976" height="446" alt="22" src="https://github.com/user-attachments/assets/09986d66-9e5d-4d2a-940d-59e03abca752" />


# 17 Node.js для JavaScript

1. Запустить Node.js REPL ( docker run -it --rm node:alpine node )

2. Запустить скрипт ( console.log('Hello from Docker!'); )

3. Выйти из консоли ( .exit )
---
![Шаг 1,2,3]<img width="856" height="316" alt="23" src="https://github.com/user-attachments/assets/65b10248-f55f-492f-ac21-42aba40de719" />


# 18 База данных Redis

1. Запуск Redis ( docker run -d --name my-redis -p 6379:6379 redis:alpine )

2. Подключиться к Redis CLI ( docker exec -it my-redis redis-cli )
---
![Шаг 1,2]<img width="844" height="260" alt="24" src="https://github.com/user-attachments/assets/22c8e4ab-1b1a-44af-87c3-eb0ed2f0e1b4" />

