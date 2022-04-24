# Building Containers

These containers will be build at Host A. The public DNS seted for this machine is *rancher.dev-lbv.com.br*.

## Cloning from Git

´´´
cd ~
git clone https://github.com/leovardiero/DevOpsNinja.git
´´´

## Redis

The redis container is used for <>. 

```
cd ~/App/redis
docker build -t leovardiero/redis:devops .
docker run -d --name redir -p 6379:6379 leovardiero/redis:devops
docker ps
docker push leovardiero/redis:devops
```

## Node

The Node container is used for <>.

```
cd ~/App/node
docker build -t leovardiero/node:devops .
docker run -d --name node -p 8080:8080 --link redis leovardiero/node:devops
docker ps
docker push leovardiero/node:devops
```

## Nginx

The Nginx container is userd for <>

```
cd ~/App/nginx
docker build -t leovardiero/nginx:devops .
docker run -d --name nginx -p 80:80 --link node leovardiero/nginx:devops
docker ps
docker push leovardiero/nginx:devops
```

## Checking aplication

After up three containers, it is possible to access the link: *rancher.dev-lbv.com.br*
