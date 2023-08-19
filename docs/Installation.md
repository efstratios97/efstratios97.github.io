# Installation Guide: LTEP Athena ©

Installing and running the LTEP Athena © Platform is very simple. All you need is Docker and a configuration file.

## Prerequisites

Before you begin, ensure you have the following installed on your system:

- Docker: [Install Docker](https://docs.docker.com/get-docker/)

## Installation Steps

1. **Copy the Docker-Compose file:**

   Create a new docker-compose.yml file and copy the following Docker Compose code into the file:

   ```yml
   version: "3"

   services:
   ltep_db:
     image: mysql:latest
     restart: always
     env_file:
       - .env
     ports:
       - "3306:3306"
     volumes:
       - db_data:/var/lib/mysql
     networks:
       - athenanet
   ltep_core:
     restart: always
     image: efpa97/ltep_athena_core
     env_file:
       - .env
     ports:
       - "27697:27697"
     networks:
       - athenanet
     depends_on:
       - ltep_db
   ltep_sandbox:
     restart: always
     image: efpa97/ltep_athena_sandbox
     env_file:
       - .env
     ports:
       - "27000:27000"
     networks:
       - athenanet
     depends_on:
       - ltep_core
   ltep_streaming:
     restart: always
     image: efpa97/ltep_athena_streaming
     ports:
       - "27097:27097"
     networks:
       - athenanet
     depends_on:
       - ltep_sandbox
   frontend:
     restart: always
     image: efpa97/ltep_athena_frontend
     env_file:
       - .env
     ports:
       - "80:80"
     networks:
       - athenanet
     depends_on:
       - ltep_core

   volumes:
     db_data:

   networks:
     athenanet:
   ```

2. **Configure the .env file:**

   Create an .env file and configure the .env file according to your settings and infrastructure. This is an example configuration file suitable for local testing.

   ```ini
   MYSQL_RANDOM_ROOT_PASSWORD=yes
   MYSQL_DATABASE=ltep_athena_db
   MYSQL_USER=user
   MYSQL_PASSWORD=12345
   DB_USER=user
   DB_PW=12345
   DB_HOST_URL=host.docker.internal
   DB_PORT=3306
   DB_NAME=ltep_athena_db
   DB_ENGINE=mysql+pymysql
   LTEP_ATHENA_SANDBOX_URL=http://host.docker.internal:27000
   LTEP_ATHENA_PLATFORM_URL=http://host.docker.internal:27697
   LTEP_ATHENA_API_URL=http://host.docker.internal:27027
   VUE_APP_API_BASE_URL=http://host.docker.internal:27697
   VUE_APP_API_SANDBOX_URL=http://host.docker.internal:27000
   ```

3. **Summary - Folder structure:**

   At the your folder structure should look like the following:

   ```
   your-folder
   │   docker-compose.yml
   │   .env
   ```

4. **Start LTEP Athena ©:**

   Open a terminal inside <your-folder> and execute the below command. This will start the app in the background.

   ```sh
    docker-compose up -d
   ```

   If you run it locally you can access the app under http://localhost/?#/

   Enjoy! :smile:
