hive-js
=======

Work in progress

## Development

### Grab the source

    git clone git@github.com:hivewallet/hive-js.git
    cd hive-js
    npm install

### Install Gulp globally

    npm install -g gulp

### Setup CouchDB

    brew install couchdb

__Enable CORS__

add the following config in `/usr/local/etc/couchdb/local.ini`:

    [httpd]
    enable_cors = true

    [cors]
    credentials = true
    origins = http://localhost:8080
    headers = accept, authorization, content-type, origin

If you want to be able to access the app from a mobile device on your local network, remember to add your host machine IP or alias to the cors origins list.

    origins = http://localhost:8080, http://192.168.1.109:8080, http://alice-computer.local:8080

__Start CouchDB__

    # start couchdb upon login
    ln -sfv /usr/local/opt/couchdb/*.plist ~/Library/LaunchAgents
    # kick it off
    launchctl load ~/Library/LaunchAgents/homebrew.mxcl.couchdb.plist
    open http://127.0.0.1:5984/_utils/index.html

Click on the bottom link "fix this" to create an admin user, say:

    username: admin
    password: password

### Profit

    DB_HOST=127.0.0.1 DB_PORT=5984 DB_USER=admin DB_PASSWORD=password gulp
    open http://localhost:8080

