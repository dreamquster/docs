# Quick Start

## Run TiDB with Docker (Standalone mode)

You can quickly test TiDB with Docker. The source repository contains the Dockerfile which contains local tidb-server.

To install Docker on your system, you can read the document on https://docs.docker.com/

```
docker pull pingcap/tidb:latest
docker run --name tidb-server -d -p 4000:4000 pingcap/tidb:latest
```

`docker pull` may take a while to download images ~560M.

Then you can use official mysql client to connect to TiDB.

```
mysql -h 127.0.0.1 -P 4000 -u root -D test --prompt="tidb> "  
```

**Notice:** Mac OS X user can use `docker-machine ip`.

## Or run a TiDB cluster

Read the documents for [binary deployment](https://github.com/pingcap/docs/blob/master/op-guide/binary-deployment.md) or [docker deployment](https://github.com/pingcap/docs/blob/master/op-guide/docker-deployment.md).

## Prerequisites

Go environment. Currently a 64-bit version of go >= 1.8 is required.
```
git clone https://github.com/pingcap/tidb.git $GOPATH/src/github.com/pingcap/tidb
cd $GOPATH/src/github.com/pingcap/tidb
make
```

## Run as a MySQL protocol server

```
make
cd bin && ./tidb-server
```

In case you want to compile a specific location:

```
make server TARGET=$GOPATH/bin/tidb-server
```

The default server port is `4000` and can be changed by flag `-P <port>`.

Run `./tidb-server -h` to see more flag options.

After you started tidb-server, you can use a MySQL client to connect to TiDB.

```
mysql -h 127.0.0.1 -P 4000 -u root -D test --prompt="tidb> " 
```
