# wpdc-wordmove

## Setup

Install docker and docker-compose to your OS.    
https://docs.docker.com/install/    
https://docs.docker.com/compose/install/

Run `docker -v && docker-compose -v` to check if you already have installed Docker and docker-compose.

Edit `.env` to configration.

If installed, just run `docker-compose up -d` after running Docker.

Develop below by default    
http://localhost:3000

## Deploy

First, enter into container

```
$ sh wormove.sh
```

And then setup SSH first.

```
# Launch ssh-agent
$ ssh-agent bash

# Add ssh-agent (configure key if needed)
$ ssh-add /home/.ssh/id_rsa
```

The following command pushes all data to the production including database and all files.

**Note: The command will override the files, therefore, make sure you don’t have any important files inside your production directory.**

```
$ wordmove push -e production --all
```

When you want to pull data from the production, you can use the following command.

```
$ wordmove pull -e production --all
```

You can even push/pull only the specific part of data using flags.

```
--all # All files and data
-w    # Only the '/wp-content/' directory
-u    # Only the '/wp-content/upload/' directory
-t    # Only the '/wp-content/theme/ directory
-p    # Only the '/wp-content/plugins/' directory 
-l    # Only the '/wp-content/language/' directory
-d    # Only the databse
-s    # dry run (does not actually transfer the files)
-e    # Specifies the environment to push or pull
-c    # Only the 'wp-config.php' file
```

You can learn more about the options in their documentation.

welaika/wordmove — Usage and flags explained:    
https://github.com/welaika/wordmove/wiki/Usage-and-flags-explained

## Reference

(WordPress) WordPress Development with Docker-Compose and Wordmove:    
https://medium.com/@KentaKodashima/wordpress-wordpress-development-with-docker-compose-and-wordmove-cf720d2618d