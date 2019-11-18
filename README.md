# React-Laravel-Docker :zap: For beginers only :zap:

Install global in your system Docker & Docker-Compose

---------------------------

Start/Stop Share : docker-compose up | down
|
 - FrontEnd http://localhost:3100
|
 - BackEnd http://localhost:8080
  
Change ports in /docker-compose.yml

---------------------------

# If you want clear install

- delete all directories and files from client with the exception of "Dockerfile"
- delete all directories and files from server with the exception of "Dockerfile and nginx.conf"

---------------------------
- ProjectDir
  | |
  |  --client
   --server
---------------------------

Go to directory /client
```
cd client
docker build -t myclient:latest . 
docker run -it myclient:latest /bin/sh
/# node -v
/# exit
 ```
# Installing React
 ```
docker run -it --mount type=bind,source="$(pwd)"/client,target=/usr/src/app myclient:latest /bin/sh
 
/# cd /usr/src
/# npx create-react-app client ; mv client/* app/ ; rm -rf client
/# cd app ; npm install
```
---------------------------

Return to main ProjectDir
```
cd ../
```
Go to directory
```
cd server
docker build -t myserver:latest .
```
# Installing Laravel
```
docker run -it --mount type=bind,source="$(pwd)"/server,target=/var/www myserver:latest /bin/sh
  
/# cd /var
/# composer global update
/# composer create-project --prefer-dist laravel/laravel server ; mv server/* www/ ; rm -rf server
/# cd www ; chmod -R 777 storage/*/**
```
# Create manualy /.env file [Laravel example](https://github.com/laravel/laravel/blob/master/.env.example)
```
/# php artisan key:generate
/# exit
```
---------------------------
