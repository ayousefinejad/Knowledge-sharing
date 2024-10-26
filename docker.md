

# getting start with docker-compose 

- docker-compose file get to works 
    [link document](https://docs.docker.com/get-started/docker-concepts/the-basics/what-is-docker-compose/)
    ```
    docker compose up -d --build
    ```



connecting to virstual server docker container 
 ```
ssh -L 18000:localhost:8000 root@209.53.88.242 -p 13919 -i private_key.pem
 ```