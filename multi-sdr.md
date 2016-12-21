# Connecting Multiple SDRs


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

## Interesting Projects

[Waterfall](https://github.com/keenerd/rtlsdr-waterfall)
