ramona
======

Your next favorite supervisor component.

Ramona is an enterprise-grade **runtime supervisor** that allows controlling and monitoring software programs during their execution life cycle.
It is heavily influenced by [supervisord](https://github.com/Supervisor/supervisor) but this is actually written from scratch due to different requirement set.

It is primarily meant to be blended into your project source code set to provide supervisor/console functionality of init.d-like start/stop control, task frontend (e.g. unit/functional/performance test launcher) and other command-line oriented features. It should ideally represent the only executable of the project - kind of 'dispatcher' to rest of a project. It is design the way that you should be able to extend that easily if needed (e.g. to include your own tasks).

It is implemented in Python but it is not limited to be used only in Python projects.

Target platforms are all modern UNIXes, BSD derivates and Windows.

Quick introduction
------------------

Let's assume your project (named _foo_) directory looks as follow:
```shell
foo/
	bin/
	share/
	src/
	docs/
	foo.py <--- this is Ramona console
	foo.conf
```

Ramona system will the provide you with following command-line API:
```
$ ./foo.py --help
usage: foo.py [-h] [-c CONFIGFILE] [-d] [-s]
               {start,stop,restart,status,help,console,server,clean,unittests}
               ...

optional arguments:
  -h, --help            show this help message and exit
  -c CONFIGFILE, --config CONFIGFILE
                        Specify configuration file(s) to read (this option can
                        be given more times). This will override build-in
                        application level configuration.
  -d, --debug           Enable debug (verbose) output.
  -s, --silent          Enable silent mode of operation (only errors are
                        printed).

subcommands:
  {start,stop,restart,status,help,console,server,clean,unittests}
    start               Launch subprocess(es)
    stop                Terminate subprocess(es)
    restart             Restart subprocess(es)
    status              Show status of subprocess(es)
    help                Display help
    console             Enter interactive console mode
    server              Launch server in the foreground
    clean               Clean project directory from intermediate files
    unittests           Seek for all unit tests and execute them
```
