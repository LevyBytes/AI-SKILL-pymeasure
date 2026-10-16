# pymeasure.instruments.danfysik.Danfysik8500

*class *pymeasure.instruments.danfysik.Danfysik8500(*adapter*, *name='Danfysik 8500 Current Supply'*, ***kwargs*)

Bases: [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

High-level interface representing the Danfysik 8500 Electromanget Current Supply for instrument interaction.

On Linux, allow user access to the Prolific Technology PL2303 Serial port adapter by creating `/etc/udev/rules.d/50-danfysik.rules` with these contents:

```none
SUBSYSTEMS=="usb",ATTRS{idVendor}=="067b",ATTRS{idProduct}=="2303",MODE="0666",SYMLINK+="danfysik"

```

After that, reload the udev rules with:

```bash
sudo udevadm control --reload-rules
sudo udevadm trigger

```

The port `/dev/danfysik` will provide access to the device.
