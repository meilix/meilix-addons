# PSLab Notebooks

This repository (https://github.com/bessman/pslab-notebooks) contains a series of tutorials and exercises for the [Pocket Science Lab](https://pslab.io) (PSLab) [Python library](https://github.com/fossasia/pslab-python).

## Requirements

The following software is required to run the notebooks:

- Python 3.8 or later
- The following python packages:
  - pslab
  - notebook
  - matplotlib

## Installing `pslab`

Recommended way to install the `pslab` package:

- Create a virtual environment called 'pslab': Run `python -m venv pslab` on the command line.
- Activate the virtual environment.
  - On Linux, run `source ./pslab/bin/activate`.
  - On Windows, run `.\pslab\Scripts\activate.bat`
- Install the dependencies: Run `pip install pslab notebook matplotlib`

Once installed, connect the PSLab board and verify that you can connect to it by running `pslab collect -c 1 -d 0.00001 oscilloscope`. This will sample the voltage on the PSLab's CH1 pin for 10 µs. The output should look something like:

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

If you get an error saying `serial.serialutil.SerialException: Device not found.`, try another USB-cable.

If you are using Linux and get an error message saying you do not have permission to access the serial port, run `pslab install` as root. This will add a udev rule allowing regular users to access the PSLab. You may need to trigger udev to reload its ruleset before this takes effect. Consult your distro's documentation for instructions on how to reload udev.

Alternativelly, you can skip the udev rule and instead become a member of the group to which the /dev/tty* device files belong to. On Debian based distros this group is called 'dialout', on Arch based distros it is called 'uucp'. It may be called something else on other distros. Again, consult your distro's documentation for how to become a member of a group.

Once this installation is complete, launch Jupyter Notebooks by running `jupyter notebook`.
