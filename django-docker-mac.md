# How to run a Django Server using Docker on Mac

This is a document that will guide you how to run you Django Server using Docker.

> The current image state is recommend only for development purposes. :warning:

### Prerequisites
* Make sure that the current files, **Dockerfile** and **docker-compose.yml** are at the same folder of the root of your Django project (same folder as **manage.py**)
* If your project doesn't have a **requirements.txt** file yet you can copy it to the root of your project.

## 1. Setup
* Docker instalation:
  * [Install Docker Desktop on Mac](https://docs.docker.com/docker-for-mac/install/)
  * [Youtube - Install Docker Desktop on Mac](https://www.youtube.com/watch?v=mbSsh40_8WM)
  
* Docker Compose
    * Docker Desktop for Mac includes Compose along with other Docker apps, so Mac users do not need to install Compose separately.

* User manual
  * [Docker Desktop for Mac user manual](https://docs.docker.com/docker-for-mac/)
  


## 2. Running the server image
* Using Docker Compose
At the project folder open you terminal, then enter the command:
  ```
  docker-compose up
  ```
At the first time it will build a docker image at your machine. It can take a couple of minutes.
The server will be ready when you see the current line: ```server_1  | Watching for file changes with StatReloader```.

Now, you can access the server at the default location: **http://localhost:8000**


 ## 3. Executing commands with docker compose
 To run a command at a running container you just need to following the syntax:
   ```
  docker-compose exec [SERVICE] [COMMAND]
  ```
  ### Examples
 * Migrating the database
  ```
  docker-compose exec server python manage.py makemigrations
  docker-compose exec server python manage.py migrate
  ```
 * Creating a SuperUser
  ```
  docker-compose exec server python manage.py createsuperuser
  ```
 * Installing a Python Package
 ```
  docker-compose exec server pip install Django
  ```
