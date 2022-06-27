# -docker-exe2
FROM  fabric8/tomcat-9
COPY  webapp.war /opt/tomcat/webapps/
docker build -t tomcat:v1 .
docker inspect tomcat:v1
docker run -d -p 20200:8080 tomcat:v1
docker run -d -p 9000:9000 -v /var/run/docker.sock:/var/run/docker.sock portainer/portainer -H unix:///var/run/docker.sock

vi /opt/tomcat/conf/tomcat-users.xml

docker login -u <docker_hub_username> -p password

docker image tag tomcat:v1 <username>/tomcat

docker push <docker_hub_username>/tomcat

<ip_adress>:5000/v2/_catalog
