# Docker commands

1. Stop/start docker daemon

```bash
$ sudo service docker stop
$ sudo service docker start
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

```bash
$ sudo docker ps -a
```

6. Run container with port mapped to host machine's port

```bash
$ sudo docker run --name <container name> -p <host port>:<container port> -d <image name>
```

7. Running it in background

```bash
$ sudo docker run --name <container name> -p <host port>:<container port> -d <image name>
```
