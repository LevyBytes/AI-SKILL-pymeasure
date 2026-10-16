# pymeasure.instruments.velleman.VellemanK8090.status

[Owning PyMeasure class, adapter and connection contract](overview.md)

*property *status*: Any*

Return the present relay status; the response command byte differs from the request.

Returns three `VellemanK8090Switches` flag values:

- Previous state: every relay's state before this event

- Current state: every relay's present state

- Timer state: every relay timer's state
