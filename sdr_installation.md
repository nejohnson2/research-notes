# SDR Installation

After many long hours, I've finally been able to build gnuradio.  Below are steps to repeat.

Steps:

- Install XCode and Commandline Tools
- Install Homebrew
- 

Check the [API Documentation](http://gnuradio.org/doc/doxygen/build_guide.html)


> Note: pyqt4 must be install in order to use gr-gsm!


### Cmake

```ruby

python_prefix = python-config --prefix
args = std_cmake_args
args << "-DPYTHON_LIBRARY='#{python_prefix}/Python'"
args << "-DPYTHON_INCLUDE_DIR='#{python_prefix}/Headers'"
args << "-DPYTHON_PACKAGES_PATH='#{lib}/#{which_python}/site-packages'"

system 'cmake', '..', *args
system 'make'
system 'make install'

def which_python
  "python" + `python -c 'import sys;print(sys.version[:3])'`.strip
end

```

### Shell Script Installation

```shell
# Install Xcode
xcode-select --install

# Install Homebrew
ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"

# add
echo "export PATH=/usr/local/bin:/usr/local/sbin:$PATH" >> ~/.bash_profile

brew install python
brew install cmake #3.3.2

brew cask install xquartz

# Gnuradio
brew install gnuradio
brew install librtlsdr
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

```
/usr/local/Homebrew/Library/Taps/homebrew/homebrew-core/Formula
```


```pre
$ brew info --github <formula>
$ brew create <url>
```

# Formula

### cmake.rb

This is a formula to install an old version of cmake-3.3.2.  Simple and tested.

```ruby
class Cmake < Formula  
  url "https://cmake.org/files/v3.3/cmake-3.3.2.tar.gz"
  sha256 "e75a178d6ebf182b048ebfe6e0657c49f0dc109779170bad7ffcb17463f2fc22"


  def install
    args = %W[
      --prefix=#{prefix}
      --no-system-libs
      --parallel=#{ENV.make_jobs}
      --datadir=/share/cmake
      --docdir=/share/doc/cmake
      --mandir=/share/man
      --system-zlib
      --system-bzip2
      --no-system-curl
    ]

    system "./bootstrap", *args
    system "make"
    system "make", "install"
  end
end
```

### gnuradio.rb

This formula is modified version of the ```homebrew/core/gnuradio.rb``` formula.  It removes the installation of cmake-3.3.2.

```ruby
class Gnuradio < Formula
  desc "SDK providing the signal processing runtime and processing blocks"
  homepage "https://gnuradio.squarespace.com/"
  url "https://gnuradio.org/releases/gnuradio/gnuradio-3.7.9.1.tar.gz"
  sha256 "9c06f0f1ec14113203e0486fd526dd46ecef216dfe42f12d78d9b781b1ef967e"
  revision 1

  bottle do
    rebuild 1
    sha256 "2cbc22df1411ef7090bd43cbec10dbb23ee16439ed8bb0e10a2b144455237e51" => :sierra
    sha256 "187f22d812f4ba86af2d2f64e9473647b49aa2373d6688d7ecfb840374285749" => :el_capitan
    sha256 "41eb9fdae72761b7a83f284f1e7613da9e3ce916e0f98f20ad3aafe417be5a4e" => :yosemite
  end

  option :universal

  depends_on "pkg-config" => :build

  depends_on :python if MacOS.version <= :snow_leopard
  depends_on "boost"
  depends_on "cppunit"
  depends_on "fftw"
  depends_on "gsl"
  depends_on "zeromq"

  # For documentation
  depends_on "doxygen" => :build
  depends_on "sphinx-doc" => :build

  depends_on "uhd" => :recommended
  depends_on "sdl" => :recommended
  depends_on "jack" => :recommended
  depends_on "portaudio" => :recommended

  resource "numpy" do
    url "https://pypi.python.org/packages/source/n/numpy/numpy-1.10.1.tar.gz"
    sha256 "8b9f453f29ce96a14e625100d3dcf8926301d36c5f622623bf8820e748510858"
  end

  # cheetah starts here
  resource "Markdown" do
    url "https://pypi.python.org/packages/source/M/Markdown/Markdown-2.4.tar.gz"
    sha256 "b8370fce4fbcd6b68b6b36c0fb0f4ec24d6ba37ea22988740f4701536611f1ae"
  end

  resource "Cheetah" do
    url "https://pypi.python.org/packages/source/C/Cheetah/Cheetah-2.4.4.tar.gz"
    sha256 "be308229f0c1e5e5af4f27d7ee06d90bb19e6af3059794e5fd536a6f29a9b550"
  end
  # cheetah ends here

  resource "lxml" do
    url "https://pypi.python.org/packages/source/l/lxml/lxml-2.0.tar.gz"
    sha256 "062e6dbebcbe738eaa6e6298fe38b1ddf355dbe67a9f76c67a79fcef67468c5b"
  end

  resource "cppzmq" do
    url "https://github.com/zeromq/cppzmq/raw/a4459abdd1d70fd980f9c166d73da71fe9762e0b/zmq.hpp"
    sha256 "f042d4d66e2a58bd951a3eaf108303e862fad2975693bebf493931df9cd251a5"
  end

  def install
    ENV["CHEETAH_INSTALL_WITHOUT_SETUPTOOLS"] = "1"
    ENV.prepend_create_path "PYTHONPATH", libexec/"vendor/lib/python2.7/site-packages"
    ENV.prepend_path "PATH", buildpath/"cmake/bin"

    res = %w[Markdown Cheetah lxml numpy]
    res.each do |r|
      resource(r).stage do
        system "python", *Language::Python.setup_install_args(libexec/"vendor")
      end
    end

    resource("cppzmq").stage include.to_s

    args = std_cmake_args

    args << "-DENABLE_DEFAULT=OFF"
    enabled_components = %w[gr-analog gr-fft volk gr-filter gnuradio-runtime
                            gr-blocks testing gr-pager gr-noaa gr-channels
                            gr-audio gr-fcd gr-vocoder gr-fec gr-digital
                            gr-dtv gr-atsc gr-trellis gr-zeromq]
    enabled_components << "gr-wavelet"
    enabled_components << "gr-video-sdl" if build.with? "sdl"
    enabled_components << "gr-uhd" if build.with? "uhd"
    enabled_components += %w[doxygen sphinx] if build.with? "documentation"

    enabled_components.each do |c|
      args << "-DENABLE_#{c.upcase.split("-").join("_")}=ON"
    end

    mkdir "build" do
      system "cmake", "..", *args
      system "make"
      system "make", "install"
    end

    rm bin.children.reject(&:executable?)
    bin.env_script_all_files(libexec/"bin", :PYTHONPATH => ENV["PYTHONPATH"])
  end

  test do
    assert_match version.to_s, shell_output("#{bin}/gnuradio-config-info -v").chomp
  end
end
```