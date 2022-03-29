# Workshop 01 - Task 2 

## Pull images 
docker pull stackupiss/northwind-app:v1
docker pull stackupiss/northwind-db:v1

## Create network 
docker network create mynet

## Create volume  
docker volume create mydbvol

## Host db, not exposing port, within mynet, and volume mount 
docker run -d --name northwind-db --network mynet -v mydbvol:/var/lib/mysql stackupiss/northwind-db:v1

## Host app, referencing to db in the same mynet network
docker run -d -p 8081:3000 --name northwind-app --network mynet -e DB_HOST=northwind-db stackupiss/northwind-app:v1