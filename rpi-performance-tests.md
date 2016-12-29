# RPi Performance Tests

## Misc Rpi Commands

[here](http://www.makeuseof.com/tag/15-useful-commands-every-raspberry-pi-user-should-know/)

[This](http://www.satsignal.eu/raspberry-pi/monitoring.html) might also be interesting

#### Shutdown

```
sudo shutdown –h
```

Taken from [here](https://www.element14.com/community/community/raspberry-pi/blog/2016/02/29/the-most-comprehensive-raspberry-pi-comparison-benchmark-ever)

```
sudo apt-get update
sudo apt-get install lscpu cpuinfo lshw
```
then:

```
lscpu
```

## Wavemon

```
$ sudo apt-get install wavemon
$ wavemon
```

## Temperature of CPU and GPU

```
# GPU temperature
$ vcgencmd measure_temp

# ARM CPU temperature
$ cpu=$(</sys/class/thermal/thermal_zone0/temp)
$ echo "$((cpu/1000)) c"
```

Create an example bash script ``` temperature.sh```:

```bash
#!/bin/bash
# Script: my-pi-temp.sh
# Purpose: Display the ARM CPU and GPU  temperature of Raspberry Pi 2/3 
# Author: Vivek Gite <www.cyberciti.biz> under GPL v2.x+
# -------------------------------------------------------
cpu=$(</sys/class/thermal/thermal_zone0/temp)
echo "$(date) @ $(hostname)"
echo "-------------------------------------------"
echo "GPU => $(/opt/vc/bin/vcgencmd measure_temp)"
echo "CPU => $((cpu/1000))'C"
```

then:

```bash
$ chmod +x temperature.sh
```

#### Python Class for Temperature

```python
#!/usr/bin/env python

import tornado.ioloop
import tornado.web
import os

class MainHandler(tornado.web.RequestHandler):
    def getCPUtemperature( self ):
        res = os.popen('vcgencmd measure_temp').readline()
        return(res.replace("temp=","").replace("'C\n",""))

    def get(self):
        self.write( "Temperature: %s" % ( self.getCPUtemperature() ) )

application = tornado.web.Application([
    (r"/", MainHandler),
])

if __name__ == "__main__":
    application.listen(8888)
    tornado.ioloop.IOLoop.instance().start()
```
