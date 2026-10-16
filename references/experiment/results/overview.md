# pymeasure.experiment.results.Results

*class *pymeasure.experiment.results.Results(*procedure*, *data_filename*)

The Results class offers an interface for data reads and writes tied to a [`Procedure`](https://pymeasure.readthedocs.io/en/latest/api/experiment/procedure.html#pymeasure.experiment.procedure.Procedure) object.

Variables:

- **COMMENT** - Character that marks a comment (default: #)

- **DELIMITER** - Character separating data fields (default: ,)

- **LINE_BREAK** - Character inserted for line breaks (default n)

- **CHUNK_SIZE** - Length of the data chunk to read

Parameters:

- **procedure** – Procedure object

- **data_filename** - Data filename where data is already stored or should be stored
