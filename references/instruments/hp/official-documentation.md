# instruments - hp documentation links

- [Hewlett Packard](https://pymeasure.readthedocs.io/en/latest/api/instruments/hp/index.html)
- [HP 33120A arbitrary waveform generator](https://pymeasure.readthedocs.io/en/latest/api/instruments/hp/hp33120A.html)
- [HP 34401A multimeter](https://pymeasure.readthedocs.io/en/latest/api/instruments/hp/hp34401A.html)
- [HP 3437A system voltmeter](https://pymeasure.readthedocs.io/en/latest/api/instruments/hp/hp3437A.html)
- [HP 3478A multimeter](https://pymeasure.readthedocs.io/en/latest/api/instruments/hp/hp3478A.html)
- [HP 8116A 50 MHz pulse and function generator](https://pymeasure.readthedocs.io/en/latest/api/instruments/hp/hp8116A.html)
- [HP 8560A / 8561B spectrum analyzer](https://pymeasure.readthedocs.io/en/latest/api/instruments/hp/hp856xx.html)
- [HP Signal generator HP8657B](https://pymeasure.readthedocs.io/en/latest/api/instruments/hp/hp8657B.html)
- [HP 8753E Vector Network Analyzer](https://pymeasure.readthedocs.io/en/latest/api/instruments/hp/hp8753E.html)
- [HP 11713A attenuator and switch driver](https://pymeasure.readthedocs.io/en/latest/api/instruments/hp/hp11713A.html)
- [HP 437B Power Meter](https://pymeasure.readthedocs.io/en/latest/api/instruments/hp/hp437B.html)
- [Support class for legacy HP devices](https://pymeasure.readthedocs.io/en/latest/api/instruments/hp/hplegacyinstrument.html)
- [HP System Power Supplies HP663XA](https://pymeasure.readthedocs.io/en/latest/api/instruments/hp/hpsystempsu.html)

Covers: HP Signal generator HP8657B; HP System Power Supplies HP663XA.

## HP Signal generator HP8657B

### HP Signal generator HP8657B

*Note:*
- Because the instrument is a listen-only GPIB device, it cannot read values back.
- The dynamic ranges feature could support implementations for other instruments in this family.
- Support is not yet present for the optional pulse modulation feature.

Glossary:

| Abbreviation | Explanation |
| --- | --- |
| AM | Amplitude Modulation |
| FM | Frequency Modulation |
| dBm | power level, expressed in dB referenced to 1mW |

Currently supported models are:

| Model | Voltage | Current | Power |
| --- | --- | --- | --- |
| 6632A | 0..20 V | 0..5.0 A | 100 W |
| 6633A | 0..50 V | 0..2.5 A | 100 W |
| 6634A | 0..100 V | 0..1.0 A | 100 W |

*Note:*
- Some command syntax is shared by HP 6621A, 6622A, 6623A, 6624A, 6625A, 6626A, 6627A & 6628A multi-channel system power supplies; this implementation could probably incorporate them.
- The B-version models (6632B, 6633B & 6634B) are SPCI-compliant, so a similar implementation approach could cover them.

Use base units for all values: time in s (Seconds), frequency in Hz (Hertz), and so on…

This implementation is currently used for these instruments, which lack SCPI support:
- HP3437A System-Voltmeter
- HP3478A Digital Multimeter
- HP6632/33/34A System power supply

Covers: Hewlett Packard; HP 8753E Vector Network Analyzer.

## Hewlett Packard

### Hewlett Packard

Use this section for documentation on the implemented Hewlett Packard instruments. For an instrument that is missing here, consider [adding the instrument](https://pymeasure.readthedocs.io/en/latest/dev/adding_instruments/index.html).

When the instrument you need is absent from this page, also look under [Agilent](https://pymeasure.readthedocs.io/en/latest/api/instruments/agilent/index.html) or [Keysight](https://pymeasure.readthedocs.io/en/latest/api/instruments/keysight/index.html) for newer instruments.
- [HP 33120A Arbitrary Waveform Generator](https://pymeasure.readthedocs.io/en/latest/api/instruments/hp/hp33120A.html)
- [`HP33120A`](https://pymeasure.readthedocs.io/en/latest/api/instruments/hp/hp33120A.html#pymeasure.instruments.hp.HP33120A)
- [HP 34401A Multimeter](https://pymeasure.readthedocs.io/en/latest/api/instruments/hp/hp34401A.html)
- [`HP34401A`](https://pymeasure.readthedocs.io/en/latest/api/instruments/hp/hp34401A.html#pymeasure.instruments.hp.HP34401A)
- [HP 3437A System-Voltmeter](https://pymeasure.readthedocs.io/en/latest/api/instruments/hp/hp3437A.html)
- [`HP3437A`](https://pymeasure.readthedocs.io/en/latest/api/instruments/hp/hp3437A.html#pymeasure.instruments.hp.HP3437A)
- [HP 3478A Multimeter](https://pymeasure.readthedocs.io/en/latest/api/instruments/hp/hp3478A.html)
- [`HP3478A`](https://pymeasure.readthedocs.io/en/latest/api/instruments/hp/hp3478A.html#pymeasure.instruments.hp.HP3478A)
- [HP 8116A 50 MHz Pulse/Function Generator](https://pymeasure.readthedocs.io/en/latest/api/instruments/hp/hp8116A.html)
- [`HP8116A`](https://pymeasure.readthedocs.io/en/latest/api/instruments/hp/hp8116A.html#pymeasure.instruments.hp.HP8116A)
- [HP 8560A / 8561B Spectrum Analyzer](https://pymeasure.readthedocs.io/en/latest/api/instruments/hp/hp856xx.html)
- [Generic Specific Attributes & Methods](https://pymeasure.readthedocs.io/en/latest/api/instruments/hp/hp856xx.html#generic-specific-attributes-methods)
- [HP8560A Specific Attributes & Methods](https://pymeasure.readthedocs.io/en/latest/api/instruments/hp/hp856xx.html#hp8560a-specific-attributes-methods)
- [HP8561B Specific Attributes & Methods](https://pymeasure.readthedocs.io/en/latest/api/instruments/hp/hp856xx.html#hp8561b-specific-attributes-methods)
- [Enumerations](https://pymeasure.readthedocs.io/en/latest/api/instruments/hp/hp856xx.html#enumerations)
- [`HP8657B`](https://pymeasure.readthedocs.io/en/latest/api/instruments/hp/hp8657B.html#pymeasure.instruments.hp.HP8657B)
- [`HP8753E`](https://pymeasure.readthedocs.io/en/latest/api/instruments/hp/hp8753E.html#pymeasure.instruments.hp.HP8753E)
- [HP 11713A Attenuator/Switch Driver](https://pymeasure.readthedocs.io/en/latest/api/instruments/hp/hp11713A.html)
- [`HP11713A`](https://pymeasure.readthedocs.io/en/latest/api/instruments/hp/hp11713A.html#pymeasure.instruments.hp.HP11713A)
- [`SwitchDriverChannel`](https://pymeasure.readthedocs.io/en/latest/api/instruments/hp/hp11713A.html#pymeasure.instruments.hp.hp11713a.SwitchDriverChannel)
- [`Attenuator_11dB`](https://pymeasure.readthedocs.io/en/latest/api/instruments/hp/hp11713A.html#pymeasure.instruments.hp.hp11713a.Attenuator_11dB)
- [`Attenuator_110dB`](https://pymeasure.readthedocs.io/en/latest/api/instruments/hp/hp11713A.html#pymeasure.instruments.hp.hp11713a.Attenuator_110dB)
- [`Attenuator_70dB_3_Section`](https://pymeasure.readthedocs.io/en/latest/api/instruments/hp/hp11713A.html#pymeasure.instruments.hp.hp11713a.Attenuator_70dB_3_Section)
- [`Attenuator_70dB_4_Section`](https://pymeasure.readthedocs.io/en/latest/api/instruments/hp/hp11713A.html#pymeasure.instruments.hp.hp11713a.Attenuator_70dB_4_Section)
- [`HP437B`](https://pymeasure.readthedocs.io/en/latest/api/instruments/hp/hp437B.html#pymeasure.instruments.hp.HP437B)
- [Support class for HP legacy devices](https://pymeasure.readthedocs.io/en/latest/api/instruments/hp/hplegacyinstrument.html)
- [`HPLegacyInstrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/hp/hplegacyinstrument.html#pymeasure.instruments.hp.HPLegacyInstrument)
- [`HP6632A`](https://pymeasure.readthedocs.io/en/latest/api/instruments/hp/hpsystempsu.html#pymeasure.instruments.hp.HP6632A)
- [`HP6633A`](https://pymeasure.readthedocs.io/en/latest/api/instruments/hp/hpsystempsu.html#pymeasure.instruments.hp.HP6633A)
- [`HP6634A`](https://pymeasure.readthedocs.io/en/latest/api/instruments/hp/hpsystempsu.html#pymeasure.instruments.hp.HP6634A)
