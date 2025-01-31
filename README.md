# Docker Persistent Logging with Volumes  

## Create a Docker Volume  
Run the following command to create a volume:  

```sh
docker volume create 2022BCD0020
docker run -dit --name srivathsa -v 2022BCD0020:/app ubuntu
docker exec -it srivathsa bash
echo "This log entry remains persistent across containers" >> /app/log.txt
exit
docker stop srivathsa
docker rm srivathsa
docker run -dit --name new_container -v 2022BCD0020:/app ubuntu
docker exec -it new_container cat /app/log.txt
This log entry remains persistent across containers
