# Keithley 2400 scripted IV measurement workflow

[Complete Keithley 2400 IV measurement script](keithley2400-iv-script.md) / [Script measurement limitations and Procedure transition](script-to-procedure-transition.md)

A script is the fastest starting point for a PyMeasure measurement. For the IV characteristic example, use this sequence:

1. Import the necessary packages

2. Choose the input parameters that define the measurement

3. Configure source_current and measure_voltage parameters

4. Connect to the Keithley 2400

5. Configure the instrument for the IV characteristic

6. Create arrays for storing measured results

7. Iterate over current points, take the voltage reading, and record it

8. Write the completed data set to a CSV file

9. Shutdown the instrument

The same workflow appears in code below.
