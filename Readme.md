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


### Multiple sites with multiple docker containers 

#### Add below to hosts file
127.0.0.1 qa1.test.com
127.0.0.1 qa1a.test.com
127.0.0.1 qa2.test.com
127.0.0.1 qa2.internal.test.com

Adding above hosts are to have those sample domains working on local machines. If you make any changes to the host names, also modify the same in conf.d file in build/loadbalancer/conf.d.

For real domains that can be resolved, shouldn't need these to be added to hosts file or to the conf.d file.

#### Now only below urls will work
http://qa1.test.com:8000/ui/app/firstapp
http://qa2.test.com:8000/ui/app/secondapp
http://qa2.internal.com:8000/ui/app/thridapp

PORT 8000 is used for test purposes, so, we dont have any other port conflicts when running locally with port 80.
try the above domain combinations with different paths will throw 404.
