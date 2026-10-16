# pymeasure.instruments.eurotest.EurotestHPP120256

*class *pymeasure.instruments.eurotest.EurotestHPP120256(*adapter*, *name='Euro Test High Voltage DC Source model HPP-120-256'*, *query_delay=0.1*, *write_delay=0.4*, *timeout=5000*, ***kwargs*)

Bases: [`Instrument`](https://pymeasure.readthedocs.io/en/latest/api/instruments/instruments.html#pymeasure.instruments.Instrument)

Provides a high-level interface for the Euro Test High Voltage DC Source model HPP-120-256 using the Euro Test command set rather than the SCPI command set.

```python
from pymeasure.instruments.eurotest.eurotestHPP120256 import EurotestHPP120256

hpp120256 = EurotestHPP120256("GPIB0::20::INSTR")

print(hpp120256.id)
print(hpp120256.lam_status)
print(hpp120256.status)

hpp120256.ramp_to_zero(100.0)

hpp120256.voltage_ramp = 50.0  # V/s
hpp120256.current_limit = 2.0  # mA
inst.kill_enabled = True  # Enable over-current protection
time.sleep(1.0)  # Give time to enable kill
inst.output_enabled = True
time.sleep(1.0)  # Give time to output on

abs_output_voltage_error = 0.02 # kV

hpp120256.wait_for_output_voltage_reached(abs_output_voltage_error, 1.0, 40.0)

# Here voltage HV output should be at 0.0 kV

print("Setting the output voltage to 1.0kV...")
hpp120256.voltage_setpoint = 1.0  # kV

# Now HV output should be rising to reach the 1.0kV at 50.0 V/s

hpp120256.wait_for_output_voltage_reached(abs_output_voltage_error, 1.0, 40.0)

# Here voltage HV output should be at 1.0 kV

hpp120256.shutdown()

hpp120256.wait_for_output_voltage_reached(abs_output_voltage_error, 1.0, 60.0)

# Here voltage HV output should be at 0.0 kV

inst.output_enabled = False

# Now the HV voltage source is in safe state

```
