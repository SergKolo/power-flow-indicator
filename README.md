# power-flow-indicator

**Indicator that displays electric current and/or power consumption of the laptop battery.**

This indicator is designed for Ubuntu Linux systems using Unity or any other desktop environment that is compatible with AppIndicators.
Tested on Ubuntu 16.04.



## Installation

You can either clone this repository to your local machine using `git` or simply download it as `.zip` archive and extract it in any arbitrary location on your computer. Just make sure that `pwi_icon.png` is in the same directory as the `power-flow-indicator` script file.


### Additional requirements

The file `power-flow-indicator` is a Python script, so you need a Python 2 interpreter installed on your system, but that is already included on all Ubuntu releases by default.
Further than that, it requires you to have the following additional packages installed:

- *to be added*

This can be done by running the command below:

    sudo apt-get install PACKAGENAME


### Optional steps

If you want to be able to run the script directly instead of passing it as argument to the `python` interpreter, you can make it executable by running the command below from inside the installation directory:

    chmod +x power-flow-indicator
    
To be able to launch `power-flow-indicator` in the terminal from any working directory without having to specify the full path to it, you have to create a symlink to it inside one of the directories specified in your system's `PATH` environment variable (e.g. `/usr/local/bin` for all users - which needs `sudo` privileges to create the link - or `~/bin` for the current user only). The command to run could look like this:

    ln -s /PATH/TO/YOUR/INSTALLATION/DIRECTORY/power-flow-indicator ~/bin/power-flow-indiactor



## Usage

Simply run it from the command-line like this (using the actual path it is located):
 
     python /PATH/TO/power-flow-indicator
     
Alternatively, if you completed the optional installation instructions, you can also only write:

    power-flow-indicator

It is convenient to add it to your *Startup Applications* so that it will launch automatically each time you log into a Unity (or compatible desktop environment) session.


### Advanced command syntax
    
    usage: power-flow-indicator [-h] [-W | -A | -a | -f FORMAT]
    
    optional arguments:
      -h, --help            show this help message and exit
      -W, --Watt            display power in Watt (W) with 2 decimals
      -A, --Ampere          display current in Ampere (A) with 3 decimals
      -a, --Milliampere     display current in Milliampere (mA)
      -f FORMAT, --format FORMAT
                            custom display format - see below...
    
    FORMAT syntax:
        Use Python's "str.format()" syntax with named parameters.
        It looks basically like this:  {<NAME>:.<DECIMALS>f}
        <NAME> can be one of "W", "A" and "mA" and specifies the value you want.
        <DECIMALS> allows you to specify the number of decimals displayed.
        Here are the format strings of the default display options as example:
        -W :  "{W:.2f} W" ,    -A :  "{A:.3f} A" ,    -a :  "{mA:.0f} mA" 
