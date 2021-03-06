## hk

Fast Heroku client.


### Overview

hk is a command line client to the Heroku runtime platform, designed to be as fast as possible.


### Notice

It doesn't work yet, and doesn't implement all of the described commands.


### Motivation

```bash
$ time heroku version
2.25.0
real	0m1.376s

$ time hk version
0.0.1
real	0m0.015s

$ time heroku ps -a morning-snow-4357 > /dev/null
real	0m2.057s

$ time hk ps -a morning-snow-4357 > /dev/null
real	0m0.763s

$ time heroku list > /dev/null
real	0m10.142s

$ time hk list > /dev/null
real    0m1.828s
```


### Installation

```bash
$ wget -qO- https://hk.heroku.com/hk.gz | zcat >/usr/local/bin/hk
$ chmod +x /usr/local/bin/hk
```


### Usage

```bash
$ hk help
Usage: hk <command> [-a <app>] [command-specific-options]

Supported hk commands are:
  addons          List add-ons
  addons-add      Add an add-on
  addons-open     Open an add-on page
  addons-remove   Remove an add-on
  create          Create an app
  destroy         Destroy an app
  env             List config vars
  get             Get config var
  help            Show this help
  info            Show app info
  list            List apps
  login           Log in
  logout          Log out
  logs            Show logs
  pg              List databases
  pg-info         Show database info
  pg-promote      Promote a database
  ps-psql         Open a psql database shell
  pg-wait         Await a database
  ps              List processes
  release         Show release info
  releases        List releases
  rename          Rename an app
  restart         Restart processes
  rollback        Rollback to a previous release
  run             Run a process
  set             Set config var
  scale           Scale processes
  stop            Stop a process
  token           Show auth token
  unset           Unset config vars
  version         Display version

See 'hk help <command>' for more information on a specific command.
```


### Development

```bash
$ cd hk
$ go get
$ mate main.go
$ go build
$ ./hk list
```

### Release

```bash
$ cd hk
$ vim main.go # edit Version
$ go build
$ ./mkpatch
# put OS-ARCH-hk.gz and OS-ARCH-VER-next.hkdiff online
```

### Design

We maintain a collections of `hk` terminal interactions in [DESIGN.md](hk/blob/master/DESIGN.md), from which you can get a sense of the tool's style.
