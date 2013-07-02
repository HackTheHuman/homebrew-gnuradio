# homebrew-gnuradio

This is a collection of [Homebrew](https://github.com/mxcl/homebrew) recipes
that makes it easier get GNU Radio and friends running on OS X.

## Installation

These steps have been tested on Lion 10.7.4 with Xcode 4.3.2 and Mountain Lion
10.8 with Xcode 4.4.1 & 10.8.4 Xcode 4.6.3.

- Specify gcc 4.2.2.
	```sh
	brew search gcc
 	brew tap homebrew/dupes
	```

- Add this line to your profile (ie `~/.bash_profile` or `~/.zshenv`) and reload
  your shell (`exec $SHELL`)

  ```sh
  export PATH=/usr/local/bin:/usr/local/share/python:$PATH
  ```

- Install the python package prerequisites

  ```sh
  brew install python gfortran swig
  ```

- Install the prerequisite python packages

  ```sh
  pip install numpy Cheetah lxml
  pip install https://github.com/scipy/scipy/tarball/v0.11.0rc2
  export PKG_CONFIG_PATH="/usr/x11/lib/pkgconfig" pip install http://downloads.sourceforge.net/project/matplotlib/matplotlib/matplotlib-1.1.1/matplotlib-1.1.1.tar.gz
  ```

- Install gnuradio (add `--with-qt` for `gr-qtgui`)

  ```sh
  brew tap hackthehuman/homebrew-gnuradio
  brew install gnuradio
  ```
- Create the `~/.gnuradio/config.conf` config file for custom block support

  ```ini
  [grc]
  local_blocks_path=/usr/local/share/gnuradio/grc/blocks
  ```

### Optional (for `gr-wxgui`)

- Before installing `gnuradio`, install `wxmac` 2.9 with python bindings

  ```sh
  brew install wxmac --python
  ```

### Optional (for rtl-sdr devices)

- Install `rtlsdr` and related blocks

  ```sh
  brew install rtlsdr gr-osmosdr gr-baz --HEAD
  ```
  
- Test your `rtlsdr` device has been succesfully installed. 

	```sh
	rtl_test -t
	```
- This is the output from my device.
`
Found 1 device(s):
  0:  Generic RTL2832U

Using device 0: Generic RTL2832U
Found Elonics E4000 tuner
Supported gain values (14): -1.0 1.5 4.0 6.5 9.0 11.5 14.0 16.5 19.0 21.5 24.0 29.0 34.0 42.0 
Benchmarking E4000 PLL...
[E4K] PLL not locked for 53000000 Hz!
[E4K] PLL not locked for 2213000000 Hz!
[E4K] PLL not locked for 1107000000 Hz!
[E4K] PLL not locked for 1249000000 Hz!
E4K range: 54 to 2212 MHz
E4K L-band gap: 1107 to 1249 MHz
`