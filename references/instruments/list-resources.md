# pymeasure.instruments.list_resources

pymeasure.instruments.list_resources()

Print the available resources and return a list of VISA resource names

```python
resources = list_resources()
#prints (e.g.)
    #0 : GPIB0::22::INSTR : Agilent Technologies,34410A,******
    #1 : GPIB0::26::INSTR : Keithley Instruments Inc., Model 2612, *****
dmm = Agilent34410(resources[0])

```
