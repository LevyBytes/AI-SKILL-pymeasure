# pymeasure.instruments.velleman.VellemanK8090.read

[Owning PyMeasure class, adapter and connection contract](overview.md)

read(***kwargs*)

Read command tailored to the K8090 protocol.

Overrides the corresponding method from the `instrument` class.

Refer to `write()`; device replies follow the same format.

Reading returns CMD, MASK, PARAM1, and PARAM2 as a list.
