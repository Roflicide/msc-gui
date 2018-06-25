# Minecraft Server Control GUI

# Index
* [Overview](#overview)
* [Prerequisites for installation](#prerequisites-for-installation)
* [Installation](#installation)
  * [Download](#download)
  * [Configuration](#configuration)
  * [Updating MSC-GUI](#updating-msc-gui)
* [Getting started](#getting-started)
  * [Basic usage](#basic-usage)
  * [Run web server in the background](#run-web-server-in-the-background)
  * [Stop web server in the background](#stop-web-server-in-the-background)
* [License](LICENSE)
* [Disclaimer](#disclaimer)

## Overview
Minecraft Server Control GUI (MSC-GUI) is a new web-based interface to the
[Minecraft Server Control Script](https://github.com/MinecraftServerControl/mscs)
that has been controlling many Linux and UNIX powered Minecraft servers since
it was first released in 2011.

MSC-GUI is currently under heavy development and will be in various stages
of usability for the immediate future.  As of this writing, the only code
available is at the proof-of-concept stage.  This proof-of-concept code will
evolve or be replaced as the concept matures.  When the MSC-GUI is in a more
usable state, this message will be removed.

## Prerequisites for installation

The Minecraft Server Control GUI uses Perl and
[Mojolicious](https://mojolicious.org/), a Perl-based web framework, to
present a web-based interface to the
[Minecraft Server Control Script](https://github.com/MinecraftServerControl/mscs).
As such, the `mscs` script must be
[installed](https://github.com/MinecraftServerControl/mscs/blob/master/README.md#installation)
and working for the GUI to function. Likewise, Mojolicious must be installed
for MSC-GUI to function. If you are running Debian or Ubuntu, you can make
sure that Mojolicious is installed by running:

    sudo apt install libmojolicious-perl

## Installation

### Download

If you followed the easiest way of [downloading the script](https://github.com/MinecraftServerControl/mscs/blob/master/README.md#downloading-the-script) when installing MSCS, then you will want to do the same here.  With `git` already installed:

    git clone https://github.com/MinecraftServerControl/msc-gui.git

##### Other ways to download

* Get the development version as a [zip file](https://github.com/MinecraftServerControl/msc-gui/archive/master.zip):

    wget https://github.com/MinecraftServerControl/msc-gui/archive/master.zip

### Configuration

Navigate to the `msc-gui` directory that you just downloaded.  Configuration
can be done with the included Makefile in Debian and Ubuntu like environments
by running:

    sudo make install
    
Then, run 
    
    chmod +x msc-gui
    
To make the webserver file executable.
    
### Updating MSC-GUI
Periodically Minecraft Server Control GUI is updated to address bug fixes
and add new features. The easiest way to fetch the latest update, assuming you
used [the easiest way to install the script](#download), is to first
`cd` into the folder where you downloaded MSC-GUI. Then, type:

    git pull

You can alternatively use [one of the other methods](#download)
to download the latest version.  Just `cd` into the folder containing the MSCS
download to continue.

Once you have the latest version of MSC-GUI downloaded, type:

    sudo make update

## Getting started

### Basic usage
Navigate to the directory where you downloaded the script.
Then, to start the web server, run:
 
    ./msc-gui daemon
    
By default, this will start the web server on port 3000. 

To specify a different port, add the `-l` argument:

     # Start the web server on port 8080
    ./msc-gui daemon -l http://*:8080 
    
Once running, you can visit the dashboard by navigating to [http://localhost:3000](http://localhost:3000)
on your machine.
    
To close the web server, press Ctrl + C (`^C`).

### Run web server in the background
You will most likely want to run the web server in the background so
you can close your terminal window without stopping the server. 

Fortunately, `screen` is a tool available on most Unix distributions that can be 
used to accomplish this. 

To start a new virtual terminal (on which you will run the server) type:

    screen -S mscgui-server
   
Your terminal will clear and you'll be entered into a new window.
You can now start the server: (see [Usage](#usage) for more options)

    ./msc-gui daemon

Finally, detach from this screen by pressing `Ctrl + A + D`.

Upon doing so, you will be returned to your main terminal window--
and the web server will remain running in the background. You can 
now close the terminal window without your web server stopping.

### Stop web server in the background
If you want to stop the web server that is running in the background 
as detailed in the [Getting started](#getting-started) section, 
you will have to 1. stop the web server and 2. delete the screen.

First, re-attach to the screen running the web server:
(the command below assumes you named the screen `mscgui-server` as 
detailed in [Getting started](#getting-started))

    screen -r mscgui-server

Then, press Ctrl + C to stop the server.

Finally, detach and delete the screen by pressing Ctrl + A and typing `:quit`.

## License

See [LICENSE](LICENSE)

## Disclaimer

Minecraft is a trademark of Mojang Synergies AB, a subsidiary of Microsoft
Studios.  MSCS and MSC-GUI are designed to ease the use of the Mojang produced
Minecraft server software on Linux and UNIX servers.  MSCS and MSC-GUI are
independently developed by open software enthusiasts with no support or
implied warranty provided by either Mojang or Microsoft.
