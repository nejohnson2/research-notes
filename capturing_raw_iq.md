# Capture Raw IQ

## Links
- [This Notebook](https://github.com/nejohnson2/misc-notebooks/blob/master/rtlsdr.ipynb) uses the ```RTLSDR``` library to collect IQ samples for a specific amount of time.  It also implements an ```FM demodulator```.  This code is taken from ```[Software Defined Radio and the RTL-SDR dongle](http://www.eas.uccs.edu/~mwickert/ece4670/lecture_notes/Lab6.pdf)```
- [Advanced Topics in Wireless Communication](http://witestlab.poly.edu/~ffund/el9043/): This is the NYU Poly class that has lots of resources.
- [This Notebook](http://localhost:8888/notebooks/SDR_Lab_1.ipynb) are notes about FM demodulation

## Notes

The snippet of code below is used to capture IQ samples for ```T``` seconds:

```python
def capture(Tc, fc=88.7e6, fs=2.4e6, gain='auto', ppm=60):
    '''Capture T seconds of I/Q samples'''
    # Setup RTLSDR
    # Tc is the time in seconds
    sdr = rtlsdr.RtlSdr()       # create the object
    sdr.sample_rate = fs        # Hz
    sdr.center_freq = fc        # Hz
    sdr.freq_correction = ppm   # 60 PPM
    sdr.gain = gain             # or auto
    Nc = np.ceil(Tc*fs)
    
    x = sdr.read_samples(Nc)
    sdr.close()
    return x
```
From here, one can demodulate the IQ as desired.

Using scipy.signal Library with RTLSDR
