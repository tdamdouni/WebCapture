# Using Docker to Create a MySQL Server

_Captured: 2017-11-03 at 18:39 from [dzone.com](https://dzone.com/articles/using-docker-to-create-a-mysql-server?edition=334833&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202017-11-03)_

When working on test code on my computer, I usually use the built-in PHP server (`php -S`), which works nicely. Every so often, I need access to MySQL and I use Docker to temporarily create a MySQL server for me. This is how I do it.

The magic command is:
    
    
      -e MYSQL_USER=rob -e MYSQL_PASSWORD=123456 -e MYSQL_DATABASE=bookshelf \

This creates a Docker container called `mysql` on port 3306. We pass three environment variables: `MYSQL_USER`, `MYSQL_PASSWORD`, and `MYSQL_DATABASE`, which are our credentials and the database name.

## Client Access to the Database

If you have the MySQL command line client installed, you can access your database like this:

We need to use TCP protocol as there's no socket in play here. If, like me, you're too lazy to type `\--protocol=TCP` each time, then set it in your `~/.my.cnf` file like this:

`~/.my.cnf`:

One of the easier ways to get a MySQL command line client on a Mac is to install [MySQL WorkBench](https://www.mysql.com/products/workbench/) and add `/Applications/MySQLWorkbench.app/Contents/MacOS` to the path, as Homebrew seems to want to install the server, too.

## Controlling the Container

Stop the container using `docker stop mysql` and restart it again with `docker start mysql`. When you're finished with it, you can delete it with `docker rm mysql`.

## Restoring a Dump File

As these MySQL instances are temporary for me, I install a database schema using:

(Obviously, you'd use same credentials as you ran your container with!)

## Fin

That's all there is to having a temporary MySQL install running locally for development.
