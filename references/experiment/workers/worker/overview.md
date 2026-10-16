# pymeasure.experiment.workers.Worker

*class *pymeasure.experiment.workers.Worker(*results*, *log_queue=None*, *log_level=20*, *port=None*)

Bases: `StoppableThread`

Worker executes the procedure and publishes procedure/status details through a ZMQ TCP port. In a child thread, a Recorder runs to write the results to
