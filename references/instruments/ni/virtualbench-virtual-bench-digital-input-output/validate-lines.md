# pymeasure.instruments.ni.virtualbench.VirtualBench.DigitalInputOutput.validate_lines

[Owning DigitalInputOutput contract](overview.md)

validate_lines(*lines*, *return_single_lines=False*, *validate_init=False*)

Validate lines string Allowed patterns (case sensitive):
- `'VBxxxx-xxxxxxx/dig/0:7'`

- `'VBxxxx-xxxxxxx/dig/0'`

- `'dig/0'`

- `'VBxxxx-xxxxxxx/trig'`

- `'trig'`

Allowed Line Numbers: 0-7 or trig

Parameters:

- **lines** (*str*) — Line string being checked

- **return_single_lines** (*bool**, **optional*) — Also return a list of line numbers, defaults to False (default: `False`)

- **validate_init** (*bool**, **optional*) — Verify that lines are initialized in `self._line_numbers`, defaults to False (default: `False`)

Returns:

Line string, with optional single-line-number list

Return type:

str, optional (str, list)
