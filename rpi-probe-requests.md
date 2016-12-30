# Sniffing Probe Reqests with RPi

There are three ways to sniff probes:

- ```airodump-ng```
- ```tcpdump```
- ```scapy```

Existing repo: [packet-sniffer](https://github.com/nejohnson2/packet_sniffer)

[Python commandline tool](https://github.com/nejohnson2/probemon)

## How-to

First you must use a specific type of wireless card.  Then you need to put that card into ```monitor-mode``` or ```promiscuous mode```.  I'm not sure the difference.  Then you can start capturing packets.

## Aircrak-ng Notes

I believe ```airodump-ng``` only outputs beacan APs.

```
# install
$sudo apt-get install aircrack-ng

# create a virtual monitor device mon0
$ sudo airmon-ng start wlan1

# check it's there
$ ifconfig mon0

# run
$ sudo airodump-ng mon0
```



