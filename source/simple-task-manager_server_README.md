# Server

The server is written in go (aka golang) so you need to install go and setup your development environment (paths, IDE, etc.)

# Setup environment

## 1. Requirements

* Installed and working go compiler (1.12 or newer to have module support)
* For the database do **one** of the following: 
    * Install and setup docker daemon (for the PostgreSQL database; setup is described later)
    * Directly install and setup PostgreSQL server (9.6 and newer should work)
* And of course an working IDE setup of your choice (I can recommend *GoLand* as fancy-pants, *LiteIDE* as pure open-source and of course *vim* as hard-core IDE)

## 2. Dependencies

**tl;dr:**
* If you use go version < 1.12 : the whole go module stuff doesn't work for you, so make sure the packages listed below are installed
* If you use go version >= 1.12 : nothing to do here

This project uses the **go module** infrastructure, so e.g. `go build` installs all dependencies for you.
The frameworks/libraries this project uses are there in order to make the development easier:

* [gorilla/mux](https://github.com/gorilla/mux) to easily create simple rest endpoints
* [gorilla/websocket](https://github.com/gorilla/websocket) for server → client communication
* [kurrik/oauth1a](https://github.com/kurrik/oauth1a) for the oauth1a authentication
* [lib/pq](https://github.com/lib/pq) for a postgres database driver
* [pkg/errors](https://github.com/pkg/errors) better error handling and enables us to show stack traces
* [hauke96/sigolo](https://github.com/hauke96/sigolo) for logging
* [hauke96/kingpin](https://github.com/hauke96/kingpin) for cli parameter and flag parsing

## 3. Setup the Database

The server requires a database called `stm` with the required tables as described below.
This description assumes that you use docker instead of an direct installation of PostgreSQL.

### Set Database user/password as environment variable

**tl;dr:**
* `export STM_DB_USERNAME=postgres STM_DB_PASSWORD=geheim`

If you want to run test expressed below, user and password must be as same as the above.

If you want to run it as public site, you should change to your own **unique and secure** password.

### Start as docker container

**tl;dr:**
* `docker-compose up --build stm-db`
* done

The `docker-compose.yml` defines such container, just execute `docker-compose up --build stm-db` to start it.

### Initialize database 

**tl;dr:**
* Make sure `psql` is installed
* start database (if not already running)
* `cd server/database/`
* `./init-db.sh`
* done

The folder `server/database/` contains the script `init-db.sh`.
Start your database and call this script (from within that folder).

You need the tools `createdb` and `psql`. Both are - for ubuntu users - available in the package `postgresql-client`.

### Reset database

**tl;dr:**
* `psql -h localhost -U postgres -c 'DROP DATABASE stm;'`
* `cd server/database`
* `./init-db.sh`
* done

This is just needed if you want to get rid of the current data (e.g. after testing).

## 4. Setup the Login

There are two approaches:

1. OSM dev-API with a real account
2. Local fake-Server emulating the OSM API

### With OSM dev-API

The default config of the server uses the [development API of OSM](https://master.apis.dev.openstreetmap.org).
So you need to have an account there and also need to register your local application the to get the OAuth credentials.

#### OSM OAuth credentials

To perform a login (even a login of your locally running application), you'll need OAuth credentials (so the OAuth consumer-key and -secret) within environment variables:

* `export OAUTH_CONSUMER_KEY="Eln7...rY66"`
* `export OAUTH_SECRET="fgg1...kl09"`

You can export these variables each time you start a new terminal or just put it into a file of your choice (e.g. `.bashrc`) to load then e.g. after your system booted.

### Local Auth-Server

There's also a pure local config.
This makes use of a very simple [OAuth-Dummy server](https://github.com/hauke96/osm-oauth1a-dummy).
Just clone the repo and start this auth server with `go run .`.

Using this approach makes you independent of the OSM server and of an internet connection in general.

**Notice:**<br>
You have to use the `local.config` file to use this locally running OAuth server, so use `go run . -c config/local.json` to start the server.

## 5. Setup finished :)

Now you can start database, server (s. below) and the client (s. [README](../../client) in the `client` folder) and access the STM application under `localhost:4200`.
Everything should work now and if not, don't hesitate to raise an issue :)

# Run server

After these variables are visible, start the server:

* `cd server`
* `go run .`

The server starts under port `8080` and has an info page to check if it's running: [localhost:8080/info](http://localhost:8080/info)

# Run Tests

Use the `server/test/run.sh` script to run tests and provide the database with dummy data (required for the tests).
This script will setup the database in a docker container, fill the database with dummy data and executes the tests.

**Warning:**
This script will remove your `postgres-data` folder created by the `stm-db` docker container.

**tl;dr:**
* `cd server/test`
* `./run.sh`
* done

# Build

**tl;dr:**
* `cd server`
* `go build .`
* done

However, I don't use this in practice as the `Dockerfile` for the server uses `go run` to build and directly start the server.

# Configuration

There are configuration files in the folder `./server/config/`.
Until there's further documentation, just take a look, the properties are quite simple and straight forward.
For local development, you don't need to change anything there.

# HTTPS

I only tried it with *let's encrypt* certificates.
At least for them, you only need to set the following properties in your configuration (next to the others of course):

```json
{
	"server-url": "https://your.domain.com",
	"ssl-cert-file": "/etc/letsencrypt/live/your.domain.com/fullchain.pem",
	"ssl-key-file": "/etc/letsencrypt/live/your.domain.com/privkey.pem",
	...
}
```

**Important:** The `server-url` property has to begin with `https` in order to activate HTTPS.

For **further information**, take a look at the `doc/operation/ssl-cert.md` file.

# Development

## Error handling

Whenever an error from a library/framework (e.g. in a database store) is returned, wrap it using `errors.Wrap(err)` (from the `github.com/pkg/errors` package) and return that.
This will later result in a nice stack trace when the HTTP response is created.
All other places just return the error because it's already wrapped (and therefore will already produce a stack trace).

New errors should also be created using `errors.New(...)`.

Whenever catching, creating or wrapping an error, feel free to print additional information using `sigolo.Error(...)`. 