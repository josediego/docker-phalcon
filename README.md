# Docker Phalcon

Container for docker and Phalcon development.

## Getting Started

This repo contains a implementation of micro application writen with Phalcon, for more information see the tree bellow

Clone the repo and be sure to have installed the prerequisites software, after that be sure to have the **docker** service up and running

### Prerequisites

- [Docker](https://docs.docker.com/install/)
- [Docker Compose](https://docs.docker.com/compose/install/)

### Folders structure

```
docker-phalcon
├── code
│   ├── .htaccess
│   ├── index.php # Micro Phalcon Application
│   ├── phpinfo.php # This is an internal file and it's not exposed through nginx
├── dockers
│   ├── phalcon
│   │   ├── Dockerfile # Custom build image for phalcon based on php:7.2-fpm
└── nginx
    ├── conf.d
    │   └── default.conf # Config file for nginx
    └── logs
        └── access.log # logs for nginx access
        └── error.log # logs for nginx errors

```

### How to up the server

Be sure to be located inside the cloned folder, then run

```
$ docker-compose build
$ docker-compose up -d
```

Once you see a message like the one bellow open you browser and go to [localhost:9999](http://localhost:9999)

```
Creating php ... done
Creating nginx ... done
Attaching to php, nginx
```

Now you can start playing, these are the endpoints and parameters expected for the micro phalcon app:

| Method | Endpoint                  | Body parameters | Description                                       |
| ------ | ------------------------- | --------------- | ------------------------------------------------- |
| GET    | /                         | \-              | Returns a welcome message                         |
| GET    | /say/hello/{name: String} | \-              | Given a name returns a salute and your IP address |
| POST   | /store/something          | name: String    | Given a name returns a salute                     |

If you want to kill the container you must run

```
$ docker-compose down
```

### How to run code inside a container

Let's say you want to run some code inside **php** container, in order to access to bash inside that container you need to run:

```
$ docker exec -it php bash
```

_Note: Make sure php container is up and running before run this command, otherwise it's going to fail_
