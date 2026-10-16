# pymeasure.instruments.hp.HP8561B.conversion_loss

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *conversion_loss*: Any*

Set the loss compensation used outside the instrument in external mixer mode, including connector-cable losses, external mixers, etc. `conversion_loss` gives the mean conversion loss for the current harmonic band. For a full frequency band, such as band K, compute the mean conversion loss by adding that band's minimum loss and maximum loss, then dividing by two. Applying this conversion-loss adjustment keeps the system calibrated, so displayed amplitude values include the conversion loss. The default for any band is 30 dB. This command works only when the spectrum analyzer is in external-mixer mode. In internal-mixer mode, a `conversion_loss` query returns a zero.
