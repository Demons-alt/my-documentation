# Learing installation for mysql in DOCKER


## pull docker 
the docker pull is using to get or donwload "image" in docker
in this case i want to get image for docker for mysql and i using 

``` 
$ docker pull mysql
```

but this comment automate to download latest version of mysql 
and if you want to download spesific verison mysql you can using this command 
you can type version like this mysql:{verison mysql}

```
$ docker pull mysql:8.12
```

### verify image

can you verify image mysql is already in container using this command 

```
$ docker image ls
```

## run mysql in docker

you can run mysql in docker using this command

```
$ docker run --name mysql-container -e MYSQL_ROOT_PASSWORD=my-secret-pw -p 3307:3306 -d mysql:latest
``` 
### breakdown command 

inside run command mysql there is 

* *docker* 
this command using to call docker

* *run* 
    * using to create and run new container from image
* *--name* 
    * using to give name the new container that will be create
    * and this i want to name mysql-container

* *-e* or *--env* 
    * using to set env container
    * this case i want set mysql root pass using "my-secret-pw"

* *-p* or *--port*
    * using to set port to ekspose to out of container
    * you can using like this pattern expose-port:runing-port

* *-d* or *--detach*
    * using to run container in background and print id container

you run command you can check the container is already to runing or not using command 
and if you want to show all container include stopped container add *-a* in last command 

```
docker ps
```

*docker ps* will be to showing all your container runing 

## start and shut down container 

#### stopped container 

you can stop docker container using command using id *stop {id container}* or using name container *stop {name container}*

```
docker stop ${id or name container}
```
but from the above statment a question wil arise like 
can i stop the multiple docker container ?

the answer is yes, you can stop multiple container even you can stop the container after time you want using *-t milisecoond*
ohh i almost forgote to answer question, you can using command 

```
docker stop ${id or name container_1} ${id or name container_1} until you want...
```

but i have alternative to stop all docker container, you can use command 
*the fun fact this command can you use if you want to search problem in you company hehe.*

```
docker stop $(docker ps -q)
```
### start container

you can start docker container using command using id *start {id container}* or using name container *start {name container}*

```
docker start ${id or name container}
```

same with start container you can start multiple container using 

```
docker start ${id or name container_1} ${id or name container_1} until you want...
```

but i have alternative to start all docker container if you lazy to start one by one your container 
the command almost same with stop docker but you add *-a* in command *docker ps -q*

```
docker start $(docker ps -q -a)
```

### how to access mysql ?

to access mysql you can making sure the all step have done evrything, you can access same as usual
using command *mysql* and you must making sure in your local pc have been installed mysql

```
mysql -u root -h {docker ip} -P 3306 -p
```

* note : if you custome port use your custome port 
