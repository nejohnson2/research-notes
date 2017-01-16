# Connecting Multiple SDRs

# Passive Radar

You need two antennas with two RTLSDR devices.  The antennas need to be somewhat directional and facing in opposite directions.  You then tune both devices to the same frequency.  This should be a frequency where stong transmissions are present such as FM or GSM frequencies.  The goal is to capture reflections of this channel.  So how do you know what is a reflection and what is the actual signal?

To accomplish this, you can use least squares regression to identify the direct dignal.  Subtract the direct signal and what you have left are the reflections.  [This Hackaday article](https://hackaday.com/author/jvierine/) describes the process a bit more.  He describes something about using autocorrelation but it's not clear.  I'm also pissed by the article because he's not shared any of the code, yet he praises open-source.  He's an academic who wants to stay in a silo - correct me if I'm wrong.

You should be able to create and image like this: <img src="http://2.bp.blogspot.com/-xISRmtiRLYk/UkSRRCZpFhI/AAAAAAAABjc/OxbWZHaiWlQ/s1600/passive-000141.png" width=400 align=right />


### PPM Offset

```
kal -s GSM850                           # scan for nearby towers
kal -c <channel> -d <device>   # calculate ppm offset
```

Recorded ppm offset values:

```
- Device 0 - ppm 39
- Device 1 - ppm 40
- Regular Device: ppm -34
```

Various applications:

- rtl_adsb
- rtl_eeprom
- rtl_fm
- rtl_power
- rtl_sdr
- rtl_tcp
- rtl_test

[ARFCN](http://niviuk.free.fr/gsm_arfcn.php)

## Installing Software for Ubuntu 16.04

I installed Ubuntu 16.04 with VirtualBox then started installing software.  This largely follows instructions on the [gr-gsm wiki](https://github.com/ptrkrysik/gr-gsm/wiki/Manual-compilation-and-installation), though the first couple of times were unsuccessful.

### Install Gr-gsm

```
sudo apt-get update
sudo apt-get upgrade

# install software
sudo apt-get install gnuradio gnuradio-dev
sudo apt-get install rtl-sdr librtlsdr-dev
sudo apt-get install gr-osmosdr libosmosdr-dev
sudo apt-get install libosmocore libosmocore-dev

# Install some dependencies
sudo apt-get install cmake libboost-all-dev libcppunit-dev swig doxygen liblog4cpp5-dev python-scipy

# Add environmental variables
export PATH=/home/YOUR_HOME_DIR/gr-gsm/bin:$PATH
export LD_LIBRARY_PATH=/home/YOUR_HOME_DIR/gr-gsm/lib:$LD_LIBRARY_PATH

# Install Gr-gsm
git clone https://github.com/ptrkrysik/gr-gsm.git
cd gr-gsm
mkdir build
cd build
cmake ..
make
sudo make install
```

### Install Multi-rtlsdr

```

```

## Interesting Projects

[Waterfall](https://github.com/keenerd/rtlsdr-waterfall)
[Dump1090](https://github.com/antirez/dump1090)
[rtl_433](https://github.com/merbanan/rtl_433)
