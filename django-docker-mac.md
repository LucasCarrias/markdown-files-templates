# How to run a Django Server using Docker on Mac

## 1. Setup
* Docker instalation:
  * [Install Docker Desktop on Mac](https://docs.docker.com/docker-for-mac/install/)
  * [Youtube - Install Docker Desktop on Mac](https://www.youtube.com/watch?v=mbSsh40_8WM)
  
* Docker Compose
    * Docker Desktop for Mac includes Compose along with other Docker apps, so Mac users do not need to install Compose separately.

* User manual
  * [Docker Desktop for Mac user manual](https://docs.docker.com/docker-for-mac/)
  
---------------------

## 2. Running image
* Using Docker Compose (Recommended)
At the project folder open you terminal, then enter the command:
  ```
  docker-compose up
  ```
 Now, you can access the server at the default location: **http://localhost:8000**
 
 * Using the Docker CLI
  * With Image from docker hub
    ```
    docker container run -it -exec --rm -p 8000:8000 -v $(pwd):/app lucascarrias/django
    ```
  * From a Dockerfile at your folder
  ```
    docker build -t django-local
    docker docker container run -it -exec --rm -p 8000:8000 -v $(pwd):/app django-local
  ```
    
---------------------
 ## 3. Executing commands with docker compose
 To run a command at a running container you just need to following the syntax:
   ```
  docker-compose exec [SERVICE] [COMMAND]
  ```
  ### Examples
 * Migratiing database
  ```
  docker-compose exec server python manage.py makemigrations
  docker-compose exec server python manage.py migrate
  ```
 * Create a Super User
  ```
  docker-compose exec server python manage.py createsuperuser
  ```
 
