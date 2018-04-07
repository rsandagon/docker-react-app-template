# Docker React Template

## Setup
1. Install Docker and docker-compose.
1. Run `docker-compose up -d --build`. This will build the environment.

## Dev
1. Spin the container,  `docker-compose start`
1. To stop, `docker-compose stop`
1. To restart, `docker-compose start`
1. To remove the container, `docker-compose down`

## Production
1. Fire up the container, `docker-compose -f docker-compose-prod.yml up -d --build`
1. To stop, `docker-compose stop`
1. To restart, `docker-compose start`
1. To remove the container, `docker-compose down`

## React Router and Nginx
If you are using react router and nginx,

1. Change the default nginx config:
```sh
RUN rm -rf /etc/nginx/conf.d
COPY conf /etc/nginx
```
1. Use the file `Dockerfile-prod-with-react-router`
1. Create the following folder structures along with the `default.conf` file:
```
└── conf
    └── conf.d
        └── default.conf
```

`default.conf`: 

```
server {
  listen 80;
  location / {
    root   /usr/share/nginx/html;
    index  index.html index.htm;
    try_files $uri $uri/ /index.html;
  }
  error_page   500 502 503 504  /50x.html;
  location = /50x.html {
    root   /usr/share/nginx/html;
  }
}
```

## Deploy
[How to deploy to AWS](https://github.com/julianespinel/stockreader/wiki/Deploy-to-AWS-using-docker-machine-and-docker-compose)

### This project was bootstrapped with [Create React App](https://github.com/facebookincubator/create-react-app)
### with the help from M. Herman's [article](http://mherman.org/blog/2017/12/07/dockerizing-a-react-app/)

