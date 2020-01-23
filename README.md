# maestro.py - Python3 Support for Pololu Maestro

Python Support for the Pololu Maestro line of servo controllers. The original 
code was written by Steven Jacobs (Aug 2013) and located at- https://github.com/FRC4564/Maestro/
These functions provide access to many of the Maestro's capabilities using the
Pololu serial protocol


Code contained in this repository was edited by Dave Foran -- Jan 2020 to fit 
into Python3 and PEP 8 Conventions. I felt it was important to update this file 
in order to bring the original code up to standard since Python2 is discontinued. 
It was also good practice for reformatting Python2 code to Python3 code.

## Getting Started / Setup

### Setting Up Pololu Maestro

To get started, you will need to install the Maestro Control Center either on Windows (https://www.pololu.com/docs/0J40/3.a) or of course, my personal favorite, Linux (https://www.pololu.com/docs/0J40/3.b)

Pololu's Maestro Windows installer sets up the Maestro Control Center, used to configure, test and program the controller.  Be sure the Maestro is configured for "USB Dual Port" serial mode, which is [not the default](https://www.pololu.com/docs/0J40/3.c).

Once you've downloaded and unzipped the package on Linux, plug in your Pololu Maestro
to your computer via USB cable and run:

    cd /maestro-linux-150116/maestro-linux/

    ./MaestroControlCenter

This will allow you to bring up the control center. Check your controller, if there is a red light, you can use "Device" and then "Restart Device", to ensure that your connection to the controller is initializing correctly. Finally, go to "Serial Settings" and under "Serial Mode:" select "USB Dual Port".

Now you're ready to start programming.
 
 ### Setting Up Python Environment

As usual, I recommend you first set up a Virtual Environment and enter into it with a set of commands like:

    python3 -m venv <environment name>

    source <environment name>/bin/activate

You'll need to have the 'pyserial' Python module installed to use maestro.py.

Using pip3 for python3

    python3 -m pip install pyserial

Finally, download the maestro.py into your directory from which you are going to be running the python scripts from. Now you are ready to begin writing code.

## Example Script

Example usage of maestro.py:

import maestro
servo = maestro.Controller()
servo.set_acceleration(0,4)      #set servo 0 acceleration to 4
servo.set_target(0,6000)  #set servo to move to center position
servo.set_speed(1,10)     #set speed of servo 1
x = servo.get_position(1) #get the current position of servo 1
servo.close()

There are other methods provided by the module. The code is well documented, if you'd like to learn more. 

For use on Windows, you'll need to provide the COM port assigned to the Maestro Command Port. You can identify the port by starting Device Manager and looking under Ports (COM & LPT). Here's how to instantiate the controller for Windows for COM port 3.

import maestro
m = maestro.Controller('COM3')

## Versioning

We use [SemVer](http://semver.org/) for versioning. For the versions available, see the [tags on this repository](https://github.com/your/project/tags). 

## Authors

* **Steven Jacobs** - *Initial work* - [FRC4564](https://github.com/FRC4564)

* **Dave Foran** - *Refactored to PEP8 Standards* - [fud0ch1](https://github.com/fud0ch1)

## License

This project is licensed under the MIT License

## Acknowledgments

* Hat tip to Steven Jacobs for his excellent code, I love using it and it works really well with the pololu maestro controller

* Inspiration - I refactored this code while working on a research project using servomechanisms and the pololu controller. I used it to control some servo-motors, LED lights, and infrared lights.

* Please reach out to me with any questions that you have at livefromtheabyss@gmail.com, I am always excited to see projects you are working on! If you have any recommendations on improving the code or formatting, please let me know as well.

* If you copy, please give credit to Steven Jacobs, (and to my Python3 PEP8 revamp)
