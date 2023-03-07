# Selenium Grid with Docker and WebdriverIO setup
You can use this repo to setup a selenium grid with docker and webdriverIO.  This is a work in progress and will be updated as I learn more about webdriverIO and docker. You will need to install docker compose if you don't have it before using the docker-compose.yml which is the easiest way to setup the docker containers after putting the yaml file wherever you want to run it from use the following command:

```docker-compose -f docker-compose.yml up```

To stop it, hit Ctrl+C

```docker-compose -f docker-compose.yml down```

These only allow for 1 instance of each nod

# Setup in webdriverIO
These are some of the steps to setup webdriverIO with docker service to work with selenium grid.  This is a work in progress and will be updated as I learn more about webdriverIO and docker.

## Initialize webdriverIO in current directory
```npm init wdio .```

## You can also install webdriverIO and create a new project with 
```npm init wdio ./path/to/my/project```

## Install webdriverIO docker service
```npm install wdio-docker-service --save-dev```

## Add docker service to wdio.conf.js

``` services: ['docker'], // add docker service to services array ```

## Add server options to wdio.conf.js (I think there is another way to do this but this is the way I did it)
```
hostname: HOSTNAME,
ports: PORT,
path: '/',  // for root path
```


## Add browser options to wdio.conf.js

I can't seem to get edge to work with docker.  I think it is because of the way the docker image is setup.  I will try to figure it out later. 

```
capabilities: [
    {
        maxInstances: 5,
        browserName: 'chrome',
        'goog:chromeOptions': {
        args: ['--disable-dev-shm-usage']
    }
    },
    {
        maxInstances: 5,
        browserName: 'firefox',
    },
    {
        maxInstances: 5,
        browserName: 'MicrosoftEdge',
    },
  ],
```



