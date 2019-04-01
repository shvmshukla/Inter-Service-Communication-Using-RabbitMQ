# Inter-Service-Communication-Using-RabbitMQ

Links of tutorials -

1) https://www.rabbitmq.com/tutorials/tutorial-one-java.html
2) https://www.baeldung.com/rabbitmq


#############################################################################################################################
Making docker containers of my project
##############################################################################################################################

Shivams-MacBook-Pro:~ shivamshukla$ cd Documents
Shivams-MacBook-Pro:Documents shivamshukla$ ls
WS			WebEx			eclipse projects
Shivams-MacBook-Pro:Documents shivamshukla$ cd WS
Shivams-MacBook-Pro:WS shivamshukla$ ls
message		rabbitmq	receiver	send
Shivams-MacBook-Pro:WS shivamshukla$ cd rabbitmq
Shivams-MacBook-Pro:rabbitmq shivamshukla$ ls
dockerfile	lib		pom.xml		src		target
Shivams-MacBook-Pro:rabbitmq shivamshukla$ docker build -t rabbitpublish
"docker build" requires exactly 1 argument.
See 'docker build --help'.

Usage:  docker build [OPTIONS] PATH | URL | -

Build an image from a Dockerfile
Shivams-MacBook-Pro:rabbitmq shivamshukla$ docker build -t rabbitpublish .
Sending build context to Docker daemon  1.282MB
Step 1/4 : FROM openjdk:8-alpine
8-alpine: Pulling from library/openjdk
8e402f1a9c57: Pull complete 
4866c822999c: Pull complete 
0b0a34324bda: Pull complete 
5da56be406b8: Pull complete 
Digest: sha256:9209ebd07f09f2e0f0e8da0884573d852b2fccb05d176852aea94923aaeffbfe
Status: Downloaded newer image for openjdk:8-alpine
 ---> 6eb8392704ff
Step 2/4 : EXPOSE 9898
 ---> Running in a3e69a848ec1
Removing intermediate container a3e69a848ec1
 ---> 7355dc89eea0
Step 3/4 : ADD /target/rabbitmq-0.0.1-SNAPSHOT.jar rabbitmq-0.0.1-SNAPSHOT.jar
 ---> 2c065c614205
Step 4/4 : CMD ["java","-jar","rabbitmq-0.0.1-SNAPSHOT.jar"]
 ---> Running in 10ae5f6df168
Removing intermediate container 10ae5f6df168
 ---> c7bc04bad683
Successfully built c7bc04bad683
Successfully tagged rabbitpublish:latest
Shivams-MacBook-Pro:rabbitmq shivamshukla$ docker images
REPOSITORY                                 TAG                 IMAGE ID            CREATED             SIZE
rabbitpublish                              latest              c7bc04bad683        10 seconds ago      105MB
openjdk                                    8-alpine            6eb8392704ff        4 days ago          105MB
mysql/mysql-server                         latest              18c55bf778f5        8 weeks ago         288MB
mysql                                      latest              71b5c7e10f9b        2 months ago        477MB
hello-world                                latest              fce289e99eb9        3 months ago        1.84kB
ubuntu                                     latest              1d9c17228a9e        3 months ago        86.7MB
k8s.gcr.io/kube-proxy-amd64                v1.10.11            7387003276ac        4 months ago        98.3MB
k8s.gcr.io/kube-apiserver-amd64            v1.10.11            e851a7aeb6e8        4 months ago        228MB
k8s.gcr.io/kube-controller-manager-amd64   v1.10.11            978cfa2028bf        4 months ago        151MB
k8s.gcr.io/kube-scheduler-amd64            v1.10.11            d2c751d562c6        4 months ago        51.2MB
docker/kube-compose-controller             v0.4.12             02a45592fbea        6 months ago        27.8MB
docker/kube-compose-api-server             v0.4.12             0f92c77fa676        6 months ago        41.2MB
k8s.gcr.io/etcd-amd64                      3.1.12              52920ad46f5b        12 months ago       193MB
k8s.gcr.io/k8s-dns-dnsmasq-nanny-amd64     1.14.8              c2ce1ffb51ed        15 months ago       41MB
k8s.gcr.io/k8s-dns-sidecar-amd64           1.14.8              6f7f2dc7fab5        15 months ago       42.2MB
k8s.gcr.io/k8s-dns-kube-dns-amd64          1.14.8              80cc5ea4b547        15 months ago       50.5MB
k8s.gcr.io/pause-amd64                     3.1                 da86e6ba6ca1        15 months ago       742kB
prakhar1989/static-site                    latest              f01030e1dcf3        3 years ago         134MB
Shivams-MacBook-Pro:rabbitmq shivamshukla$ docker run -it rabbitpublish
no main manifest attribute, in rabbitmq-0.0.1-SNAPSHOT.jar
Shivams-MacBook-Pro:rabbitmq shivamshukla$ pwd
/Users/shivamshukla/Documents/WS/rabbitmq
Shivams-MacBook-Pro:rabbitmq shivamshukla$ ls
dockerfile	lib		pom.xml		src		target
Shivams-MacBook-Pro:rabbitmq shivamshukla$ cd target
Shivams-MacBook-Pro:target shivamshukla$ ls
archive-tmp						rabbitmq-0.0.1-SNAPSHOT
classes							rabbitmq-0.0.1-SNAPSHOT-jar-with-dependencies.jar
generated-sources					rabbitmq-0.0.1-SNAPSHOT.jar
generated-test-sources					surefire-reports
maven-archiver						test-classes
maven-status
Shivams-MacBook-Pro:target shivamshukla$ java -jar rabbitmq-0.0.1-SNAPSHOT-jar-with-dependencies.jar
Hello World!
Shivams-MacBook-Pro:target shivamshukla$ pwd
/Users/shivamshukla/Documents/WS/rabbitmq/target
Shivams-MacBook-Pro:target shivamshukla$ cd ..
Shivams-MacBook-Pro:rabbitmq shivamshukla$ cd ..
Shivams-MacBook-Pro:WS shivamshukla$ ls
message		rabbitmq	receiver	send
Shivams-MacBook-Pro:WS shivamshukla$ cd receiver
Shivams-MacBook-Pro:receiver shivamshukla$ docker build -t rabbitsubscribe .
Sending build context to Docker daemon  1.893MB
Step 1/4 : FROM maven:3.3.9-jdk-8
3.3.9-jdk-8: Pulling from library/maven
6d827a3ef358: Pull complete 
2726297beaf1: Pull complete 
7d27bd3d7fec: Pull complete 
e61641c845ed: Pull complete 
cce4cca5b76b: Pull complete 
6826227500b0: Pull complete 
c03b117ffd91: Pull complete 
821a1547b435: Pull complete 
2bd47f6b1b42: Pull complete 
e4cf3e9f705c: Pull complete 
3733107c5c01: Pull complete 
Digest: sha256:18e8bd367c73c93e29d62571ee235e106b18bf6718aeb235c7a07840328bba71
Status: Downloaded newer image for maven:3.3.9-jdk-8
 ---> 9997d8483b2f
Step 2/4 : EXPOSE 9999
 ---> Running in 9ae1d26a7096
Removing intermediate container 9ae1d26a7096
 ---> 5ad1958f96ba
Step 3/4 : ADD /target/microservice-starter-jetty-1.0.0-jar-with-dependencies.jar microservice-starter-jetty-1.0.0-jar-with-dependencies.jar
ADD failed: stat /var/lib/docker/tmp/docker-builder239855164/target/microservice-starter-jetty-1.0.0-jar-with-dependencies.jar: no such file or directory
Shivams-MacBook-Pro:receiver shivamshukla$ docker build -t rabbitsubscribe .
Sending build context to Docker daemon  1.893MB
Step 1/4 : FROM maven:3.3.9-jdk-8
 ---> 9997d8483b2f
Step 2/4 : EXPOSE 9999
 ---> Using cache
 ---> 5ad1958f96ba
Step 3/4 : ADD /target/receiver-0.0.1-SNAPSHOT.jar receiver-0.0.1-SNAPSHOT.jar
 ---> 97fba93a4e01
Step 4/4 : CMD ["java","-jar","receiver-0.0.1-SNAPSHOT.jar"]
 ---> Running in 71aaf004629a
Removing intermediate container 71aaf004629a
 ---> a1e17c4da406
Successfully built a1e17c4da406
Successfully tagged rabbitsubscribe:latest
Shivams-MacBook-Pro:receiver shivamshukla$ docker images
REPOSITORY                                 TAG                 IMAGE ID            CREATED             SIZE
rabbitsubscribe                            latest              a1e17c4da406        6 seconds ago       653MB
rabbitpublish                              latest              c7bc04bad683        18 minutes ago      105MB
openjdk                                    8-alpine            6eb8392704ff        4 days ago          105MB
mysql/mysql-server                         latest              18c55bf778f5        8 weeks ago         288MB
mysql                                      latest              71b5c7e10f9b        2 months ago        477MB
hello-world                                latest              fce289e99eb9        3 months ago        1.84kB
ubuntu                                     latest              1d9c17228a9e        3 months ago        86.7MB
k8s.gcr.io/kube-proxy-amd64                v1.10.11            7387003276ac        4 months ago        98.3MB
k8s.gcr.io/kube-apiserver-amd64            v1.10.11            e851a7aeb6e8        4 months ago        228MB
k8s.gcr.io/kube-controller-manager-amd64   v1.10.11            978cfa2028bf        4 months ago        151MB
k8s.gcr.io/kube-scheduler-amd64            v1.10.11            d2c751d562c6        4 months ago        51.2MB
docker/kube-compose-controller             v0.4.12             02a45592fbea        6 months ago        27.8MB
docker/kube-compose-api-server             v0.4.12             0f92c77fa676        6 months ago        41.2MB
k8s.gcr.io/etcd-amd64                      3.1.12              52920ad46f5b        12 months ago       193MB
k8s.gcr.io/k8s-dns-dnsmasq-nanny-amd64     1.14.8              c2ce1ffb51ed        15 months ago       41MB
k8s.gcr.io/k8s-dns-sidecar-amd64           1.14.8              6f7f2dc7fab5        15 months ago       42.2MB
k8s.gcr.io/k8s-dns-kube-dns-amd64          1.14.8              80cc5ea4b547        15 months ago       50.5MB
k8s.gcr.io/pause-amd64                     3.1                 da86e6ba6ca1        15 months ago       742kB
maven                                      3.3.9-jdk-8         9997d8483b2f        2 years ago         653MB
prakhar1989/static-site                    latest              f01030e1dcf3        3 years ago         134MB
Shivams-MacBook-Pro:receiver shivamshukla$ docker run -it rabbitsubscribe
no main manifest attribute, in receiver-0.0.1-SNAPSHOT.jar
Shivams-MacBook-Pro:receiver shivamshukla$ ls
dockerfile	lib		pom.xml		src		target
Shivams-MacBook-Pro:receiver shivamshukla$ cd target
Shivams-MacBook-Pro:target shivamshukla$ ls
archive-tmp						maven-status
classes							receiver-0.0.1-SNAPSHOT-jar-with-dependencies.jar
generated-sources					receiver-0.0.1-SNAPSHOT.jar
generated-test-sources					surefire-reports
maven-archiver						test-classes
Shivams-MacBook-Pro:target shivamshukla$ java -jar receiver-0.0.1-SNAPSHOT-jar-with-dependencies.jar
Hello World!
Shivams-MacBook-Pro:target shivamshukla$ 
#############################################################################################################################
