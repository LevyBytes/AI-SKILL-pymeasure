# pymeasure.instruments.hp.HP3437A.trigger

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *trigger

Return the currently selected trigger mode; this property is settable.

Possible values are:

| Value | Explanation |
| --- | --- |
| internal | automatic trigger (internal) |
| external | external trigger (back connector or GET) |
| hold/manual | holds the measurement or issues a manual trigger |
