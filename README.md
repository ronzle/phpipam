<h2>phpipam</h2>

Container for PHPIPAM (http://phpipam.net/) 

<h3>Features</h3>

- configurable ssl support
- configurable mysql environment variables

<h3>Dependencies</h3>

Web Server

```
rlaborius\web
```

MySQL Server

```
rlaborius\mysql
```

<h3>Run with fig</h3>

1. create a ```fig.yml```

```yaml
phpipam:
  image: rlaborius/phpipam
  links:
    - mysql
  # comment out if the contain will not run behind a proxy
  #ports:
  #  - "80:80"
  #  - "443:443"
  environment:
    - MYSQL_HOST=mysql
    - MYSQL_USER=phpipam
    - MYSQL_PASSWORD
    - MYSQL_DB=phpipam
    - SSL_CN
    - VIRTUAL_HOST
    - VIRTUAL_PORT
  volumes:
    - /home/core/docker/phpipam/http_data:/etc/apache2/certs
mysql:
  image: rlaborius/mysql
  volumes:
    - /home/core/docker/phpipam/mysql_data:/var/lib/mysql
  environment:
    - MYSQL_ROOT_PASSWORD
```

2. Start the container with following command

behind a proxy
```
MYSQL_ROOT_PASSWORD=YOURPASS MYSQL_PASSWORD=YOURPASS SSL_CN=sub.example.com VIRTUAL_HOST=sub.example.com  ./fig up -d

```

standalone
```
MYSQL_ROOT_PASSWORD=YOURPASS MYSQL_PASSWORD=YOURPASS SSL_CN=sub.example.com ./fig up -d

```

```

MYSQL_ROOT_PASSWORD sets a root password in mysql (only if you use rlaborius\mysql) 

```
```

MYSQL_PASSWORD sets a password fuer db phpipam (only if you use rlaborius\mysql)

```
```
SSL_CN sets the CommonName for the new generated certificate 

```
```

VIRTUAL_HOST is needed if you use a proxy 

```

<h3>Used Proxy</h3>

``` jwilder/nginx-proxy:latest ```
