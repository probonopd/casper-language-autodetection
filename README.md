# casper Language Autodetection

## User story

As a user of Ubuntu based Live systems, I would like to have the keyboard layout (keyboard language) autodetected. I find it very cumbersome to select the keyboard layout each time I boot a Ubuntu based Live system.

Ideally, I would also like to get sensible defaults for the locale (application language) and timezone based on that.

## Theory of operation

Ubuntu Live systems are using casper to configure the Live system during the boot process. [casper](https://packages.ubuntu.com/search?keywords=casper&searchon=names) is modular and runs various scripts that become part of the initrd.

By adding one more script, we can autodetect the keyboard layout (keyboard language) based on the following indicators:

* [Raspberry Pi Keyboard and Hub](https://www.raspberrypi.com/products/raspberry-pi-keyboard-and-hub/) USB information ([details](https://gist.github.com/probonopd/9646c69f876ff2b4b879aeb1c1cbc532))
* The EFI variable `prev-lang:kbd` which is usually set on systems running macOS ([details](https://github.com/helloSystem/hello/wiki/EFI-NVRAM))

Additional indicators may be added in the future; please open an issue if you have ideas, e.g.,

* USB keyboards should standardize on a way to communicate their keyboard layout (keyboard language)
* The *nix world should standardize on some EFI NVRAM variables for keyboard layout (keyboard language), locale (application language), timezone, etc.

It is still possible to override the autodetected values by passing kernel arguments as usual (e.g., `console-setup/layoutcode=de locale=de_DE timezone=Europe/Berlin`).

## Status

* Setting the keyboard layout (keyboard language) works
* Setting the locale (application language) does not seem to work yet - why?
* Setting the timezone does not seem to work yet - why?

Please open an issue in this repository if you know the answer to any of those.

## Open questions

* Where is the source code repository for casper? (Hopefully somewhere on GitHub and not hidden away in Launchpad?)
* Who is the maintainer of casper?
* How can we get this merged into casper eventually?

Please open an issue in this repository if you know the answer to any of those.
