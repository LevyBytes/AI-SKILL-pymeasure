# pymeasure.instruments.advantest.advantestR624X.SMUChannel.select_for_output

[Owning PyMeasure class, adapter and connection contract](overview.md)

select_for_output()

Choose this channel as the source for measurement data output (`FCH?`).

Issues the FCH? query to choose the channel whose measurement data is returned. After that, call `read_measurement()` to retrieve the value.

The instrument manual recommends this sequence:

```python
smu.ch_A.select_for_output()   # Select channel A
smu.trigger()                   # Trigger measurement
value = smu.read_measurement()  # Read channel A data

```

If a prior trigger has already produced data, use this sequence instead:

```python
smu.ch_B.select_for_output()   # Switch to channel B
value = smu.read_measurement()  # Read channel B data

```

Note

Using the RMM command to read measurements does not change the channel chosen by the FCH command. By default, channel A measurement data is returned.
