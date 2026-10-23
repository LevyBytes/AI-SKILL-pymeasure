# pymeasure.instruments.advantest.advantestR624X.AdvantestR624X.set_output_format - set_output_format signature, delimiters and terminator selection

[Owning PyMeasure class, adapter and connection contract](overview.md) / [set_output_format complete four header-character tables](output-format-headers.md)

set_output_format(*delimiter_format*, *block_delimiter*, *terminator*)

Configure the GPIB output data format and terminator (`FMT`).

Parameters:

- **delimiter_format** (*int*) – Delimiter format type

- **block_delimiter** (*int*) – Block delimiter type

- **terminator** (*int*) – Termination character type

&lt;EOI&gt; (End or Identify) is output at these timings: 1,2: at the same time as LF 4: at the same time as the last output data

When binary format is selected for output data, the terminator is fixed to &lt;EOI&gt; only, so the terminator selection is ignored.

delimiter_format:
1. ASCII format with header

2. No header, ASCII format

3. Binary format

block_delimiter:
1. Use the same setting as the terminator.

2. Use semicolon ;

3. Use comma ,

terminator:
1. CR, LF&lt;EOI&gt;

2. LF&lt;EOI&gt;

3. LF

4. &lt;EOI&gt;
