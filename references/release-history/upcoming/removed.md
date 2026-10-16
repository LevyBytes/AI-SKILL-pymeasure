# Upcoming release — Removed

- GUI packages are no longer part of the default dependency set. To include the GUI extras, install PyMeasure with `pip install pymeasure[gui]`; Conda installations continue to include every dependency.

- The deprecated `control` arguments `command_process` and `kwargs` have been removed.

- For Toptica Ibeamsmart, the deprecated methods `laser_enabled`, `channel1_enabled`, and `channel2_enabled` were removed; use `emission` together with the driver channels.
