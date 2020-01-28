# Basic MAC

Basic MAC is a portable implementation of the LoRa™ Alliance's LoRaWAN™
specification in the C programming language. It is a fork of IBM's LMiC
library, and supports multiple regions, which are selectable at compile and/or
run time. It can handle Class A, Class B, and Class C devices.

#### Documentation

The full documentation is available at
[https://doc.sm.tc/mac](https://doc.sm.tc/mac).

#### Additional Documentation

The official documentation glosses over a few details which will be documented here.

##### Building

Follow the [build process](https://doc.sm.tc/mac/gettingstarted.html#build-process) in the instructions above.

To build for a specific region, you use:

```shell
$ cd $MAC_REPO/projects/ex-join
$ VARIANT=us915 make
```

To use the load Makefile target, you need a few python3 dependencies

```shell
pip3 install click
pip3 install intelhex
```

Now you can use the load functionality from the Makefile:

```shell
$ cd $MAC_REPO/projects/ex-join
$ VARIANT=us915 make load
```

##### Testing

There is an undocumented test suite which simulates the MCU using Python's Unicorn package.

You'll need to pip install a few things:

```shell
pip3 install unicorn
pip3 install numpy
pip3 install pycryptodome
```

It's important that you use `pycryptodome` and not simly the `crypto` package, as the latter does not include `Hash.CMAC`. If you already have `crypto` install, run `pip3 uninstall crypto`.


```shell
$ cd $MAC_REPO/projects/ex-join
$ VARIANT=simul make test
```

The full test suite runs in less than 40 seconds and presumably could be simplified to test an area of interest during development.
