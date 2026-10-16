# pymeasure.instruments.advantest.advantestR624X.AdvantestR624X.store_highspeed_sequence

[Owning PyMeasure class, adapter and connection contract](overview.md)

store_highspeed_sequence(*program_number*, *command*)

Store commands under a high-speed sequence program number (`PGST~;END`).

Parameters:

- **program_number** (*int*) – Program number from 1 to 20.

- **command** (*str*) – Command string to store; commands are separated by semicolons.

Note

Do not call this method while a standard sequence is being built, meaning between `init_sequence()` and `end_sequence()`, because the standard sequence system will intercept the write.
