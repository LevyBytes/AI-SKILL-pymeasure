# pymeasure.instruments.hp.hp856Xx.HP856Xx.errors

HP856Xx.errors

Return current errors as a list of `ErrorCode` values. An empty list indicates no errors. Reading ‘errors’ clears all HP-IB errors. Query for error data immediately after checking errors for best results.

Type: `ErrorCode`

```python
from pymeasure.instruments.hp.hp856Xx import ErrorCode

errors = instr.errors
if len(errors) > 0:
    print(errors[0].code)

for error in errors:
    print(error)

if ErrorCode(112) in errors:
    print("yeah")

```

Example output produced by this python snippet:

```text
112
ErrorCode("??CMD?? - Unrecognized command")
ErrorCode("NOP NUM - Command cannot have numeric units")
yeah

```
