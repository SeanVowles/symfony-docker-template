# Get started
## Building the container
The contents of the container is already configured in the relevent Dockerfiles. Docker compose will take care of constructing the containers.

Start by building the containers.
```
docker-compose -d --build
```

## Installing symfony
Create a new directory called `symfony`.

You're folder structure should look like:
```
docker
  ...
symfony
  ...
README.md
```

Firstly we want to install symfony via the container... Our compose file is already aware of the volumes and bind mounts, so the files will appear straight back in our host machine.

```
docker exec -it  symfony-docker_php_1 bash
```

We are now inside the symfony docker php container on the bash cmdline.

Symfony will only correctly install if the container your installing on knows which git account to link to.
```
*** Please tell me who you are.
Run
git config --global user.email "you@example.com"
git config --global user.name "Your Name"
to set your account's default identity
```

Now we can install Symfony

* Get the symfony cli installed on the container using curl
* mv the symfony cli to the /usr directory (make it globally available)
* install symfony ... This example will go for the minimal install

```
curl -sS https://get.symfony.com/cli/installer | bash
mv /root/.symfony/bin/symfony /usr/local/bin/symfony
symfony new symfony --dir=/var/www/symfony
```
