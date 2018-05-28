P2P Cloud
===================

[![Build Status - master](https://api.travis-ci.org/subutai-io/p2p.png?branch=master)](https://travis-ci.org/subutai-io/p2p) 
[![Build status](https://ci.appveyor.com/api/projects/status/1qyikpu9x3ecn8ay/branch/master?svg=true)](https://ci.appveyor.com/project/crioto/p2p/branch/master)
[![codecov](https://codecov.io/gh/subutai-io/p2p/branch/master/graph/badge.svg)](https://codecov.io/gh/subutai-io/p2p)
[![Go Report Card](https://goreportcard.com/badge/github.com/subutai-io/p2p)](https://goreportcard.com/report/github.com/subutai-io/p2p)
[![GoDoc](https://godoc.org/github.com/subutai-io/p2p?status.svg)](https://godoc.org/github.com/subutai-io/p2p)

P2P Cloud project allows users to build their private networks. 

Building
-------------------

p2p is shipped with a Makefile, so building it a pretty easy task. You just run
```
make
``` 
command to buld a single binary for current platform or you can try to
```
make all
```
in order to build p2p for linux, windows and macos

Running
-------------------

> **MacOS** users should install [TUN/TAP driver](http://tuntaposx.sourceforge.net) and create a config.yaml file with the following line: ``` iptool: /sbin/ifconfig ```

> **Windows** users should install [TAP-windows NDIS6](https://openvpn.net/index.php/open-source/downloads.html) driver from OpenVPN suite

p2p is managed by a daemon that controls every instance of your private networks (if you're participating in a different networks at the same time). To start a daemon simply run *p2p daemon* command. Note, that application will run in a foreground mode. 

```
p2p daemon
```

Now you can start manage the daemon with p2p command line interface. To start a new network or join existing you should run p2p application with a -start flag.

```
p2p start -ip 10.10.10.1 -hash UNIQUE_STRING_IDENTIFIER
```

You should specify an IP address which will be used by your virtual network interface. All the participants should have an agreement on ranges of IP addresses they're using. In the future this will become unnecessary, because DHCP-like service will be implemented.

With a -hash flag user should specify a unique name of his network. 

Instance of P2P network can be stopped with use of stop command

```
p2p stop -hash UNIQUE_STRING_IDENTIFIER
```

To learn more about available commands run

```
p2p help
```

or append name of command to print detailed help about this command. For example:

```
p2p help daemon
```

will display detailed information about *daemon* command

Development & Branching Model
-------------------

* 'master' is always stable. 
* 'dev' contains latest development snapshot that is under heavy testing
