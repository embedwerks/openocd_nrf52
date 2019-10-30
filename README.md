# openocd_nrf52
OpenOCD + patches for nRF52

# Download
[https://embedwerks.iotaware.xyz/openocd.html](https://embedwerks.shravanj.com/openocd.html)

# Setup
Tested on Raspbian Stretch on a Raspberry Pi 3 with an ST-Link v2 purchased from Adafruit.com. nRF52832 was on the Adafruit Feather nRF52 dev board.

1.  Install git, autoconf, and libusb-1.0.0-dev
2.  Clone the st-link repository: git clone https://github.com/texane/stlink
3.  cd stlink
4.  ./autogen.sh
5.  ./configure
6.  make
7.  Once st-link has compiled, copy the binaries and udev rules with the following:
8.  sudo cp st-* /usr/bin
9.  find . -name "*.rules"
10.  sudo cp ./etc/udev/rules.d/49-stlinkv2.rules /etc/udev/rules.d
11.  Apply the udev rules with the following:
12.  sudo udevadm control --reload-rules
13.  sudo udevadm trigger
14.  Verify the ST-Link shows up via dmesg
15.  Download and unzip the openocd zip, once unzipped run the following:
16.  cd openocd_nrf52_patched
17.  ./bootstap
18.  ./configure
19.  make
20.  sudo make install
21.  Once installed, download the config file and S132 SoftDevice then run the following (must be in working directory):
22.  openocd -f openocd_nrf52.cfg
23.  The SoftDevice will be programmed and you should see no errors
24.  To program your app logic just add 'program yourapp.hex verify' under the SoftDevice programming line in openocd_nrf52.cfg

# Need help?
Open an issue [here](https://github.com/embedwerks/openocd_nrf52/issues)
