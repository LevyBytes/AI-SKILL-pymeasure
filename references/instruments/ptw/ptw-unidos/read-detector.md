# pymeasure.instruments.ptw.ptwUNIDOS.read_detector

[Owning PyMeasure class, adapter and connection contract](overview.md)

read_detector(*guid='ALL'*)

Read properties for the requested detector.

Parameters:

**guid** (*str*) - optional detector ID. If *guid* is not provided, returns every detector.

Type:

dict or list[dict]

Dict keys:

`calibrationFactor`, `calibrationFactorUnit`, `calibrationLab`, `calibrationProcedure`, `calibrationTemp`, `calibrationType`, `calibrationUser`, `comment`, `guid`, `manufacturer`, `maxHv`, `measuredQuantity`, `minHv`, `name`, `nominalHv`, `polarity`, `radiationQuality`, `range`, `serialNumber`, `testDate`, `testLimits`, `testResult`, `testTarget`, `timebase`, `type`, `typeNumber`

Return type:

`Union`[`dict`, `list`[`dict`]]
