# pymeasure.instruments.advantest.advantestR624X.AdvantestR624X.clear_highspeed_sequence

[Owning PyMeasure class, adapter and connection contract](overview.md)

clear_highspeed_sequence(*program_number*, *clear_mode*)

Clear one or more programs from high-speed sequence memory (`PCEL`).

Parameters:

- **program_number** (*int*) – Program number from 1 to 20.

- **clear_mode** (int or `ProgramClearMode`) – Clear mode selector.

Clear modes:

1. Clear only the selected program number.

2. Clear the selected program number plus every later program.
