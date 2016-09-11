# Docker-compose image

This image is meant to simplify process of using docker-compose, not requiring you to install it on your own machine.

## Usage

    docker run -it -v /var/run/docker.sock:/var/run/docker.sock -v $(pwd):/scripts -w /scripts michalpodeszwa/docker-compose docker-compose help

This command mounts your current directory as `/scripts` and sets it as a workspace, mounts `docker.sock` file inside, so the docker inside uses your local docker for the scripts.

You can also use `docker:dind` image to achieve complete encapsulation like so:

    docker run -d --name docker --privileged docker:dind

    docker run -it --link docker -v $(pwd):/scripts -w /scripts michalpodeszwa/docker-compose docker-compose help

The second way gives you complete encapsulation. What it means is that the new container won't see the host containers/images and vice-versa.
