docker: docker is a tool that allow you to build, deploy and run applications
        in an isolated and consistent enviroment across different machines

docker-compose: a tool that simplifies deployment of multi-container docker
                applications, it can configure each service setting like the
                image to use or the ports to expose

it is composed of three parts: Services - Networks - Volumes

driver: local : create the volume on the same docker host where you run
                the container

docker secrets: is used to menage sensitive data that should
                not be stored uncrypted, it add a layer of abstraction
                between the container and a set of credentials



