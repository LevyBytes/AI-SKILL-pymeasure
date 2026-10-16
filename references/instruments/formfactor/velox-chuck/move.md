# pymeasure.instruments.formfactor.velox.Chuck.move

[Owning PyMeasure class, adapter and connection contract](overview.md)

move(*x*, *y*, *pos_ref='home'*, *unit='microns'*, *velocity=100*)

Move the chuck by the requested distance.

Parameters:

- **x** (*float*) - Distance in X direction

- **y** (*float*) - Distance in Y direction

- **pos_ref** (*str*) - Position reference, strictly `home`, `zero`, `center` or `diehome`.

- **unit** (*str*) - Unit for **x** and **y**, strictly `micron`, `mils`, `jogs`, `encoder` or `index`.

- **velocity** (*float*) - Speed in percent, strictly from `0.1` to `100`.
