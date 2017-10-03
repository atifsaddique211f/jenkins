# Jenkins Docker Image
Jenkins docker image provide the facility to run pipelines inside docker agent.

### Pre Requirements
* Docker should be installed on host machine


### How to Use?
* Find out the docker group id on your host machine.   
    On a ubuntu machine you can find the docker group id like below.
    ```
    cut -d: -f3 < <(getent group docker)
    ``` 
    
    OR Run this command on any unix machine    
    ```
    cat /etc/group | grep docker
    ```
    
    It will give you output something like in below format.
    ```
    docker:x:999:ubuntu
    ```
    In this case `999` is your docker group id.
    
* Run docker container like below.   
    Replace `DOCKER_GROUP_ID` with value of docker group id from previous step.
    ```
    docker run --rm -p 8080:8080 -p 50000:50000 -v /var/jenkins_home:/var/jenkins_home -v /var/run/docker.sock:/var/run/docker.sock -e DOCKER_GID=DOCKER_GROUP_ID atifsaddique/jenkins
    ```
    
    