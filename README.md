NOTE: We'd moved this repo to https://github.com/weesan/es_cli

# es

A Python script to manage Elasticsearch clusters via a set of RESTful APIs.

## Usage

```
$ es [options] command [argv1] [argv2] ...
```

## To find out all the supporting commands

```
$ es help
```

## Some examples

### To check out the health of an ES cluster:

```
$ es -s localhost -p 9200 -u username -P passwd health
```

To avoid typing `-s`, `-p`, `-u` and `-P` all the time, one can set
the enviroment variables: `ES_SERVER`, `ES_PORT`, `ES_USERNAME` and
`ES_PASSWORD` respectively:

```
$ export ES_SERVER=localhost
$ export ES_PORT=9200
$ export ES_USERNAME=username
$ export ES_PASSWORD=passwd
$
$ es health
```

Please note that `ES_SERVER` and `ES_PASSWORD` is set to `localhost`
and `9200` respectively by default.

### To find out the equivalent `curl` command for `es health`

```
$ es -v health
```

### To check the state of the ES cluster

```
$ es state
```

### To find out which shards are `UNASSIGNED`

```
$ es shards | grep "UNASSIGNED"
```

### Some unix-like commands which treat the indices as "files"

For example, if you have an index called `stores`, you may use the
commands as follows:
```
$ es ls
$ es cat stores
$ es grep "nike" stores
$ es rm stores
```

The command `ls`, `cat`, `grep`, `rm` are similar to the unix-like
commands and should be self-explanatory.

Note that **"es rm stores"** can actually delete the index
`stores` from the ES cluster.  Please use it with care and your
own risk.
