# pymeasure.instruments.formfactor.velox.Chuck.move_index

[Owning PyMeasure class, adapter and connection contract](overview.md)

move_index(*x_steps*, *y_steps*, *pos_ref='home'*, *velocity=100*)

Move the chuck by index steps.

Parameters:

- **x_steps** (*int*) - Index steps in X direction

- **y_steps** (*int*) - Index steps in Y direction

- **pos_ref** (*str*) - Position reference, strictly `home`, `zero`, `center` or `diehome`.

- **velocity** (*float*) - Speed in percent, strictly from `0.1` to `100`.
