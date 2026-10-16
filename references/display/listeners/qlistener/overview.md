# pymeasure.display.listeners.QListener

*class *pymeasure.display.listeners.QListener(*port*, *topic=''*, *timeout=0.01*)

Bases: [`StoppableQThread`](https://pymeasure.readthedocs.io/en/latest/api/display/thread.html#pymeasure.display.thread.StoppableQThread)

Base class for QThreads that listen for messages on a ZMQ TCP port and support stopping through a thread- and process-safe method call.
