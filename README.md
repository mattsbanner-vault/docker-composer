# Composer
**Composer in a lightweight Debian based container.**

I like to run everything I can within Docker, that way when I'm switching between Mac & Linux, I have exactly the same environment. That's why I've built this repository and the subsequent images on [DockerHub](https://hub.docker.com/r/mattbanner/composer/tags).

## Executing Composer
To execute Composer within Docker, you first need to decide on a Docker image [tag](https://hub.docker.com/r/mattbanner/composer/tags) to use. They're all named appropriately depending on which versions of PHP and Composer they contain.

There's no need for the `composer` prefix as that's where the container starts. 

## Executing

```shell script
$ docker run --rm -it -v $PWD:/app mattbanner/composer:7.3-1.9.1 install
```

## Alias It!
That's a pretty lengthy command to have to type every time you need to install some packages. Therefore I have this aliased to the command `composer` on my machine. I've actually uninstalled Composer locally; yet I can still run `composer install` just like anyone else.

```
alias npm='docker run --rm -it -v $PWD:/app mattbanner/composer:7.3-1.9.1 install'
```
