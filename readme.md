# MySQL Database for Any Project

1. Go to the project directory of your desire. If you don’t have one, create a new directory called example-mysql and cd into it.

### This can be any directory of your desire, whether it’s a wordpress instance, node.js app, rails app, etc. Basically, wherever you run the commands to get your app up and running

2. Create a new file called docker-compose.yml in our example-mysql directory (or in your project directory of choice).

#### Input the following:

```bash
# Version 3 only recently came out, so we'll stick with 2 since it's
# tried and true at this point.  This would convert directly over to
# Version 3 anyway.
version: '2'

services:
  # Name of the service as Docker will reference.
  mysqlDb:

    # The image, change 5.7 to any of the supported docker versions.
    image: mysql:5.7

    # Required environment variables.  Creates a Database with a
    # root user, non-root user both with passwords.
    #
    # MYSQL_ROOT_PASSWORD defines the root password of the root user
    # MYSQL_DATABASE names the DB
    # MYSQL_USER is the non-root user
    # MYSQL_PASSWORD is the non-root user password
    environment:
      MYSQL_ROOT_PASSWORD: "rootpwd"
      MYSQL_DATABASE: "devdb"
      MYSQL_USER: "devuser"
      MYSQL_PASSWORD: "devpwd"


    ports:
      - 3306:3306

    # We're using a named volume here that docker manages for us.  This is a special
    volumes:
      - devmysqldb:/var/lib/mysql

# if you use a named volume, you must also define it here.
volumes:
  devmysqldb:


```

### Let’s start it up.

3. Open up your shell to this directory and simply run:

```bash
$ docker-compose up
```
