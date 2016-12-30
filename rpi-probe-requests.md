# Sniffing Probe Reqests with RPi

There are three ways to sniff probes:

- ```airodump-ng```
- ```tcpdump```
- ```scapy```

Existing repo: [packet-sniffer](https://github.com/nejohnson2/packet_sniffer)

[Python commandline tool](https://github.com/nejohnson2/probemon)

## How-to

First you must use a specific type of wireless card.  Then you need to put that card into ```monitor-mode``` or ```promiscuous mode```.  I'm not sure the difference.  Then you can start capturing packets.

[Read this](https://github.com/azz2k/scapy-rssi/blob/master/scapy-rssi.py)

### Tcpdump

A simple ```tcpdump``` capture looks like this:

```
sudo tcpdump -i mon0 -l type mgt subtype probe-req -vvv
```

Notice that the interface is ```mon0``` which is setup using ```aircrack-ng start wlan1```.  ```aircrack-ng``` starts the virtual interface which is then used by tcpdump.

You can wrap that in a python script like this:

```python

```

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



