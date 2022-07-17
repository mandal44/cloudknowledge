
1. rsync -avh /var/lib/jenkins/workspace/cloudknowledge-job/Dockerfile root@172.31.95.120:/opt   ---- ansible server private ip (ssh on jenkins)
   

2. cd /opt  ---- (ssh on ansible)

docker image build -t $JOB_NAME:v1.$BUILD_ID .
docker image tag $JOB_NAME:v1.$BUILD_ID mandal44/$JOB_NAME:v1.$BUILD_ID
docker image tag $JOB_NAME:v1.$BUILD_ID mandal44/$JOB_NAME:latest
docker image push mandal44/$JOB_NAME:v1.$BUILD_ID
docker image push mandal44/$JOB_NAME:latest
docker image rmi $JOB_NAME:v1.$BUILD_ID mandal44/$JOB_NAME:v1.$BUILD_ID mandal44/$JOB_NAME:latest



3. ansible-playbook /sourcecode/docker.yml  --- (post build ssh on ansible to run container on docker-host/webserver)
