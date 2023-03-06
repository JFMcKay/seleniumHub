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
```
capabilities: [
    {
        maxInstances: 5,
        browserName: 'chrome',
        'goog:chromeOptions': {
        args: ['--headless', '--disable-gpu', '--no-sandbox', '--disable-dev-shm-usage']
    }
    },
    {
        maxInstances: 5,
        browserName: 'firefox',
        'moz:firefoxOptions': {
        args: ['--headless']
        }
    },
    {
        maxInstances: 5,
        browserName: 'edge',
        'ms:edgeOptions': { args: ['--headless']}
    }
  ],
```



