# pymeasure.experiment.listeners.Recorder

*class *pymeasure.experiment.listeners.Recorder(*results*, *queue*, ***kwargs*)

Bases: `QueueListener`

Recorder reads the initial Results for a filepath and appends data received over a queue. The queue prevents data loss between the Recorder and Worker.
