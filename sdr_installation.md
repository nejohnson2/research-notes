# SDR Installation

> Note: This installation script is not complete.  Pyqt4 must be install in order to use gr-gsm!


After many long hours, I've finally been able to build gnuradio.  Below are steps to repeat.

Steps:

- Install XCode and Commandline Tools
- Install Homebrew
- 


Check the [API Documentation](http://gnuradio.org/doc/doxygen/build_guide.html)


### Shell Script Installation

```shell
# Install Xcode
xcode-select --install

# install homebrew
ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"

# Homebrew path
echo "export PATH=/usr/local/bin:/usr/local/sbin:$PATH" >> ~/.bash_profile

# not sure if these are necessary
echo "export PYTHONPATH=/usr/local/lib/python2.7/site-packages" >> ~/.bash_profile
echo "export PKG_CONFIG_PATH=\"/usr/X11/lib/pkgconfig\"" >> ~/.bash_profile 

# Dependencies
brew install python
brew tap homebrew/python
brew install numpy
brew install matplotlib 
brew install gsl
brew install pygtk
brew install wxpython
brew install boost
brew install cppunit
brew install fftw
brew install zeromq
brew install doxygen
brew install uhd
brew install portaudio
brew install sdl
brew install jack
brew install scipy
brew install swig
brew install sip

pip install Cheetah
pip install lxml
pip install sphinx

brew cask install xquartz

# More dependencies
brew tap nejohnson2/homebrew-sdr
brew install cmake

# Gnuradio
brew install gnuradio
brew install librtlsdr

brew install gr-osmosdr gr-baz --HEAD

# gr-gsm
brew install libosmocore --HEAD
brew install gr-gsm --HEAD
```

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

Homebrew formula are located here:

```pre
# Formula Location
$ /usr/local/Homebrew/Library/Taps/homebrew/homebrew-core/Formula
```


```pre
$ brew info --github <formula>
$ brew create <url>
```
