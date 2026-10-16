# pymeasure.instruments.advantest.advantestR624X.SMUChannel.trigger_input

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *trigger_input*: Any*

Configure the trigger input type (`TJM`).

Type:

`TriggerInputType`

| Trigger input types | 1 | 2 | 3 |
| --- | --- | --- | --- |
| *TRG | O | O | X |
| XE 0 | O | O | X |
| XE Channel | O | O | O |
| GET | O | O | X |
| Trigger input signal | O | X | X |

O is usable, X is not usable

Note

The trigger input signal cannot start sweep operation. Start it with the ‘XE’ command; after that, a trigger input signal can advance the sweep.
