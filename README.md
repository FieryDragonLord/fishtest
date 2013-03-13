# Overview
Fishtest is a distributed task queue for testing chess engines.  It is currently being used
for testing changes on Stockfish with tens of thousands of games per change. The following
setup describes a step-by-step installation for a machine that will run test matches.

### Windows setup

On Windows you will need to install Python 2.7.x for x86 (not 3.x series and not
64 bit) from

http://www.python.org/download/releases/2.7.3/

Then setuptools for 2.7.x from

https://pypi.python.org/pypi/setuptools

Once installation is complete, you will find an easy_install.exe program in your
Python Scripts subdirectory. Be sure to add this directory to your PATH environment
variable, if you haven't already done so.

Then install pip with:

```
easy_install pip
```

### Setup fishtest

First you need to install some prereqs ('sudo' is not needed on Windows):

```
sudo pip install pymongo
sudo pip install requests
```

Then you will need the fishtest package. You can download fishtest as a zipball
directly from https://github.com/glinscott/fishtest or, in case you have a git
installation, you can clone it.

```
git clone https://github.com/glinscott/fishtest.git
```

### Get username/password

Please e-mail us.  Once you have your username and password, you can add use them
to start the worker, see below.

## Launching the worker

To launch the worker open a console/terminal window in fishtest/worker directory
and run the following command (after changing concurrency to the correct value for
your system, see below), providing username and password you've being given.

```
python worker.py --concurrency 3 username password
```

Option 'concurrency' refers to the number of available cores in your system (not
including Hyperthreaded cores!), leaving one core for the OS.  For example,
on my 4 core machine, I use --concurrency 3.

## Running the website

This is only if you wish to run your own testing environment (ie. you are testing changes on another engine).

As a pre-requisite, the website needs a mongodb instance.  By default it assumes there is one
running on localhost.  You can set FISHTEST_HOST envrionment variable to connect to a different host.

To launch a development version of the site, you can simply do:
```
cd ~/fishtest/fishtest
sudo python setup.py develop
./start.sh
```
