# SDR Installation

Steps:

- Install XCode and Commandline Tools
- 

I also have a tremendous amount of work trying to get a fluid installation script.  At this point, none of them are working and most should be removed as they are outdated.

The big challenge that I kept facing was not being able to install ```gr-osmosdr```.  In the end, I determined this was a results of ```cmake > 3.2``` which screwed up the ```Gnuradio``` installation.  This was happening when trying to install gnuradio from my repos.  Instead, gnuradio has now been added to Homebrew core formula's and therefore can be complied without tapping any other repository.

## Installing Older Version of Cmake w/ Homebrew

In whatever Formula you're trying to install, you should add something like this:

```ruby
  resource "cmake" do
    url "https://cmake.org/files/v3.3/cmake-3.3.2.tar.gz"
    sha256 "e75a178d6ebf182b048ebfe6e0657c49f0dc109779170bad7ffcb17463f2fc22"
  end
  
  def install  
    resource("cmake").stage do
      args = %W[
        --prefix=#{buildpath}/cmake
        --no-system-libs
        --parallel=#{ENV.make_jobs}
        --datadir=/share/cmake
        --docdir=/share/doc/cmake
        --mandir=/share/man
        --system-zlib
        --system-bzip2
        --system-curl
      ]

      system "./bootstrap", *args
      system "make"
      system "make", "install"
    end
  
    # the rest of the install process
  end
```
The above code was taken from the ```Homebrew/core/gnuradio``` Formula which

## Homebrew Tips and Tricks

```pre
$ brew info --github <formula>
$ brew create <url>
```
