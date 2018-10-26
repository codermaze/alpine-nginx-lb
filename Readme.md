# ALPINE based NGINX loadbalancer

alpine-nginx-lb is an alpine linux flavored docker container with nginx used to loadbalance applications with a minimal image with size less than 7MB.

build/sites.conf -> file is used to configure the uri paths of the applications to be load balanced.

docker-compose.yaml - is used to bring up application containers to be loadbalanced and also brings up the nginx container after all dependent containers are available.

## Start/stop using Docker-Compose?
### How to start
```
    docker-compose -f docker-compose.yml -p local-app-lb up -d
```

### How to stop
```
    docker-compose -f docker-compose.yml -p local-app-lb down
```

## Start/Stop using NPM
### How to start
```
    npm start
```

### How to stop
```
    npm stop
```

### URL's to be accessible by the loadbalancer

[Server 1 Direct](http://localhost:3200/ui/app/firstapp) 
[Server 2 Direct](http://localhost:3300/ui/app/secondapp) 
[Server 3 Direct](http://localhost:3400/ui/app/thirdapp) 

[Server 1 LB](http://localhost/ui/app/firstapp) 
[Server 2 LB](http://localhost/ui/app/secondapp) 
[Server 3 LB](http://localhost/ui/app/thirdapp) 
