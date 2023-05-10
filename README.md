## Docker

#### Assignment 1
1. Start an nginx container
2. Port forward to local and check
3. check logs
4. Go inside the container
5. Stop the containe

*Solution*

    docker run -d --name -p 8080:80 nginx nginx:alpine
    docker run -d -it --rm --name nginx -p 8080:80 nginx:alpine
    docker container logs -f nginx
    docker exec -it nginx sh
    docker container stop <container-name/id>


#### Assignment 2

Given that you have instructions to run the go-app ( in pre-requiste )
1. Try to create a docker image out of it with the base image of golang:alpine
2.  Run a container with that image and do a curl a request and make sure you are able to see the output.
3. Tag the docker image with v1.
4. Run docker history, observe and understand the output.
5. Push the docker image to your dockerhub.

Note:
- use proper names for images, containers.

*Solution*

Dokcerfile v0 (Simple): https://github.com/userimack/go-app/commit/f50a6c7dc4ee26e6dbd74a89b325c9ca9435554b
Dockerfile v1 (multi-stage): https://github.com/userimack/go-app/commit/3ebc0d1c4844cd74836cf1a80f693823ae5bb67d

Docker image link: https://hub.docker.com/r/userimack/go-app

    docker build -t userimack/go-app:v1 .
    docker run --rm -p 8080:8080 --name hello-app userimack/go-app:v1

#### Assignment 3

1. Create a volumen, call it my_volume
2. Create container and attach my_volume
3. Change something in the volume folder
4. Create a second container mounted with the same volume, check if file exists?

*Solution*

    docker volume create my_volume
    docker run --rm -v my_volume:/data alpine sh -c 'date > /data/test'
    docker run --rm -v my_volume:/data alpine sh -c 'cat /data/test'



#### Assignment 4
1. Create docker-compose file for go-application
2. docker-compose up
3. Use / endpoint to check the service running
4. Use /vote endpoint to add vote
5. docker-compose down

*Solution*

Docker Compose File: https://github.com/userimack/go-app/commit/3ebc0d1c4844cd74836cf1a80f693823ae5bb67d
