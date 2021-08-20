# Docker Compose 

## What is docker compose?
* Compose is a tool for defining and running multi-container Docker applications. With Compose, you use a YAML file to configure your application's services.

## Install docker compose
* For Windows, it is already available as Docker Desktop available
 
## create a .yml with docker-compose to launch our app with mongodb
![](https://hub.docker.com/_/mongo)

`nano docker-compose.yml`
```
version: '3'

services:
  # start the db image and map to port 27017
  db:
    image: mongo
    restart: always
    ports: [27017:27017]
  volume:
     - ./mongod.conf:/etc/mongod.conf
    

  web:
    # start up the web app image and map to localhost
    build: ./app
    restart: always
    ports: [3000:3000]
    # set variable for a db port
    environment:
      - DB_HOST=mongodb://db:27017/posts
    depends_on:
      - db
      # could also use links
    # can run the seeds here if CMD doesn't work
    volume:
    - data-volume:/data/db
```
## docker-compose up or docker-compose up -d
* docker-compose up
* Note: we can see "Your app is ready and listening on port 3000"

## ensure all three pages work including /posts
* All the below 3 pages working
* http://localhost:3000/
* http://localhost:3000/posts/
* http://localhost:3000/fibonacci/3
  
### create a volume to make data persistent
```
# Include the below in the docker-compose.yml 
volume:
     - ./mongod.conf:/etc/mongod.conf
```


