# pymeasure.instruments.lakeshore.LakeShore425

Covers: Lake Shore 425 Gaussmeter; Lake Shore 211 Temperature Monitor; Lake Shore 224 Temperature Monitor; Lake Shore Cryogenics; Lake Shore 3xx Temperature Controller.

## Lake Shore 425 Gaussmeter

### Lake Shore 425 Gaussmeter

 *class *pymeasure.instruments.lakeshore.LakeShore425(*adapter*, *name='LakeShore 425 Gaussmeter'*, ***kwargs*)

Bases: [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Models the LakeShore 425 Gaussmeter, exposing a high-level interface for instrument interaction.

For Linux user access to the LakeShore 425 Gaussmeter, add `/etc/udev/rules.d/52-lakeshore425.rules` containing:

```none
SUBSYSTEMS=="usb",ATTRS{idVendor}=="1fb9",ATTRS{idProduct}=="0401",MODE="0666",SYMLINK+="lakeshore425"

```

Afterwards, reload the udev rules using:

```bash
sudo udevadm control --reload-rules
sudo udevadm trigger

```

Access the device at `/dev/lakeshore425`.
