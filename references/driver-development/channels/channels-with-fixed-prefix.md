# Channels with fixed prefix

Override a channel's `insert_id()` method when every command for that channel must carry a fixed prefix, such as `"SOURceA:"` for channel A. This is especially useful when only one channel uses that type, for example because it represents one instrument function rather than another.

```python
class VoltageChannelPrefix(Channel):
    """A channel of a voltage source, every command has the same prefix."""

    def insert_id(self, command):
        return f"SOURce{self.id}:{command}"

    voltage = Channel.control(
        "VOLT?", "VOLT %g",
        """Control the output voltage of this channel.""",
    )

```

This channel class performs the same communication as the earlier example, but the channel prefix is handled inside `insert_id()` instead of being repeated in each property created by `control()`.
