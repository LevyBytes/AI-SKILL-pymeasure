# pymeasure.instruments.anaheimautomation.DPSeriesMotorController.wait_for_completion

[Owning PyMeasure class, adapter and connection contract](overview.md)

wait_for_completion(*interval=0.5*)

Block while the controller remains "busy"; in other words, wait until the motor stops moving.

Parameters:

**interval** - (float) seconds to wait between queries of the "busy" flag. (default: `0.5`)

Returns:

None
