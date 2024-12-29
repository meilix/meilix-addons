# Getting Started with the Pocket Science Lab

The goal of this workshop is to introduce participants to the PSLab and to
enable them to conduct experiments with it. <https://pslab.io>

This workshop uses Python to interface with the PSLab. Basic familiarity with
your operating system's command line is required, and prior experience with
Python is recommended.

The workshop is self-paced. It is given in the form of a series of Jupyter
Notebooks, which introduce the PSLab's core instruments (multimeter, power
supply, oscilloscope, waveform generator, pwm generator, and logic analyzer).
A PSLab developer will be present to help with problems and answer questions.

You can bring your own PSLab, buy one at the FOSSASIA assembly (49€), or borrow
one at the workshop.

To save time at the workshop, you are encouraged to download the tutorial and
install the required Python packages ahead of time. Keep reading for
instructions on how to do that. All steps up to and including 'Installation'
can be completed without a PSLab.

## Downloading the tutorial

Download the tutorial notebooks by either

- `git clone`ing this repository (<https://github.com/fossasia/pslab-notebooks>)
- `cd` into it

or

- Download this repository as a ZIP archive by clicking the green
  '<> Code'-button in the Github web interface, and then select "Download ZIP"
- Unpack the ZIP archive and `cd` into it

## Requirements

- A computer
- with Python3.9+ with pip and venv
  - pip and venv are typically installed along with Python. However, some Linux
    distros (notably Debian and Ubuntu) package them separately. In this case,
    they must be installed from the distro's package repos with e.g.
    `apt install python3-pip python3-venv`.

### Additional Linux-specific requirements

Windows and MacOS users can skip this section.

Your user most likely does not have permission to access serial ports, which
means you can't talk to the PSLab yet. You need to become a member of the
group which owns the serial port device file. The device file is typically
called '/dev/ttyUSB0', and the owner group is usually either 'dialout' (on
Debian-, RedHat-, and Suse-based systems) or 'uucp' (on Arch-based systems).

Check which group owns the serial port with this command (replace
'/dev/ttyUSB0' with the actual path of your device file, if necessary):

```bash
stat -c %G /dev/ttyUSB0
```

The output from this command should be a single group name, e.g.

```bash
dialout
```

You need to be a member of this group. Check if you already are with (replace
'dialout' with the name of the owner group, if necessary):

```bash
getent group dialout
```

The output of this command should be a line from '/etc/group', e.g.

```bash
dialout:x:20:alexander
```

If your username is present in the response, you are already a member of the
group. You can move on to the next section of the guide.

If your username is not present in the response, you are not a member of the
group which owns the serial port. On most distros, this can be done with
(replace 'dialout' with the name of the owner group, if necessary, and
'username' with your username):

```bash
usermod -aG dialout username
```

You need to log out and log back in for the group change to take effect.

## Installation

- Create a Python venv (virtual environment) with `python3 -m venv venv`
- Activate the virtual environment.
  - On Linux or MacOS, run `source ./venv/bin/activate`
  - On Windows, run `./venv/Scripts/activate.bat`
- Install the dependencies: Run `pip install -r requirements.txt`

## Verifying the installation

Once installed, connect the PSLab board and verify that you can connect to it
by running `pslab collect -c 1 -d 0.00001 oscilloscope`. This will sample the
voltage on the PSLab's CH1 pin for 10 µs. The output should look something
like:

```
Timestamp,CH1
0.0,0.016129032258064058
0.5,0.016129032258064058
1.0,0.016129032258064058
1.5,0.016129032258064058
2.0,0.016129032258064058
2.5,0.016129032258064058
3.0,0.016129032258064058
3.5,0.016129032258064058
4.0,0.016129032258064058
4.5,0.016129032258064058
5.0,0.016129032258064058
5.5,0.016129032258064058
6.0,0.016129032258064058
6.5,0.016129032258064058
7.0,0.016129032258064058
7.5,0.016129032258064058
8.0,0.016129032258064058
8.5,0.016129032258064058
9.0,0.016129032258064058
9.5,0.016129032258064058
```

If you get an error saying
`serial.serialutil.SerialException: Device not found.`, try another USB-cable.

Once this installation is complete, launch Jupyter Notebooks by running
`jupyter notebook`. A web interface should open in your default browser,
showing the current directory. You can open notebooks (.ipynb-files) by
clicking on them.
