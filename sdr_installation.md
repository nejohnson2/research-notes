# SDR Installation

Steps:

- Install XCode and Commandline Tools
- 

I also have a tremendous amount of work trying to get a fluid installation script.  At this point, none of them are working and most should be removed as they are outdated.

The big challenge that I kept facing was not being able to install ```gr-osmosdr```.  In the end, I determined this was a results of ```cmake > 3.2``` which screwed up the ```Gnuradio``` installation.  This was happening when trying to install gnuradio from my repos.  Instead, gnuradio has now been added to Homebrew core formula's and therefore can be complied without tapping any other repository.

## Homebrew Tips and Tricks

```pre
$ brew info --github <formula>
$ brew create <url>
```
