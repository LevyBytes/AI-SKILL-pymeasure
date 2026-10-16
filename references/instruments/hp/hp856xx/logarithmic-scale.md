# pymeasure.instruments.hp.hp856Xx.HP856Xx.logarithmic_scale

HP856Xx.logarithmic_scale

Set or query the logarithmic amplitude scale. In linear mode, querying ‘logarithmic_scale’ returns “0”. Allowed values are 0, 1, 2, 5, 10.

Type: `int`

```python
if instr.logarithmic_scale:
    pass

# set the scale to 10 db per division
instr.logarithmic_scale = 10

```
