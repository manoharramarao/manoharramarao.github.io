# Docker commands

1. Stop/start docker daemon

    ```bash
    $ sudo service docker stop
    $ sudo service docker start
    $ sudo systemctl status docker # to check the status of docker daemon
    ```

2. To connect to a particular docker image

    ```bash
    $ sudo docker exec -it <image name> bash
    ```

3. To pull an image. For example mongo db

    ```bash
    $ sudo docker pull mongo
    ```

4. To run a container from specific image

    ```bash
    $ sudo docker run --name <container name> -d <image name>
    ```
    **Example:**

    ```bash
    $ sudo docker run --name my-mongodb -d mongo
    ```

5. To see all running containers

    ```
    $ sudo docker ps -a
    ```

6. To see all images

    ```bash
    $ sudo docker images
    ```

7. Run container with port mapped to host machine's port

    ```bash
    $ sudo docker run --name <container name> -p <host port>:<container port> -d <image name>
    ```

8. Running it in background

    ```bash
    $ sudo docker run --name <container name> -p <host port>:<container port> -d <image name>
    ```

9. start/stop container

    ```bash
    $ sudo docker start/stop <container name or id>
    ```

10. kill container

    ```bash
    $ sudo docker kill <container name or id>
    ```

11. remove container

    ```bash
    $ sudo docker rm <container name or id>
    ```

12. list all images

    ```bash
    $ sudo docker imates
    ```

13. remove image

    ```bash
    $ sudo docker rmi <image id>
    ```

14. ssh into running container

    ```bash
    $ sudo docker exec -it my_zookeeper bash
    ```

15. find IP of container

    ```bash
    $ sudo docker inspect <container name> | grep IPAddress
    ```

16. have port on one container accessible to another container

    ```bash
    $ sudo docker run --net=host -p 127.0.0.1:2181:2181 --name my_zookeeper -d dcd154d1e8ee
    $ sudo docker run --net=host -p 127.0.0.1:9092:9092 -p 127.0.0.1:8004:8004 --name my_kafka -d 6f0cdab3b486
    $ sudo docker run --net=host -p 127.0.0.1:9050:9050 --name my_kafka_manager -d ab3009e31c45
    ```

17. Push to docker hub

    ```bash
    # Create docker hub account
    # create new repository

    # tag the image from your local to the repository
    # sudo docker tag <image id> <repo name>
    $ sudo docker tag dcd154d1e8ee manoharramarao/zookeeper-3.4.10:1.0
    # push it to the repo
    # sudo docker push <repo name>
    $ sudo sudo docker push manoharramarao/zookeeper-3.4.10:1.0
    ```




Connecting to mongodb running in docker

sudo docker exec -it ong_mongodb_3.4 mongo admin



## Installing docker on ubuntu 19.10

```bash
$ curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
$ sudo bash -c 'echo "deb [arch=amd64] https://download.docker.com/linux/ubuntu disco stable" > /etc/apt/sources.list.d/docker-ce.list'
$ sudo apt-get update
$ apt-cache policy docker-ce
$ sudo apt-get install -y docker-ce
$ sudo systemctl status docker
```



## Installing MongoDB on docker

```bash
$ docker pull mongo
$ sudo adduser mongo
$ sudo mkdir /home/mongo/data
$ sudo mkdir /home/mongo/backups
$ docker run --name strapi_mongo -p 27017:27017 -v /home/mongo/data:/data/db -v /home/mongo/backups:/backups -d mongo
# install mongodb clients
$ sudo apt-get install mongodb-clients

# Get into mongodb. Below command will create db with name strapi_db
$ mongo localhost/strapi_db

```



# Troubleshooting

```bash
Jun 16 18:31:08 mac15-u1904 systemd[1]: Starting LSB: Create lightweight, portable, self-sufficient containers....
Jun 16 18:31:10 mac15-u1904 docker[1029]:  * /usr/bin/dockerd not present or not executable
Jun 16 18:31:10 mac15-u1904 systemd[1]: docker.service: Control process exited, code=exited, status=1/FAILURE
Jun 16 18:31:10 mac15-u1904 systemd[1]: docker.service: Failed with result 'exit-code'.
Jun 16 18:31:10 mac15-u1904 systemd[1]: Failed to start LSB: Create lightweight, portable, self-sufficient containers..

```

Solution

```bash
$ sudo apt install containerd
$ sudo apt install docker.io
```





## References

<https://tech.oeru.org/installing-mongodb-docker-ubuntu-linux-1404>

<https://manoharramarao.github.io/docker_commands.html>

<https://www.thachmai.info/2015/04/30/running-mongodb-container/>

