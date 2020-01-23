# Composer
**The [Composer PHP Dependency Manager](https://getcomposer.org/) in a lightweight Debian based container.**

Composer do not release a Docker image tag for every version of PHP, this can lead to issues with their underlying PHP version, with it being either too old, or too new for your dependencies.

I like to run everything I can within Docker, that way when I'm switching between Mac & Linux, I have exactly the same environment. That's why I've built this repository and the subsequent images on [DockerHub](https://hub.docker.com/r/containphp/composer/tags).

I'm currently building an automated way to create every combination of PHP and Composer version as they're released. However, for the moment please open an [issue](https://github.com/containphp/composer/issues/new?labels=build-request&title=Build%20Request&body=Specify%20the%20versions%20of%20PHP%20and%20Composer%20you%20require%20here&assignees=mattsbanner) should you require a version I haven't built. I'll get to it as soon as possible.

## Executing Composer
To execute Composer within Docker, you first need to decide on a Docker image [tag](https://hub.docker.com/r/containphp/composer/tags) to use. They're all named appropriately depending on which versions of Composer and PHP they contain. The `latest` branch will always be set to whatever I'm using at the time if you're not fussy!

There's no need for the `composer` prefix as that's where the container starts. 

**Composer Install**
```sh
$ docker run --rm -it -v $PWD:/app containphp/composer:latest install
```

**Composer Update**
```sh
$ docker run --rm -it -v $PWD:/app containphp/composer:latest update
```
You get the gist, change the last word for any composer command you wish to run.

## Alias It!
That's a pretty lengthy command to have to type every time you need to update some packages. Therefore I have this aliased to the command `composer` on my machine. I've actually uninstalled Composer locally; yet I can still run `composer install` just like anyone else.

```
alias composer='docker run --rm -it -v $PWD:/app containphp/composer:latest'
```
