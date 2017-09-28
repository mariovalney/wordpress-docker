# WordPress Docker

Welcome to the Source.

## Docker

Docker is a software technology providing containers, promoted by the company Docker, Inc. Docker provides an additional layer of abstraction and automation of operating-system-level virtualization on Windows and Linux.

## Initial Requirements

* Install Docker: https://docs.docker.com/engine/installation/

* Install Docker-compose: https://docs.docker.com/compose/install/

## Starting Your Project

1. Fork this repository or download a zip.
1. Go to directory
1. Start docker-compose with `docker-compose up`

## Tips

### Host

Add a hostname to your docker IP.

1. Get the container ID (first column): `docker ps`
1. Inspect container: `docker inspect <container ID>`
1. Go to your host file and add it (I always use dev subdomain)

### WP Config


This will be your config to WP:
(with DEBUG)

```
/** The name of the database for WordPress */
define('DB_NAME', 'wordpress');

/** MySQL database username */
define('DB_USER', 'root');

/** MySQL database password */
define('DB_PASSWORD', 'wordpress');

/** MySQL hostname */
define('DB_HOST', 'db:3306');

/** Database Charset to use in creating database tables. */
define('DB_CHARSET', 'utf8');

/** The Database Collate type. Don't change this if in doubt. */
define('DB_COLLATE', '');

/** Make sure you can download stuff **/
define('FS_METHOD', 'direct');

/** Everyone loves DEBUG **/
define( 'WP_DEBUG', true );
define( 'SCRIPT_DEBUG', true );
define( 'WP_DEBUG_LOG', true );
define( 'WP_DEBUG_DISPLAY', false );
```

### File Permission

If you have problems with file/folder permission you can add your user to `www-data` group and define the folder owner (recursively) to `youruser:www-data`.

Then you can give 775/664 permission to WP files:

```
sudo find . -type d -exec chmod 775 {} \; && sudo find . -type f -exec chmod 664 {} \;
```
