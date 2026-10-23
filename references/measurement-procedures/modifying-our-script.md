# Modifying our script

With the Procedure class features and execution model covered, return to the IV characteristic measurement and rewrite it with Procedures. The example below shows the revised script as a IVProcedure class.

The complete program is in the [upstream source](https://raw.githubusercontent.com/pymeasure/pymeasure/08c4a91f5255c937a909cc21e70fa3fafd76333e/docs/tutorial/procedure.rst).

Parentheses in `COLUMN` entries declare the physical unit for that column. For example, `'Voltage Std (V)'` declares Volts. For a dimensionless value such as Mach number, use (1). Compound units such as (m/s) or the long form (meter/second) are accepted too. The class `Results` stores data using the declared unit; in this case the unit is Volts. A `pint.Quantity` of 500 mV, for instance, is stored as 0.5 V. Strings are converted to a Quantity first, while plain numbers such as float or int are treated as already using the correct unit. Thus 5 is stored as 5 V. If a value is incompatible, either because its unit is wrong, such as meters for a voltage column, or because the value is not numeric, a warning is logged and ‘nan’ is written to the file. When no unit is given, meaning there are no parentheses, that column is not unit-checked unless a Quantity is later provided for it. In that case, the column unit becomes the base unit of the supplied value, such as meter for a value in kilometers, and later entries in the column are unit-checked. Use columns without unit checks, meaning without parentheses, for strings or booleans as well.

You now know how to build a Procedure sub-class. The next section uses those procedures in a graphical environment with live-plotting and simple queuing for multiple experiments. Those capabilities come from the Procedure object.
