# pymeasure.instruments.racal.Racal1992.channel_settings

[Owning PyMeasure class, adapter and connection contract](overview.md)

channel_settings(*channel_name*, ***settings*)

Set channel configuration parameters.

Parameters:

- **channel_name** – ‘A’ or ‘B’

- **settings** –

one or more of these entries:

Any of these may be supplied: ’coupling’ can be ‘AC’ or ‘DC’; ‘attenuation’ can be ‘X1’ or ‘X10’; ‘trigger’ can be ‘auto’ or ‘manual’; ‘impedance’ can be ‘50’ or ‘1M’; ‘slope’ can be ‘pos’ or ‘neg’; ‘filtering’ can be True or False (only allowed for channel A); ‘input_select’ can be ‘separate’ or ‘common’ (only allowed for channel B); ‘trigger_level’ uses &lt;floating point number&gt;
