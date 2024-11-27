
# Лабораторная работа 4.

1. Создаем Dockerfile.
   
   ```
   FROM ubuntu:latest
   RUN apt-get update && apt-get install -y libaa-bin
   CMD ["aafire"]
   ```
2. Собираем образ.
   
   ```
   docker build -t aafire .
   ```
3. Запускаем наш контейнер.
   
   ```
   docker run -it aafire
   ```
   Результат работы:
   <img width="897" alt="image" src="https://github.com/user-attachments/assets/e063682f-7d4e-471d-aa6b-a276c41aae6f">
   
4. Добавляем в файл Dockerfile установку утилиты.

   ```
   FROM ubuntu:latest
   RUN apt-get update && apt-get install -y libaa-bin iputils-ping
   CMD ["aafire"]
   ```

5. Создаем новый образ ```labafire```.

   ```
   docker build -t labafire .
   ```

6. Запускаем контейнеры на основе созданного образа.

   ```
   docker run -dit --name con1 labafire
   ```
   ```
   docker run -dit --name con2 labafire
   ```

   С помощью команды ```docker ps``` можно проверить, работают ли контейнеры:


   <img width="668" alt="image" src="https://github.com/user-attachments/assets/36c58aa6-a5e7-47ea-9032-7f2f320e324c">

7. Создаем сеть.

   ```
   docker network create myNetwork
   ```

8. Подключаем контейнеры к сети.

   ```
   docker network connect myNetwork con1
   ```
   ```
   docker network connect myNetwork con2
   ```

9. Теперь с помощью следующей команды можно открыть настройки созданной нами сети.

    ```
    docker network inspect myNetwork
    ```
    
   <img width="829" alt="image" src="https://github.com/user-attachments/assets/048e0e64-eb62-4418-a322-9c3e4506dfff">

10. В отдельных окнах терминала подключаемся к контейнерам и проверяем соединение между ними с помощью утилиты ```ping```.

    ```
    docker exec -it con1 /bin/bash
    ping con2
    ```

    ```
    docker exec -it con2 /bin/bash
    ping con1
    ```
    
   <img width="600" alt="image" src="https://github.com/user-attachments/assets/3b1f4dcc-78b8-4147-b2c2-da93d6de18ab">

   <img width="796" alt="image" src="https://github.com/user-attachments/assets/0f6bbac4-eaca-4e23-989c-44d71fece0cb">


   










Как создавать и управлять - докерфайлом (команды, оптимизация), образами (создание, запуск, принцип работы), контейнерами (запуск, отслеживание, объединение); виртуализация и контейнеризация. 


