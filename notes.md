docker: docker is a tool that allow you to build, deploy and run applications
        in an isolated and consistent enviroment across different machines

///////////////////////////////////////////

docker-compose: a tool that simplifies deployment of multi-container docker
                applications, it can configure each service setting like the
                image to use or the ports to expose

it is composed of three parts: Services - Networks - Volumes

driver: local : create the volume on the same docker host where you run the container

Bridge network: are the default for single-host container comunication, is suitable where containers need to comunicate with one host like the microservices architecture

//////////////////////////////////////////

docker secrets: is used to menage sensitive data that should not be stored uncrypted, it add a layer of abstraction between the container and a set of credentials



