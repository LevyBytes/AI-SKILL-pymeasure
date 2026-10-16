# pymeasure.experiment.listeners.Listener

*class *pymeasure.experiment.listeners.Listener(*port*, *topic=''*, *timeout=0.01*)

Bases: `StoppableThread`

Base class for Threads that listen on a ZMQ TCP port for incoming messages and support stopping through a thread-safe method call.
